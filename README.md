# Principles of writing consistent, idiomatic CSS

## Table of contents

1. [General principles](#1-general-principles)
2. [Whitespace](#2-whitespace)
3. [Comments](#3-comments)
4. [Format](#4-format)
5. [Naming](#5-naming)
6. [Practical example](#6-practical-example)
7. [Organization](#7-organization)
8. [Build and deployment](#8-build-and-deployment)

## 1. General principles

> "Part of being a good steward to a successful project is realizing that writing code for yourself is a Bad Idea™. If thousands of people are using your code, then write your code for maximum clarity, not your personal preference of how to get clever within the spec." - Idan Gazit

* All code in any code-base should look like a single person typed it, no matter how many people contributed.
* This document outlines the practices that I seek to adhere to in all code that I originally author.
* If in doubt use existing, common patterns.


## 2. Whitespace

Only one style should exist across the entire source of your project. Always be consistent in your use of whitespace. Use whitespace to improve readability.

* _Never_ mix spaces and tabs for indentation.
* Choose between soft indents (spaces) or real tabs. Stick to your choice without fail. (Preference: spaces)
* If using spaces, choose the number of characters used per indentation level. (Preference: 4 spaces)

Tip: configure your editor to "show invisibles". This will allow you to eliminate end of line whitespace, eliminate unintended blank line whitespace, and avoid polluting commits.


## 3. Comments

Well commented code is extremely important. Take time to describe components, how they work, their limitations, and the way they are constructed. Don't leave others in the team guessing as to the purpose of uncommon or non-obvious code.

Comment style should be simple and consistent within a single code base.

* Place comments on a new line above their subject.
* Avoid end of line comments.
* Keep line-length to a sensible maximum, e.g., 80 columns.
* Make liberal use of comments to break CSS code into discrete sections.
* Use "sentence case" comments and consistent text indentation.

Tip: configure your editor to provide you with shortcuts to output agreed-upon comment patterns.

#### CSS example:

```css
/* ====================================================================
   Section comment block
   ==================================================================== */

/* Sub-section comment block
   ==================================================================== */

/*
 * Group comment block.
 * Ideal for multi-line explanations and documentation.
 */

/* Basic comment */
```

#### SCSS example:

```scss
// ====================================================================
// Section comment block
// ====================================================================

// Sub-section comment block
// ====================================================================

//
// Group comment block
// Ideal for multi-line explanations and documentation.
//

// Basic comment
```


## 4. Format

The chosen code format must ensure that code is: easy to read; easy to clearly comment; minimizes the chance of accidentally introducing errors; and results in useful diffs and blames.

1. One discrete selector per line in multi-selector rulesets.
2. A single space before the opening brace of a ruleset.
3. One declaration per line in a declaration block.
4. One level of indentation for each declaration.
5. A single space after the colon of a declaration.
6. Always include a semi-colon at the end of the last declaration in a declaration block.
7. Place the closing brace of a ruleset in the same column as the first character of the ruleset.
8. Separate each ruleset by a blank line.

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

#### Declaration order

Declarations should be ordered in accordance with a single principle. Although alphabetical ordering is sometimes used, preference is for related properties to be grouped together and for structurally important properties (e.g. positioning and box-model) to be declared prior to typographic, background, and color properties.

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

#### Exceptions and slight deviations

Large blocks of single-line declarations can use a slightly different, single-line format. In this case, a space should be included after the opening brace and before the closing brace (see the complete example below).

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Very long property values - such as complex collections of gradients or shadows - can themselves be arranged across multiple lines in an effort to improve readability and produce more useful diffs.

#### Misc

* Use lowercase hex values, e.g., `#aaa`.
* Use single or double quotes consistently. Preference is for double quotes, e.g., `content: ""` or `input[type="checkout"]`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.

### Preprocessors: additional format considerations

Different CSS preprocessors have different features, functionality, and syntax. Your conventions should be extended to accomodate the particularities of any preprocessor in use. The following guidelines are in reference to Sass.

* Limit nesting to 1 level deep. Reassess any nesting more than 2 levels deep. This prevents overly specific CSS selectors.
* Avoid large numbers of nested rules. Break them up when readability starts to be affected. Preference to avoid nesting that spreads over more than 20 lines.
* Always place `@extend` statements on the first lines of a declaration block.
* Where possible, group `@include` statements at the top of a declaration block, after any `@extend` statements.
* Consider prefixing custom functions with `x-` or another namespace. This helps to avoid any potential to confuse your function with a native CSS function, or to clash with functions from libraries.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}
```


## 5. Naming

You are not a human code compiler/compressor, so don't try to be one.

Use clear and thoughtful names for HTML classes. Pick an understanderable and consistent naming pattern that makes sense both within HTML files and CSS files.

```css
/* Example of code with bad names */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Example of code with better names */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


## 6. Practical example

An example of various conventions.

```scss
/* =====================================================================
   Grid layout
   ===================================================================== */

/*
 * Example HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    @include box-sizing(border-box);
    overflow: visible;
    height: 100%;
    // Prevent inline-block cells wrapping
    white-space: nowrap;
    // Remove inter-cell whitespace
    font-size: 0;
}

.cell {
    @include box-sizing(border-box);
    @include transition(box-shadow, 0.25s, ease-in-out, 0s);
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    // Set the inter-cell spacing
    padding: 0 $grid-gutter;
    border: 2px solid #333;
    vertical-align: top;
    // Reset white-space
    white-space: normal;
    // Reset font-size
    font-size: $fontsize-default;

    /* Cell states */

    &.is-animating {
        background-color: $cell-highlight-color
    }
}

/* Cell dimensions
   ===================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell modifiers
   ===================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


## 7. Organization

Code organization is an important part of any CSS code base, and crucial for large code bases.

* Logically separate distinct pieces of code.
* Use separate files (concatenated by a build step) to help break up code for distinct components.
* If using a preprocessor, abstract common code into variables for color, typography, etc.


## 8. Build & deployment

Projects should always attempt to include some generic means by which source can be linted, tested, compressed, and versioned in preparation for production use. For this task, [grunt](https://github.com/cowboy/grunt) by Ben Alman is an excellent tool.
