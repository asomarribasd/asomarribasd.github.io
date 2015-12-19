---
layout: post
title:  "Tablas Pivote en tus querys con SQL!"
date:   2015-12-17 18:00:00
categories: ["MSSQL"]
tags: [MSSQL, "Data Science"]
---


## Que es una tabla pivote?


En el procesamiento de datos, una tabla pivote es una herarmienta de sumarizacion y visualizacion de datos. Se puede encontrar en herramientas de "Inteligencia de Negocios". Tambien pueden buscar los terminos "tabulacion cruzada". Si quieren pensarlo en una forma simple, imaginense reordenar una tabla, donde las columnas se convierten en lineas y las lineas se agrupan(sumatoria, average, etc) para poder desplegarse. 

Por que hacemos esto? Bueno datos son datos y solo sirven de algo si tienen algun sentido para alguien, por lo tanto tu trabajo es ordenar esos datos de la manera que tenga mas sentido para el usario, que le sea mas facil asimilar la informacion. 

No quiero adentrarme mucho por que problablemente ya conozcan los terminos, pero de no ser asi, siempre tenemos a wikipedia:

Definiciones Wikipedia [aqui](https://es.wikipedia.org/wiki/Tabla_din%C3%A1mica) y en ingles [aqui](https://en.wikipedia.org/wiki/Pivot_table)


## Requisitos


Para seguir este ejemplo necesitaran MS SQL por supuesto, pueden usar la version express. Les dejo el link a MS-SQL aqui si no lo tienen. Tambien les dejo el link a la base de datos de AdventureWorks, buscaremos por ahi algo que podamos usar para el ejemplo.

[MS-SQL](https://msdn.microsoft.com/library/mt590198.aspx)
[AdventureWorks Base de datos de ejemplo](http://msftdbprodsamples.codeplex.com/)


## La expresion PIVOT 


Iniciemos con la sintaxis de PIVOT, la obtuve de MSDN y le traduje los comentarios.

{% highlight sql %}

SELECT <non-pivoted column>,
    [primera columna pivoteada] AS <column name>,
    [segunda columna pivoteada] AS <column name>,
    ...
    [ultima columna pivoteada] AS <column name>
FROM
    (<SELECT query that produces the data>)
    AS <alias for the source query>
PIVOT
(
    <aggregation function>(<column being aggregated>)
FOR
[<column that contains the values that will become column headers>]
    IN ( [first pivoted column], [second pivoted column],
    ... [last pivoted column])
) AS <alias for the pivot table>
<optional ORDER BY clause>;

{% endhighlight %}


## Sobre los datos


Para Nuestro ejemplo utilizaremos solo dos tablas:

`[AdventureWorks2012].[Sales].[SalesOrderHeader]`
`[AdventureWorks2012].[Person].[Person]`


#### Revisas la estructura y encuentras:


{% highlight sql %}

SELECT COLUMN_NAME, DATA_TYPE 
FROM INFORMATION_SCHEMA.COLUMNS c
WHERE c.TABLE_SCHEMA = 'Person' 
	AND TABLE_NAME = 'Person'

{% endhighlight %}

|BusinessEntityID|int|
|PersonType|nchar|
|NameStyle|bit|
|Title|nvarchar|
|FirstName|nvarchar|
|MiddleName|nvarchar|
|LastName|nvarchar|
|Suffix|nvarchar|
|EmailPromotion|int|
|AdditionalContactInfo|xml|
|Demographics|xml|
|rowguid|uniqueidentifier|
|ModifiedDate|datetime|

{% highlight sql %}

SELECT COLUMN_NAME, DATA_TYPE 
FROM INFORMATION_SCHEMA.COLUMNS c
WHERE c.TABLE_SCHEMA = 'Sales' 
	AND TABLE_NAME = 'SalesOrderHeader'

{% endhighlight %}


|SalesOrderID|int|
|RevisionNumber|tinyint|
|OrderDate|datetime|
|DueDate|datetime|
|ShipDate|datetime|
|Status|tinyint|
|OnlineOrderFlag|bit|
|SalesOrderNumber|nvarchar|
|PurchaseOrderNumber|nvarchar|
|AccountNumber|nvarchar|
|CustomerID|int|
|SalesPersonID|int|
|TerritoryID|int|
|BillToAddressID|int|
|ShipToAddressID|int|
|ShipMethodID|int|
|CreditCardID|int|
|CreditCardApprovalCode|varchar|
|CurrencyRateID|int|
|SubTotal|money|
|TaxAmt|money|
|Freight|money|
|TotalDue|money|
|Comment|nvarchar|
|rowguid|uniqueidentifier|
|ModifiedDate|datetime|


## Un Ejemplo


Imaginense esto, estas tranquilamente tomando cafe cuando se te hacerca el gerente de ventas y te comenta que quiere conocer cuanto venden sus vendedores anualmente, te quedas pensa, para que carajos quiere esto y pues bueno como no te da trabajo le dice que si que con gusto le envias las ventas. Vas a tu escritorio y haces algo como esto (Y si lo haces en produccion te traes abajo el servidor)

{% highlight sql %}

SELECT P.FirstName + ' ' + P.LastName AS [Vendedor], 
		year(OrderDate) AS 'year', 
		SUM([TotalDue]) as [TotalVentas]
FROM	[AdventureWorks2012].[Sales].[SalesOrderHeader] Sales 
		INNER JOIN [AdventureWorks2012].Person.[Person] P 
		ON P.BusinessEntityID = Sales.SalesPersonID
GROUP BY P.FirstName + ' ' + P.LastName, 
		year(OrderDate)

{% endhighlight %}

Le envias los dato y te responde, si esa es la informacion que ocupaba muchas pero ... mem podria acomodar las ventas totales en columnas, es que ocupamos comparar el rendimiento de los vendedores. Y bueno hasta ahi te llega la sonrisa. Inicialmente podrias tener dos opciones:

Tomar un cursor y ordenar los datos en una forma manual usando una tabla temporal con  las columnas. O crear un query con la sumarizacion de cada columna y luego unirlos todos.
Cualquiera que sea la opcion es bastante costosa en terminos de recursos y hace que un reporte que en teoria no deberia se dificil de obtener se vuelva una tarea campal.

Por suerte ya podemos expresar esta tabla pivote en una forma mas rapida y menos costosa.

Noten que la seleccion inicial esta anidada dentro de otra que simplemente lista todo. Esto se debe a que de otra manera al revisar tu query el compilador no encuentra las columnas compuestas. Yo tengo varias, primero para obtener el nombre del vendedor y segundo para mostrar el mes de la venta. No tienen que estar sumadas. PIVOT se encarga de definir las columnas a mostrar, que son daos que tienen que estar en una delas columanas y a sumarizar. El resto de las columnas que se utilizen seran las primeras columans en esta tabla pivote.

{% highlight sql %}

SELECT * FROM (
	SELECT	P.FirstName + ' ' + P.LastName AS [Vendedor], 
			year(OrderDate) AS 'year', 
			[TotalDue] as [TotalVenta]
	FROM	[AdventureWorks2012].[Sales].[SalesOrderHeader] Sales 
			INNER JOIN [AdventureWorks2012].[Person].[Person] P 
			ON P.BusinessEntityID = Sales.SalesPersonID
 ) AS Ventas
PIVOT (
	SUM (TotalVenta)
	FOR [year] in ([2005], [2006], [2007], [2008])
	) as [MontoVentasAnuales]


{% endhighlight %}


El resultado:


|Vendedor			|2005			|2006			|2007			|2008|
|-------------		|-------------	|-------------	|-------------	|-------------|
|Amy Alberts		|NULL			|97271.0569		|617725.2728	|111421.137|
|David Campbell		|570467.7098	|1327676.9362	|1549495.7049	|760254.2516|
|Garrett Vargas		|532111.8814	|1340859.9994	|1554236.1881	|642214.142|
|Jae Pak			|NULL			|2842719.9744	|4705252.1691	|2037152.8042|
|Jillian Carson		|1404871.479	|4286904.7229	|4104089.9192	|1546519.7757|
|José Saraiva		|1170079.0677	|2045617.8737	|2075082.0159	|1392757.701|
|Linda Mitchell		|1288179.9682	|3653236.6626	|4626811.8662	|2126790.5635|
|Lynn Tsoflias		|NULL			|NULL			|795341.1682	|811100.2789|
|Michael Blythe		|846580.2377	|3470328.7471	|4425590.0827	|1732868.0076|
|Pamela Ansman-Wolfe|684031.4513	|1326617.7801	|1004700.5413	|732896.3491|
|Rachel Valdez		|NULL			|NULL			|1107155.8886	|955237.2485|
|Ranjit Varkey Chudukatil|NULL		|956325.5603	|2582651.4735	|1549000.1782|
|Shu Ito			|999685.163		|2406552.1732	|2641228.7519	|1212101.788|
|Stephen Jiang		|32567.9155		|406620.0734	|515622.909		|281123.5472|
|Syed Abbas			|NULL			|NULL			|165622.0321	|29906.7517|
|Tete Mensa-Annan	|NULL			|288368.6887	|1376371.1384	|943376.5484|
|Tsvi Reiter		|1555332.8072	|2798718.4618	|2505390.5003	|1226631.9068|



[Ejemplo en MSDN](https://technet.microsoft.com/en-us/library/ms177410(v=sql.105).aspx)
[Otro Ejemplo](http://blogs.msdn.com/b/spike/archive/2009/03/03/pivot-tables-in-sql-server-a-simple-sample.aspx)

Bueno ya saben. Experimentando se aprende!

