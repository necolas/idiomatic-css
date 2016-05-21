# 编写如一、符合习惯的CSS的原则

以下文档将概述一个合理的CSS开发风格指导。本指导文件强烈鼓励开发者使用已经存在了的、常见的、合理的文风。您应该有选择地吸纳一些内容来创造您自己的风格指南。

这个文档将持续更新，欢迎提出新的想法。还请多多贡献。

[Principles of writing consistent, idiomatic CSS（原版）](https://github.com/necolas/idiomatic-css)


## 目录

1. [通用原则](#general-principles)
2. [空格](#whitespace)
3. [注释](#comments)
4. [格式](#format)
5. [实例](#example)

[致谢](#acknowledgements)

[许可](#license)

<a name="general-principles"></a>
## 1. 通用原则

> “作为成功的项目的一员，很重要的一点是意识到只为自己写代码是很糟糕的行为。如果将有成千上万人使用你的代码，
> 那么你需要编写最具明确性的代码，而不是以自我的喜好来彰显自己的智商。” - Idan Gazit

* 别想着过早地优化代码。先得保证它们可读又可理解才行。
* 在任何代码库中，无论有多少人参与及贡献，所有代码都应该如同一个人编写的一样。
* 严格执行一致认可的风格。
* 如果有疑议，则使用现有的、通用的模式。


<a name="whitespace"></a>
## 2. 空格

在项目的所有代码中，应该只有一个风格。在空格的使用上，必须始终保持一致。使用空格来提高可读性。

* *永远不要*在缩进时混用空格和制表符（又称TAB符号）。
* 在软缩进（使用空格）和真正的制表符间选择其一，并始终坚持这一选择。（推荐使用空格）
* 如果使用空格进行缩进，选择每个缩进所使用的空格数。（推荐：4个空格）

提示：将编辑器配置为“显示不可见内容”，或者设置自动清除行尾空格。

提示：确定好一种空格格式后，您可以用一个[EditorConfig](http://editorconfig.org/)文件（或者其他相同的东西）来帮助在代码库之间维持这种基本的空格约定。

<a name="comments"></a>
## 3. 注释

良好的注释是非常重要的。请留出时间来描述组件（component）的工作方式、局限性和构建它们的方法。不要让你的团队其它成员
来猜测一段不通用或不易理解的代码的用途。

注释的风格应当简洁，并在代码库中保持统一。

* 将注释放在被注释代码上方并独占一行。
* 控制每行长度在合理的范围内，比如80列。
* 灵活使用注释将CSS代码分隔为独立的部分。
* 使用“句首大写方式”（仅句子首字母大写）注释，并且使用一致的文本缩进。

提示：通过配置编辑器，可以提供快捷键来输出一致认可的注释模式。

#### CSS示例：

```css
/* ==========================================================================
   区块代码注释
   ========================================================================== */

/* 次级区块代码注释
   ========================================================================== */

/**
 * “Doxygen式注释格式”的简短介绍
 *
 * 较长的说明文本从这里开始，这是这段文字的第一句话，而且这句话还
 * 没结束，过了好一会儿，我了个去终于结束了，烦不烦啊。
 *
 * 当需要进行更细致的解释说明、提供文档文本时，较长的说明文本就很
 * 有用了。这种长长的说明文本，可以包括示例HTML啦、链接啦等等其
 * 他你认为重要或者有用的东西。
 *
 * @tag 这是一个叫做“tag”的标签。
 *
 * TODO: 这个“‘需做’陈述”描述了一个接下来要去做的小工作。这种文本，
 *   如果超长了的话，应该在80个半角字符（如英文）或40个全角字符（
 *   如中文）后便换行，并（在“ * ”的基础上）再在后面缩进两个空格。
 */

/* 一般的注释 */
```

<a name="format"></a>
## 4. 格式

最终选择的代码风格必须保证：易于阅读，易于清晰地注释，最小化无意中引入错误的可能性，可生成有用的diff和blame。

* 在多个选择器的规则集中，每个单独的选择器独占一行。
* 在规则集的左大括号前保留一个空格。
* 在声明块中，每个声明独占一行。
* 每个声明前保留一级缩进。
* 每个声明的冒号后保留一个空格。
* 使用小写字母如可以使用hex简写方式，如#aaa。
* 使用单引号或者双引号，并保持一致。偏向使用双引号，如content: ""。
* 选择器中的属性加引号，如input[type="checkbox"]。
* 只要允许，避免给零值指定单位，如margin: 0。
* 在逗号分隔的特性和函数参数的每个逗号后要包含一个空格。 
* 对于声明块的最后一个声明，始终保留结束的分号。
* 规则集的右大括号保持与该规则集的第一个字符在同一列。
* 每个规则集之间保留一个空行。

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

#### 声明顺序

如果样式声明要保持一致的顺序，它应遵循一个单一，简单的原则。

小型的开发团体，可能会想要把相关的属性声明（比如说定位和箱模型）摆在一起。

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

大型团队，则可能更喜欢按字母排序，因为这样做起来很方便，而且维护起来很容易。

#### 例外及细微偏移原则的情况

对于大量仅包含单条声明的声明块，可以使用一种略微不同的单行格式。在这种情况下，在左大括号之后及右大括号之前都应该保留一个空格。

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

对于以逗号分隔并且非常长的属性值 -- 例如一堆渐变或者阴影的声明 -- 可以放在多行中，这有助于提高可读性，并易于生成有效的diff。这种情况下有多
种格式可以选择，以下展示了一种格式。

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

### 预处理：格式方面额外的考虑

不同的CSS预处理有着不同的特性、功能以及语法。编码习惯应当根据使用的预处理程序进行扩展，以适应其特有的功能。推荐在使用SCSS时遵守以下指导。

* 将嵌套深度限制在1级。对于超过2级的嵌套，给予重新评估。这可以避免出现过于详实的CSS选择器。
* 避免大量的嵌套规则。当可读性受到影响时，将之打断。推荐避免出现多于20行的嵌套规则出现。
* 始终将`@extend`语句放在声明块的第一行。
* 如果可以的话，将`@include`语句放在声明块的顶部，紧接着`@extend`语句的位置。
* 考虑在自定义函数的名字前加上`x-`或其它形式的前缀。这有助于避免将自己的函数和CSS的原生函数混淆，或函数命名与库函数冲突。

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
## 5. 实例

下面是含有上述约定的示例代码：

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

## 翻译

* [Bahasa Indonesia](https://github.com/necolas/idiomatic-css/tree/master/translations/id-ID)
* [Bulgarian](https://github.com/vestimir/idiomatic-css)
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
## 致谢

感谢所有对[idiomatic.js](https://github.com/rwldrn/idiomatic.js)提供翻译和对其贡献代码的每一个人。

## 许可
_Principles of writing consistent, idiomatic CSS_ 是Nicolas Gallagher发布在[Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/)许可证下的作品。该许可证适用于本代码栈中的所有文档，包括翻译文本。

本作品基于[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css)著就。
