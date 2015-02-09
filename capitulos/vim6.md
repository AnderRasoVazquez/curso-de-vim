# Aprende a usar Vim desde cero: 6 - El modo de comandos

Bienvenido a la sexta entrega del curso sobre cómo usar Vim, el editor de código modal que te hace ser más productivo. Esta vez toca que hablemos del modo de comandos.

Vim hereda comandos de su ancestro vi, con el cual se popularizó el modo de edición modal de archivos. A su vez, vi se basa en un editor antiguo llamado ex, esa es la razón por la que hoy en día tenemos comandos ex en Vim. La sangre de los antiguos editores de Unix corre por las venas de Vim. En este post hablaremos de como podemos usar el modo de comandos de Vim para realizar comandos en diferentes líneas, haciendo nuestras tareas habituales mucho más rápido y de esa manera, para tener más tiempo libre para dedicar a otros menesteres (o para picar más y más código si todavía te quedan fuerzas).

Esta sección de la guía es poca teoría y mucha práctica así que harás bien en tener Vim abierto desde la terminal para ir practicando los comandos a medida que vas leyendo. Empecemos con ello.

## Te presento la línea de comandos de Vim

Lo fundamental que hay que saber es que para entrar al modo de comandos de Vim hay que pulsar `:` y no lo olvides porque en Vim lo usarás mil y una veces. En este modo se escriben los comandos y se ejecutan pulsando `enter`. También hay otro modo de comandos especializado en búsquedas que se activa desde el modo normal pulsando `/`, pero hablaremos de él en detalle en otra ocasión. Desde este modo también podremos abrir pestañas, ventanas y manejar iferentes archivos pero lo veremos en los próximos posts.

+ `:[rango]d[elete]` **borra** las líneas especificadas.
+ `:[rango]y[ank]` **copia** líneas.
+ `:[línea]put` **pega** el texto en la línea descrita.
+ `:[rango]co[py] {dirección}` **copia** líneas especificadas **debajo de la dirección**. También se le invoca pulsando `:t`.
+ `:[rango]m[ove] {dirección}` **mueve** líneas especificadas **a la dirección** elegida.
+ `:[rango]j[oin]` **junta** líneas.
+ `:[rango]norm[al] {comando}` **ejectuda comandos del modo normal** en las líneas especificadas.
+ `:[rango]s[ubstitute]/{pattern}/{string}/[flags]` **Reemplaza las ocurrencias** de {pattern} con {string} en cada línea especificada.
+ `:[rango]g[lobal]/{pattern}/[comando]` **ejecuta un comando** en cada línea especificadas que coincidan pon el **patrón de búsqueda** {pattern}.
+ `:[rango]p[rint]` su misión es **mostrarnos el rango**, perfecto para practicar.
+ `:h [comando]` **información detallada de cada comando**.

En la lista anterior, podemos ver diferentes comandos que podemos ejecutar. Es importante saber que no hace falta que escribamos la palabra completa. En el caso de `delete` podremos usar solo `d`, y en el de `normal` podríamos usar solo `norm`. En cuanto al rango de alcance de nuestro comando, tendremos que aprender a definirlo. Para ello hay que aprender como denomina Vim a las posiciones:

+ `1` **primera línea** del arhivo.
+ `$` **última línea** del archivo.
+ `0` **línea encima de la primera** (no existe la línea 0), se usa para mover o pegar texto encima de la primera línea.
+ `.` el punto, es la **línea está ubicado nuestro cursor**.
+ `'m` **línea que contiene la marca** (hablaremos de las marcas más adelante) *m*.
+ `'<` inicio de la **seleción visual**, `'>` final de la **selección visual**. Si seleccionamos unas líneas en el modo visual y seguido pulsamos `:` **se creará el siguiente rango automáticamente**: `:'<,'>`.
+ `%` **todo el archivo**, un atajo para el rango `:1,$`.

## Manos a la obra

Ahora que ya sabemos unos cuantos comandos y las indicaciones de posición de Vim podremos *hablar Vim* indicando los rangos de acción. Para ello, aquí os dejo un ejemplo de las funciones que podréis hacer con el comando `:[rango]p[rint]`, perfecto para practicar rangos (podréis aplicar lo que hacemos con print a otros comandos):

+ `:5p` muestra lo que hay en la línea 5.
+ `2,10p` muestra las líneas desde la número 2 hasta la 10.
+ `.,+3p` muestra la línea donde está nuestro cursor y 3 más hacia abajo (con `-` sería hacia arriba).
+ `:'<,'>p` muestra la selección visual

Ahora que ya nos hemos hecho una idea de como se definen los rangos hagamos ejemplos que podemos aplicar en una situación de verdad:

+ Hemos puesto el punto y coma final usando `A;` a una línea de JavaScript y queremos hacer lo mismo en varias líneas más. Podemos hacer una selección visual líneal con `V` y ejecutar el comando en todas ellas con `:'<,'>norm .` (recordad que el `.` es para repetir el último comando.)
+ `.m0` mover la línea en la que estamos al principio del archivo.
+ `4t9` copiar la línea 4 debajo de la línea 9
+ `%s/Madrid/Bilbao` reemplaza Madrid por Bilbao en todo el archivo.
+ `@:` repetir el último comando.

Y lo que se os vaya ocurriendo a vosotros.