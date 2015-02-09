# Aprende a usar Vim desde cero: 15 - Comandos globales

En estos últimos posts hemos estado aprendiendo las bondades de los comandos del modo Ex de [Vim](http://bitelia.com/tag/curso-de-vim). Ahora que ya sabemos crear patrones y aplicarlos para sustituir diferentes elementos, va siendo hora de subir el nivel y conocer **otra de las herramientas más productivas de Vim, el comando `:global`, el cual es usado para trabajos repetitivos**. Seguro que se convierte en uno de vuestros comandos favoritos.

Como suelo hacer, **primero vamos a aprender un poco de la teoría sobre este comando y después voy a mostrar varios ejemplos** útiles que he ido recopilando, estoy seguro que os van a encantar.

## ¿Qué hace el comando `:global`?

**El comando `:global` nos permite ejecutar un comando Ex en las líneas que coincidan con el patrón que le indicquemos**. Su estructura es la siguiente (para más información consultad `:h :g`):

`:[range] global[!] /{pattern}/ [cmd]`

+ **El rango de este comando por defecto es todo el archivo**, es importante diferenciarlo de otros comandos como `:delete` por ejemplo, que actçua sobre la línea en la que estemos posicionados.
+ `{pattern}` es el **patrón de busqueda**. Como vimos en el [post anterior](http://bitelia.com/2015/01/como-usar-vim-14), podemos dejarlo en blanco para que tome el patrón de la búsqueda anterior.
+ `[cdm]` no es más que **el [comando](http://bitelia.com/tag/comandos) Ex que queramos ejecutar**, si lo dejamos en blanco por defecto utilizará el comando `:print`. Perfecto para que nos muestre el lugar de actuación antes de usar un comando.
+ Os habréis fijado en el signo de exclamación junto a `global[!]`. Todo lo que está entre corchetes es opcional escribirlo. En este caso, **si añadimos la exclamación (o escribimos `:vglobal`) el comando actuará sobre las líneas que no coincidan** con el patrón, muy útil.

Ahora veamos unos ejemplos en la vida real donde podamos usar estos comandos.

## Ejemplos para dominar el comando `:global`

**Extraer contenido tags HTML con `:g/re/d`**

Si habéis escrito alguna vez [HTML](http://bitelia.com/tag/html) sabéis que para poner listas se puede usar el tag `<ol><li">Contenido</li></ol>`. Supongamos que tenemos un archivo en el solo **queremos quedarnos con el contenido de una lista con multitud de elementos**, es decir, queremos deshacernos de esas etiquetas automáticamente porque borrarlas a mano es una lata. Para ello haríamos lo siguiente.

1. `/\v\<\/?\w+>` primero hacemos la búsqueda. Busca un `\<` y un `\/?` después si existe. A la búsqueda le siguen uno o más caracteres `\w+` y termina con un `>`. Si no sabéis hacer expresiones regulares os recomiendo que las aprendáis, son muy útiles.
2. `:g//d` ahora ejecutamos el comando, lo dejamos vacío y adoptará el contenido de la expresión regular (`re`) anterior. La `g` es el comando `global` y la `d` es `delete`.

**Quedarnos solo con los enlaces de un texto HTML con `v/re/d`**

Recordemos que el comando `:vglobal` (abreviado `:v`) afectará a todo menos a nuestro patrón. Este es un ejemplo sencillito:

`:v/href/d`

Se traduce en 'elimina todo menos las líneas que contengan un `href`'. Hemos usado un simple comando para quedarnos con lo que nos interesa.

**Recoger tareas pendientes con `g/re/p` u otros**

`//TODO: crear ua función que haga...` **Esta es una buena forma de manejar nuestras tareas en el código**. En este caso hemos usado un comentario en un archivo [JavaScript](http://bitelia.com/tag/javascript), pero como están desperdigados por el archivo estaría bien recogerlso para saber que es lo que nos toca hacer ahora.

+ `:g/TODO` es una opción, no hace falta la `p` porque es el comportamiento por defecto.
+ `g/TODO/yank A` ahora las hemos copiado al registro`A`. Podemos ver el contenido con `:reg a`
+ `g/TODO/t$` copia las tareas al final del archivo.

**Ordenar contenido de propiedades CSS alfabéticamente**

`:g/{/ .+1,/}/-1 sort` Ordena alfabeticamente lo que este entre `{` y `}`, suponiendo que los corchetes están en líneas aparte de su contenido.

## Posts anteriores sobre cómo usar Vim

[1: Introducción a Vim](http://bitelia.com/2014/09/como-usar-vim-1-introduccion-a-vim)
[2: Editar al estilo Vim](http://bitelia.com/2014/09/como-usar-vim-cero-2)
[3: El modo normal](http://bitelia.com/2014/09/como-usar-vim-3)
[4: El modo insertar](http://bitelia.com/2014/10/como-usar-vim-4)
[5: El modo visual](http://bitelia.com/2014/10/como-usar-vim-5)
[6: El modo de comandos](http://bitelia.com/2014/10/como-usar-vim-6)
[7: Editar múltiples archivos](http://bitelia.com/2014/10/como-usar-vim-7)
[8: Paneles y pestañas](http://bitelia.com/2014/11/como-usar-vim-8)
[9: Cómo moverse rápido por los archivos](http://bitelia.com/2014/11/como-usar-vim-9)
[10: Cómo moverse rápido por los archivos 2](http://bitelia.com/2014/11/como-usar-vim-10)
[11: Dominar los registros](http://bitelia.com/2014/11/como-usar-vim-11)
[12: El poder de las macros](http://bitelia.com/2014/12/como-usar-vim)
[13: Patrones](http://bitelia.com/2014/12/como-usar-vim-13)
[14: Sustituciones](http://bitelia.com/2015/01/como-usar-vim-14)