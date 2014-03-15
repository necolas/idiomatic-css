# 일관성 있는 CSS다운 CSS를 작성하기 위한 원칙

이 문서는 CSS 개발을 위한 합리적인 스타일가이드의 중요한 내용입니다.
가이드라인들은 현존하고 일반적이며 분별력 있는 패턴을 사용하는 것을
권장합니다. 이 가이드라인들은 자신만의 스타일 가이드를 만들 때
참고만 해주세요.

이 문서는 계속 변경해 나갈 예정이므로 새로운 아이디어를 계속해서 추가해
나갈 생각입니다. 많은 아이디어를 주시면 고맙겠습니다.

한글 문서는 2014년 3월에 갱신되었고
[1634a08777](https://github.com/necolas/idiomatic-css/blob/1634a08777f47902c17efadf67c1e193e05fd410/README.md)를 기준으로 번역했습니다.

## 목차

1. [일반원칙](#general-principles)
2. [공백](#whitespace)
3. [주석](#comments)
4. [포맷](#format)
5. [실제 예제](#example)

[감사의 말](#acknowledgements)

[저작권](#license)


<a name="general-principles"></a>
## 1. 일반규칙

> "성공적인 프로젝트를 관리하는 방법 중에는 자신을 위해 코드를 작성하는 것이
> 나쁜 아이디어™ 라는 것을 깨닫는 것이 있다. 많은 사람이 당신의 코드를
> 사용하고 있다면, 최대한 명확한 코드를 작성하고, 개인적인 취향을 빼고,
> 사양 안에서 최대한 똑똑해야 한다." - Idan Gazit

* 성급하게 코드를 최적화하지 마십시오. 읽을 수 있고 이해할 수 있어야 합니다.
* 아무리 많은 사람이 참여했다고 하더라도, 코드는 한 사람이 작성한 것처럼
  보여야 합니다.
* 동의하에 스타일을 엄격하게 지키도록 하세요.
* 고민스러운 상황에서는 좀 더 이미 있고 일반적인 패턴을 사용하세요.


<a name="whitespace"></a>
## 2. 공백

프로젝트의 모든 소스코드에 같은 스타일을 사용해야 합니다. 공백은 늘
일관성이 있어야 합니다. 공백은 가독성을 높이기 위해서 쓰세요.

* 들여쓰기에 _절대로_ 탭, 스페이스를 섞어서 사용해서는 안 됩니다.
* 들여쓰기는 스페이스로 할지 아니면 탭으로 할지를 결정하고, 도중에
  변경해서는 안 됩니다. (스페이스가 좋습니다)
* 만약 스페이스를 사용하는 경우에는 들여쓰기에 사용하는 문자 수를
  결정 하세요. (4 스페이스가 좋습니다)

팁: 편집기에 숨긴 문자 표시(show invisibles) 기능이나 줄 끝의 공백을
자동으로 삭제하도록 설정하세요.

팁: 소스코드에 대한 합의 된 기본 공백 규칙을 유지하기 위해
[EditorConfig](http://editorconfig.org/) 파일(이나 비슷한 것)을
사용하세요.


<a name="comments"></a>
## 3. 주석

상세한 주석이 달린 코드는 매우 중요합니다. 시간을 들여 컴포넌트가
어떤 식으로 동작하는 건지, 어떤 제약이 있는지, 어떤 구성을 하고
있는지를 기술하세요. 팀원이 일반적이지 않고 명확하지도 않은 코드를
추측하게끔 하면 안 됩니다.

같은 소스코드의 주석은 간단하고 일관적이어야 합니다.

* 주석은 대상이 되는 컴포넌트의 상단에 배치하세요.
* 최대 라인 길이(예를 들면, 80자)를 지키세요.
* CSS 코드를 구분(break)하기 위해 주석을 사용하는 것은 자유롭게
  하세요.
* 주석의 맨 앞 자는 대문자로 하고 텍스트의 들여쓰기는 일관성을
  갖도록 합니다.

힌트: 편집기의 설정에 정해진 주석 패턴을 단축키로 등록해놓고 사용하세요.

예:

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
## 4. 포맷

코드 포맷의 선택에는 다음과 같은 점들이 고려되어야 합니다. (코드가 읽기
쉬운지, 명확하게 주석 달기 쉬운지, 예상치 못한 에러를 최대한 방지하고
있는지, diff, blame의 결과가 유용한지)

* 복수 셀렉터를 가진 룰셋의 경우, 셀렉터를 한 줄씩 기술해야 합니다.
* 룰셋에서 맨 첫 괄호의 앞에는 스페이스 한 개만 띄워야 합니다.
* 선언 블록 안에서는 선언을 한 줄씩 기술해야 합니다.
* 각 선언은 한 단계 들여쓰기해야 합니다.
* 선언문의 콜론 뒤에 스페이스 한 개만 띄워야 합니다.
* 소문자의 축약형 hex값(예를 들면 `#aaa`)을 사용합니다.
* 작은따옴표와 큰따옴표를 일관성 있게 사용합니다. 큰따옴표가 좋습니다.
  예를 들면 `content: ""`
* 셀렉터안의 속성값은 따옴표로 묶어줍니다. (예를 들면
  `input[type="checkbox"]`)
* _허용된 경우_, 0 값에 단위를 지정하지 마세요. (예를 들면 `margin: 0`)
* 쉼표로 구분된 속성이나 함수 값에서 쉼표 뒤에는 공백을 한 개만 띄워야
  합니다.
* 선언 블록 안의 맨 마지막의 선언문에는 늘 세미콜론이 있어야 합니다.
* 룰셋의 닫기 괄호는 룰셋안의 첫 번째 문자의 위치와 맞춥니다.
* 룰셋은 빈 줄로 구분합니다.

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

#### 선언 순서

선언을 일관적으로 배열하고 싶다면, 하나의 간단한 원칙을 따라야 합니다.

작은 팀은 관련 속성(예를 들면, 위치지정이나 box-model)을 그룹화하는
것이 좋을 거에요.

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

큰 팀은 알파벳 순서로 하는 것이 간단하고 유지 보수하기 편할 거에요.

#### 예외 및 작은 편차

한 줄 선언이 많아지게 되는 경우, 지금까지와 다르게 한 줄 포맷을
사용하기도 합니다. 이 경우에는 중괄호 안쪽의 양쪽 끝에 공백을
한 자씩 넣어야 합니다.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

그러데이션이나 쉐도우같이 길고, 쉽표로 구분하여 사용하는 속성 값을
가진 경우에는 읽기 쉽고 diff를 좀 더 유용하게 하기 위해 여러 줄을
사용해도 괜찮습니다. 여러 가지의 포맷이 있을 것으로 생각되지만 밑에
적은 것과 비슷한 형태일 것입니다.

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

### 프리프로세서: 추가 포맷 고려 사항

CSS 프리 프로세서의 특성, 기능, 문법은 각각 다릅니다. 규칙은 사용하고
있는 프리 프로세서의 특성에 맞춰서 확장되어야 합니다. 밑의
가이드라인은 Sass를 기준으로 하고 있습니다.

* 중첩(nesting)은 한 단계만 허용합니다. 2단계 이상 중첩된 모든
  코드는 재평가가 필요합니다.
* 중첩 룰이 많아지는 것을 피합니다. 가독성에 영향을 주기 시작할 때
  쪼갭(break)시다. 20줄 이상의 코드블록이 있는 룰셋은 피하는 것이
  좋습니다.
* `@extend`문은 항상 선언 블록의 최상단에 있어야 합니다.
* 가능한 한 `@include`는 선언 블록 안의 `@extend`의 다음에 모아둡니다.
* 커스텀 함수의 접두어로 `x-`나 다른 네임스페이스를 사용해보세요.
  이렇게하면 네이티브 CSS 함수와 커스텀 함수를 구별하기 쉽게 하고,
  라이브러리에서 함수의 충돌을 피할 수 있습니다.

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
## 5. 실제 예제

다양한 규칙의 예입니다.

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

## 번역

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
## 감사의 말

[idiomatic.js](https://github.com/rwldrn/idiomatic.js)에 참여해주신
여러분 감사합니다. idiomatic.js는 기발한 생각이며, 인용과
가이드라인의 원본입니다.


<a name="license"></a>
## 저작권

Nicolas Gallagher의 _일관성 있는 CSS다운 CSS를 작성하기 위한 원칙_은
[Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/)하에 있습니다.

이는 [github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css)
를 기준으로 작업 된 이 저장소에 있는 모든 문서와 번역에 적용됩니다.
