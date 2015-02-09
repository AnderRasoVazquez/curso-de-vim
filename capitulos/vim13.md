# Aprende a usar Vim desde cero: 13 - Patrones

Ya estamos en la recta final del curso sobre [cómo usar Vim](http://bitelia.com/tag/curso-de-vim) desde cero. En estos últimos capítulos **hablaremos sobre los métodos que podemos usar para buscar texto (o patrones) y hacer sustituciones**. También me gustaría hacer después una entrega final en la que haga un recopilatorio de los mejores plugins que he encontrado durante todo este tiempo usando Vim.

En la entrega de hoy, vamos a hablar de la búsqueda de patrones específicos. En los [editores de código](http://bitelia.com/2014/09/editores-codigo-mas-versatiles) más convencionales, solemos encontrar una función en un menú o una caja de texto en la que podemos insertar el texto a encontrar y hacer una búsqueda hacia adelante o hacia atrás. En algunos incluso podemos usar **expresiones regulares en nuestras búsquedas, una de las mejores funciones que podemos esperar de un buen editor de texto**. Vim también hace uso de esa función, con la diferencia que dependiendo del *modo de búsqueda* especificado escribiremos el patrón de forma diferente.

**Para hacer una búsqueda hacia adelante simplemente pulsaremos`/` desde el modo normal (hacia atrás es con `?`), introduciremos el texto a buscar y pulsaremos la tecla `enter`.** Si queremos que nos redirija al siguiente resultado pulsaremos `n` y para el anterior será con `N`.

## ¿Tener en cuenta las mayúsculas?

Podemos decirle a Vim que tome o no en cuenta las mayúsculas de forma global o especificarlo en cada búsqueda. Si **no queremos que Vim tome en cuenta las mayúsculas** pondremos en nuestro `.vimrc` lo siguiente:

`set ignorecase`

Sin importar la opción que tengamos definida por defecto, podemos **especificar si queremos que las tome en cuenta en la propia búsqueda** mediante los elementos `\c` y `\C`. El primero hará que no tenga en cuenta las máyusculas mientras que el segundo sí lo hará, de forma que podemos esperar el comportamiento siguiente (no importa si los ponemos al principio o al final):

+ `hola` encontrará (si activamos *ignorecase*) `Hola hola HoLa`
+ `hola` encontrará (sin *ignorecase*) `hola`
+ `\chola` encontrará (sin importar la opción por defecto) `hola Hola HoLa`
+ `hola\C` encontrará (sin importar la opción por defecto) `hola`

De todas formas. **tenemos otro amigo más en nuestro repertorio**:

`set smartcase`

Cuya función es la de **tomar en cuenta las mayúsculas si en nuestra búsqueda incluímos una**. De no ser así, buscará todos los resultados posibles.

## Expresiones regulares en Vim

Supongamos que tenemos un código como el siguiente en un archivo `.css` de nuestra página web y nuestro objetivo es buscar todos los colores hexadecimales que haya.

`a { color: #0000EE; }` (ejemplo)

Lo primeto que tendríamos que hacer es una búsqueda con el siguiente contenido (no os asustéis lo vamos a reducir mucho):

`#\([0-9a-fA-F]\{6}\|[0-9a-fA-F]\{3}\)`

Explicar las expresiones regulares va más hallá de los propósitos de este curso pero voy a intentar explicar brevemente su funcionamiento. Lo que hace esta expresión es buscar las palabras que empiecen por `#` y que contengan 6 o 3 caracteres con un contenido alfanumérico. Los `\` sirven para escapar caracteres que tienen un significado especial.

Escribir esto cada vez que queremos hacer una búsqueda así es muy doloroso a la par que poco productivo. Para ello tenemos `\v` también llamado *very magic search*.

`\v#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})`

Con esto conseguiremos el mismo efecto y hecmos recortado la expresión, pero podemos reducirla todavía más:

`\v#(\x{6}|\x{3})`

En vez de escribir `[0-9a-fA-F]` podemos utilizar una clase para caracteres llamada `\x` que tiene el mismo contenido (para más información sobre estas clases `:h /character-classes`).

**NOTA**: Si usamos busquedas para palabras como `a.k.a.` que tienen puntos en medio, no podríamos usar la búsqueda `/a.k.a.` ya que el punto significa *todos los caracteres* y podría darnos resultados que no queremos. Para hacerlo bien escaparíamos los puntos `/a\.k\.a\.` o **usaríamos el *very nomagic* search** que se hace con `\V` de la siguiente manera: `/\Va.k.a.`


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