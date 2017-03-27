# Markup Coding Conventions <small>(Markup Coding Style Guide)</small>



## Table of Contents

<a href="#glossaries">Glossaries</a>

- <a href="#html">1. HTML</a>
    - <a href="#html-syntax">1-1. Syntax</a>
    - <a href="#html-doctype">1-2. Doctype</a>
    - <a href="#html-metadata">1-3. Metadata</a>
    - <a href="#html-elements">1-4. Elements</a>
    - <a href="#html-attributes">1-5. Attributes</a>
    - <a href="#html-import">1-6. Import</a>
    - <a href="#html-comments">1-7. Comments</a>
- <a href="#css">2. CSS</a>
    - <a href="#css-syntax">2-1. Syntax</a>
    - <a href="#css-charset">2-2. Charset</a>
    - <a href="#css-selectors">2-3. Selectors</a>
    - <a href="#css-properties">2-4. Properties</a>
    - <a href="#css-import">2-5. Import</a>
    - <a href="#css-nesting">2-6. Nesting</a>
    - <a href="#css-media-query">2-7. Media Query</a>
    - <a href="#css-resets">2-8. Resets</a>
    - <a href="#css-prefix">2-9. Prefix</a>
    - <a href="#css-comments">2-10. Comments</a>
- <a href="#naming">3. Naming</a>
    - <a href="#naming-selectors">3-1. Selectors</a>
    - <a href="#naming-exception">3-2. Exception</a>

<a href="#changelogs">Changelogs</a>  
<a href="#license">License</a>



<h2 id="glossaries">Glossaries</h2>

먼저 컨벤션에 자주 사용되는 용어의 정의를 설명한다.

<dl>
    <dt>엘리먼트(Element)</dt>
    <dd>HTML 문서를 구성하는 요소(태그)를 의미한다.</dd>
    <dt>애트리뷰트(Attribute)</dt>
    <dd>엘리먼트에 부여할 수 있는 특성을 의미한다.</dd>
    <dt>선택자(Selector)</dt>
    <dd>엘리먼트를 식별할 수 있는 이름을 의미한다.</dd>
    <dt>스타일(Style)</dt>
    <dd>엘리먼트에 부여할 스타일 시트(Style Sheet)를 의미한다. 인라인 스타일(Inline Style), 내부 스타일(Internal Style), 외부 스타일(External Style), CSS 네가지로 구분된다.</dd>
    <dt>프로퍼티(Property)</dt>
    <dd>스타일과 관련하여 사용했을 경우 스타일 시트의 속성을 의미한다.</dd>
    <dt>프리픽스(Prefix) & 서픽스(Suffix)</dt>
    <dd>네이밍 시 사용되는 접두사, 접미사를 의미한다.</dd>
    <dt>컴포넌트(Component)</dt>
    <dd>하나 이상의 기능 또는 역할을 가진 컨텐츠 단위의 UI 구성요소를 의미한다.</dd>
</dl>



<h2 id="html">1. HTML</h2>

HTML 코드의 작성 규칙을 설명한다.

<h3 id="html-syntax">1-1. Syntax</h3>

- 들여쓰기는 2개 &middot; 4개의 공백 문자(소프트탭) 또는 하드탭 중 하나의 규칙으로 통일하여 작성한다.
- 엘리먼트 명과 애트리뷰트 명은 영문 소문자를 사용한다.
- 모든 애트리뷰트값은 큰 따옴표(`"`)를 사용하여 감싼다.
- 단일 태그 엘리먼트는 슬래시(`/`)를 사용하지 않는다.
- 닫는 태그가 선택적인 경우에도 생략하지 않는다. (ex: `</li>`, `</body>`)

<h3 id="html-doctype">1-2. Doctype</h3>

Doctype은 일반적으로 HTML5 DTD로 선언한다.
 
```html
<!DOCTYPE html>
```

<h3 id="html-metadata">1-3. Metadata</h3>

`<head>` 엘리먼트의 자식 엘리먼트 순서는 아래와 같다.

1. Charset
2. X-UA-Compatible
3. Viewport
4. Title
5. Meta
6. Style
7. JavaScript
    
```html
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no,target-densitydpi=medium-dpi">
<title>예제 페이지 - 구글</title>
..
```

#### A. Charset

문서의 언어셋은 일반적으로 `UTF-8`으로 선언한다.

```html
<meta charset="utf-8">
```

#### B. X-UA-Compatible

IE 브라우저의 호환성을 위해 문서모드를 `Edge`로 선언하여 최신 버전의 IE로 렌더링한다.

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

<h3 id="html-elements">1-4. Elements</h3>

- 렌더링 엔진 최적화를 위해 **스타일 또는 스크립트 제어가 필요한 모든 엘리먼트에는 클래스를 부여**한다.

#### A. 스타일 제어가 어려운 엘리먼트

자식 엘리먼트 태그가 한정적인 엘리먼트(ex. `<table>`) 또는 스타일 제어에 한계를 가진 엘리먼트(ex. `<select>`)가 컴포넌트의 루트 엘리먼트로 사용될 경우 의미없는 엘리먼트로 감싸는 것을 권장한다.

> 이 외의 불필요한 엘리먼트 상속은 피한다.

```html
<!-- Not Bad -->
<table class="table"></table>

<!-- Good -->
<div class="table">
    <table></table>
</div>
```

#### B. 테이블 제목

`<caption>` 엘리먼트의 뷰를 숨길 때는 의미없는 엘리먼트로 감싸서 숨긴다.

```html
<!-- Bad -->
<table>
    <caption class="blind"></caption>
</table>

<!-- Good -->
<table>
    <caption>
        <div class="blind"></div>
    </caption>
    ..
</table>
```

테이블의 제목이 필요하지 않거나 이미 `<table>` 엘리먼트 앞에 제공되었다면 생략한다.

```html
<!-- Bad -->
<h4>테이블 제목</h4>
<table>
    <caption class="blind">테이블 제목</caption>
</table>

<!-- Good -->
<h4>테이블 제목</h4>
<table>
    ..
</table>
```

#### C. 테이블 그룹

`<table>` 엘리먼트를 제작 시 `<thead>`, `<tfoot>`의 유무와 관계없이 `<tbody>`를 반드시 사용한다.

```html
<!-- Bad -->
<table>
    <tr>..</tr>
</table>

<!-- Good -->
<table>
    <tbody>
        <tr>..</tr>
    </tbody>
</table>
```

#### D. 입력 폼

회원가입 등의 문서 작성 폼에 사용되는 `<input>`, `<select>`, `<textarea>` 엘리먼트의 유동적인 너비, 높이 값은 인라인 스타일로 제어한다.

```html
<!-- Bad -->
<input type="text" class="input input--width-120">
<input type="text" class="input input--width-180">

<!-- Good -->
<input type="text" class="input" style="width:120px">
<input type="text" class="input" style="width:180px">
```

#### E. 버튼

`<button>` 엘리먼트는 `type` 애트리뷰트가 선언되지 않으면 문서 맥락에 따라 `type`이 다른 동작을 하므로 `type="button"`을 반드시 선언한다.

> `type` 애트리뷰트를 지정하지 않은 `<button>` 엘리먼트가 `<form>` 엘리먼트 안에 들어가면 submit 이벤트를 발생시킨다.

```html
<!-- Bad -->
<button></button>

<!-- Good -->
<button type="button"></button>
```

<h3 id="html-attributes">1-5. Attributes</h3>

엘리먼트 애트리뷰트의 선언 순서는 상황에 맞게 가변 애트리뷰트를 가장 나중에 작성한다.

```html
<input class="input" type="password" name="Password" id="Password" title="비밀번호" style="width:100px" disabled>
```

HTML5는 Boolean 애트리뷰트는 값을 지정하지 않은 채 선언되어도 `true`를 의미하므로 필요치 않다면 값을 지정하지 않는다.

```html
<!-- Not Bad -->
<button disabled="true"></button>

<!-- Good -->
<button disabled></button>
```

<h3 id="html-import">1-6. Import</h3>

- HTML5는 CSS와 JS 파일을 불러올 때 `type` 애트리뷰트는 이미 기본값이 지정되어 있으므로 선언하지 않는다.
- 일반적으로 JS 파일은 `<head>` 또는 `<body>` 엘리먼트의 가장 마지막에 작성한다.

<h3 id="html-comments">1-7. Comments</h3>

주석을 한줄로 작성할 경우 주석기호와 주석내용 사이에 한칸의 공백을 추가하며, 두줄 이상의 경우 주석기호와 주석내용 사이에 개행과 들여쓰기를 추가한다.

```html
<!-- This comment is 1 line -->
<!--
    This comment is
    2 lines
-->
```



<h2 id="css">2. CSS</h2>

CSS 코드의 작성 규칙을 설명한다.

<h3 id="css-syntax">2-1. Syntax</h3>

- **CSS는 컨벤션의 내용을 준수함과 동시에 원하는 스타일(nested, expanded, compact, compressed, ..) 중 하나의 규칙으로 통일하여 작성한다.**
- 들여쓰기는 2개 &middot; 4개의 공백 문자(소프트탭) 또는 하드탭 중 하나의 규칙으로 통일하여 작성한다.
- 프로퍼티는 영문 소문자를 사용한다.
- 일반적으로 작은 따옴표(`'`)를 사용하며 @charset 선언과 선택자 안에서만 큰 따옴표(`"`)를 사용한다. 만약 따옴표를 생략할 수 있는 경우에는 반드시 생략한다.

<h3 id="css-charset">2-2. Charset</h3>

문서의 언어셋은 일반적으로 `UTF-8`으로 선언하며 최상위에 선언한다. 언어셋이 정해진 번들링 파일이라면 선언하지 않는다.

```css
@charset "UTF-8";
```

<h3 id="css-selectors">2-3. Selectors</h3>

- **선택자는 가급적 종속하지 않는다.**
- **스타일 제어를 위해 아이디 선택자를 사용하는 것은 지양한다.**
- **렌더링 성능 최적화를 위해 클래스, 가상 선택자 외의 선택자는 사용을 지양한다.**
 
> ###### 참고 자료
> - <a href="http://markdotto.com/2012/03/02/stop-the-cascade/">Stop the cascade &middot; @mdo</a>
> - <a href="https://developer.mozilla.org/ko/docs/Web/CSS/Writing_Efficient_CSS">효율적인 CSS 작성하기 - CSS | MDN</a>

<h3 id="css-properties">2-4. Properties</h3>

#### A. 속기 프로퍼티 (Shorthand Properties)

속기로 작성 가능한 프로퍼티는 속기로 작성한다. 

```css
/* Bad */
.foo {
    border-top-style: none;
    font-family: palatino, georgia, serif;
    font-size: 100%;
    line-height: 1.6;
    padding-bottom: 2em;
    padding-left: 1em;
    padding-right: 1em;
    padding-top: 0;
}

/* Good */
.bar {
    border-top: 0;
    font: 100%/1.6 palatino, georgia, serif;
    padding: 0 1em 2em;
}
```

#### B. 단위 생략

속성값이 0인 값은 단위를 생략한다.

```css
/* Bad */
.foo {
    margin: 0px;
}

/* Good */
.bar {
    margin: 0;
}
```

#### C. 0 선행 생략

소수값 앞에 오는 0은 생략한다.

```css
/* Bad */
.foo {
    opacity: 0.5;
}

/* Good */
.bar {
    opacity: .5;
}
```

#### D. 속기 16진수

16진수 값들은 가능하다면 축약형으로 표현한다.

```css
/* Bad */
.foo {
    color: #aabbcc;
}

/* Good */
.bar {
    color: #abc;
}
```

<h3 id="css-import">2-5. Import</h3>

**CSS에서 기본으로 제공하는 `@import`는 성능 문제로 절대 사용하지 않는다.** 대신 아래의 방법 중 하나를 사용한다.

- 여러개의 `<link>` 엘리먼트를 사용
- 하나의 CSS 파일로 작성
    - 태스크러너 등의 도구를 이용하여 CSS 파일을 하나로 합침
    - SASS나 Stylus 등의 CSS 전처리기에서 제공하는 `@import`를 사용

```html
<!-- Too Bad -->
<style>
    @import url("one.css");
    @import url("two.css");
    @import url("three.css");
</style>

<!-- Good -->
<link rel="stylesheet" href="one.css">
<link rel="stylesheet" href="two.css">
<link rel="stylesheet" href="three.css">

<!-- Very Good -->
<link rel="stylesheet" href="bundle.css"> <!-- one.css, .. in bundle.css -->
```

<h3 id="css-nesting">2-6. Nesting</h3>

우리는 선택자의 중첩을 최대한 지양하므로 SASS, LESS, Stylus 등의 CSS 전처리기가 지원하는 Nesting 문법은 가급적 사용하지 않는다. **이것을 무분별하게 사용할 경우 컴파일된 CSS가 엉망이 될 수 있다.**

```scss
/* Bad */
.foo {
    .bar {
        color: #abc;
    }
}

/* Good */
.foo__bar {
    color: #abc;
}
```
 
> <a href="#css-selectors">2-3. Selectors</a> 섹션 참고

<h3 id="css-media-query">2-7. Media Query</h3>

미디어 쿼리의 위치는 상황에 따라 문서의 마지막에 작성하거나 또는 컴포넌트 단위로 분류하여 관련 규칙 바로 뒤에 작성한다.

```css
.foo-a {}
.foo-b {}

.bar {}

@media (min-width: 768px) {
  .foo-a {}
  .foo-b {}
}

/* or */

.foo-a {}
.foo-b {}
@media (min-width: 768px) {
  .foo-a {}
  .foo-b {}
}

.bar {}
```

<h3 id="css-resets">2-8. Resets</h3>

CSS 초기화 스타일은 서비스에 맞게 정의한다. 만약 <a target="_blank" href="http://necolas.github.io/normalize.css/">normalize.css</a>를 사용하는 경우 스타일 초기화를 하지 않는다.

<h3 id="css-prefix">2-9. Prefix</h3>

브라우저별 프리픽스 프로퍼티는 일반 프로퍼티보다 먼저 선언한다. 

```css
/* Bad */
.foo {
    box-shadow: 0 1px 2px rgba(0, 0, 0, .15);
    -webkit-box-shadow: 0 1px 2px rgba(0, 0, 0, .15);
}
/* Good */
.foo {
    -webkit-box-shadow: 0 1px 2px rgba(0, 0, 0, .15);
    box-shadow: 0 1px 2px rgba(0, 0, 0, .15);
}
```

<h3 id="css-comments">2-10. Comments</h3>

주석을 한줄로 작성할 경우 주석기호와 주석내용 사이에 한칸의 공백을 추가하며, 두줄 이상의 경우 아래의 문법을 따른다.

```css
/* This comment is 1 line */
/*
    This comment is
    2 lines
*/
```

#### A. 프로젝트 주석

프로젝트 정보를 나타내는 주석은 아래의 양식에 맞게 `@charset` 바로 아래에 작성한다. (`/*! */`)

```css
/*!
    @author My Name <email_id@domain.com> 
    @version v1.2.0 2016-04-11
*/
```

<dl>
    <dt><code>@author</code></dt>
    <dd>작성자 정보. 이름과 이메일을 작성한다.</dd>
    <dt><code>@version</code></dt>
    <dd>문서의 버전 및 작성일. 둘 중 하나만 작성하여도 상관없다.</dd>
</dl>

#### B. 참고 주석

작업 진행에 참고해야 하는 주석은 아래의 양식에 맞게 작성한다. (`/*# */`)

```css
/*#
    @title CSS z-index Guidelines 

    blah, blah, blah..
*/
```

<dl>
    <dt><code>@title</code></dt>
    <dd>주석 내용의 제목.</dd>
</dl>

#### C. 코드 주석

코드 그룹의 정보를 나타내는 주석은 아래의 형식에 맞게 작성한다. (`/*= */`)

```css
/*=
    @type Generic
    @name Reset
*/
article, aside, details, figcaption, figure, footer, header, menu, nav, section {}

/*=
    @type Components
    @name Combobox
    @since v1.1.0 2016-04-08
*/
.combobox {}
```

<dl>
    <dt><code>@type</code></dt>
    <dd>엘리먼트 그룹의 타입. 타입은 후술할 <a href="#naming">3. Naming</a>의 규칙과 동일하다.</dd>
    <dt><code>@name</code></dt>
    <dd>엘리먼트 그룹의 이름.</dd>
    <dt><code>@author</code></dt>
    <dd>작성자 정보. 프로젝트 주석에 표기된 작성자와 동일 인물이 아닐 경우에만 작성한다.</dd>
    <dt><code>@since</code></dt>
    <dd>작성된 버전 및 작성일. 문서의 최초 작성 이후 추가된 코드에만 표기하며, 프로젝트 주석의 <code>@version</code>과 같은 양식으로 작성한다.</dd>
</dl>



<h2 id="naming">3. Naming</h2>

네이밍 규칙을 설명한다.

<h3 id="naming-selectors">3-1. Selectors</h3>

> **이 컨벤션은 *<a target="_blank" href="https://en.bem.info/methodology/naming-convention/">BEM</a> 네이밍 컨벤션*과 *<a target="_blank" href="http://csswizardry.net/talks/2014/11/itcss-dafed.pdf">ITCSS</a> 아키텍쳐*가 조합된 *<a target="_blank" href="http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/">BEMIT</a> 방법론*을 기반으로 한다.**
>
> *참고 문서*
> - BEM
>   - <a target="_blank" href="https://en.bem.info/">BEM</a>
>   - <a target="_blank" href="http://getbem.com/">Get BEM</a>
> - ITCSS
>   - <a target="_blank" href="http://csswizardry.net/talks/2014/11/itcss-dafed.pdf">Managing CSS Projects with ITCSS</a>
>   - <a target="_blank" href="https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/">ITCSS: SCALABLE AND MAINTAINABLE CSS ARCHITECTURE</a>
>   - <a target="_blank" href="https://willianjusten.com.br/organizando-seu-css-com-itcss/">Organizando seu CSS com ITCSS</a>
> - BEMIT
>   - <a target="_blank" href="http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/">BEMIT: Taking the BEM Naming Convention a Step Further</a>
>   - <a target="_blank" href="http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/">More Transparent UI Code with Namespaces</a>
>   - <a target="_blank" href="http://www.jamesturneronline.net/blog/bemit-naming-convention.html">The BEMIT naming convention</a>


- 스타일시트의 계층(Section)은 Settings, Tools, Generic, Base, Objects, Components, Containers, Themes, Trumps로 나뉜다.
- 클래스명은 반드시 엘리먼트의 의미를 전부 담아야 한다.
- 클래스명은 가급적 메뉴 및 페이지 등에 상속받지 않으며, 디자인보다는 구조, 기능, 목적을 나타내는 이름으로 네이밍한다.
- **스타일 제어를 위해 아이디 선택자를 사용하는 것은 지양한다.**

#### A. Naming

Syntax: `[<namespace>-]<BLOCK>[__<ELEMENT>][--<MODIFIER>][.is|has-<STATE>]`

BEM의 네이밍 문법에 ITCSS 네임스페이스를 추가하고, 상태 클래스는 `modifier`에서 분리한다.

```html
<fieldset class="c-fieldset c-fieldset--simple">
    <input class="textfield" type="text">
    <input class="btn" type="reset">
    <input class="btn btn--submit is-disabled" type="submit" disabled>
</fieldset>
```

```css
.c-fieldset {}
.c-fieldset--simple {}
.textfield {}
.btn {}
.btn.is-disabled {}
.btn--submit {}
.btn--submit.is-disabled {}
```

#### B. Architecture

##### `@import` example with SASS(scss)

```scss
@import "settings/_breakpoints";
@import "settings/_colors";

@import "tools/_functions";
@import "tools/_mixins";

@import "generic/_normalize";

@import "base/_forms";
@import "base/_headings";
@import "base/_hr";
@import "base/_links";
@import "base/_lists";
@import "base/_page";
@import "base/_quotes";
@import "base/_tables";

@import "objects/_grid";

@import "components/_comment";
@import "components/_fields";
@import "components/_dialog";
@import "components/_drawer";
@import "components/_footer";
@import "components/_header";
@import "components/_page-title";
@import "components/_pagination";
@import "components/_post";
@import "components/_share-menu";

@import "containers/_about";
@import "containers/_archive";
@import "containers/_contact";
@import "containers/_error";
@import "containers/_faq";
@import "containers/_process";

@import "trumps/_blind";
```

##### a. Settings

CSS 전처리기를 사용할 경우 전역 변수를 작성한다.

```scss
$breakpoints: (
    'tablet': 'screen and (min-width: 600px) and (orientation: portrait), screen and (min-width: 1024px)',
    'tablet_portrait': 'screen and (min-width: 600px) and (orientation: portrait)',
    'tablet_landscape': 'screen and (min-width: 1024px)'
);
```

##### b. Tools

CSS 전처리기를 사용할 경우 Function과 Mixin을 작성한다.

```scss
$default-breakpoint: root;
$current-breakpoint: $default-breakpoint;
@mixin media($breakpoint) {
    $value: map-get($breakpoints, $breakpoint);
    @if $value != null {
        $current-breakpoint: $breakpoint !global;
        @media #{$value} {
            @content;
        }
        $current-breakpoint: $default-breakpoint !global;
    }
    @else {
        @warn "Invalid breakpoint `#{$breakpoint}`.";
    }
}
```

##### c. Generic

CSS 초기화 또는 normalize.css 등의 문서 초기 스타일을 지정한다.

```scss
html,
body {}
a,
input,
textarea,
button {}
```

##### d. Base

태그 선택자 또는 타입 선택자를 이용하여 각 태그 엘리먼트의 기본 스타일을 작성한다.

```scss
button,
input[type='button'],
input[type='submit'],
input[type='reset'],
input[type='image'] {}
```

##### e. Objects

Namespace: `o`

반복적이며 재사용이 가능한 디자인 패턴을 작성한다.  
이는 시각적인 효과보단 레이아웃을 위한 스타일을 중점으로 작성한다.

```scss
.o-row {}
.o-col {}
.o-col--s12 {}
.o-col--m12 {}
.o-col--l12 {}
```

###### 계층 간의 관계

| | Objects | Components | Containers |
| :--- | :---: | :---: | :---: |
| 조합 (`.object.foo`) | X | O | O |
| 포함 (`.object > .foo`) | O | O | O |

##### f. Components

Namespace: -

컴포넌트란 입력 필드, 버튼과 같이 완성된 UI 모듈을 뜻한다.  
여기서 컴포넌트는 기능을 가지지 않고 시각적으로만 완성된 `Dumb/Presentational Component`를 뜻한다.

```scss
.combobox {}
.combobox__item {}
.combobox.is-expanded {}
```

###### 계층 간의 관계

| | Objects | Components | Containers |
| :--- | :---: | :---: | :---: |
| 조합 (`.component.foo`) | O | X | X |
| 포함 (`.component > .foo`) | O | △ | X |

##### g. Containers

Namespace: `c`

컨테이너는 컴포넌트의 일종으로 기능을 가진 모듈(`Smart/Container Component`)을 뜻한다.

```scss
.c-about__title {}
.c-about__info {}
.c-about__contact {}
```

###### 계층 간의 관계

| | Objects | Components | Containers |
| :--- | :---: | :---: | :---: |
| 조합 (`.container.foo`) | O | X | X |
| 포함 (`.container > .foo`) | O | O | O |

##### h. Themes - optional

Namespace: `t`

테마 스타일을 작성한다. **이 클래스는 반드시 `body` 엘리먼트에만 추가**할 수 있다.
관리 방법은 여러가지가 있으나, 하나의 프로젝트 또는 서비스 내에서는 한가지 방법으로 통일한다.

###### Inline

엘리먼트와 함께 작성한다.

```scss
.combobox {
    .t-light & {}
}
```

```scss
.combobox {}
.t-light {
    .combobox {}
}
```

###### Separated layers

`Containers` 계층과 `Trumps` 계층 사이에 작성한다.

```scss
..
@import "containers/_about";

@import "themes/_light";

@import "trumps/_blind";
..
```

###### Separated CSS files

CSS 파일을 분리하여 작성한다.

```html
<link rel="stylesheet" href="/css/project.css">
<link rel="stylesheet" href="/css/theme-light.css">
```

##### i. Trumps(Utilities)

Namespace: `u`

스타일을 오버라이드하거나 전역 스타일로 사용할 수 있는 헬퍼를 작성한다.  
만약 스타일시트의 상단에 작성해야 할 경우 모든 프로퍼티에 `!important`를 추가한다.

```scss
.u-blind {}
```

<h3 id="naming-exception">3-2. Exception</h3>

#### A. 폼 애트리뷰트

- `id`, `name` 애트리뷰트 값은 서버사이드 언어의 네이밍 컨벤션에 맞게 작성한다. 단, 하이픈(`-`)을 사용하는 `케밥 표기법`(`kebab-case`)은 사용하지 않으며, 컨벤션이 없다면 `파스칼 표기법`(`PascalCase`)을 권장한다.
- `<form>` 엘리먼트에 제공되는 `name` 애트리뷰트는 서픽스 `form`을 반드시 추가한다.

```html
<!-- Good (PascalCase) -->
<form class="my-form" name="MyForm" id="MyForm">
    <input type="text" name="UserName" id="UserName">
</form>

<!-- Bad (kebab-case) -->
<form class="my-form" name="my-form" id="my-form">
    <input type="text" name="user-name" id="user-name">
</form>
```

#### B. ID 관계 애트리뷰트

> 여기서 이야기하는 ID 관계 애트리뷰트란, 엘리먼트의 관계 표시를 위해 `id` 애트리뷰트 값을 사용하는 모든 애트리뷰트를 말한다.

엘리먼트의 관계를 설명하기 위해 제공되는 `id` 애트리뷰트 값은 앞에 언더스코어(`_`) 하나를 추가한다. 만약 다른 용도(ex. 앵커의 참조 엘리먼트)로 함께 사용될 경우 언더스코어를 생략한다.

```html
<div id="lnb" role="navigation" aria-labelledby="_lnb-heading">
    <h2 id="_lnb-heading">Local Navigation Bar</h2>
</div>
```



<h2 id="changelogs">Changelogs</h2>

<a target="_blank" href="https://github.com/choi4450/markup-coding-conventions">https:&#47;&#47;github.com&#47;choi4450&#47;markup-coding-conventions</a>

> - 2016.06.21 네이밍 개편(BEMIT 도입)
> - 2016.04.08 개편
> - 2015.04.15 작성 완료



<h2 id="license">License</h2>

이 저작물은 <a rel="license" target="ccl" href="http://creativecommons.org/licenses/by-nc-sa/4.0/" style="vertical-align:top">크리에이티브 커먼즈 저작자표시-비영리-동일조건변경허락 4.0 국제 라이선스</a>에 따라 이용할 수 있습니다.

<img alt="" title="" style="border-width:0;vertical-align:top" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" />
