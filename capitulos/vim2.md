# Aprende a usar Vim desde cero: 2 - Editar al estilo VIM

En esta segunda entrada sobre cómo usar [**Vim**](http://www.vim.org/), antes de adentrarnos en los modos de edición, vamos a aprender una de las características estrella de Vim, los comandos de repetición de tareas. A parte, también haremos nuestras primeras modificaciones al archivo `.vimrc`, el cual, se encuentra en la raíz de nuestra carpeta personal.

Durante nuestras sesiones de edición de código, cuántas veces habremos pensado lo genial que sería que algunas tareas repetitivas se hicieran solas. Si nunca has usado un editor que pudiera automatizar tareas, ya sea con macros o con otra característica, **esto te va a sorprender gratamente. Se podría decir que Vim es un editor para vagos**.

**No importa si usas la versión de Vim con interfaz gráfica o la que se ejecuta en terminal, podrás seguir la guía de igual manera**. Lo primero que haremos será añadir las siguientes líneas a nuestro `.vimrc`, las cuales activarán más funciones de Vim que por defecto vienen bloqueadas. Además del resaltado de sintaxis.

`set nocompatible`

`filetype plugin on`

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
