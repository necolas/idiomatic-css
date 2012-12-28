# Prinsip Penulisan CSS yang Konsisten, Idiomatic

Dokumen dibawah ini menjelaskan petunjuk umum dalam pengembangan CSS.
Petunjuk ini sangat mengutamakan penggunaan pola umum yang ada.
Dan sebaiknya digunakan dalam Penulisan CSS sesuai kebutuhan anda.

Dokumen ini sedang digunakan oleh banyak orang, dan sangat terbuka
dengan saran yang masuk. Silahkan berpartisipasi.

## Daftar Isi
1. [Prinsip Umum](#general-principles)
2. [Whitespace](#whitespace)
3. [Komentas](#comments)
4. [Format](#format)
5. [Contoh Penggunaan](#example)

[Terima Kasih](#acknowledgements)

[Lisensi](#license)


<a name="general-principles"></a>
## 1. Prinsip Umum

> "Salah satu bagian untuk menjadi staf yang baik dalam Proyek adalah memahami
> bahwa menulis kode untuk diri sendiri adalah hal yang buruk. Jika ribuan
> sedang menggunakan kode anda, maka tulislah kode anda dengan jelas dan
> objektif, jangan menggunakan cara pribadi dalam memahami kode." - Idan Gazit

* Jangan mencoba menjadi manusia Compiler.
* Semua kode harus tampak seperti ditulis oleh satu orang, walaupun ada banyak
orang yang berpartisipasi.
* Melaksanakan pola yang disepakati dengan ketat.
* Jika ragu dengan pola tersebut, gunakan pola yang ada dan umum.


<a name="whitespace"></a>
## 2. Whitespace

Anda disarankan menggunakan satu pola dalam seluruh kode. Harap konsisten
dengan penggunaan whitespace pada kode. Gunakan Whitespace untuk memudahkan
pembacaan kode.

* _Hindari_ membaurkan Spasi dan Tab untuk indentasi.
* Pilih salah satu antara _Soft Indents_ (Spasi) atau Tab original. Yakinlah
akan pilihan anda. (Disarankan: Spasi)
* Jika menggunakan Spasi, pilih jumlah karakter yang digunakan ditiap
indentasi. (Disarankan: 4 Spasi)

Tip: Setting Editor anda untuk mengaktifkan "show invisibles". Hal ini
meperbolehkan anda menghapus whitespace yang tidak diinginkan.

Tip: Gunakan File [EditorConfig](http://editorconfig.org) (atau yang sejenis)
untuk membantu pengaturan Whitespace yang anda gunakan pada kode anda.


<a name="comments"></a>
## 3. Komentar

Kode yang dikomentari dengan baik sangatlah penting. Sisihkan waktu untuk
menjelaskan komponen, bagaimana mereka bekerja, dan cara penggunaannya. Jangan
membiarkan staf di Tim anda untuk menduga-duga atau menebak-nebak karena kode
yang kurang jelas.

Pola Komentar harus sederhana dan konsisten di setiap kode anda.

* Tempatkan Komentar di atas subjeknya.
* Tetapkan standar panjang karakter ditiap Komentar. Contoh: 80 Karakter
* Anda bebas untuk menentukan Komentar sebagai pemecah kode CSS menjadi
beberapa bagian.
* Gunakan "Sentence Case" pada Komentar dan penggunaan indentasi yang konsisten

Tip: Buat snippet pada Editor anda sebagai shortcut untuk Komentar yang akan
anda gunakan.

Contoh:
```css
/* ==========================================================================
   Blok Bagian
   ========================================================================== */

/* Blok Sub-Bagian
   ========================================================================== */

/**
 * Deskripsi Singkat menggunakan format Komentar Doxygen-style
 *
 * Kalimat pertama dari Deskripsi Detail dimulai di sini dan berlanjut di baris
 * selanjutnya hingga sampai kepada kesimpulan pada akhir paragraf.
 *
 * Deskripsi Detail sangat ideal untuk Penjelasan yang lebih lengkap dan
 * sebagai Dokumentasi. Disini anda dapat memasukkan contoh HTML, URL, atau
 * informas-informasi lain yang berguna untuk penjelasan.
 *
 * @tag Tag ini dinamakan 'tag'
 *
 * @todo Ini adalah Statemen Todo yang mendeskripsikan tugas-tugas yang harus
 *   anda selesaikan di waktu yang akan datang. Bagian ini memilik panjang
 *   maksimal 80 karakter dan baris dibawahnya di indentasi menggunakan 2 spasi
 */

/* Komentar standar */
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
a single, simple principle. My preference is for structurally important
properties (e.g. positioning and box-model) to be declared prior to all
others.

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

Strict alphabetical ordering is also relatively popular, but the drawback is
that it separates related properties. For example, position offsets are no
longer grouped together and box-model properties can end up spread throughout a
declaration block.

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
 * Must only contain `.cell` children.
 */

.grid {
    height: 100%;
    /* Remove inter-cell whitespace */
    font-size: 0;
    /* Prevent inline-block cells wrapping */
    white-space: nowrap;
}

/**
 * Grid cells
 * No explicit width by default. Extend with `.cell-n` classes.
 */

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
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


## Translations

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
* [简体中文](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-CN)


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
