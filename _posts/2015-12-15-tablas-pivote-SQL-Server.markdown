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

'[AdventureWorks2012].[Sales].[SalesOrderHeader]'
'Person.[Person]'

#### Revisas la estructura y encuentras:


{% highlight sql %}


SELECT COLUMN_NAME, DATA_TYPE 
FROM INFORMATION_SCHEMA.COLUMNS c
WHERE c.TABLE_SCHEMA = 'Person' 
	AND TABLE_NAME = 'Person'

{% endhighlight %}

BusinessEntityID	int
PersonType	nchar
NameStyle	bit
Title	nvarchar
FirstName	nvarchar
MiddleName	nvarchar
LastName	nvarchar
Suffix	nvarchar
EmailPromotion	int
AdditionalContactInfo	xml
Demographics	xml
rowguid	uniqueidentifier
ModifiedDate	datetime


{% highlight sql %}

SELECT COLUMN_NAME, DATA_TYPE 
FROM INFORMATION_SCHEMA.COLUMNS c
WHERE c.TABLE_SCHEMA = 'Sales' 
	AND TABLE_NAME = 'SalesOrderHeader'

{% endhighlight %}

SalesOrderID	int
RevisionNumber	tinyint
OrderDate	datetime
DueDate	datetime
ShipDate	datetime
Status	tinyint
OnlineOrderFlag	bit
SalesOrderNumber	nvarchar
PurchaseOrderNumber	nvarchar
AccountNumber	nvarchar
CustomerID	int
SalesPersonID	int
TerritoryID	int
BillToAddressID	int
ShipToAddressID	int
ShipMethodID	int
CreditCardID	int
CreditCardApprovalCode	varchar
CurrencyRateID	int
SubTotal	money
TaxAmt	money
Freight	money
TotalDue	money
Comment	nvarchar
rowguid	uniqueidentifier
ModifiedDate	datetime	

## Un Ejemplo

Imaginense esto, estas tranquilamente tomando cafe cuando se te hacerca el gerente de ventas y te comenta que quiere conocer cuanto venden sus vendedores anualmente, te quedas pensa, para que carajos quiere esto y pues bueno como no te da trabajo le dice que si que con gusto le envias las ventas. Vas a tu escritorio y haces algo como esto (Y si lo haces en produccion te traes abajo el servidor)

{% highlight sql %}

SELECT P.FirstName + ' ' + P.LastName AS [Vendedor], 
		year(OrderDate) AS 'year', 
		[TotalDue] as [TotalVentas]
FROM	[AdventureWorks2012].[Sales].[SalesOrderHeader] Sales 
		INNER JOIN Person.[Person] P 
		ON P.BusinessEntityID = Sales.SalesPersonID

{% endhighlight %}

