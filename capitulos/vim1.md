# Aprende a usar Vim desde cero: 1 - Introducción a Vim

Si quieres saber cómo usar Vim desde cero sigue leyendo, este post será la primera toma de contacto con este maravilloso editor de código.

como usar vim

[**Vim**](http://www.vim.org/), del inglés *Vi Improved*, **es una versión mejorada del editor de texto Vi**, el cual, fue creado en 1976 por Bill Joy que tomó recursos de ed y ex, dos editores de texto para Unix. Vim, fue presentado en el año 1991 y desde entonces no ha dejado de experimentar infinidad de mejoras. **La madurez de este editor de código es indiscutible pues lleva desarrollándose más de 20 años**.

La característica más destacable de este [editor](http://bitelia.com/2014/09/editores-codigo-mas-versatiles) es su **modo de edición modal**, en los que seremos capaces de realizar distintos tipos de operaciones. Si nunca has usado un editor modal, te recomiendo que te olvides por un momento de lo que sabes hasta ahora sobre editar archivos de texto, pues aquí no te va a servir. **La gracia de usar Vim está en que no tendremos que usar más el ratón ni las teclas de dirección para editar archivos**.

Os debo advertir que las primeras veces que lo uséis os sentiréis muy lentos, **aprender a hablar Vim requiere de una gran curva de aprendizaje** pero no os desaniméis, os prometo que cuando os hayáis acostumbrado a él, **vuestra productividad aumentará notablemente**. Tenemos la versión Vim, que se ejecuta en la terminal escribiendo `Vim` y gVim que se ejecuta en una ventana, tiene menús y ayudas para novatos. Recomiendo instalar este último para empezar pero podéis usar el que queráis. Podéis instalarlo con `sudo apt-get install vim-gtk` en Ubuntu 14.04. Hay binarios para Windows y Mac en la [página oficial](http://www.vim.org/).

## Los diferentes modos de Vim

**Modo Normal**.
Vim empieza en este modo. Se pueden emplear combinaciones de teclas para, por ejemplo, copiar líneas y trabajar en el formato del texto. Éste es el modo central, desde el que se cambia a los otros modos. Pulsando la tecla `Escape` siempre se puede volver al modo normal. Por defecto, podremos mover el cursor por el archivo con `hjkl` (izquierda, abajo, arriba y derecha respectivamente) o con las teclas de dirección. 

**Modo insertar**.
Es el modo en el que podemos introducir texto. Se puede entrar a este modo desd el modo normal pulsando la tecla `i`. Existen otros comandos que nos llevarán al modo inserción pero se diferencian uno del otro por la acción que realizan, como cambiar una palabra dentro de unas comillas, cambiar el texto hasta el final de la línea o hasta el cierre de un corchete, `}` etc. Un usuario avanzado ahorrará mucho tiempo utilizando estos atajos.

**Modo de comandos**.
Se accede pulsando `:`. Permite introducir diferentes comandos, como buscar y reemplazar con expresiones regulares. También podremos personalizar aspectos de Vim para esa sesión, ya que no quedarán guardados los cambios permanentemente.

**Modo visual**.
Se entra pulsando la tecla `v`. Es como seleccionar texto con el cursor, solo que podremos escribir comandos para manipularlo.

**Modo selección**.
Se entra desde el modo visual pulsando `Ctrl-G`. Tiene un comportamiento similar al modo visual solo que al escribir no realizaremos comandos sino que reemplazaremos el texto, como en un editor de texto normal,

**Modo Ex**.
Este modo se asemeja al modo de comandos, con la diferencia de que tras la ejecución de una orden no se vuelve al modo normal. Se entra pulsando `Q` y se sale con `vi`.

## Vim es como un lenguaje

Usar Vim es una experiencia completamente distinta a usar cualquier otro editor de código. Vamos a hacer una breve desmostración. **Se utiliza una sintaxis de** `verbo-modificador-objeto`. Empezaremos en el modo normal, pulsaremos `i` para introducir unos cuantos párrafos de texto, pulsaremos `Esc` para volver al modo normal y aquí empieza la magia. **No os procupéis, iremos mirando cada uno de ellos detalle en siguientes posts, pero podéis ir echándoles un vistazo**.

**Aprende algunos verbos**: **v** (visual), **c** (change/cambiar), **d** (delete/borrar), **y** (yank/copiar).

**Aprende algunos modificadores**: **i** (inside/dentro de), **a** (around/alrededor), **t** (till../hasta que encuentra el carácter), **f** (find../hasta que encuentra el carácter incluyéndolo), **/** (buscar).

**Aprende algunos objetos**: **w** (word/palabra), **s** (sentence/frase) **p** (paragraph/párrafo) **b** (block/parentesis), **t** (tag/ para html/xml).

## Hablemos Vim

**Ahora que estamos en el modo normal podemos hablar Vim (no se pulsa todo a la vez, se hace letra a letra)**:
>Elimina la palabra donde esté el cursor: **diw** (delete inside word) <br>
Cambia la frase en la que estés: **cis** (change inside sentence)<br>
Cambia lo que haya dentro de las comillas: **ci”** (change inside quote)<br>
Cambia lo que haya hasta ‘foo’: **c/foo** (change search foo)<br>
Cambia todo lo que haya hasta la letra X: **ctX**<br>
Selecciona un párrafo: **vap** (visual around paragraph)

Con esto tenéis material para ir probando Vim esta semana. **En los siguientes post de esta serie nos iremos deteniendo en profundidad por cada modo** y veremos con detalle lo que podremos hacer en cada uno. Hemos acabado la teoría para entender Vim, lo siguiente será todo práctica. **¿Qué os ha parecido Vim?**
