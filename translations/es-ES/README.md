# Principios para escribir CSS idiomático y consistente

El siguiente documento ofrece una guía razonable de estilo para el desarrollo
de CSS.  No es mi intención ser preceptivo y no deseo imponer mis preferencias
de estilo en el código de otras personas. Sin embargo esta guía anima
enérgicamente a que se utilicen los patrones existentes, que son de sentido
común.

Este es un documento vivo y nuevas ideas son siempre bienvenidas. Por favor
contribuya.

[CSS idiomático en inglés (Original)](https://github.com/necolas/idiomatic-css/)


## Tabla de contenido

1. [Principios generales](#general-principles)
2. [Espacios en blanco](#whitespace)
3. [Comentarios](#comments)
4. [Formato](#format)
5. [Ejemplos prácticos](#example)

[Agradecimientos](#acknowledgements)

[Licencia](#license)

<a name="general-principles"></a>
## 1. Principios generales

> "Parte de ser un buen administrador al crear un proyecto exitoso es darse
> cuenta que escribir código para uno mismo es una Mala Idea™. Si miles de
> personas están utilizando tu código, entonces escríbelo con la máxima
> claridad, no con tus preferencias personales de cómo ser inteligente con la
> especificación." - Idan Gazit

* No trate de optimizar prematuramente su código, siga siendo legible y comprensible.
* Todo el código en una aplicación debe parecer como si sólo una persona lo
  hubiese escrito, no importa cuántas personas hayan contribuido.
* Fuerce a que se respete el estilo acordado.
* Si tiene dudas utilice los patrones de uso común.


<a name="whitespace"></a>
## 2. Espacios en blanco

Sólo debe existir un estilo en el código de su proyecto. Siempre sea
consistente en el uso de los espacios en blanco. Utilice espacios en blanco
para mejorar la legibilidad.

* _Nunca_ mezcle espacios y tabulaciones para indentar.
* Elija entre indentaciones blandas (espacios) o tabulaciones reales. Apéguese
  a su elección sin fallo. (Preferencia: espacios)
* Si utiliza espacios, elija el número de caracteres a usar para cada nivel de
  indentación.  (Preferencia: 4 espacios)

Consejo: configure su editor para que "muestre los caracteres invisibles". Esto
le permitirá eliminar los espacios en blanco al final de las líneas, eliminar
espacios en blanco de líneas en blanco y evitar commits con basura.

Consejo: Utilice el editor [EditorConfig](http://editorconfig.org/) (o algún
equivalente) para ayudarse a mantener las convenciones básicas que han sido
acordadas en su proyecto.


<a name="comments"></a>
## 3. Comentarios

Un código bien comentado es muy importante. Tómese el tiempo necesario para
describir los componente, cómo trabajan, sus limitaciones y la forma en que
fueron construidos. No deje que otros miembros de su equipo tengan que adivinar
el propósito de un código poco común o poco obvio.

El estilo de los comentarios debe ser siempre simple y consistente con un mismo
código base.

* Coloque los comentarios en una línea nueva sobre cada objeto.
* Mantenga el largo de cada línea con un máximo razonable, por ejemplo, 80
  columnas.
* Haga un uso libre de los comentarios para separar código CSS en secciones
  discretas.
* Realice comentarios que comiencen con una letra mayúscula y con indentación
  consistente.

Consejo: configure su editor para que le ofrezca atajos para la creación de
comentarios comunes.

Ejemplos:

```css
/* ==========================================================================
   Bloque de comentario de sección
   ========================================================================== */

/* Bloque de comentario de sub-sección
   ========================================================================== */

/**
 * Pequeña descripción utilizando el formato de comentario Doxygen.
 *
 * La primer oración de una descripción larga comienza aquí y continúa en
 * esta linea durante un tiempo para finalmente terminar aquí al final de
 * este párrafo.
 *
 * Las descripciones largas son ideales para explicaciones de mayor detalle
 * y documentación. Pueden incluir ejemplos de HTML, URLs o cualquier otro
 * tipo de información que es considerada necesaria o útil.
 *
 * @tag Esto es una etiqueta llamada 'tag'
 *
 * TODO: Esto es una declaración 'todo' ("a realizar") que describe una tarea
 *   atómica (específica) a realizar posteriormente. Continua luego de 80
 *   caracteres por lo que las lineas consecutivas son indentadas con dos
 *   espacios adicionales.
 */

/* Comentario básico */
```


<a name="format"></a>
## 4. Formato

El formato del código elegido debe asegurarse de que el código: es fácil de
leer, es fácil de comentar claramente, minimiza las posibilidades de introducir
errores accidentalmente, y facilita el hallazgo de diferencias y
responsabilidades.

* Utilice un selector discreto por línea en un conjunto de reglas con multi
  selectores.
* Incluya un solo espacio antes de la llave de apertura en un conjunto de
  reglas.
* Incluya una declaración por línea en un bloque de declaraciones.
* Utilice un nivel de indentación para cada declaración.
* Incluya un solo espacio luego de los dos puntos en una declaración.
* Utilice minúsculas y valores hexadecimales abreviados, ejemplo `#aaa`.
* Utilice comillas simples o dobles pero de forma consistente. Se prefiere la
  utilización de comillas dobles, ejemplo `content: ""`.
* Utilice comillas en los valores de los atributos de los selectores, ejemplo
  `input[type="checkbox"]`.
* _Siempre que pueda_, evite especificar valores de 0, por ejemplo `margin:
  0`.
* Incluya un espacio luego de cada coma en las propiedades separadas por comas
  o en los valores de las funciones.
* Siempre incluya un punto y coma al final de la línea de la última declaración
  en un bloque de declaraciones.
* Coloque la llave de cierre de un conjunto de reglas en la misma columna que
  el primer carácter del conjunto.
* Separe cada conjunto de reglas con una línea en blanco.

```css
.selector-1,
.selector-2,
.selector-3[type="text"] {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selector-a,
.selector-b {
    padding: 10px;
}
```

#### Orden de las declaraciones

Las declaraciones deben ser ordenadas con un único principio. Mi preferencia es
que las propiedades relacionadas con la estructura (por ejemplo, de posición y
box-model) sean declaradas antes que las demás.

```css
.selector {
    /* Posicionamiento */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Display & Box Model */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Otras */
    background: #000;
    color: #fff
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

El ordenamiento alfabético es también muy popular, pero la desventaja es que
las propiedades relacionadas no se mantienen juntas. Por ejemplo, los
desplazamientos de posición no permanecen juntos y las propiedades de box-model
pueden ser esparcidas a través del bloque de declaraciones.

#### Excepciones y pequeñas desviaciones

Bloques grandes de una sola declaración pueden ser ligeramente diferentes,
utilizando el formato de una sola línea. En este caso, un espacio debe ser
incluido luego de la llave de apertura y antes de la llave de cierre.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Grandes propiedades de valores separados por coma -tal como una colección de
gradientes o sombras- pueden ser organizadas en múltiples líneas en un intento
de mejorar la legibilidad y producir visualizaciones de diferencias más
útiles.  Hay varios formatos que pueden ser utilizados: uno, por ejemplo, es
mostrado más abajo.

```css
.selector {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

### Preprocesadores: consideraciones a formatos adicionales

Cada preprocesador de CSS tiene sus características, funcionalidades y
sintaxis.  Sus convenciones deben extenderse para adaptarse a las
particularidades de cada preprocesador en uso. La siguiente guía está referida
a Sass.

* Limítese a anidar con 1 nivel de profundidad. Corrija cualquier anidado de
  más de 2 niveles. Esto previene que existan selectores de CSS muy
  específicos.
* Evite realizar un gran número de reglas anidadas. Sepárelas cuando la
  legibilidad comience a ser afectada. Se prefiere evitar el anidado que se
  extiende a más de 20 líneas.
* Siempre coloque las declaraciones `@extend` en la primer línea de los bloques
  declarativos.
* Dónde sea posible, agrupe las declaraciones `@include` en la parte superior
  del bloque declarativo, luego de las declaraciones `@extend`.
* Considere prefijar funciones personalizadas con `x-` u otro separador. Esto
  ayuda a evitar cualquier confusión potencial con una función nativa de CSS, o
  entrar en conflicto con una función de alguna librería.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}
```


<a name="example"></a>
## 5. Ejemplos prácticos

Un ejemplo de varias convenciones.

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/**
 * Diseño de columna con desplazamiento horizontal.
 *
 * Esto crea una sola fila de altura completa, culumnas en linea que
 * pueden navegarse horizontalmente dentro de su padre.
 *
 * Ejemplo HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * Contenedor de grilla
 *
 * Solo debe contener hijos `.cell`.
 *
 * 1. Elimina los espacios en blanco entre celdas
 * 2. Previene que las celdas salten de linea
 */

.grid {
    height: 100%;
    font-size: 0; /* 1 */
    white-space: nowrap; /* 2 */
}

/**
 * Celdas de grilla
 *
 * No tienen un ancho definido por defecto. Usar junto con clases `.cell-n`.
 *
 * 1. Define el espacio entre celdas
 * 2. Restablece los espacios en blanco heredado de `.grid`
 * 3. Restablece el tamaño de fuente heredado de `.grid`
 */

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    height: 100%;
    padding: 0 10px; /* 1 */
    border: 2px solid #333;
    vertical-align: top;
    white-space: normal; /* 2 */
    font-size: 16px; /* 3 */
}

/* Estados de las celdas */

.cell.is-animating {
    background-color: #fffdec;
}

/* Dimensiones de las celdas
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Modificadores de celdas
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


## Translations

* [English](https://github.com/necolas/idiomatic-css/tree/master)
* [Bahasa Indonesia](https://github.com/necolas/idiomatic-css/tree/master/translations/id-ID)
* [Česky](https://github.com/necolas/idiomatic-css/tree/master/translations/cs-CZ)
* [Dansk](https://github.com/necolas/idiomatic-css/tree/master/translations/da-DK)
* [Deutsch](https://github.com/necolas/idiomatic-css/tree/master/translations/de-DE)
* [Español](https://github.com/necolas/idiomatic-css/tree/master/translations/es-ES)
* [Français](https://github.com/necolas/idiomatic-css/tree/master/translations/fr-FR)
* [Italiano](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [日本語](https://github.com/necolas/idiomatic-css/tree/master/translations/ja-JP)
* [한국어](https://github.com/necolas/idiomatic-css/tree/master/translations/ko-KR)
* [Nederlands](https://github.com/necolas/idiomatic-css/tree/master/translations/nl-NL)
* [Polski](https://github.com/necolas/idiomatic-css/tree/master/translations/pl-PL)
* [Português (Brasil)](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Русский](https://github.com/necolas/idiomatic-css/tree/master/translations/ru-RU)
* [Srpski](https://github.com/necolas/idiomatic-css/tree/master/translations/sr-SR)
* [Türkçe](https://github.com/necolas/idiomatic-css/tree/master/translations/tr-TR)
* [正體中文](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-TW)
* [简体中文](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-CN)


<a name="acknowledgements"></a>
## Agradecimientos

Gracias a todos los que han proporcionado traducciones y contribuido en
[idiomatic.js](https://github.com/rwldrn/idiomatic.js).
Ha sido fuente de inspiración, referencia y guía.

<a name="license"></a>
## Licencia

_Principios para escribir CSS idiomático y consistente_ por Nicolas Gallagher está licenciado bajo [Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/). Esto se aplica a todos los documentos y traducciones en este repositorio.

Basado en un trabajo de
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).
