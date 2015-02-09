Puede chocar mucho la forma de trabajar que tiene Vim para todos aquellos que vienen de usar otros [editores de código]. El objetivo principal de Vim es la productividad y su filosofía se centra en que no hay que levantar las manos del teclado jamás. Puede que parezca una tontería, pero si nos ponemos a pensar en las veces que dejamos el teclado para coger el ratón, con el tiempo nos ahorramos varios segundos que al cabo de un tiempo serán minutos y al final horas. No solo por el simple hecho de mover la mano fuera del teclado sino por que cuando *hablamos Vim* podemos hacer selecciones muy precisas en apenas un segundo.

Poder realizar cambios en los rextos de esta manera es muy útil, pero una de las cosas que notaremos las primeras veces que usamos Vim es la necesidad (el autoreflejo) de querer mover la mano a las teclas del dirección o al ratón. Cuando inicié el estudio de este editor, al estar acostumbrado a moverme con las teclas de dirección y sabiendo que no debería de usar el ratón para moverme por el archivo, casi me desespero. ¿Cómo iba a moverme rápido por el archivo si tenía que moverme pulsando teclas?

Los desarrolladores de Vim no son idiotas y en todos estos años de desarrollo de esta completa herramienta, han conseguido añadirle unas características llamadas *motions* cuya traducción aproximada podría ser la de *movimientos*.

## Las teclas de dirección te hacen más lento

- Imagen del remapeo

Ya hemos hablado en otras ocasiones de algunas de estas *motions*, pero al ser una función tan importante para nuestra productividad merece que nos detengamos un poco en ellas. Además, voy a dar unos consejos para que nos acostumbremos a usar Vim sin las teclas de dirección y sin el ratón. Lo priemro de todo es que debemos reposar siempre los dedos en la línea media del teclado. Las teclas para movernos en Vim por defecto en el teclado inglés serán `h` (izquierda), `j` (línea abajo), `k` (línea arriba), `l` (derecha) pero ya vimos en un post [anterior] cómo cambiarlas al equivalente del teclado español si queríamos. Yo las he dejado por defecto, ya que estoy dejando el teclado qwerty y empezando a usar dvorak, así que para mí no tiene mucho sentido cambiarlas.

	" inhabilitar las teclas de dirección
	noremap <Up> <Nop>
	noremap <Down> <Nop>
	noremap <Left> <Nop>
	noremap <Right> <Nop>

A veces no podemos evitar ir a las teclas de dirección, por esa razón os he dejado unas líneas para que insertéis en vuestro `.vimrc`, con ellas quitaréis el hábito de ir a las teclas de dirección. Incluso podéis remapearlas para que tengan una fucnión máś útil.

## Usa las *motions* para moverte más rápido por el archivo

- imagen frase

Hemos hablado antes de las *motions* cuando hablábamos de los comandos que podíamos usar en los diferentes modos de Vim. Para tenerlo un poco más ordenado he pensado en dejaros esta lista:

+ **j** bajar un número de línea, es decir, líneas separadas por un retorno de carro. 
+ **gj** bajar una línea visible, comportamiento habitual de los editores normales.
+ **k** sube un número de línea.
+ **gk** sube una línea como lo haría un editor corriente.
+ **0** va al principio de la línea real.
+ **g0** va al principio de la línea visible en pantalla.
+ **^** va al primer carácter no en blanco de la línea real.
+ **g^** va al primer carácter no en blanco de la línea visible en pantalla.
+ **$** va al final de la línea real.
+ **g$** va al final de la línea visible en pantalla.
+ **w** va hacia el principio de la siguiente palabra.
+ **b** va hacia atrás, al principio de la palabra actual o de la anterior.
+ **e** va al final de la palabra actual y si estamos allí, de la siguiente palabra.
+ **ge** va al final de la palabra anterior.
+ **/búsqueda** muy útil para dirigirno hacia palabras concretas en el texto. Además se puede combinar por ejemplo con `d` para borrar desde nos encrontramos hasta donde está nuestra búsqueda `d/palabra`.
+ **f{carácter}** va hacia delante hasta que encuentre el carácter.
+ **F{carácter}** lo mismo que el anterior pero en dirección contraria.
+ **t{carácter}** va hacia adelante y se para en una columna antes del carácter.
+ **T{carácter}** lo mismo que el anterior pero en dirección contraria.
+ **;** repite la última búsqueda de carácter.
+ **,** da la vuelta a la última búsqueda.

## Un plugin útil para movernos

Normalmente con esto tendremos suficiente para movernos por el archivo pero hay plugins que nos pueden ayudar. El nombre de uno de ellos es [**vim-easymotion**](https://github.com/Lokaltog/vim-easymotion).