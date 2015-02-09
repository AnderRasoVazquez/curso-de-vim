# Aprende a usar Vim desde cero: 7 - Trabajar con múltiples archivos

Bienvenido a la séptima entrega del curso sobre cómo usar Vim, el editor de código modal que te hace ser más productivo. Esta vez trabajaremos con múltiples archivos.

Después de hacer un tour por los modos que tiene Vim ya va siendo hora de que nos pongamos a trabajar con múltiples archivos. La forma que tiene Vim de manejar los archivos me encanta. No se vosotros, pero yo cuando usaba editores de código como Sublime Text acababa llenando el espacio de trabajo con multitud de pestañas. Puede que la culpa fuese mía por no saber administrarme bien con editores así pero no importa, porque con Vim ya no tengo un espacio de trabajo abarrotado. He pasado del caos al orden y es de eso de lo que voy a hablar en este post.

Vim no solo soporta pestañas, también soporta paneles, es decir, unas divisiones por cada pestaña que pueden ser horizontales o verticales. Si alguna vez habéis usado [tmux]() ya sabéis de lo que estoy hablando. Hablaremos de ello en el siguiente post.

## La lista de buffers

Algo importante que tenemos que saber es que Vim hace una distinción entre archivos y *buffers*. Un archivo está guardado ene l disco mientras que un buffer se guarda en la memoria. Cuando decimos que estamos editando un archivo lo que en realidad editamos es un buffer. Imaginemos que tenemos una carpeta con varios archivos de texto, ya sabéis esos que acaban en `.txt`. Desde nuestra terminal podemos abrir todos los archivos que tengan esa terminación con el comando `vim *.txt`. Cuando Vim se abra veremos que en la ventana solo tenemos un archivo abierto, pero en realidad Vim ha creado un buffer para todos los archivos `.txt` de la carpeta, solo que solo vemos un archivo en pantalla. Veamos que podemos hacer con esos buffers:

+ `:ls` nos muestra una lista de los buffers. Si vemos el símbolo `#` delante del nombre de un buffer significa que es el buffer anterior al que hemos estado. Podemos volver al buffer anterior con `<Ctrl-^>`. No es una combinación muy cómoda para el teclado español, pero siempre podemos editar nuestro `.vimrc` para ponerlo al gusto. Por otro lado si un archivo de la lista va precedido por el símbolo `%` significa que es el archivo que estamos editando en este momento.
+ `:bn[ext]` podemos escribir `:bn` o `:bnext` para que se ejecute este comando. Su función es la de abrir el siguiente buffer de la lista.
+ `:bp[revious]` abre el buffer anterior.
+ `:bf[irst]` abre el primer buffer de la lista.
+ `:bl[ast]` abre el último buffer de la lista.
+ `:bd[elete]` eliminar buffer de la lista, no elimina el archivo del disco.
+ `:args` muestra la lista de argumentos, a diferencia de `:ls` solo muestra el nombre de los archivos y en cual estamos. Podemos añadir por ejemplo todos los archivos `.js` de las carpetas con el comando `:args **/*.js`.
+ `:argdo [comando]` nos permite realizar un comando en todos los archivos de la lista a la vez. Muy útil si queremos reemplazar algun texto en todos los archivos.
+ `w[rite]a[all]` guarda todos los archivos.
+ `q[uit]a[all]` sale de todos los archivos. Si le añadimos el signo `!`, saldrá sin guardar los cambios.

Aquí os dejo un remapeo de teclas de ejemplo para que podáis añadir a vuestro `.vimrc`. Solo es un ejemplo, para mí funciona pero si se te ocurre una combinación que funcione mejor para ti cámbialo a tu gusto. Lo que hace estas líneas es que cuando pulsemos por ejemplo `[b` será lo mismo que si hubiéramos escrito `:bprevious`. Si no lo estáis haciendo ya recomiendo que os acostumbréis a crear vuestros atajos, os hará más productivo con las acciones que repitáis a menudo. Si todavía no usáis el plugin [vim-airline]() os lo recomiendo, para más información podéis visitar este sensual [post]().

	nnoremap <silent\> [b :bprevious<CR>
	nnoremap <silent> ]b :bnext<CR>
	nnoremap <silent> [B :bfirst<CR>
	nnoremap <silent> ]B :blast<CR>

## Posts anteriores sobre cómo usar Vim

[1: Introducción a Vim](http://bitelia.com/2014/09/como-usar-vim-1-introduccion-a-vim)
[2: Editar al estilo Vim](http://bitelia.com/2014/09/como-usar-vim-cero-2)
[3: El modo normal](http://bitelia.com/2014/09/como-usar-vim-3)
[4: El modo insertar](http://bitelia.com/2014/10/como-usar-vim-4)
[5: El modo visual](http://bitelia.com/2014/10/como-usar-vim-5)
[6: El modo de comandos](http://bitelia.com/2014/10/como-usar-vim-6)