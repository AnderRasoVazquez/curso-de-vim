Aprende a usar Vim desde cero: 10 – Cómo moverse rápido por los archivos 2

En el capítulo anterior estuvimos viendo formas que podemos usar para movernos rápido por nuestros archivos. Algunos de los comandos fueron mencionados en posts anteriores de forma suelta, divididos por los diferentes modos de Vim. Al ser comandos con un propósito similar, tiene sentido hacer una lista con todos ellos y profundizar más en el tema que nos ocupa añadiendo unos cuantos más. De esta forma, los tendremos a mano para consultar más adelante.

Esta semana en este décimo (doble cifra ya) post sobre Vim, vamos a seguir viendo formas de movernos rápido por nuestro archivo sin usar el ratón. Además, veremos **una de mis características favoritas de Vim, las llamadas *marcas***, con las que podremos marcar secciones relevantes del archivo para poder saltar a ellas cuando sea preciso.

##Hacer selecciones precisas

Movernos rápido por el archivo también tiene que ver con hacer selecciones de una manera rápida, sencilla y eficaz. De eso mismo va este apartado, en el que si os fijáis reconoceréis varios de los comandos que he puesto en la siguiente lista. **i** significa *dentro de X elemento*, mientras que **a** significa *alrededor de X elemento*. La gracia de estos comandos que vais a ejecutar desde el modo normal es que vayan precedidos de `v` (selección visual), `c` (cambiar texto) o `d` (borrar texto) ya que por sí solos no hacen ninguna función.


- **a)** / a** paréntesis.
- **i)** / ib** paréntesis.
- **a}** / aB** llaves.
- **i}** / iB** llaves.
- **a]** corchete.
- **i]** corchete.
- **a>** para mayor o menor que.
- **i<** para mayor o menor que.
- **a’** comillas simples.
- **i’** comillas simples.
- **a”** comillas dobles.
- **i”** comillas dobles.
- **a`** acento grave.
- **i`** acento grave.
- **at** para tags HTML.
- **it** para tags HTML.
- **aw** palabras.
- **iw** palabras.
- **aW** PALABRAS.
- **iW** PALABRAS.
- **as** frase.
- **is** frase.
- **ap** párrafo.
- **ip** párrafo.

## Marca lugares relevantes para volver a ellos fácilmente

El comando `m{a-zA-Z}` crea una marca (o varias si definimos más) en el archivo a la que podremos saltar cuando queramos usando el acento grave más la letra del alfabeto que hayamos usado. Por ejemplo, podríamos usar la marca mm movernos por el archivo y volver a ella con ``m`. Con el tiempo os daréis cuenta de que esta es una herramienta muy útil y podréis moveros por el archivo sin miedo a perder la posición de interés. Lo bueno de las marcas es que hay algunas que se añaden solas, aquí tenéis unos cuantos comandos que se ejecutan desde el modo normal y sin los dos puntos:


- **“** ir a la posición antes del último salto en el archivo actual.
- **`.**  ir a la localización del último cambio.
- **`^**  ir a la posición de la última inserción.
- **`[**  ir a la posición inicial del último cambio o copia (yank).
- **`]**  ir a la posición final del último cambio o copia (yank).
- **`<**  ir a la posición inicial de la última selección visual.
- **`>**  ir a la posición final de la última selección visual.

Si queréis saber más de esta función podéis consultar la ayuda con `:h m`.

## Plugin de interés

En Vim hay un **plugin llamado machit** que hay que activar editando el `.vimrc`. Su función es la de aumentar el alcance del comando `%` que por defecto, si lo pulsamos sobre paréntesis o llaves nos lleva a su pareja de cierre. Mediante *machit* conseguiremos que nos lleve en un archivo HTML de una etiqueta a su cierre o en un archivo Ruby nos lleve a los pares de `class/end`, `def/end` y `if/end`.

`set nocompatible`

`filetype plugin on`

`runtime macros/matchit.vim`

Hay otro plugin que nos va a facilitar mucho la vida para **cambiar el elemento que se encuentre rodeando nuestra selección**, su nombre es [vim-surround](https://github.com/tpope/vim-surround). Usando este plugin, podremos sustituir por ejemplo las dobles comillas por paréntesis o por lo que elijamos, añadir etiquetas HTML que se cierran solas en una selección o borrar lo que rodea a nuestra selección.
