# Markup Coding Conventions <small>(Markup Coding Style Guide)</small>



## Table of Contents

<a href="#glossaries">Glossaries</a>

- <a href="#html">1. HTML</a>
    - <a href="#html-syntax">1-1. Syntax</a>
    - <a href="#html-doctype">1-2. Doctype</a>
    - <a href="#html-encoding">1-3. Encoding</a>
    - <a href="#html-metadata">1-4. Metadata</a>
    - <a href="#html-elements">1-5. Elements</a>
    - <a href="#html-attributes">1-6. Attributes</a>
    - <a href="#html-import">1-7. Include</a>
    - <a href="#html-comments">1-8. Comments</a>
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
    - <a href="#naming-files">3-2. Files</a>
    - <a href="#naming-prefix">3-3. Prefix</a>

<a href="#changelogs">Changelogs</a>  
<a href="#license">License</a>



<h2 id="glossaries">Glossaries</h2>

먼저 **마크업 코딩 컨벤션**에 자주 사용되는 용어의 정의를 설명한다.

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
    <dt>프리픽스(Prefix)</dt>
    <dd>네이밍 시 사용되는 접두사를 의미한다.</dd>
    <dt>컴포넌트(Component)</dt>
    <dd>온전한 기능을 가진 컨텐츠 단위의 UI 구성요소를 의미한다. 사이트의 메뉴, 쇼핑몰의 상품 목록, 언론 사이트의 댓글 폼 등을 예로 들 수 있다.</dd>
    <dt>모듈(Module)</dt>
    <dd>반복적이며 재사용이 가능한 작은 단위의 UI 구성요소를 의미한다. 이는 컴포넌트보다 작은 단위이다. 예를 들어 텍스트 박스, 셀렉트 박스, 버튼 등이 있다.</dd>
</dl>



<h2 id="html">1. HTML</h2>

HTML 코드의 작성 규칙을 설명한다.

<h3 id="html-syntax">1-1. Syntax</h3>

- 들여쓰기는 4개의 공백 문자를 가지는 하드탭(<kbd>tab</kbd>)을 사용한다.
- 엘리먼트 명과 애트리뷰트 명은 영문 소문자를 사용한다.
- 모든 애트리뷰트값은 큰 따옴표(`"`)를 사용하여 감싼다.
- 단일 태그 엘리먼트는 슬래시(`/`)를 사용하지 않는다.
- 닫는 태그가 선택적인 경우에도 생략하지 않는다. (ex: `</li>`, `</body>`)

<h3 id="html-doctype">1-2. Doctype</h3>

Doctype은 일반적으로 HTML5 DTD로 선언한다.
 
```html
<!DOCTYPE html>
```

<h3 id="html-encoding">1-3. Encoding</h3>

문서의 `Charset`은 일반적으로 `UTF-8`으로 선언하며 `<head>` 엘리먼트 내에서 최초의 엘리먼트로 작성한다.

```html
<meta charset="utf-8">
```

<h3 id="html-metadata">1-4. Metadata</h3>

- IE 브라우저의 호환성을 위해 문서모드를 `Edge`로 선언하여 최신 버전의 IE로 렌더링되도록 한다.
    ```html
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    ```
- 아래의 `<meta>` 엘리먼트를 추가하여 브라우저가 전화번호 또는 이메일, 주소 포맷을 가진 문자를 감지하지 못하도록 한다.
    ```html
    <meta name="format-detection" content="telephone=no,address=no,email=no">
    ```
- 필요에 따라 `keywords`, `description` 등의 다른 `<meta>` 엘리먼트를 추가하도록 한다.
- `<head>` 엘리먼트의 자식 엘리먼트 작성 순서는 아래와 같다.
    1. Charset
    2. X-UA-Compatible
    3. Viewport
    4. Title
    5. ..

<h3 id="html-elements">1-5. Elements</h3>

- 렌더링 엔진 최적화를 위해 **스타일 또는 스크립트 제어가 필요한 모든 엘리먼트에는 클래스를 부여**하도록 한다.

#### A. 스타일 제어가 어려운 엘리먼트

자식 엘리먼트로 사용할 수 있는 태그가 한정적인 엘리먼트(`<table>`, `<ul>`, ..) 또는 자기 자신의 스타일 제어에 한계를 가진 엘리먼트(`<img>`, `<select>`, ..)는 의미없는 엘리먼트로 감싸는 것을 권장한다. (이 외의 불필요한 엘리먼트 상속은 피하도록 함)

```html
<!-- Not Bad -->
<table class="table"></table>

<!-- Good -->
<div class="table">
    <table></table>
</div>
```

#### B. 테이블 제목

`<caption>` 엘리먼트를 숨김 처리할 때는 의미없는 엘리먼트로 감싸서 숨기도록 한다.

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

#### C. 테이블 그룹

`<table>` 엘리먼트를 제작 시 `<thead>`, `<tfoot>`의 유무와 관계없이 `<tbody>`를 사용하도록 한다.

```html
<!-- Bad -->
<table>
    <tr></tr>
</table>

<!-- Good -->
<table>
    <tbody>
        <tr></tr>
    </tbody>
</table>
```

#### D. 입력 폼

회원가입 등의 문서 작성 폼에 사용되는 `<input>`, `<select>`, `<textarea>` 엘리먼트는 서로 너비 값이 상이하다면 인라인 스타일로 제어한다.

```html
<!-- Bad -->
<input type="text" class="input type-width_120">
<input type="text" class="input type-width_180">

<!-- Good -->
<input type="text" class="input" style="width:120px">
<input type="text" class="input" style="width:180px">
```

#### E. 버튼

`<button>` 엘리먼트는 `type` 애트리뷰트가 선언되지 않으면 `<form>` 엘리먼트에서 의도치 않은 액션을 발생시키므로 기본값으로 `type="button"`을 선언한다.

```html
<!-- Bad -->
<button></button>

<!-- Good -->
<button type="button"></button>
```

<h3 id="html-attributes">1-6. Attributes</h3>

- 엘리먼트 애트리뷰트의 선언 순서는 상황에 맞게 가변 애트리뷰트를 가장 나중에 작성한다.
    ```html
    <input class="input" type="password" name="field-pw" id="field-pw" title="비밀번호" style="width:100px" disabled>
    ```
- HTML5에서 Boolean 애트리뷰트는 값을 지정하지 않은 채 선언되어도 `true`를 의미하므로 필요치 않다면 값을 지정하지 않는다.

<h3 id="html-import">1-7. Include</h3>

- HTML5는 CSS와 JS 파일을 불러올 때 `type` 애트리뷰트는 이미 기본값이 지정되어 있으므로 선언하지 않는다.
- 일반적으로 JS 보다 CSS를 먼저 선언한다.
- 일반적으로 JS 파일은 종류에 따라 `<head>` 또는 `<body>` 엘리먼트의 마지막에 작성한다.

<h3 id="html-comments">1-8. Comments</h3>

주석을 한줄로 작성할 경우 주석기호와 주석내용 사이에 한칸의 공백을 추가하며, 두줄 이상의 경우 주석기호와 주석내용 사이에 개행과 들여쓰기를 추가한다.

```html
<!-- This comment is 1 line -->
<!--
    This comment is
    2 lines
-->
```

#### A. 참고 주석

작업 진행에 참고해야 하는 주석은 맨 앞에 `@desc`를 추가하여 작성한다.

```html
<!-- @desc
    blah, blah, blah..
-->
```

#### B. 엘리먼트 주석

레이아웃 또는 그루핑된 엘리먼트의 시작과 끝을 알리는 주석은 아래의 형식에 맞게 작성하며, 맨 앞에 `@start` 또는 `@end`를 표기한다.

```html
<!-- @start Content -->
<div id="content" role="main"></div>
<!-- @end Content -->
```



<h2 id="css">2. CSS</h2>

CSS 코드의 작성 규칙을 설명한다.

<h3 id="css-syntax">2-1. Syntax</h3>

- **CSS의 코드 스타일은 컨벤션에서 강제하는 내용을 준수함과 동시에 자신이 원하는 스타일(nested, expanded, compact, compressed, ..)로 작성한다. 단, 하나의 프로젝트 또는 서비스 내에서는 통일된 스타일로 작성하도록 한다.**
- 들여쓰기는 4개의 공백 문자를 가지는 하드탭(<kbd>tab</kbd>)을 사용한다.
- 프로퍼티는 영문 소문자를 사용한다.
- 일반적으로 작은 따옴표(`'`)를 사용하며 @charset 선언과 선택자 안에서만 큰 따옴표(`"`)를 사용한다. 만약 따옴표를 생략할 수 있는 경우에는 반드시 생략한다.
    ```css
    @charset "UTF-8";
    input[type="text"] {
        background: url(bg.gif);
        font-family: Dotum,'돋움';
        content: 'lol';
    }
    ```

<h3 id="css-charset">2-2. Charset</h3>

문서의 `Charset`은 일반적으로 `UTF-8`으로 선언하며 최상위에 선언한다.

```css
@charset "UTF-8";
```

<h3 id="css-selectors">2-3. Selectors</h3>

- **선택자는 가급적 종속하지 않는다.**
- **아이디는 스타일 제어를 위한 선택자로 절대 사용하지 않는다.**
- **렌더링 성능 최적화를 위해 클래스, 가상 선택자 외의 선택자는 사용을 지양한다.** 

<dl>
    <dt>참고 자료</dt>
    <dd>
        <ul>
            <li><a href="http://markdotto.com/2012/03/02/stop-the-cascade/">Stop the cascade &middot; @mdo</a></li>
            <li><a href="https://developer.mozilla.org/ko/docs/Web/CSS/Writing_Efficient_CSS">효율적인 CSS 작성하기 - CSS | MDN</a></li>
        </ul>
    </dd>
</dl>

<h3 id="css-properties">2-4. Properties</h3>

- 16진수 값들은 가능하다면 축약형으로 표현한다. (ex: `#ffffff` 대신 `#fff`)
- 속성값이 0인 값은 단위를 생략한다. (ex: `0px` 대신 `0`)
- `0.*`의 소수값은 소수점 앞의 0을 생략한다. (ex: `0.5` 대신 `.5`)
- 프로퍼티값 안의 콤마는 뒤에 공백 문자 하나를 포함한다.
    ```css
    /* Bad */
    .foo { box-shadow: 0px 1px 2px #ccc,inset 0 1px 0 #fff; }
    
    /* Good */
    .foo { box-shadow: 0px 1px 2px #ccc, inset 0 1px 0 #fff; }
    ```
- rgb(), rgba(), hsl(), hsla() 등의 색상을 나타내는 프로퍼티값은 다른 프로퍼티값과의 차별화를 위해 콤마 뒤에 공백 문자를 포함시키지 않는다.
    ```css
    /* Bad */
    .foo { background: rgba(0, 0, 0, .33); }
    
    /* Good */
    .foo { background: rgba(0,0,0,.33); }
    ```
- rect() 프로퍼티값 안에서는 구버전의 IE 브라우저와의 호환성을 위해 콤마 대신 공백 문자만 표기한다.
    ```css
    /* Bad */
    .foo { position: absolute; clip: rect(0, 0, 0, 0); }
    
    /* Good */
    .foo { position: absolute; clip: rect(0 0 0 0); }
    ```
- 프로퍼티 작성 순서는 아래 순서를 따르며, 명시되지 않은 프로퍼티는 적절한 위치에 배치하여 사용한다.
    - content
    - overflow
    - opacity
    - display
    - zoom
    - visibility
    - position
    - float
    - clear
    - box-sizing
    - width
    - height
    - padding
    - border
    - margin
    - background
    - color
    - font-size
    - line-height

<h3 id="css-import">2-5. Import</h3>

**CSS에서 기본으로 제공하는 `@import`는 성능 문제로 절대 사용하지 않는다.** 대신 아래의 방법 중 하나를 사용하도록 한다.

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
```

<h3 id="css-nesting">2-6. Nesting</h3>

SASS, LESS, Stylus 등의 CSS 전처리기에서 선택자 중첩 시 <a href="#css-selectors">2-3. Selectors</a> 섹션에서 설명한 것과 같이 최대 3단계까지만 중첩하며, 가급적 중첩하지 않는다. **이것을 무분별하게 사용할 경우 컴파일된 CSS가 엉망이 될 수 있다.**

<h3 id="css-media-query">2-7. Media Query</h3>

미디어 쿼리의 위치는 상황에 따라 문서의 마지막에 작성하거나 스타일 코드를 모듈, 컴포넌트 등의 단위로 분류하여 관련 규칙 바로 뒤에 작성한다.

```css
.element {}
.element-foo {}
.element-bar {}
@media (min-width: 768px) {
  .element {}
  .element-foo {}
  .element-bar {}
}
```

<h3 id="css-resets">2-8. Resets</h3>

CSS 초기화 스타일은 서비스에 맞게 정의한다.  
단 <a target="_blank" href="http://necolas.github.io/normalize.css/">normalize.css</a>를 사용하는 경우 스타일 초기화는 하지 않는다.

<h3 id="css-prefix">2-9. Prefix</h3>

브라우저별 프리픽스 프로퍼티는 일반 프로퍼티보다 먼저 선언한다. 

```css
/* Bad */
.foo {
    box-shadow: 0 1px 2px rgba(0,0,0,.15);
    -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
/* Good */
.foo {
    -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
    box-shadow: 0 1px 2px rgba(0,0,0,.15);
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
    @type Base
    @name Reset
*/
article, aside, details, figcaption, figure, footer, header, menu, nav, section {}

/*=
    @type Module
    @name Combobox
    @namespace foo
    @since v1.1.0 2016-04-08
*/
#foo-cbo {}

/*=
    @type Media
    @name Screen Reader
    @author Your Name <email_id@domain.com>
*/
@media aural, speech {}
```

<dl>
    <dt><code>@type</code></dt>
    <dd>엘리먼트 그룹의 타입. <code>Setting</code>, <code>Tool</code>, <code>generic</code>, <code>base</code>, <code>object</code>, <code>layout</code>, <code>component</code>, <code>theme</code>, <code>trump</code>로 나뉜다. (<a target="_blank" href="http://csswizardry.net/talks/2014/11/itcss-dafed.pdf">ITCSS</a>)</dd>
    <dt><code>@name</code></dt>
    <dd>엘리먼트 그룹의 이름.</dd>
    <dt><code>@namespace</code></dt>
    <dd>엘리먼트 그룹의 네임스페이스. 네임스페이스가 없거나 모듈의 기본값(<code>mod</code>)이라면 생략 가능하다.</dd>
    <dt><code>@author</code></dt>
    <dd>작성자 정보. 프로젝트 주석에 표기된 작성자와 동일 인물이 아닐 경우에만 작성한다.</dd>
    <dt><code>@since</code></dt>
    <dd>작성된 버전 및 작성일. 문서의 최초 작성 이후 추가된 코드에만 표기하며, 프로젝트 주석의 <code>@version</code>과 같은 양식으로 작성한다.</dd>
</dl>



<h2 id="naming">3. Naming</h2>

선택자, 이미지, 파일 및 폴더의 네이밍 규칙을 설명한다.

<h3 id="naming-selectors">3-1. Selectors</h3>

> **이 문서는 *<a target="_blank" href="https://en.bem.info/methodology/naming-convention/">BEM</a> 네이밍 컨벤션*과 *<a target="_blank" href="http://csswizardry.net/talks/2014/11/itcss-dafed.pdf">ITCSS</a> 아키텍쳐*가 조합된 *<a target="_blank" href="http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/">BEMIT</a> 방법론*을 기본으로 한다.** (BEM + ITCSS = BEMIT)  
> 스타일시트의 계층(또는 섹션)은 Settings, Tools, Generic, Base, Objects, Layouts, Components, Themes, Trumps로 나뉜다.
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

- **아이디는 스타일 제어를 위한 선택자로 절대 사용하지 않는다.**
- 클래스명은 반드시 엘리먼트의 의미를 전부 담아야 한다.  
  용량 축소의 문제로 byte 수를 줄여야 할 경우 클래스명을 축약할 수 있으며, 이러한 경우 CSS의 해당 선택자에 주석으로 원래 명칭을 반드시 기재한다.
- 클래스명은 가급적 메뉴 및 페이지 등에 상속받지 않도록 하며, 디자인적인 면보다는 구조, 기능, 목적을 나타내는 이름으로 네이밍한다.

#### A. Naming

Syntax: `[<namespace>-]<block-name>[__<element-name>][--<modifier-name>][.is|has-<state-name>]`

BEM의 네이밍 문법에 ITCSS의 네임스페이스가 추가되었다.

```html
<fieldset class="fieldset fieldset--simple">
    <input class="fieldset__input" type="text">
    <input class="fieldset__btn" type="reset">
    <input class="fieldset__btn fieldset__btn--submit is-disabled" type="submit">
</fieldset>
```

```css
.fieldset {}
.fieldset--simple {}
.fieldset__input {}
.fieldset__btn {}
.fieldset__btn.is-disabled {}
.fieldset__btn--submit {}
.fieldset__btn--submit.is-disabled {}
```

#### B. Architecture

##### `@import` example with SASS

```sass
@import "settings/_breakpoints";
@import "settings/_colors";

@import "tools/_functions";
@import "tools/_mixins";

@import "generic/_normalize.scss";

@import "base/_forms";
@import "base/_headings";
@import "base/_hr";
@import "base/_links";
@import "base/_lists";
@import "base/_page";
@import "base/_quotes";
@import "base/_tables";

@import "objects/_combobox";
@import "objects/_overlays";
@import "objects/_toggle-button";

@import "layouts/_aside";
@import "layouts/_container";
@import "layouts/_drawer";
@import "layouts/_footer";
@import "layouts/_header";
@import "layouts/_wrapper";

@import "components/_about";
@import "components/_ads-banner";
@import "components/_archive";
@import "components/_comments";
@import "components/_contact";
@import "components/_error";
@import "components/_faq";
@import "components/_page-title";
@import "components/_pagination";
@import "components/_post";
@import "components/_process";
@import "components/_share-menu";

@import "trumps/_blind";
@import "trumps/_clearfix";
```

##### a. Settings

전역 변수를 작성한다.

```sass
$breakpoints: (
    'tablet': 'screen and (min-width: 600px) and (orientation: portrait), screen and (min-width: 1024px)',
    'tablet_portrait': 'screen and (min-width: 600px) and (orientation: portrait)',
    'tablet_landscape': 'screen and (min-width: 1024px)'
);
```

##### b. Tools

CSS 전처리기를 사용할 경우 Function과 Mixin을 작성한다.

```sass
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

```sass
article,
aside,
details,
figcaption,
figure,
footer,
header,
menu,
nav,
section {}
html,
body {}
```

##### d. Base

클래스 없이 태그 선택자 또는 타입 선택자를 이용하여 각 태그 엘리먼트의 기본 스타일을 작성한다.

```sass
button,
input[type='button'],
input[type='submit'],
input[type='reset'],
input[type='image'] {}
```

##### e. Objects

Namespace: `o`

반복적이며 재사용이 가능한 디자인 패턴을 작성한다.  
블로그 댓글, 트윗 등의 미디어 객체 또는 모듈 등이 해당된다.

```sass
.o-combobox {}
.o-combobox__item {}
.o-combobox.is-expanded {}
```

##### f. Layouts

Namespace: `l`

레이아웃의 스타일을 작성한다.  
이는 `Objects` 계층에 포함되어 있었으나 용도를 더 명확히 구분하기 위해 분리하였다.

```sass
.l-header {}
.l-header__item {}
.l-header--fixed {}
```

##### g. Components

Namespace: `c`

컴포넌트의 스타일을 작성한다.

```sass
.c-modal {}
.c-modal__title {}
.c-modal--gallery {}
```

##### h. Themes - optional

Namespace: `t`

테마 스타일을 작성한다. **이 클래스는 반드시 `body` 엘리먼트에만 추가**할 수 있다.
관리 방법은 여러가지가 있으나, 하나의 프로젝트 또는 서비스 내에서는 한가지 방법으로 통일하도록 한다.

###### Inline

엘리먼트와 함께 작성한다.

```sass
.c-modal {
    .t-light & {}
}
```

```sass
.c-modal {}
.t-light {
    .c-modal {}
}
```

###### Separated layers

`Components` 계층과 `Trumps` 계층 사이에 작성한다.

```sass
..
@import "components/_share-menu";

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

```sass
.u-blind {}
.u-clearfix {}
```

<h3 id="naming-files">3-2. Files</h3>

#### A. HTML

HTML 파일은 페이지명을 토대로 네이밍한다.

#### B. CSS

CSS 파일은 컨텐츠를 토대로 네이밍하며, 하나의 CSS만 사용할 경우 `style.css`로 네이밍한다.

#### C. 이미지

- 이미지 확장자와 관계없이 중복되지 않도록 네이밍한다.
    ```shell
    bg-exam.jpg
    bg-exam2.gif
    bg-exam3.png
    bg-menu
    bg-menu--hover.jpg
    bg-menu.type-compact--hover.jpg
    bg-menu.type-compact--scrolled.jpg
    ```
- 임시 이미지의 경우 앞에 언더스코어(`_`)를 추가한다.
    ```shell
    _img-exam.png
    _bg-exam.png
    ```

<h3 id="naming-prefix">3-3. Prefix</h3>

#### A. 폼 애트리뷰트

`<input>`, `<select>` 등의 사용자 입력을 받는 폼과 관련된 엘리먼트에 제공되는 `id`, `name` 애트리뷰트 값은 프리픽스 `field`를 추가한다.
**엘리먼트가 데이터를 주고받는 용도로 사용되지 않을 경우 *관계 애트리뷰트*의 규칙을 따른다.**

```html
<label for="field-car">Select car</label>
<select id="field-car" name="field-car">
    <option value="volvo">Volvo</option>
    <option value="mercedes">Mercedes</option>
    <option value="audi">Audi</option>
</select>
```

#### B. 테이블 셀 애트리뷰트

`<th>`, `<td>` 엘리먼트에 제공되는 `id`, `headers` 애트리뷰트 값은 프리픽스 `cell`를 추가한다.

```html
<table>
    <tbody>
        <tr>
            <th id="cell-name">Name</th>
            <th id="cell-email">Email</th>
        </tr>
        <tr>
            <td headers="cell-name">Overtimeman</td>
            <td headers="cell-email">overtimeman@example.com</td>
        </tr>
    </tbody>
</table>
```

#### C. 관계 애트리뷰트

> 여기서 얘기하는 관계 애트리뷰트(Relationship Attributes)란,  
> 'rel' 애트리뷰트가 아닌 엘리먼트의 관계를 나타내는 모든 애트리뷰트를 뜻한다.  
> 위에서 이미 설명한 애트리뷰트의 경우 이 섹션에서 다루는 내용과는 별개로 예외처리한다.

엘리먼트의 관계를 설명하기 위해 제공되는 `id` 애트리뷰트 값은 앞에 언더스코어(`_`) 하나를 추가한다.
**앵커의 참조 엘리먼트로 사용될 경우 가급적 언더스코어를 지우도록 한다.**

```html
<div id="lnb" role="navigation" aria-labelledby="_lnb_heading">
    <h2 id="_lnb_heading">Local Navigation Bar</h2>
</div>
```



<h2 id="changelogs">Changelogs</h2>

<a target="_blank" href="https://github.com/choi4450/markup-coding-conventions">https:&#47;&#47;github.com&#47;choi4450&#47;markup-coding-conventions</a>

> - 2016.06.21 네이밍 개편(BEMIT 도입) - 최규민
> - 2016.04.08 개편
> - 2016.02.02 컴포넌트 관련 용어 재정의, 프리픽스 네이밍 변경(글로벌 컴포넌트, ui → 모듈, mod) - 최규민
> - 2016.01.23 확장 네이밍 분류 정의 및 조합 방법 변경 - 최규민
> - 2016.01.07 렌더링 엔진 최적화를 위한 클래스 사용 방법 정의 - 최규민
> - 2015.12.14 글로벌 컴포넌트 익스텐션 정의 - 최규민
> - 2015.10.28 프리픽스 네이밍 수정, 키보드 접근성 내용 추가 - 최규민
> - 2015.09.10 네이밍 규칙 개선 - 최규민
> - 2015.05.29 전역 및 컨텐츠 네이밍 내용 보충 - 최규민
> - 2015.05.18 글로벌 컴포넌트 네이밍 방법 정의 - 최규민
> - 2015.04.15 작성 완료



<h2 id="license">License</h2>

이 저작물은 <a rel="license" target="ccl" href="http://creativecommons.org/licenses/by-nc-sa/4.0/" style="vertical-align:top">크리에이티브 커먼즈 저작자표시-비영리-동일조건변경허락 4.0 국제 라이선스</a>에 따라 이용할 수 있습니다.

<img alt="" title="" style="border-width:0;vertical-align:top" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" />
