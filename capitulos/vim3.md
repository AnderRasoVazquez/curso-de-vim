# Cómo usar Vim desde cero : 3 - El modo normal

Vim nos proporciona una interfaz modal. Esto significa que el resultado de pulsar cualquier tecla de nuestro teclado, puede variar dependiendo el modo que esté activado en ese momento. Es vital saber el modo que está activado y también saber la forma de cambiar de un modo a otro. En esta parte de la guía sobre cómo usar Vim vamos a ver lo que podemos hacer en el modo normal.

Se podría decir que el modo normal de Vim es el estado de reposo. Otros editores de texto pasan la mayor parte del tiempo en lo que a Vim equivale al modo insertar. Para alguien que acaba de llegar a este editor modal, puede parecer extraño que pasemos la mayor parte del tiempo en ese modo. Para explicarlo podemos basarnos en la metáfora del modo de trabajo de un pintor.

¿Cuánto tiempo piensas que un pintor está con el pincel sobre el cuadro? Es obvio que el tiempo va a variar dependiendo del artista pero sumando el tiempo que emplea en estudiar las formas, perspectivas, combinaciones de colores y el modo de aplicarlas... Posiblemente llegue a la mitad del tiempo que tarda en realizar su obra. Un pintor no descansa dejando el pincel sobre el cuadro, ni nosotros tampoco lo haremos en Vim.

## Regula como deshaces tus cambios

En otros editores de texto pulsar el comando deshacer nos eliminará las últimas palabras o caracteres. En Vim el comando de deshacer se invoca pulsando `u` y el de rehacer con `Ctrl-R`. Se puede deshacer cualquier cosa que haya cambiado texto del documento, eso incluye cambios realizados desde el modo normal, visual o incluso del modo de línea de comandos. Por lo tanto, un cambio puede ser simplemente `i{insertamos texto}<ESC>`.

Si invocamos el comando deshacer en otro editor de texto no modal, pueden pasar dos cosas. Puede eliminar el último carácter o puede eliminar las últimas palabras escritas. Sin embargo, en Vim podemos controlar el nivel de lo que queremos deshacer.

Desde el momento en el que insertamos texto hasta que volvemos al modo normal, todo lo que escribamos cuenta como un cambio. Así que podemos moderar el efecto del comando deshacer sobre caracteres, frases o párrafos dependiendo del uso que hagamos de la tecla `<ESC>`.

## Comandos esenciales

En el post anterior hicimos una modificación en nuestro `.Vimrc` en el que cambiamos las teclas de dirección a unas más acordes con el teclado español. Por lo tanto para movernos por el texto usaremos las teclas `jklñ`. Pero tenemos muchos más comandos para movernos por el texto, como `gg` que nos llevará a la primera línea del documento, mientras que `G` nos llevará a la última. `0` nos llevará al inicio de la frase y `$` al final.

En Vim tenemos que diferenciar una *palabra* de una *PALABRA*. Una *palabra* se diferencia por puntos, guiones u otros caracteres mientras que una *PALABRA* se diferencia por espacios. `e` nos lleva al final de las *palabras* mientras que `E` sirve para el final de las *PALABRAS*. `w` y `W` hacen lo mismo pero para el inicio de las palabras y por último, `b` y `B` es igual que el anterior pero hacia atrás. `{` y `}` nos mueven al inicio y al final del párrafo.

En el primer post de está guía vimos lo que hacían comandos como `d`, `f`, `t` y `x`. No podemos olvidarnos de `y` (copiar) ni de `p` (pegar). Dependiendo de si los invocamos con mayúscula o minúscula tendrán efectos distintos en el texto. `F` y `T` irán marcha a tras, `P` pegará el texto en la misma línea, `Y` actuará sobre la línea completa y `D` tendrá el mismo efecto que `d$`. Por último, están `ctrl+a` y `ctrl+x` que invocados sobre un número harán operaciones aritméticas de sumar o restar. Por ejemplo, `10 ctrl+a` sumará 10 al número donde tengamos el cursor, ideal para cuando editamos CSS.
