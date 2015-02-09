Hoy hemos llegado a mi tema favorito en el curso sobre cómo usar [Vim](http://bitelia.com/tag/vim). **Si hay una característica en especial que me hiciera plantearme dar el paso a usar este editor de código son las macros.** Ya sabemos múltiples formas con las que podemos repetir comandos o cambios en el código en Vim, pero no son todas las formas que existen en este programa. De repetir va la cosa, pues las macros nos permiten almacenar en un registro una serie de cambios específicos que podremos repetir más tarde a nuestra merced.

Con el [comando](http://bitelia.com/2014/11/bro-pages) punto "`.`" vimos que podíamos repetir una serie de pasos hasta que pulsábamos la tecla `escape` pero, ¿qué pasa si los cambios que queremos hacer son una serie de comandos en los que cambiaremos de modo varias veces?

## Grabar y ejecutar una macro

**Las macros se empiezan a grabar en cuanto pulsamos la tecla `q` y le asignamos un registro**, para parar de grabar pulsaremos de nuevo `q`. Si quisiéramos guardar la macro escogida en el registro `a` usaríamos el comando `qa`. Por [comodidad](http://bitelia.com/2014/11/fondo-pantalla-y-productividad) yo siempre grabo mis macros con el comando `qq` ya que siendo la misma letra me evita pensar en que registro he guardado mi macro, **para dejar de grabar de nuevo `q`**. Para entender como funciona esta fantástica característica de Vim solo tenemos que seguir el siguiente ejemplo, en el que corregiremos el `;` final y añadiremos el `var` que falta. Empezamos a grabar con `qq`:

**Este es nuestro código sin modificar**
`uno = 1`
`dos = 2` 
`suma = uno + dos`

**En la primera línea añadimos el punto y coma con `A;<escape>`, declaramos la variable con `Ivar<espacio><escape>`, nos movemos una casilla abajo con `j` y dejamos de grabar con `q`**
`var uno = 1;`
`dos[ ]= 2` 
`suma = uno + dos`

**¿Por qué nos hemos movido hacia abajo?** Muy sencillo, lo primero es saber que para ejecutar la macro pulsaremos `@q` (si hemos grabado con `qa` sería con `@a`). Pero recordad que las macros van de repetición, imaginad que en lugar de 3 líneas tenemos 20. No sería muy [productivo](http://bitelia.com/productividad) ir bajando nosotros cada línea y ejecutar `@q` cada vez. Por lo tanto, bajar una vez nos permite ejecutar la macro las veces seguidas deseadas (si queremos por ejemplo que sean 3 veces usaremos `3@q`) ya que los cambios se aplicarán en una línea y bajarán a la siguiente antes de volver a ejecutarse. A esto se le llama **ejecutar las macros en serie**. 

## Jugando con variables

Tenemos una lista que tenemos que numerar:

`Bilbao`
`Madrid`
`París`
`...etc`

**El resultado será dejar la lista ordenada del tipo  `1) Bilbao`**. Para ello primero crearemos una variable que se irá incrementando, con el comando `:let i=1` (para ver el contenido podemos hacer `:echo i`). Ahora comenzamos a [grabar](http://bitelia.com/2014/09/asciinema) con por ejemplo `qa` y empezamos a hacer los cambios en la primera línea.

`I<Ctrl-r>=i<enter>)<espacio>` nos dejará un resultado de `1) Bilbao`. Ahora, aumentaremos la variable `i` mediante el comando `:let i+=1`. Ya podemos dejar de grabar la macro con `q`. Podemos hacer como antes y ejecutar la macro en serie si además nos movemos hacia abajo antes de guardar o podemos hacer una selección en el modo visual, pulsar `:` y escribir `normal @q`. A esto se le llama ejecutar la macro en paralelo y sirve para que si tenemos un fallo en una línea, no se nos pare de ejecutar la macro en las siguientes. En cualquier caso, **cada vez que usemos la macro aumentará en uno el número de nuestra lista.**

***Nota**: el comando `<Ctrl-r>=i` sirve para pegar el contenido de la variable.* 

## Trucos útiles

+ Para las macros usa [comandos](http://bitelia.com/2014/04/comandos-basicos-terminal) como `A` y `I` que normalicen la posición del cursor.
+ Para repetir una macro que acabamos de ejecutar por ejemplo con `@q` usaremos `@@` las veces que queramos.
+ Para ver el contenido de nuestra macro `a` podemos usar el comando `:reg a`.
+ Para editar una macro llamada por ejemplo `a`, podemos pegar su contenido con `:put a` y cuando la hayamos editado al gusto copiarla de nuevo al registro con `"ay$`.
+ Ejecutar una macro en todos los buffers abiertos `:argdo normal @a`.

Coger soltura con las macros nos va a hacer muy productivos, espero que os sea útil en vuestros proyectos.

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