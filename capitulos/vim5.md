# Aprende a usar Vim desde cero: 5 – El modo visual

Hemos llegado al quinto post sobre cómo usar Vim, nuestro editor modal de código favorito. Llevamos más de un mes hablando de este editor y de las cosas magníficas que podemos hacer con él. Nos quedan muchos temas por tratar, pero **a lo que modos de Vim se refiere solo nos queda comentar el modo visual y el modo de la línea de comandos**. Cuando acabemos con ellos, empezaremos a mirar cómo podemos manejar múltiples archivos a la vez.

Conozcamos **el modo visual**, un modo que se asemeja a la selección de texto en otros editores de código. Normalmente, seleccionaríamos el texto y lo copiaríamos, pegaríamos o lo sustituiríamos, pero el enfoque que toma Vim es un poco diferente. **Seleccionaremos texto y ejecutaremos acciones sobre él**. Lo más importante que hay que saber sobre el modo visual es que **Vim tiene tres variantes de este modo**. Uno que selecciona por caracteres y palabras, otro que selecciona líneas completas y por último uno que selecciona bloques rectangulares de texto.

## Domina el modo visual

**Para entrar al modo visual pulsaremos desde el modo normal la tecla** `v`. Si utilizamos las teclas de dirección seremos capaces de aumentar o disminuir la longitud de nuestra selección. Mientras estamos en el modo visual la tecla o cambia la dirección por la que modificamos la extensión de nuestra selección.

Como en todos los modos de Vim, tendremos diferentes teclas que ejecutarán diversas funciones. Hay varias que tienen la misma función como las teclas de dirección, el comando `f{letra}` que nos llevará hacia la primera letra que contenga nuestra búsqueda (podremos usar `;` o `,` para repetir la búsqueda). También hará lo mismo el comando `c`, con el que borraremos la selección y entraremos directos al modo insertar parar hacer los cambios necesarios. También seremos capaces de hablar Vim con comandos como `vi)` o `viw`.

**Podemos entrar al modo visual-lineal con el comando** `V`, ejecutándolo desde el modo normal. Este es un modo que nos sirve para seleccionar líneas completas y ejecutar comandos sobre ellas. Por último, tenemos **el modo visual-bloque, el cual se activa con la combinación** `Ctrl-v` y sirve para seleccionar columnas, dejándonos con una selección con forma de tetraedro en el texto.

## Veamos unos ejemplos prácticos de cómo usar el modo Visual

**Usa el modo visual para editar la capitalización de las palabras**

Una de las situaciones en las que nos veremos con frecuencia será la de **editar el texto para ponerlo en mayúsculas o minúsculas**. En el siguiente ejemplo usaremos vit desde el principio de la línea para seleccionar directamente el texto dentro de los tags. Una vez seleccionado podemos **convertir el texto a mayúsculas** usando la tecla `U`. Para el **efecto contrario** usaremos `u` o `~` que cambia las mayúsculas a minúsculas y al contrario. En este caso la idea es poner en mayúsculas la palabra inicio, probadlo y veréis como se capitaliza con cualquiera de los dos comandos que describe la imagen.

**Usa el modo visual lineal para indentar el texto**

El ejemplo más típico que podíamos ver es el de la indentación de texto, algo que hacemos de forma regular cuando editamos código. Mediante el modo visual-lineal seleccionaremos las líneas que queremos indentar y después ejecutaremos el **comando de indentación** `>` o `<`, el cual, también funciona en el modo normal.

**Usa el modo visual-bloque para la maquetación de tablas**

Este es un ejemplo un poco más complejo pero de gran utilidad. Saber realizar este último apartado nos va a ayudar a entender cómo funciona este modo y seremos capaces de aplicarlo en otras situaciones que se nos ocurran. El ejemplo que muestro es la maquetación de una tabla. **Eliminamos espacios que sobran y los sustituimos por un borde** hecho con |. Por último copiamos una línea y la sustituimos por - para **crear un borde superior**. Parece mucho pero una vez entendido se hace en pocos segundos.

`set nocompatible`

`filetype`

`plugin on`

`syntax on`

|  Comandos |  Contenido del buffer |
|---|---|
| {posición inicial}  |  `L`ínea uno |
| x  | `í`nea uno  |
|  . |  `n`ea uno |

El comando `dd`, sirve para eliminar una línea. Si después usamos el comando punto, eliminaremos otra línea. De forma que si nos movemos por el documento **podremos eliminar líneas completas solamente pulsando el comando punto**, ¿bastante cómodo verdad?

## Muévete en Vim como en un teclado español

Vim por defecto, nos tiene acostumbrados a movernos por el archivo con las teclas **hjkl**, pero en un teclado español nosotros ponemos los dedos sobre **jklñ**. Por lo tanto, he decidido que para mí es más cómodo cambiar esas teclas, de tal forma que siempre tendré mis dedos en la posición del teclado español. Para ello he añadido esto a mi `.vimrc`.

teclas de dirección en el modo normal como en el teclado español

`nnoremap j h` `nnoremap k j` `nnoremap l k` `nnoremap ñ l`

teclas para movernos por paneles como en el teclado español

`nnoremap j h` `nnoremap k j` `nnoremap l k` `nnoremap ñ l` `nnoremap J H` `nnoremap K J` `nnoremap L K` `nnoremap Ñ L`

teclas para cambiar de línea en frases largas como en un teclado español

`nnoremap gk gj` `nnoremap gl gk`

teclas para el modo visual como en el teclado español

`vnoremap j h` `vnoremap k j` `vnoremap l k` `vnoremap ñ l`

## Casos prácticos

Podemos **indentar un archivo** con `>>`, de esta forma, si queremos continuar indentando más líneas solo tendremos que movernos a ellas y pulsar el comando punto. No importa en que lugar de la línea estemos, podemos indentar aunque estemos a final de la frase, pulsando el punto.

| Comandos | Contenido del buffer |
|---|---|
|{posición inicial}|`L`ínea uno|
| |Línea dos|
| | Línea tres|
|k>>|Línea uno|
| | &ensp;&ensp;&ensp;&ensp;&ensp;`L`ínea dos|
| | Línea tres|

**Un error habitual cuando editamos JavaScript es olvidarnos del ; final** de algunas líneas de código. Si nos hemos olvidado de ello en varias líneas, el comando punto también nos puede ayudar. La tecla `$` lleva a nuestro cursor al final de la línea y la tecla `a`, nos cambia al modo insertar en un carácter siguiente de donde tenemos el cursor. Sin embargo, **la misma funcionalidad se puede conseguir simplemente pulsando `A`**.

| Comandos | Contenidos del buffer |
|---|---|
|{Posición inicia}|`v`ar foo = 1|
|A;| var foo = 1`;`

Después, saldremos del modo insertar al normal pulsando la tecla `<esc>`. Ahora, si tenemos más líneas a las que les falten el `;` simplemente con pulsar el comando `.` se añadirá, sin importar la posición de la frase en la que estemos. **Como podéis ver, el comando `.` es todoterreno y nos ayudará a hacer las cosas mucho más rápido que manualmente**.
