# Aprende a usar Vim desde cero: 16 – Autocompletado

**¿Qué editor de código que se precie no tiene una función de autocompletado?** Uno de mis editores favoritos siempre ha sido el famoso [Sublime Text](http://bitelia.com/2014/04/sublime-text-vs-brackets). Aparte de sus muchas bondades, una de las características que siempre me pareció tremendamente útil era el autocompletado. Recuerdo que en [otros programas](http://bitelia.com/2014/09/editores-codigo-mas-versatiles), escribía una variable y cuando tenía que voverla a escribir en otros lugares del archivo siempre había alguna en el que metía la pata y terminaba escribiendola mal, con los errores que acarreaba luego.

El autocompletado es una de las funciones que yo al menos, considero más útiles cuando editamos [código](http://bitelia.com/tag/codigo). Escribir el principio de una variable o de una palabra larga y que nuestro editor nos muestre sugerencias es fantástico. Pero... **¿y si os dijera que Vim va un paso más allá?**

Hoy, en esta sección de nuestro curso de Vim, echaremos un vistazo a las **opciones diferentes que nos proporciona Vim para el autocompletado**.

## El autocompletado más completo

La [guía](http://bitelia.com/tag/como-usar-vim) de esta semana va a ser más teoría que otra cosa, pues no hay mucho que mostrar. Eso sí, os recomiendo que probéis con vuestro Vim lo que vamos a ir mirando en breve. Lo primero que tenemos que aclarar es que en** Vim tendremos varias opciones para el autocompletado y que este se realiza siempre en el *modo insertar***. Para activar las diferentes opciones de autocompletado tenemos los siguientes atajos de teclado (`<C-n>` equivale a `<Control-n>`):

+ `<C-n>` **el autocompletado de Vim se activa mediante el atajo de teclado anterior o mediante **`<C-p>`, el primero seleccionara el siguiente resultado en una lista de palabras mientras que el segundo seleccionara el resultado anterior.
+ `<C-x><C-n>` sirve para **buscar una lista de palabaras en el buffer** (el archivo que estamos editando) en el que estemos.
+ `<C-x><C-i>` muestra **autocompletado de archivos incluidos**. Muchos lenguajes de programación permiten incluir archivos, este atajo sirve para buscar palabras en ellos.
+ `<C-x><C-]>` su función es `<C-x><>`. Un archivo *tags* tiene un índice de funciones, clases u otro tipo de estructuras. Pero esto se merece un post completo más adelante para entenderlo.
+ `<C-x><C-k>` mira una **lista de palabras en el diccionario**. Así es, en Vim también podemos tener un corrector de palabras en español, pero esto lo discutiremos más a fondo en otro post.
+ `<C-x><C-l>` este atajo hace un **autocompletado de líneas completas**. Imaginad que estamos editando un archivo CSS y vamos a repetir ciertas propiedades, como por ejemplo el *background*. Podríamos usar `ba<C-x><C-l>` y nos rellenaría la línea completa, perfecto para ahorrarnos tiempo en escribirlo.
+ `<C-x><C-f>` **autocompletado para nombres de archivos o carpetas**. En mi caso, encuentro tremendamente útil esta opción a la hora de escribir localización. Por ejemplo `/bin/b<C-x><C-f>` nos mostraría una lista con los archivos que empiezan por la letra `b` en el directorio `/bin/`.
+ `<C-x><C-o>` sirve para la *omni-completion*, **sugerencias basadas en el código como propiedades CSS** que podemos utilizar (imagen anterior). Hay varios lenguajes de programación soportados y mediante plugins podemos agregar más.

Como habéis podido leer, el autocompletado de Vim toma en cuenta diferentes contextos y solo nos muestra lo que necesitamos. Toma un tiempo recordar los [comandos](http://bitelia.com/tag/comandos) pero una vez aprendidos, nuestra productividad se disparará. Espero que os haya sido útil y volveremos con más la semana que viene. **¿Cómo lo lleváis hasta ahora?**

## Posts anteriores sobre cómo usar Vim

[1: Introducción a Vim](http://bitelia.com/2014/09/como-usar-vim-1-introduccion-a-vim)
[2: Editar al estilo Vim](http://bitelia.com/2014/09/como-usar-vim-cero-2)
[3: El modo normal](http://bitelia.com/2014/09/como-usar-vim-3)
[4: El modo insertar](http://bitelia.com/2014/10/como-usar-vim-4)
[5: El modo visual](http://bitelia.com/2014/10/como-usar-vim-5)
[6: El modo de comandos](http://bitelia.com/2014/10/como-usar-vim-6)
[7: Editar múltiples archivos](http://bitelia.com/2014/10/como-usar-vim-7)
[8: Paneles y pestañas](http://bitelia.com/2014/11/como-usar-vim-8)
[9: Cómo moverse rápido por los archivos](http://bitelia.com/2014/11/como-usar-vim-9)
[10: Cómo moverse rápido por los archivos 2](http://bitelia.com/2014/11/como-usar-vim-10)
[11: Dominar los registros](http://bitelia.com/2014/11/como-usar-vim-11)
[12: El poder de las macros](http://bitelia.com/2014/12/como-usar-vim)
[13: Patrones](http://bitelia.com/2014/12/como-usar-vim-13)
[14: Sustituciones](http://bitelia.com/2015/01/como-usar-vim-14)
[15: Comandos globales](http://bitelia.com/2015/01/como-usar-vim-15)