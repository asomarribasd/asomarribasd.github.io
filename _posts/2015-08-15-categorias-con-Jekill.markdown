---
layout: post
title:  "Categorias y Tags en Jekyll"
date:   2015-08-15 18:00:00
categories: [jekyll]
tags: [jekyll, octopress]
---

## Clasificaciones en Jekyll

Para la clasificaci&oacute;n y crear relaciones en tus blogs, Jekyll implementa dos metodologias similares en la forma de difinirlas pero diferentes en cuanto a sus caracteristicas.
Estas son [categorias] y [tags] las cuales se definen en la cabecera del Blog.

## Categorias en Jekyll

Las categorias en Jekyll son una herramienta para ordernar por tematica tus blogs, puedes definir una o mas categorias por blog y Jekyll exportara el blog tomando en cuenta una ruta creada, basandose en las categorias seleccionadas.
Se usa por lo general para marcar la tematica global a la que pertenece el blog, personalmente no recomiendo usar mas de 3 niveles de categorias, se vuelve un poco largo y dificil de leer el path del blog generado.

## Tags en Jekyll

Los tags son palabras "claves" con las que se puedes relacionar tus blog, sin que esto determine un cambio en la categoria o clasificaci&oacute;n general del blog.
Tener tags en los blogs se puede utilizar para relacionarlos con temas comunes y navegar atravez de dichos temas.
Algo que me gusta de los tags es que son perfectos para crear secciones como "Posts Similares" o una "nube" de terminos/tematica.

## Post Similares con Tags

Una forma para lo cual usar Tags se vuelve muy util es para crear secciones de "posts similares" de esta forma asignando tags con palabras claves del contenido de tu blog puedes mostrar al lector blogs con contenido similar que el lectori podr&iacute;a estar interesado en leer.
Despues de buscar un poco encontre algo que se ajustaba a mi necesidad de agregar post similares al que el lector se encontraba leyendo. El siguiente me gusta en especial por que no es un plugin. Esta basado en codigo de Liquid y hasta el momento no he tenido ningun problema.

Se los dejo.

{% highlight html %}

{% raw %} 
{% assign hasSimilar = '' %}
{% for post in site.related_posts %}
    {% assign postHasSimilar = false %}
    {% for tag in post.tags %}
        {% for thisTag in page.tags %}
            {% if postHasSimilar == false and hasSimilar.size < 6 and post != page and tag == thisTag %}
                {% if hasSimilar.size == 0 %}
                <h4>Posts Similares</h4>
                <ul>
                {% endif %}
                <li class="relatedPost">
                    <a href="{{ site.url }}{{ post.url }}">{{ post.title }}
                    {% if post.series %}
                        (Series: {{ post.series }})
                    {% endif %}
                    </a>
                </li>
                {% capture hasSimilar %}{{ hasSimilar }}*{% endcapture %}
                {% assign postHasSimilar = true %}
            {% endif %}
        {% endfor %}
    {% endfor %}
{% endfor %}
{% if hasSimilar.size > 0 %}
    </ul>
{% endif %}
{% endraw %}
{% endhighlight %}

Este codigo es autoria de 
[Post Similares](http://zhangwenli.com/blog/2014/07/15/jekyll-related-posts-without-plugin/) y funciona a la perfeccion.
Con unas pocas modificaciones pueden verlo funcionando en la parte inferior del blog.






