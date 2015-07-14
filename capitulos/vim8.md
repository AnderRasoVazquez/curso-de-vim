Aprende a usar Vim desde cero: 8 – Paneles y pestañas

Ya son 8 semanas escribiendo sobre cómo usar Vim, los que me hayáis podido seguir hasta aquí podéis sentiros orgullosos. Hemos tocado los temas más básicos con los que poder manejar Vim con un poco de soltura, pero ahora toca expandir los conocimientos un poquito más. En cuanto a hablar Vim podríamos decir que ya hemos terminado así que de ahora en adelante nos vamos a centrar en conocer las funciones adicionales de este editor de código.

En cuanto a dichas funciones que veremos en los siguientes posts, se incluyen las **macros, la administración de los registros, navegación dentro del archivo que estamos editando, búsquedas, sustituciones** y aparte de lo que se me vaya ocurriendo me gustaría dedicar un par de posts a hablar sobre los diferentes plugins que me parecen útiles. Si os interesa que hablemos más de plugins avisadme por los comentarios, yo creo que da para varios posts interesantes. De todas formas, si queréis un adelanto sobre plugins siempre podéis visitar este sensual post. Hoy hablaremos de los paneles y las pestañas de Vim, una función de la que hace tiempo que quería hablar.

## Paneles

Esto, que nosotros conocemos como paneles de emuladores de terminal como Terminator, Vim lo llama ventanas. Si habéis usado Sublime Text alguna vez, lo conoceréis como layouts. **Cuando abrimos Vim, tiene solo un panel pero podemos dividirlo tanto horizontalmente como verticalmente** con los comandos que veis en la imagen anterior o desde el modo de comandos de esta manera:


- `:sp[lit] {archivo}` divide el panel de forma horizontal, cargando el archivo si lo especificamos en el nuevo panel. Si no especificamos un archivo se divide el panel con el mismo archivo, muy útil cuando queremos estar mirando dos partes de un mismo archivo al mismo tiempo.
- `:vsp[lit] {archivo}` divide el panel de forma vertical.

Nótese que **un panel que se ha dividido con el mismo archivo no son dos instancias abiertas del archivo**. ¿Qué significa esto? Que los cambios en un panel serán reflejados en el otro automáticamente sin tener que recargar el archivo, pensad en ello como en **tener los ojos puestos en dos partes del archivo a la vez**. Podríamos movernos por los paneles usando el cursor, pero eso le quitaría el objetivo principal a Vim, dejar las manos siempre sobre el teclado. Así que vamos a ver que comandos se usan para movernos de un panel a otro. **NOTA**: Vim llama `C` a `Ctrl`.

- `<c-w>w` moverse por los paneles. Pulsaremos de forma conjunta la tecla control y `w`, soltaremos las teclas y pulsaremos `w` de nuevo.
- `<c-w>h` ir al panel de la izquierda.
- `<c-w>j` ir al panel de abajo.
- `<c-w>k` ir al panel de arriba.
- `<c-w>l` ir al panel de la derecha.
- `<c-w>c` cerrar panel. También hace lo mismo `:cl[ose]`.
- `<c-w>o` mantener el panel activo, cerrando los demás. También nos sirve `:on[ly]`.
- `<c-w>=` iguala la altura y anchura de los paneles.
- `<c-w>_` maximiza la altura del panel activo.
- `<c-w>|` maximiza el alncho del panel activo.
- `[N]<c-w>_` la alturá será de `[N]` filas.
- `[N]<c-w>|` la anchura será de `[N]` columnas.
- `:h window-moving` como siempre me gusta hacer, os dejo un **comando de ayuda** para que os acostumbréis a buscar en la documentación. En realidad, la mayoría de lo que veis escrito aquí sale de comandos de ayuda como este de Vim. Con este en concreto aparecen comandos para mover los paneles, echadles un vistazo.


##Pestañas

Sinceramente, no es que use mucho las pestañas de Vim. Puede parecer raro porque la mayoría de editores de código se vale de este diseño para editar múltiples archivos simultáneamente. Por otra parte, los paneles los uso muchísimo pero he aprendido a administrar los archivos como lo hicimos en el anterior post y es bastante más cómodo para mí. De todas formas, organizarnos con pestañas y paneles puede ser una buenísima idea, ya que podemos dividir las distintas áreas del proyecto por pestañas y en cada una tendremos paneles con los archivos que pertenezcan a esa área. Es una idea, con la libertad que nos da Vim cada uno que se organice a su manera. Veamos los comandos que se usan para las pestañas.


- `:tabnew` abre una nueva pestaña.
- `:lcd {ruta}` cambia la ruta (la carpeta) donde apunta el panel.
- `:windo lcd {ruta}` cambia la ruta donde apuntan todos los paneles de una pestaña. Como ya he dicho antes, muy útil para organizar nuestro proyecto por áreas.
- <c-w>T mueve el panel actual a una nueva pestaña.
- :tabe[dit] {archivo} abre un archivo en una nueva pestaña
- :tabc[lose] cerrar la pestaña. Como podéis comprobar son muy parecidos a los comandos de los paneles.
- :tabo[nly] cerrar todas las pestañas menos la activa.
- :tabn[ext] {N} ir a la pestaña {N}. También nos sirve {N}gt
- :tabn[ext] ir a la siguiente pestaña. gt hará lo mismo.
- :tabp[revious] ir a la pestaña anterior. gT tiene el mismo resultado.
- :tabmove [N] sirve para mover las pestañas.
- :h tabpage por último, el comando de ayuda. Hay muchos más comandos que podemos usar para organizar las pestañas. Hemos visto los que usaremos con más frecuencia pero si queréis saber más mirad la documentación.
