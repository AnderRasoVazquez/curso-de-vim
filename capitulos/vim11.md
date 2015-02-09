# Aprende a usar Vim desde cero: 11 - 

Bienvenido a la onceava entrega del curso sobre cómo usar Vim, el editor de código modal productivo. Esta semana aprenderemos a usar los registros de Vim.

Cómo usar Vim desde cero: 10 - Moverse por el archivo 2

cómo usar Vim

En el post de esta semana vamos a hablar sobre una de las funciones que es vital entender en [Vim](http://bitelia.com/tag/vim), los registros. Lo primero que debemos tener claro es que **un registro es un contenedor que guarda texto**. De la misma forma que usamos el portapapeles del sistema para copiar, pegar y cortar texto aunque también se puede utilizar como macro, para guardar comandos. Hoy veremos como funcionan estos registros para las acciones del portapapeles, la semana que viene iremos con las macros.

En Vim, a diferencia de otros [editores de código](http://bitelia.com/2014/09/editores-codigo-mas-versatiles) más convencionales, **tendremos varias casillas en nuestro portapapeles para guardar el texto. A esas diferentes casillas las llamaremos registros** y por defecto, determinadas acciones guardarán el texto en un registro determinado. Ahora veremos unos ejemplos para poder sacarle el máximo partido y no confundirnos.

## Eliminar (delete), copiar (yank) y pegar (put)

Se que no es la traducción exacta en español pero es la manera más sencilla de entender lo que hacen estos [comandos](http://bitelia.com/2014/07/comandos-basicos-terminal-parte-iii). **Cuando borramos algo, se guarda en el registro sin nombre**. Por ejemplo si nos colocamos :

	var a = [;]2   // colocamos el cursor sobre sobre ;
	var a = [2]    // pulsamos X para borrar ;
    var a = 2[;]   // pulsamos p para pegar ;
<br>

¿Qué acaba de pasar? El comando `delete` de Vim hace lo mismo que el comando cortar, es decir, si borramos algo de forma automática se guarda en el registro si nombre. **Por lo tanto debemos tener cuidado con el típico problema que tendremos con los registros, fastidiar el contenido del registro**. Supongamos que queremos cambiar el orden de las palabras `dos` y `uno` en la siguiente línea. Intuitivamente cometeríamos el siguiente error:

	resultado("[d]os", "uno"); // nos situaríamos sobre "dos"
    resultado("[d]os", "uno"); // copiaríamos con yi"
    resultado("dos", "[u]no"); // nos situaríamos sobre "uno"
    resultado("dos", "["]);    // borraríamos con di"
    // ahora viene el error
    resultado("dos", ["]uno"); // a la izquierda con h, pegamos con p
<br>

¿Qué acaba de pasar? Hemos vuelto a copiar lo mismo, el registro se ha sobreescrito con lo que hemos [borrado](http://bitelia.com/2013/06/borrado-seguro-de-archivos-windows).

## Los registros de Vim

Acceder a los registros de Vim es sencillo, solamente hay que especificarlos con `"{registro}`. En el ejemplo anterior hemos visto como Vim con el comando `delete` guarda lo borrado en el registro sin nombre, al que se accede con `""`. Imaginemos que queremos copiar algo al registro llamado `a`, lo haríamos con el comando `"ayiw` (copiar una palabra al registro *a*). O imaginemos que queremos pegar algo del registro *b*, lo haremos con el comando `"bp`. **Si no especificamos el registro a usar Vim simplemente usará el registro sin nombre**. Por lo tanto, fastidiar nuestro registro es muy sencillo y nos puede traer problemas, aquí es cuando es necesario saberse bien la teoría. Ahora veremos cómo solucionar el error.

Es importantísimo saber que **el comando `yank` no solo copia al registro sin nombre, si no que también copia al registro *0***. Por lo tanto si en el último comando donde cometimos el error hubiéramos hecho lo siguiente:

	// ahora viene el error -> corregido
    resultado("dos", ["]dos"); // a la izquierda con h, pegamos con "0p
<br>

Al pegar con `"0p` hemos pegado el contenido del registro *0* que se ha guardado con el comando `yank`. **Otra opción sería no borrar la palabra `uno`, sino seleccionarla con `ve`** y pegar nuestro texto con `p`. Mucho más fácil ya que no tendremos que andar pensando en los registros, pero para esta guía había que explicar con el anterior ejemplo como funcionan los registros.

## Otros registros

Aparte del registro sin nombre y los que creemos nosotros, hay mas registros que tenemos que conocer.

+ `"_` **el registro *agujero negro***. Es un registro que no guarda texto, útil si queremos borrar algo `"d{motion}` sin que se sobreesriba la [copia](http://bitelia.com/2014/03/copias-seguridad-importancia) que tenemos en el registro sin nombre.
+ `"+` / `"*` **el portapapeles del sistema**. Importantísmo. Gracias a este registro podremos copiar al portapapeles del sistema y pegar texto externo en Vim.
+ Como siempre para saber más de los registros **os dejo el comando de ayuda `:h registers`**, hay muchísima información y se habla de muchos más registros. Pero nosotros, para un primer contacto con estos nos sobra.


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

