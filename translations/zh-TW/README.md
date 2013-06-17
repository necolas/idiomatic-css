# 通順一致的CSS編寫原則

以下的文件描述了一個合理的CSS開發風格規範。
這些守則特別著重於使用現有那些普遍且合理的形式。你可以採用它們來創造你自己的風格規範。

這是一份持續更新的文件，而且永遠歡迎新的想法，別吝於貢獻。


## 目錄

1. [通用原則](#general-principles)
2. [空格](#whitespace)
3. [註解](#comments)
4. [格式](#format)
5. [實例](#example)

[Acknowledgements](#acknowledgements)

[License](#license)


<a name="general-principles"></a>
## 1. 通用原則

> 「良好管理成功專案的其中一點是能夠了解到
> 只為自己寫代碼是很糟糕的行為。如果有很多人正在使用你寫的代碼，
> 那麼盡可能保持你的代碼明確可讀，而不是在規格中隨個人喜好取巧。」- Idan Gazit

* 不要嘗試過早地優化你的代碼。讓它保持易讀且容易理解。
* 不論有多少人參與，專案內任何項目的代碼都應該要看起來像是同一人的手筆。
* 嚴格實行眾人認同的風格。
* 當對風格有疑義時應採行現有而普遍的形式。


<a name="whitespace"></a>
## 2. 空格

在全部的項目原始碼中只能有唯一的風格，在使用空白時應永遠保持一致性。
使用空白來提升可讀性。


* _絕對_ 不要在縮排時混用空格和跳格。
* 在偽縮排（空格）或是真正的跳格中擇一。並且堅持你的選擇不要漏失。（建議使用：空格）
* 如果使用空格，指定每個縮進等級使用的字元長度。（建議使用：4個空格）

提示: 設定你的編輯器「顯示不可見字元」或是自動移除行尾空白。

提示: 使用 [EditorConfig](http://editorconfig.org/) 設定檔 （或是類似的工具） 來協助維護項目中已被接受的基本空白慣例。


<a name="comments"></a>
## 3. 註解

代碼有良好註解是非常重要的。留些時間去描述元件是如何作用，有哪些侷限，以及是如何組成的。
別讓團隊裡的其他人去猜測那些不尋常的或是意圖不明顯的代碼。

註解的風格在同一專案項目中應該力求簡明一致。

* 將註解放在解釋的對象上方並獨立成行。
* 保持單行長度在一個合理的最大值，例如：80個字元。
* 使用字面上的註解把 CSS 代碼分隔成不同的部分。
* 使用與一般文句相同的大小寫以及一致的段落縮排。

提示: 設定你的編輯器以提供快捷鍵來輸出眾人認同的註解形式。

範例:

```css
/* ==========================================================================
   註解章節區塊
   ========================================================================== */

/* 註解子章節區塊
   ========================================================================== */

/**
 * 使用Doxygen風格註解格式的簡短描述
 *
 * 這一長段敘述的第一個句子從這裡開始，在這行持續一下子，
 * 最後收尾在這段的結尾。
 *
 * 這一長段敘述對於更仔細的解釋以及說明是很合適的。它可以包含一些範例 HTML、URL，
 * 或是任何其他有用或必要的資訊。
 *
 * @tag 這是一個命名為'tag'的標籤
 *
 * TODO: 這是描述一個要在稍後完成的簡單任務的待辦事項。
 *   它在80個字元長度後斷行（譯註：中文沒有）且以下每行
 *   都使用兩個空白縮進。
 */

/* 基本註解 */
```


<a name="format"></a>
## 4. Format

The chosen code format must ensure that code is: easy to read; easy to clearly
comment; minimizes the chance of accidentally introducing errors; and results
in useful diffs and blames.

* Use one discrete selector per line in multi-selector rulesets.
* Include a single space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of indentation for each declaration.
* Include a single space after the colon of a declaration.
* Use lowercase and shorthand hex values, e.g., `#aaa`.
* Use single or double quotes consistently. Preference is for double quotes,
  e.g., `content: ""`.
* Quote attribute values in selectors, e.g., `input[type="checkbox"]`.
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

#### Declaration order

If declarations are to be consistently ordered, it should be in accordance with
a single, simple principle.

Smaller teams may prefer to cluster related properties (e.g. positioning and
box-model) together.

```css
.selector {
    /* Positioning */
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

    /* Other */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Larger teams may prefer the simplicity and ease-of-mainteance that comes with
alphabetical ordering.

#### Exceptions and slight deviations

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
be used; one example is shown below.

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

### Preprocessors: additional format considerations

Different CSS preprocessors have different features, functionality, and syntax.
Your conventions should be extended to accommodate the particularities of any
preprocessor in use. The following guidelines are in reference to Sass.

* Limit nesting to 1 level deep. Reassess any nesting more than 2 levels deep.
  This prevents overly-specific CSS selectors.
* Avoid large numbers of nested rules. Break them up when readability starts to
  be affected. Preference to avoid nesting that spreads over more than 20
  lines.
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
    // other declarations
}
```


<a name="example"></a>
## 5. Practical example

An example of various conventions.

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/**
 * Column layout with horizontal scroll.
 *
 * This creates a single row of full-height, non-wrapping columns that can
 * be browsed horizontally within their parent.
 *
 * Example HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * Grid container
 *
 * Must only contain `.cell` children.
 *
 * 1. Remove inter-cell whitespace
 * 2. Prevent inline-block cells wrapping
 */

.grid {
    height: 100%;
    font-size: 0; /* 1 */
    white-space: nowrap; /* 2 */
}

/**
 * Grid cells
 *
 * No explicit width by default. Extend with `.cell-n` classes.
 *
 * 1. Set the inter-cell spacing
 * 2. Reset white-space inherited from `.grid`
 * 3. Reset font-size inherited from `.grid`
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

/* Cell states */

.cell.is-animating {
    background-color: #fffdec;
}

/* Cell dimensions
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell modifiers
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="acknowledgements"></a>
## Acknowledgements

Thanks to everyone who has provided translations and to all those who
contributed to [idiomatic.js](https://github.com/rwldrn/idiomatic.js). It was a
source of inspiration, quotations, and guidelines.


<a name="license"></a>
## License

_Principles of writing consistent, idiomatic CSS_ by Nicolas Gallagher is
licensed under the [Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/). This applies to all
documents and translations in this repository.

Based on a work at
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).
