# Aprende a usar Vim desde cero: 14 - Sustituciones

En el [anterior post](http://bitelia.com/2014/12/como-usar-vim-13) estuvimos hablando acerca de la elaboración de patrones de búsqueda. Hoy, **vamos a utilizar lo aprendido anteriormente para entender el funcionamiento de uno de los comandos *Ex* más poderosos que encontraremos en Vim, las sustituciones**. Hablaremos de los diferentes modos de sustitución y de ciertos aspectos que debemos tener en cuenta para sacar el mejor provecho a este [comando](http://bitelia.com/tag/comandos), además de algunos trucos útiles como por ejemplo reusar los patrones de búsqueda anteriores para no tener que repetir las búsquedas o que Vim nos pida confirmación por cada encuentro. Los más avanzados también podrán usar scripts de Vim en las sustituciones con las que incluso se pueden realizar operaciones aritméticas, pero enseñar el lenguaje de Vim queda por encima del objetivo de este curso.

## El comando sustituir

El comando `:substitute` es un comando que puede parecer más complejo que el típico `ctrl+f` de otros [editores de código](http://bitelia.com/tag/editor-de-texto), **le proporcionaremos un patrón de búsqueda y después el texto que queramos sustituir**. Su complejidad radica en las múltiples opciones que cambiarán el comportamiento de este comando, esas opciones son llamadas *flags*. El comando sustituir tiene la siguiente estructura:

`:[range]s[ubstitute]/{pattern}/{string}/[flags]`

Estas son unas cuantas flags útiles (para más información consultad `:h :s_flags`):

+ `g`: hace que el comado de sustitución **actúe de forma global**, cambiando cada patrón que encuentre en una línea en lugar de cambiar únicamente el primero.
+ `c`: nos da la oportunidad de **confirmar los cambios**, para mí es una de las más útiles.
+ `n`: suprime el comportamiento habitual del comando sustituir, **nos informa del número de casos que se verían afectados** si ejecutásemos el comando.
+ `&`: esta flag le indica al comando sustituir que **reutilice las flags del comando anterior**.

Es importante saber los **carácteres especiales que podemos usar** como reemplazo (para más info consultad `:h sub-replace-special`):

+ `\r`: inserta un retorno de carro (en palabras llanas, un *enter*).
+ `\t`: inserta una tabulación.
+ `\\`: inserta un `\`, como es un carácter que se usa como especial necesita estar precedido de un `\`.
+ `\1`: inserta el primer *submatch* (lo veremos en acción enseguida).
+ `\2`: inserta el segundo *submatch*, y así sucesivamente.
+ `\0`: inserta el patrón de búsqueda completo.
+ `&`: inserta el patrón de búsqueda completo.
+ `~`: usa el `{string}` de comando de sustitución anterior.
+ `\={Vim Script}`: evalua una expresión {Vim script} y usa el resultado como el `{string}` a reemplazar.

## Empecemos con la práctica

La mejor forma para entender el funcionamiento del comando de sustitución es fijarnos en estas sencillas líneas:

`[L]ínea 1 - Madrid, Madrid.` (`[]` -> nuestra posición)
`Línea 2 - Madrid, Madrid.`

**Supongamos que queremos sustituir la palabra *Madrid* por cualquier otra de nuestra elección**. Dependiendo de las flags que usemos obtendremos diferente resultado.

+ `s/Madrid/Bilbao`: sustiuirá **el primer Madrid** de la primera línea.
+ `s/Madrid/Bilbao/g`: sustiruitá **todos** los Madrid **de la primera línea**.
+ `%s/Madrid/Bilbao/`: sustituirá **el primer Madrid de todas las líneas** del archivo.
+ `%s/Madrid/Bilbao/g`: sustituirá **todos** los Madrid del archivo.
+ `%s/Madrid/Bilbao/gc`: nos pedirá **confirmación** para sustituir cada Madrid. Podemos contestar: `y` sí, `n` no, `q` (quit) terminar de sustituir, `l` (last) sustituir este y dejar de sustituir, `a` (all) todos, `Ctrl+e` mover la pantalla hacia arriba o `Ctrl+y` mover la pantalla hacia abajo.
+ Supongamos que se nos ha olvidado indicar con `%` que queríamos ejecutar el comando en todo el archivo. No hay problema, podemos usar `g&` que es equivalente a `:%s//~/&`.

## Trucos útiles

**Es común dividir el patrón de la sustitución**, ya que normalmente, si usamos expresiones regulares suele llevarnos más de un intento elaborar correctamente la que queremos. Tomando como ejemplo la búsqueda de colores hexadecimales del post anterior, podríamos dividir el proceso de esta manera:

1. `\v#(\x{6}|\x{3})` Es el primer paso, para encontrar lo que queremos.
2. `%s//#FFFFFF/gc` Como podéis ver, si no indicamos nada en el patrón utiliza el de la búsqueda anterior, pero si aún así queréis escribirlo podéis pegar la búsqueda anterior ejecutando `:%s/Control+r//#FFFFFF/gc`. La primera forma es menos intimidante que escribir `%s/\v#(\x{6}|\x{3})/#FFFFFF/gc`. También podemos indicar el contenido de otros registros con `\=@0` por ejemplo, que pegará el contenido del registro del *yank* mientras que `@"` lo hará del registro por defecto.

Supongamos que tenemos un archivo *CSV* con una estructura de `apellido,nombre,email` por cada línea y **nuestro objetivo es reordenar las columnas de forma que nos queden en orden contrario** `email,nombre,apellido`. Podríamos utilizar los *submatch* mencionados anteriormente:

1. `/\v^([^,]*),([^,]*),([^,]*)$`
2. `:%s//\3,\2,\1`

Hay muchos apartados que se podrían cubrir en detalle, pero **aquí tenéis una buena introducción a las bondades de este comando** en este [curso de Vim](http://bitelia.com/tag/curso-de-vim). Aprender a elaborar expresiones regulares es muy útil y combinado con el poder de este editor nos hará muy productivos.

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