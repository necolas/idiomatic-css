# Principles of writing consistent, idiomatic CSS

The following document outlines a reasonable style guide for CSS development.
It is not meant to be prescriptive and we do not wish to impose our style
preferences on other people’s code. However, these guidelines do strongly
encourage the use of existing, common, sensible patterns.

This is a living document and new ideas are always welcome. Please
contribute.

## Table of contents

1. [General Principles](#general-principles)
2. [Whitespaces](#whitespaces)
3. [Comments](#comments)
4. [Format](#format)
  1. [Declaration Order](#declaration-order)
  2. [Exceptions & Slight Deviations](#exceptions)
  3. [Preprocessors: Additional Format Considerations](#preprocessors)
5. [Naming](#naming)
6. [Practical Example](#example)
7. [Organization](#organization)
8. [Build & Deployment](#build-and-deployment)

[Translations](#translations) & [Acknowledgements](#acknowledgements)



<a name='general-principles'></a>
## 1. General Principles

> “Part of being a good steward to a successful project is realizing that
> writing code for yourself is a Bad Idea™. If thousands of people are using
> your code, then write your code for maximum clarity, not your personal
> preference of how to get clever within the spec.” — Idan Gazit.

* You are not a human code compiler/compressor, so don’t try to be one.
* All code in any code-base should look like a single person typed it, no
  matter how many people contributed.
* Strictly enforce the agreed upon style.
* If in doubt when deciding upon a style, use existing, common patterns.

<a name='whitespaces'></a>
## 2. Whitespaces

Only one style should exist across the entire source of your code-base. Always
be consistent in your use of whitespace. Use whitespace to improve
readability.

* _Never_ mix spaces and tabs for indentation.
* Choose between soft indents —spaces— or real tabs. Stick to your choice
  without fail. _Preference: spaces_.
* If using spaces, choose the number of characters used per indentation level.
  _Preference: 2 spaces_.

Tip: configure your editor to “show invisibles”. This will allow you to
eliminate end of line whitespace, eliminate unintended blank line whitespace,
and avoid polluting commits.

Tip: use an [EditorConfig](http://editorconfig.org/) file —or equivalent— to
help maintain the basic whitespace conventions that have been agreed for your
code-base.


<a name='comments'></a>
## 3. Comments

Well commented code is extremely important. Take time to describe components,
how they work, their limitations, and the way they are constructed. Don’t leave
others in the team guessing as to the purpose of uncommon or non-obvious
code.

Comment style should be simple and consistent within a single code base.

* Place comments on a new line above their subject.
* Avoid end of line comments.
* Keep line-length to a sensible maximum, e.g., 80 columns.
* Make liberal use of comments to break CSS code into discrete sections.
* Use “sentence case” —unless is a title section— comments and consistent text indentation.

Tip: configure your editor to provide you with shortcuts to output agreed-upon
comment patterns.

#### Example:

```css
/* ====================================================================== */
/* ===== 1st Section Title ============================================== */
/* ====================================================================== */

/* ============================================================ */
/* ----- > 2nd Section Title ---------------------------------- */
/* ============================================================ */

/* -------------------------------------------------- */
/* ----- >> 3rd Section Title ----------------------- */
/* -------------------------------------------------- */

/* ---------------------------------------- */
/* ----- >>> 4th Section Title ------------ */
/* ---------------------------------------- */

/*
Long description first sentence starts here and continues on this line for a
while finally concluding here at the end of this paragraph.

The long description is ideal for more detailed explanations and
documentation. It can include example HTML, URLs, or any other information
that is deemed necessary or useful.

Here are some code examples:
* “<element>”: This is an element named “element”, e.g., “<body>”.
* “#id”: This is an id named “id”, e.g., “#header”.
* “.class”: This is a class named “class”, e.g., “.column-12”.
* “:property”: This is a property named “property”, e.g., “:padding-top”.
* “'value'”: This is a value, e.g., “'3.1416em'”.
* “TODO”: This is a todo statement that describes an atomic task to be completed
  at a later date. It wraps after 80 characters and following lines are
  indented by 2 spaces, e.g., “TODO: Finish this style guide before 2022.”.
*/

/*
This is a single paragraph comment, it has only two lines of text, but it could
have more, like three, four, six, or event seven if you like writing.
*/

/* Basic comment. */
```



<a name='format'></a>
## 4. Format

The chosen code format must ensure that code is: easy to read; easy to clearly
comment; minimizes the chance of accidentally introducing errors; and results
in useful diffs and blames.

* Use one discrete selector per line in multi-selector rulesets.
* Include a single space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of indentation for each declaration.
* Include single space after the colon of a declaration.
* Use lowercase and shorthand hex values _when possible_, e.g., `#fff`.
* Use single or double quotes consistently. _Preference: single quotes_.
* Quote attribute values in selectors, e.g., `input[type='checkbox']`.
* Don’t use quotes in URL values, e.g., `url(images/logotype.png)`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.
* Include a space after each comma in comma-separated property or function
  values.
* Include a semi-colon at the end of the last declaration in a declaration
  block.
* Place the closing brace of a ruleset in the same column as the first
  character of the ruleset.
* Separate each ruleset by a blank line.

```css
.selector-1,
.selector-2,
.selector-3[type='text'] {
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

<a name='declaration-order'></a>
#### 4.1. Declaration Order

Declarations should be ordered in accordance with a single principle.
There are three main ways: alphabetical, grouped by type or by length.
The preference is to group by type. Here we offer a list of preference order,
but you could do it in a more simpler way, declaring structurally important
properties —e.g. positioning and box-model— before to all others.

Note that in the bellow list, only are listed the short-hand declarations or
just a name pattern followed by “-*”. The following declarations can be placed
in any order, nevertheless, always use the same logic.

```css
.selector {

  /* Generated content */
  content: value;
  counter-*: value;
  quotes: value;

  /* Dimensions, paddings, margins & box display */
  width: value;
  height: value;
  min-*: value;
  max-*: value;
  padding-*: value;
  margin-*: value;
  display: value;
  visibility: value;
  clip: value;
  overflow-*: value;
  z-index: value;

  /* Flexible box */
  box-*: value;

  /* Grid & columns */
  grid-*: value;
  column-*: value;
  columns: value;

  /* Position & float behavior */
  position: value;
  top: value;
  right: value;
  bottom: value;
  left: value;
  float: value;
  clear: value;

  /* Lists & tables */
  list-*: value;
  border-collapse: value;
  border-spacing: value;
  caption-side: value;
  empty-cells: value;
  table-layout: value;

  /* User interface */
  appearance: value;
  box-sizing: value;
  box-shadow: value;
  icon: value;
  nav-*: value;
  resize: value;
  cursor: value;
  opacity: value;

  /* Typography */
  font-*: value;
  text-*: value;
  letter-spacing: value;
  line-height: value;
  white-space: value;
  word-*: value;
  direction: value;
  color: value;

  /* Animations, transitions & transformations */
  animation-*: value;
  rotation: value;
  transform-*: value;
  perspective-*: value;
  backface-visibility: value;
  transition-*: value;
  rotation-*: value;

  /* Background, borders, outline & box style */
  background-*: value;
  border-*: value;
  outline-*: value;
  opacity: value;
  box-shadow: value;

  /* Others */
  color-profile: value;
  page-*: value;

  /* Appendix: vendor prefixes */
  -webkit-*: value;
  -khtml-*: value;
  -epub-*: value;
  -moz-*: value;
  -ms-*: value;
  -o-*: value;

}
```

Strict alphabetical ordering or bye length are also relatively popular, but the
drawback is that separates related properties. For example, position offsets
are no longer grouped together and box-model properties can end up spread
throughout a declaration block.


<a name='exceptions'></a>
#### 4.2. Exceptions & Slight Deviations

Large blocks of single declarations can use a slightly different, single-line
format. In this case, a space should be included after the opening brace and
before the closing brace.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Long, comma-separated property values - such as collections of gradients or
shadows - can be arranged across multiple lines in an effort to improve
readability and produce more useful diffs. There are various formats that could
be used; two examples are shown below.

```css
.selector-1 {
  background-image:
    linear-gradient(#fff, #ccc),
    linear-gradient(#f3c, #4ec);
}

.selector-2 {
  box-shadow: 1px 1px 1px #000,
    2px 2px 1px 1px #ccc inset;
}
```

<a name='preprocessors'></a>
### 4.3. Preprocessors: Additional Format Considerations

Different CSS preprocessors have different features, functionality, and syntax.
Your conventions should be extended to accommodate the particularities of any
preprocessor in use. The following guidelines are in reference to Sass.

* Limit nesting to 1 level deep —or 2 if you are targeting a pseudo-class or
  a pseudo-element with “&”—. Reassess any nesting more than 2 levels deep.
  This prevents overly specific CSS selectors.
* Avoid large numbers of nested rules. Break them up when readability starts
  to be affected.
* Always place `@extend` statements on the first lines of a declaration
  block.
* Where possible, group `@include` statements at the top of a declaration
  block, after any `@extend` statements.
* Consider prefixing custom functions with `x-` or another namespace. This
  helps to avoid any potential to confuse your function with a native CSS
  function, or to clash with functions from libraries.

```scss
.selector-1 {
  @extend .other-rule;
  @include clearfix();
  @include box-sizing(border-box);
  width: x-grid-unit(1);
  // Other declarations.
}
```



<a name='naming'></a>
## 5. Naming

Naming is hard, but very important. It’s a crucial part of the process of
developing a maintainable code base, and ensuring that you have a relatively
scalable interface between your HTML and CSS.

* Avoid _systematic_ use of abbreviated class names. Don’t make things
  difficult to understand.
* Use clear, thoughtful, and appropriate names for _HTML classes_.
* Pick an understandable and consistent naming pattern that makes sense both
  within HTML files and CSS files.
* Selectors for components should uses class names; avoid the use of generic
  tags and unique ids.

```css
/* Example of code with bad names */

.s-scr {
  overflow: auto;
}

.c1 {
  background: #000;
}

/* Example of code with better names */

.is-scrollable {
  overflow: auto;
}

.column-1 {
  background: #000;
}
```



<a name='example'></a>
## 6. Practical Example

An example of various conventions.

```css

/* ====================================================================== */
/* ===== Grid Layout ==================================================== */
/* ====================================================================== */

/*

Example HTML:

<div class='grid'>
  <div class='cell cell-5'></div>
  <div class='cell cell-5'></div>
</div>

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
  position: relative;
  display: inline-block;
  overflow: hidden;
  box-sizing: border-box;
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

/* Cell states */

.cell.is-animating {
  background-color: #fffdec;
}

/* ============================================================ */
/* ----- > Cell Dimensions ------------------------------------ */
/* ============================================================ */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }


/* ============================================================ */
/* ----- > Cell Modifiers ------------------------------------- */
/* ============================================================ */

.cell--detail,
.cell--important {
  border-width: 4px;
}

```



<a name='organization'></a>
## 7. Organization

Code organization is an important part of any CSS code base, and crucial for
large code bases.

* Logically separate distinct pieces of code.
* Use separate files —concatenated by a build step— to help break up code for
  distinct components.
* If using a preprocessor, abstract common code into variables for color,
  typography, etc.



<a name='build-and-deployment'></a>
## 8. Build & Deployment

Projects should always attempt to include some generic means by which source
can be linted, tested, compressed, and versioned in preparation for production
use. For this task, [grunt](https://github.com/cowboy/grunt) by Ben Alman is an
excellent tool.



<a name='translations'></a>
## Translations

* [Deutsch](https://github.com/necolas/idiomatic-css/tree/master/translations/de-DE)
* [Français](https://github.com/necolas/idiomatic-css/tree/master/translations/fr-FR)
* [Italiano](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [日本語](https://github.com/necolas/idiomatic-css/tree/master/translations/ja-JP)
* [한국어](https://github.com/necolas/idiomatic-css/tree/master/translations/ko-KR)
* [Nederlands](https://github.com/necolas/idiomatic-css/tree/master/translations/nl-NL)
* [Português (Brasil)](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Русский](https://github.com/necolas/idiomatic-css/tree/master/translations/ru-RU)
* [Srpski](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)
* [Türkçe](https://github.com/necolas/idiomatic-css/tree/master/translations/tr-TR)
* [简体中文](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-CN)



<a name='acknowledgements'></a>
## Acknowledgements

Thanks to everyone who has contributed to
[idiomatic.js](https://github.com/rwldrn/idiomatic.js). It was a source of
inspiration, quotations, and guidelines. Also thanks to the translators
and contributors of this document.