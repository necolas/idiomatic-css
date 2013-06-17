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

提示: 設定你的編輯器以提供快捷鍵來輸出被一致接受的註解形式。

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
 *   它在80個字元長度後斷行（譯註：翻成中文後在這裡並非如此）且以下每行
 *   都使用兩個空白縮進。
 */

/* 基本註解 */
```


<a name="format"></a>
## 4. 格式

指定的代碼格式必須要確保的是：易於閱讀；易於清晰地註解；減少意外引入錯誤的機會；
而且可以產生實用的diff以及blame。

* 在有許多選擇器的樣式集中，讓每個單獨的選擇器單獨成行。
* 在樣式集的開始括號前保留一個空格。
* 在樣式區塊中保持每個樣式至少一行。
* 在每個樣式前使用一個段落的縮進。
* 在每個樣式的冒號後保留一個空格。
* 使用小寫以及縮略的HEX數值，例如：`#aaa`。
* 一致地使用單引號或是雙引號。推薦使用雙引號，例如：`content: ""`。
* 在選擇器中以引號夾注屬性值，例如： `input[type="checkbox"]`。
* _可以的話_，避免在值為零時指定單位，例如：`margin: 0`。
* 在每一個以逗號分隔的屬性的逗號或是函式值後面保留一個空格。
* 在樣式區塊的最後一個樣式結尾保留分號。
* 樣式集的結束括號應該擺放在與樣式集的第一個字元同樣位置。
* 以一個空白行分隔每個樣式集。

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

#### 宣告順序

如果宣告按照順序一貫地排列下來，應當要符合一個簡單的原則。

比較小的團隊們也許會偏好將有關聯的屬性（例如位置和容器模型）群組在一起。

```css
.selector {
    /* 位置 */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* 顯示 & 區塊模型 */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* 其它 */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

比較大的團隊們也許會偏好以字母排序所帶來的簡潔性以及易於維護。

#### 例外與細微偏差

對於大量只包含單條樣式宣告的區塊，可以採用一種稍微不同的單行格式。
在這種情況下，應在開始括號之後以及結束括號之前都保留一個空格。

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

對於很長且以逗號分隔的屬性值——例如漸層或是陰影的集合——可以整理成多行達到改善可讀性以及產生更有用diff的效果，這時有許多種格式可以使用。
底下有個例子。

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

### 預處理器: 額外的格式考量

不同的 CSS 預處理器有不同的特色、功能、以及語法。
應該要考慮到隨著所採用的不同預處理器的特點而去擴充你們的慣例。以下是關於 Sass 的守則。

* 將嵌套深度限制在一個階層。對於任何兩階以上的深度重新評估。這將避免寫出過於針對性的 CSS 選擇器。
* 避免大量的嵌套規則。當可讀性開始受到影響時將它們打散。盡量避免超過20行的嵌套。
* 永遠將 `@extend` 宣告擺在樣式區塊的第一行。
* 可能的話，將 `@include` 宣告群組置於樣式區塊的頂部，緊接著任何 `@extend` 宣告之後。
* 考慮在自訂函式的前面加上`x-`或是其他的命名空間。這有助於避免與原生的 CSS 函式混淆，或是與其它函式庫衝突。

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
## 5. 實例

這是遵循上述那些規範的範例。

```css
/* ==========================================================================
   格線佈局
   ========================================================================== */

/**
 * 帶有橫向捲軸的欄位佈局。
 *
 * 這會產生一個由全高且不斷開的多欄區塊組成的單列，可以在它的上層容器中橫向瀏覽。
 *
 * 範例 HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * 格線容器
 *
 * 必須只包含 `.cell` 子元素.
 *
 * 1. 移除網格間的空白
 * 2. 避免 inline-block 網格斷開
 */

.grid {
    height: 100%;
    font-size: 0; /* 1 */
    white-space: nowrap; /* 2 */
}

/**
 * 系統網格
 *
 * 不預設固定的寬度. 用 `.cell-n` 類別來變化。
 *
 * 1. 設定網格內間距
 * 2. 重設自 `.grid` 串接來的 white-space 屬性
 * 3. 重設自 `.grid` 串接來的 font-size 屬性
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

/* 網格狀態 */

.cell.is-animating {
    background-color: #fffdec;
}

/* 網格維度
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* 網格修飾
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
