---
layout: post
title:  "Jekyll con Disqus!"
date:   2015-09-01 19:56:14
categories: [jekyll]
tags: [jekyll, disqus]
---

## Que es Disqus y para que me sirve?

Disqus es una herramienta maravillosa para tu sitio o blog. En especial para sitios estaticos como los generados por jekyll.

Que tiene de maravilloso? 

Para empezar podria mencionar que no se que me tomo mas tiempo si registrarme en su sitio (45 segundos) o habilitar el codigo en mi blog.
Es tan sencillo como copiar el script que te ponen a tu disposici&oacute;n, en el lugar que quieres que se muestren los comentarios. Lo cual es usualmente al final del blog.

Tan facil como te digo, puedes tener una seccion de comentarios para cada pagina que desees y tus lectores, amigos, criticos y demas pueden dejarte comentarios con solo tener una cuenta de facebook / google plus o twitter, suena bien no? Pues trabaja igual de bien, si no solo ve al final de este blor y mira la seccion de comentarios.

## Como implemento Disqus en Jekyll

Implementar Disqus es mas facil de lo que uno podria imaginarse. Segun donde quieras aceptar comentarios, en mi caso quiero que todos los posts tengan sus propios comentarios.

Para ello solo me dirijo al layout de `posts.html` y agrego donde quiero que esten los comentarios el script que adjuto. Por lo general se agregan estos comentarios en la parte baja del post.


## Implementaci&oacute;n

{% highlight html %}
<div id="disqus_thread"></div>
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES * * */
    var disqus_shortname = 'tucuenta';
    
    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
{% endhighlight %}

La version m&aacute;s reciente de este c&oacute;digo esta [aqu&iacute;](https://slothslab.disqus.com/admin/settings/universalcode/)


