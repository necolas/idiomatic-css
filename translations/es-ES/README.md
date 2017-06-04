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
5. [Nomenclatura](#naming)
6. [Ejemplos prácticos](#example)
7. [Organización](#organization)
8. [Construcción y distribución](#build-and-deployment)

[Agradecimientos](#acknowledgements)


<a name="general-principles"></a>
## 1. Principios generales

> "Parte de ser un buen administrador al crear un proyecto exitoso es darse
> cuenta que escribir código para uno mismo es una Mala Idea™. Si miles de
> personas están utilizando tu código, entonces escríbelo con la máxima
> claridad, no con tus preferencias personales de cómo ser inteligente con la
> especificación." - Idan Gazit

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
* Evite los comentarios al final de las líneas.
* Mantenga el largo de cada línea con un máximo razonable, por ejemplo, 80
  columnas.
* Haga un uso libre de los comentarios para separar código CSS en secciones
  discretas.
* Realice comentarios que comiencen con una letra mayúscula y con indentación
  consistente.

Consejo: configure su editor para que le ofrezca atajos para la creación de
comentarios comunes.

#### Ejemplo de CSS:

```css
/* ==========================================================================
   Bloque de comentario de sección
   ========================================================================== */

/* Bloque de comentario de sub-sección
   ========================================================================== */

/*
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
 * @todo Esto es una declaración 'todo' ("a realizar") que describe una tarea
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


<a name="naming"></a>
## 5. Nomenclatura

La nomenclatura es difícil, pero muy importante. Es una parte crucial del
proceso de desarrollo y mantenimiento del proyecto, y le asegura a usted tener
una interfaz relativamente escalable entre su código HTML y CSS.

* Evite la _sistemática_ utilización de abreviaciones en los nombres de las
  clases. No haga las cosas difíciles de entender.
* Utilice nombres claros y meditados para las _clases HTML_.
* Elija un patrón comprensible y consistente de nombres que tengan sentido
  tanto para los archivos HTML como para los archivos CSS.
* Los selectores para los componentes deben utilizar nombres de clases; evite
  la utilización de etiquetas genéricas e ids únicos.


```css
/* Ejemplo de código con nombres incorrectos */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Ejemplo de código con nombres correctos */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. Ejemplos prácticos

Un ejemplo de varias convenciones.

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/*
 * Ejemplo HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Prevent inline-block cells wrapping */
    white-space: nowrap;
    /* Remove inter-cell whitespace */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Set the inter-cell spacing */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Reset white-space */
    white-space: normal;
    /* Reset font-size */
    font-size: 16px;
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


<a name="organization"></a>
## 7. Organización

La organización del código es una parte importante en cualquier base de código
CSS, y crucial para grandes bases de código.

* Separe las distintas partes de código de forma lógica.
* Utilice archivos independientes (unidos por un proceso de construcción) para
  ayudar a separar código para distintos componentes.
* Si utiliza un preprocesador, abstraiga código común en variables para el
  color, la tipografía, etc.


<a name="build-and-deployment"></a>
## 8. Construcción y distribución

Los proyectos deben siempre intentar incluir algunos medios genéricos para que
el código pueda ser verificado, probado, comprimido y versionado para luego ser
utilizado en producción. Para esta tarea,
[grunt](https://github.com/cowboy/grunt), de Ben Alman es una excelente
herramienta.


<a name="acknowledgements"></a>
## Agradecimientos

Gracias a todos los que han contribuido en
[idiomatic.js](https://github.com/rwldrn/idiomatic.js).
Ha sido fuente de inspiración, referencia y guía.
