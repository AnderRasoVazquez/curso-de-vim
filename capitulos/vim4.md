# Cómo usar Vim: 4 - El modo insertar

Bienvenido a la cuarta entrega del curso sobre cómo usar Vim, el editor de código modal que te haceser más productivo. Esta vez toca que hablemos del modo insertar.

La mayoría de los comandos de Vim se ejecutan en otros modos, pero algunas de las funciones también se pueden usar en el modo insertar. En esta entrada, vamos explorar algunos de esos comandos y veremos cómo insertar caracteres especiales. 

También hablaremos del modo reemplazar, el cual sobreescribe los caracteres existentes en el documento por lo que escribamos. Veremos ejemplos de cúando puede sernos de utilidad esta función y descubriremos el modo insertar-normal (*insert normal mode*), un submodo que nos permite usar un comando y volver directos al modo insertar.

En este modo también se puede usar la función de autocompletado de Vim, pero eso es algo que lo veremos más adelante.

## Haz correcciones al instante desde el modo Insertar

Cometer un fallo en Vim no significa que tengamos que cambiar de modo para poder corregirlo. Lo podemos hacer directamente desde el modo insertar. Además de usar la tecla de retroceso tenemos más combinaciones que permitirán una corrección rápida y precisa. Aprender mecanografía para usar correctamente Vim es esencial. No podremos ser productivos si tenemos que estar mirando al teclado por cada caracter que tenemos que insertar en nuestro documento. Cuando ya hemos dominado nuestro teclado al aprender caligrafía llegamos a un momento en el que cuando escribimos desarrollamos una especie de sexto sentido en el que sabemos que nos vamos a equivocar en una tecla justo antes de escribirla, es como si nos hubiéramos tropezado. Es cierto que podemos usar la tecla retroceso para corregir rápidamente ese traspiés. Pero, ¿qué pasa cuando el fallo ocurre al inicio de la palabra?

Mecanógrafos expertos recomiendan medidas drásticas como eliminar las palabras completas, es una medida que podemos aplicar si podemos escribir al menos 60 palabras por minuto ya que solo nos tomaría un segundo escribir la palabra. También podríamos salirnos del modo, borrar la palabra y después pulsar `A` para volver al modo insertar. Pero esta vez vamos a usar comandos que funcionan tanto en el modo insertar, en el modo de comandos e incluso en la shell Bash.

><Ctrl-h> Borra un caracter hacia atrás (igual que el retroceso)
><Ctrl-w> Borra una palabra hacia atrás
><Ctrl-u> Borra hasta el principio de la línea
><Ctrl-r>0 Pega el texto que hayamos copiado al registro 0 (el de por defecto)
><Ctrl-r>= Podemos hacer operaciones aritméticas e insertará el resultado
><Ctrl-o> Entra la modo insertar-normal

El modo insertar-normal de Vim es un modo que nos regala una bala. Esa bala es uncomando que podremos disparar, después nos devuelve directamente al modo insertar. Podremos usarlo por ejemplo para situar nuestra vista al centro de la pantalla como si hubiéramos hecho scroll hacia abajo `<Ctrl-o>zz`.

## Insertar caracteres especiales

En Vim podremos insertar cualquier caracter por su código númerico, algo fantástico para cuando queremos insertar elementos que no aparecen en nuestro teclado. Lo único que haremos será escribir `<Ctrl-v>{código}`, por ejemplo, al caracter `A` le corresponde `<Ctrl-v>065`. Si quieres saber cuál es el código numérico de cualquier caracter sitúate sobre el desde el modo normal y pulsa `ga`.

<C-v>{123} Insertar caracter por código decimal
<C-v>u{1234} Insertar caracter por código hexadecimal
<C-k>{char1}{char2} Ejemplo `¿` == <Ctrl-k>?I

## Sobreescribe el texto con el modo reemplazar

El modo reemplazar es idéntico al modo insertar con la peculiaridad de que si escribimos y delante tenemos texto, en lugar de moverlo un espacio hacia adelante, escribe sobre él sustituyendo el caracter que teníamos delante por el que hemos escrito. Para entrar a ese modo lo haremos simplemente pulsando la tecla `R`.

Otra variante es el modo reemplazar para un solo caracter, se invoca con `r` y es muy útil para sustituir el caracter que queramos corregir. `r` nos devuelve al modo normal, mientras que `s` hace lo mismo pero nos deja en el modo insertar. Si lo que queremos corregir es la capitalización de un caracter lo podemos hacer pulsando `~`, es más rápido que pasarlo a mayúsculas o minúsculas a mano.
