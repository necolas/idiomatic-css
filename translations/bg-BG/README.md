# Принципи за писане на консистентен, идиоматичен CSS код

Този документ описва разумен наръчник за стил на писане, при разработката на CSS код.
Тези насоки горещо насърчават използването на вече съществуващи, общи, разумни модели.
Адаптирайте ги както се наложи за да създадете свой собствен наръчник за стил.

Този документ подлежи на промяна и новите идеи са добре дошли. Моля, допринасяйте към него.


## Съдържание

1. [Общи положения](#general-principles)
2. [Празни символи (whitespace)](#whitespace)
3. [Коментари](#comments)
4. [Формат](#format)
5. [Практически пример](#example)

[Благодарности](#acknowledgements)

[Лиценз](#license)


<a name="general-principles"></a>
## 1. Общи положения

> "Част от това да бъдеш добър участник в успешен проект е осъзнаването,
> че писането на код за себе си е Лоша Идея™. Ако хиляди хора ще ползват твоя код,
> тогава го пиши, така че да бъде максимално четим, не намесвай своите предпочитания
> за това как да хитрувате в рамките на спецификацията. " - Idan Gazit

* Не се опитвайте предварително да пре-оптимизирате своя код; старайте се да е четим и разбираем.
* Целият код трябва да изглежда така, все едно един единствен човек го е написал,
дори и много хора да са допринесли за него.
* Стриктно налагайте стилът за който сте се разбрали.
* Ако се съмнявате кой е удачния в конкретна ситуация стил - използвайте общовалидни правила.


<a name="whitespace"></a>
## 2. Празни символи (whitespace)

Използвайте само един стил за целия код на проекта. Винаги бъдете консистентни в употребата на празни символи
(интервал, табулация и нов ред). Използвайте ги за да подобрите четимостта на кода.

* _Никога_ не смесвайте интервали и табулация за индентация.
* Изберете между 'мека' индентация (интервали) и истински табове. Придържайте се към избора си навсякъде.
(Предпочитано: интервали)
* Ако използвате интервали, изберете броя символи, за базово ниво на индентация. (Предпочитано: 4 интервала)

Идея: конфигурирайте редактора си да показва невидимите символи, или автоматично да премахва празните символи на края на реда.

Идея: използвайте конфигурационен файл за [EditorConfig](http://editorconfig.org/) (или еквивалент),
за да спомогнете за поддържането на единнатa конвенция при употребата на празни символи във вашия код.


<a name="comments"></a>
## 3. Коментари

Добре коментираният код е изключително важен. Отделете време да опишете компонентите, начина на работа с тях,
техните ограничения и това как са конструирани. Не оставяйте останалите в екипа,
да се опитват да познаят предназначението на код, който не е очевиден.

Стилът на коментарите трябва да бъде лесен и консистентен за единна база от код.

* Поставяйте коментарите на нов ред, над това което поясняват.
* Поддържайте разумна дължина на реда, напр. 80 символа.
* Използвайте коментари за да разбиете CSS кода на обособени секции.
* Нека всяко изречение от коментара започва с главна буква и използвайте консистентна индентация.

Идея: конфигурирайте своя редактор, така че чрез клавишни комбинации да въвеждате темплейти за коментари.

Пример:

```css
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* Sub-section comment block
   ========================================================================== */

/**
 * Short description using Doxygen-style comment format
 *
 * The first sentence of the long description starts here and continues on this
 * line for a while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * TODO: This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */

/* Basic comment */
```


<a name="format"></a>
## 4. Формат

Избрания от вас формат за кода трябва да поддържа кода: четим; лесен за коментари;
намалява възможносттите за грешки; да резултира в полезни diff-ове и blame-ове.

* Използвайте по един селектор на линия при CSS правила за повече от един селектор.
* Поставяйте интервал преди отварящата скоба на правилото.
* Във всеки блок от декларации, дефиницията на атрибутите трябва да бъде на отделен ред.
* Използвайте едно ниво на индентация за всяка дефиниция на стойност.
* Поставяйте интервал след двоеточието на атрибута.
* Използвайте lowercase (малки букви) и краткия синтаксис за деклариране на шестнадесетични стойности, напр. `#aaa`
* Използвайте консистентни кавички. Предпочитат се двойните кавички, напр. `content: ""`.
* Ограждайте в кавички стойностите на атрибути в селектори, напр. `input[type="checkbox"]`.
* _Когато може_, избягвайте да включвате мерните единици за за стойности равни на нула, напр. `margin: 0`.
* Поставяйте интервал след всяка запетая, в стойности или функции, разделяни от запетаи.
* Поставяйте точка и запетая на края на последната дефиниция от блок.
* Поставяйте затварящата скоба за дадено правил на същата колона като отварящата.
* Разделяйте всеки блок от правила с нов ред.

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

#### Ред на атрибутите

Ако атрибутите са консистентно подредени, то това трябва да се случва на един и същ,
лесен принцип.

Малките екипи ще предпочетат да обособяват свързаните помежду им атрибути
(напр. позициониране и box-model).

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

По-големите екипи могат да предпочетат лесната подръжка, които носи азбучния ред.

#### Изключения и леки отклонения

Големи блокове с дефиниции от един ред използват по-различен, едноредов формат.
В такива случаи, трябва да се поставя интервал след отварящата скоба и преди затварящата.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Дълги, разделени от запетая стойности за атрибути - например няколко CSS градиента,
или множество сенки - могат да бъдат подреждани на няколко реда, за да се по-добра четимост,
както на кода, така и в diff. Съществуват няколко формата, които могат да бъдат използвани,
по-долу можете да намерите един от тях.

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

### CSS препроцесори: допълнителни уточнения по форматирането

Различните CSS препроцесори имат различни възможности, функционалности и синтаксис.
Вашите конвенции трябва да бъдат разширени така, че да позволят особеностите на всеки използван препроцесор.
Следните правила са адаптирани за Sass.

* Ограничете дълбочината на вмъкване до 1 ниво. Премислете всичко по-дълбоко от 2 нива навътре.
  Това предотвратява появата на прекалено специфични CSS селектори.
* Избягвайте големи бройки вмъкнати правила. Разбийте ги когато четимоста започва страда.
  Предпочита се да се избягва вмъкнат навътре код, което се разпростира на повече от 20 линии.
* Винаги поставяйте `@extend` дефинициите на първите редове от даден блок.
* Когато е възможно, групирайте `@include` дефинициите в началото на блок, или след `@extend`.
* Помислете, дали да не сложите префикс (`x-`, или друго) на дефинираните от вас функции,
  за да избегнете тяхното объркване с чист CSS код, или проблеми с функции от други библиотеки.

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
## 5. Практически пример

Пример, показващ различните конвенции.

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


## Преводи

* [Bahasa Indonesia](https://github.com/necolas/idiomatic-css/tree/master/translations/id-ID)
* [Български](https://github.com/necolas/idiomatic-css/tree/master/translations/bg-BG)
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
## Благодарности

Благодаря на всички, които предоставиха преводи,
както и на тези, които допринесоха към [idiomatic.js](https://github.com/rwldrn/idiomatic.js).
Idiomatic.js бе извор на вдъхновение, цитати и правила


<a name="license"></a>
## Лиценз

_Principles of writing consistent, idiomatic CSS_ от Nicolas Gallagher,
е лицензирано като [Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/). Същото се отнася за всички документи и преводи в това хранилище.

Базирано на труд от
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).
