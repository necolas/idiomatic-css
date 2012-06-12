# Principios para escribir CSS consistentes e idimomáticos

El siguiente documento perfila una guía de estilo razonable para el desarrollo de CSS.
No se pretende ser preceptino y no pretendo imponer mis preferencias de estilo en el 
código de otras personas. No obstante, estas directrices recomiendan energéticamente
el use de pautas ya existentes, comunes y razonables.

Este es un documento vivo y las nuevas ideas son siempre bienvenidas. Aportad por favor.


## Traducciones

* [Italian](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [Portuguese](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Serbian](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)
* [Spanish](https://github.com/necolas/idiomatic-css/tree/master/translations/es-ES)


## Tabla de contenido

1. [Principios generales](#general-principles)
2. [Espacios en blanco](#whitespace)
3. [Comentarios](#comments)
4. [Formatos](#format)
5. [Denominación](#naming)
6. [Ejemplos prácticos](#example)
7. [Organización](#organization)
8. [Construcción y despliegue](#build-and-deployment)

[Agradecimientos](#acknowledgements)


<a name="general-principles"></a>
## 1. Principios generales

> "Una parte de ser un buen administrador de un proyecto existoso es darse cuenta
> de que escribir código para uno mismo es Una Mala Idea™. Si miles de personas usan
> su código, entonces escriba tu código buscando la mayor claridad posible, no según 
> sus preferencias personales sobre como ser ingenioso con la especificación" - Idan Gazit

* Todo código en cualquier repositorio debe parecer escrito por una misma persona, 
  sin importar cuantos hayan contribuido.
* Hacer cumplir estrictamente el estilo acordado.
* De haber dudas, utilize pautas comunes ya existentes.


<a name="whitespace"></a>
## 2. Espacios en blanco

Solo debe existir un estilo a lo largo de las fuentes de su proyecto. Sea siempre consistente
en el uso de los espacios en blanco. Use los espacios en blanco para mejorar la legibilidad.

* _Nunca_ mezcle espacios y tabulaciones para indentar.
* Elija entre indentaciones lógicas (espacios) o tabulaciones reales. Ciñase a esa elección 
  siempre. (Preferentemente: espacios)
* Si utiliza espacios, elija el número de carácteres por nivel de indentación.
  (Preferentemente: 4 espacios)

Consejo: Configure su editor para "mostrar invisibles". Esto le permitirá eliminar espacios
en blanco al final de la linea, eliminar espaciados involutarios y evitar polución en los commit.


<a name="comments"></a>
## 3. Comentarios

Comentar bien el código es extremandamente importante. Tomese tiempo para describir componentes,
como trabajan, sus limitaciones y la manera en que están construidos. No deje
a otros del equipo adivinar el proposito de un código átipico y poco evidente.

Es estilo de los comentarios debe ser simple y consistente en el mismo repositorio.

* Situe los comentarios en una nueva linea sobre el objetivo.
* Evite comentarios de fin de linea.
* Ciña la longitud de linea a un máximo sensato, p.ej. 80 columnas.
* Utilice libremente los comentarios para dividir el código CSS en secciones concretas.
* Use "sentence case" comments and consistent text indentation.

Consejo: configure su editor para proveerse de atajos para mostrar la salida siguiendo las pautas
acordadas.

#### CSS de ejemplo:

```css
/* ==========================================================================
   Bloque del comentario de sección
   ========================================================================== */

/* Bloque de la Sub-sección
   ========================================================================== */

/*
 * Bloque del comentario de grupo.
 * Ideal para aclaraciones multi-linea y documentación.
 */

/* Comentario básico */
```

#### SCSS de ejemplo:

```scss
// ==========================================================================
// Bloque del comentario de sección
// ==========================================================================

// Bloque de la Sub-sección
// ==========================================================================

//
// Bloque del comentario de grupo.
// Ideal para aclaraciones multi-linea y documentación.
//

// Comentario básico
```


<a name="format"></a>
## 4. Formato

El formato elegido debe asegurar que ese código es: facil de leer; facil de
comentar con claridad; minimiza las posibilidades es introducir errores
accidentalmente; y que resulte útil en diffs y blames.

1. Un selector concreto por linea en las reglas con multiples selectores.
2. Un espacio único anterior a la llave de apertura del conjunto de reglas.
3. Una delcaración por linea en bloque declarativo.
4. Un nivel de indentacion por cada declaración.
5. Un espacio únido después de los dos puntos de una declaración.
6. Incluir siempre un punto y coma al final de la última declaración en un
   bloque declarativo.
7. Situe la llave de cierre del conjunto de reglar es la misma columna que 
   el primer caracter del conjunto.
8. Separe cada conjunto de reglas por una linea en blanco.

```css
.selector-1,
.selector-2,
.selector-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

#### Orden de las declaraciones

Las declaraciones deben ser ordenadas en concordancia a un único principio. Mi
prefernecia es agrupar propiedades relacionadas y aquellas propiedades 
estructuralmente importantes (p.ej. posicionamiento y box-model) declararlas
con prioridad a propiedades tipográficas, fondos y colores.

```css
.selector {
    position: relative;
    display: block;
    width: 50%;
    height: 100px;
    padding: 10px;
    border: 0;
    margin: 10px;
    color: #fff
    background: #000;
}
```

La ordenación alfabética es también popular, pero como contra separa propiedades
relacionadas. Por ejemplo, desplazamientos de la posición no se siguen agrupando
juntos y las propiedades box-model pueden acabar esparcidos por todo el bloque 
declarativo

#### Excepciones y variacioens leves

Los bloques prolongados de declaraciones simples pueden utlizar una ligera variación
del formato a una linea. En este caso, debe incluirse un espacio despues de la llave
de apertura y antes de la de cierre.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Los valores largos separados por comas - como las colecciones de gradientes o sombreados -
puede ser colocados a lo largo de varias lineas en el interés de mejorr la legibilidad y
producir diffs más útiles. Hay varios formatos que pueden emplease; como el ejemplo a
continuación.

```css
.selector {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

#### Miscelanea

* Utilice valores hexadecimales en minúsculas, p.ej., `#aaa`.
* Utilice comillas simples o dobles consistentemente. Preferentemente dobles,
  p.ej., `content: ""`.
* Utilice siempre valores entrecomillados en los selectores, 
  p.ej., `input[type="checkout"]`.
* _Cuando sea posible_, evite especifiar unodes para valores de 0, 
  p.ej., `margin: 0`.

### Preprocesadores: consideraciones adicionales al formato

Los diferentes preprocesadores CSS tienen diferentes características, funcionalidad
, y sintaxis. Sus convenciones deben adaptase para acomodad las particularidades de
cualquier preprocesador en uso. Las siguientes guias hacen referencia a Sass.

* Limite el anidamiento a 1 nivel de profundidad. Reconsidere cualquier anidamiento 
  de más de 2 niveles. Estó evitará selectores CSS excesivamente especificicos.
* Evite grandes cantidades de reglas anidadas. Dividalas cuando la legibilidad 
  empiece a verse afectada. Preferentemente evite anidamientos que se extiendan
  durante más de 20 lineas.
* Ponga siempre declaraciones `@extend` en las primeras lineas de un bloque 
  declarativo.
* Donde sea posible, agrupe las declaraciones `@include` al final del bloque  
  declarativo, después de cualquier declaración `@extend`.
* Considere prefijar funciones concretas con un `x-` u otro namespace. Esto ayudará
  a evitar cualquier confusión potencial de su función con una funcion CSS nativa, o
  la colisión con funciones de librerias.

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
## 5. Denominación

Usted no es un compilador/compresor humano, así que no intente ser uno.

Utilice nombres claros y previsibles para las clases HTML. elija una pauta de 
denominación comprensible y consistente que tenga sentido en ambos ficheros HTML 
y CSS.

```css
/* Ejemplo de código con malos nombres */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Ejemplo de código con mejores nombres */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. Ejemplo práctico

Un ejemplo de varias convenciones.

```css
/* ==========================================================================
   Disposición en Grid
   ========================================================================== */

/*
 * Example HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Evita que las celdas inline-block se envuelvan */
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
    /* Fija el espaciado interior de la celda */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Reinicia white-space */
    white-space: normal;
    /* Reinicia font-size */
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

/* Modificadores de las celdas
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Organización

La organización del código es una parte importante de cualquier repositorio CSS y
crucial para repositorios grandes.

* Separe de forma logica distintas piezas de código.
* Emplee ficheros separados (concadenados en el paso de construcción) para ayudar
  a dividor el código de distintos componentes.
* Si está utilizando un preprocesador, abstraiga código frecuente a variables para 
  color, tipografía, etc.


<a name="build-and-deployment"></a>
## 8. Construcción y despliegue

Los proyectos siempre pueden intentar incluir medios por los cuales el código sea
verificado, probado, comprimido y versionado en preparacion para su uso en producción.
Para esta tarea, [grunt](https://github.com/cowboy/grunt) de Ben Alman es una 
excelente herramienta.


<a name="acknowledgements"></a>
## Agradecimientos

Gracias a todos aquellos que han contribuido a 
[idiomatic.js](https://github.com/rwldrn/idiomatic.js). Ha sido una fuente de 
inspiración, anotaciones y directrices