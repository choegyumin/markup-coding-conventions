# Markup Coding Conventions <small>(HTML/CSS Style Guide)</small>


## Table of Contents

[Glossaries](#glossaries)  

- [1. HTML](#html)
  - [1-1. Syntax](#html-syntax)
  - [1-2. Doctype](#html-doctype)
  - [1-3. Metadata](#html-metadata)
  - [1-4. Elements](#html-elements)
  - [1-5. Attributes](#html-attributes)
  - [1-6. Import](#html-import)
- [2. CSS](#css)
  - [2-1. Syntax](#css-syntax)
  - [2-2. Charset](#css-charset)
  - [2-3. Selectors](#css-selectors)
  - [2-4. z-index](#css-z-index)
  - [2-5. Import](#css-import)
  - [2-6. Media Query](#css-media-query)
  - [2-7. Nesting](#css-nesting)
  - [2-8. Extend](#css-extend)
  - [2-9. Reset](#css-reset)
  - [2-10. Vendor Prefix](#css-vendor-prefix)
- [3. Naming](#naming)
  - [3-1. Selectors](#naming-selectors)

[Changelogs](#changelogs)  
[License](#license)  



<h2 id="glossaries">Glossaries</h2>

먼저 스타일 가이드에 자주 사용되는 용어의 정의를 설명합니다.

<dl>
  <dt>엘리먼트(Element)</dt>
  <dd>HTML 문서를 구성하는 요소(태그)를 의미합니다.</dd>
  <dt>애트리뷰트(Attribute)</dt>
  <dd>엘리먼트에 부여할 수 있는 특성을 의미합니다.</dd>
  <dt>선택자(Selector)</dt>
  <dd>엘리먼트를 식별할 수 있는 이름을 의미합니다.</dd>
  <dt>스타일(Style)</dt>
  <dd>엘리먼트에 부여할 스타일 시트(Style Sheet)를 의미합니다. 인라인 스타일(Inline Style), 내부 스타일(Internal Style), 외부 스타일(External Style), CSS 네가지로 구분합니다.</dd>
  <dt>프로퍼티(Property)</dt>
  <dd>스타일과 관련된 문맥일 경우 스타일 시트의 속성을 의미합니다.</dd>
  <dt>프리픽스(Prefix) & 서픽스(Suffix)</dt>
  <dd>네이밍 시 사용되는 접두사, 접미사를 의미합니다.</dd>
  <dt>컴포넌트(Component)</dt>
  <dd>하나 이상의 기능 또는 역할을 가진 컨텐츠 단위의 UI 구성요소를 의미합니다.</dd>
</dl>


[↑ Table of Conetnts](#table-of-contents)



<h2 id="html">1. HTML</h2>

HTML 코드의 작성 규칙을 설명합니다.

<h3 id="html-syntax">1-1. Syntax</h3>

> **<a target="_blank" href="http://editorconfig.org/">EditorConfig</a>의 사용을 권장합니다!**

- 들여쓰기는 2개의 공백 문자(소프트탭)을 사용하세요. 다른 규칙으로 통일하여 작성해도 됩니다.
- 모든 엘리먼트 명과 애트리뷰트 명은 케밥 표기법(`kebab-case`)으로 작성하세요.
- 모든 애트리뷰트 값은 큰 따옴표(`"`)로 감싸세요.
- 닫는 태그가 선택적이라도 생략하지 마세요. (ex: `</li>`, `</body>`)

<h3 id="html-doctype">1-2. Doctype</h3>

Doctype은 HTML5 DTD로 선언하세요. 이어서 자기 마침 태그(Self-Closing Tags)에 후행 슬래시(`/`)를 사용하지 마세요.

```html
<!DOCTYPE html>
```

```html
<!-- Bad -->
<input />
<br />

<!-- Good -->
<input>
<br>
```

<h3 id="html-metadata">1-3. Metadata</h3>

`<head>` 엘리먼트의 자식 엘리먼트는 아래의 순서대로 작성하세요.

1. Charset
1. X-UA-Compatible
1. Viewport
1. Title
1. Meta
1. Style
1. JavaScript

```html
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no,target-densitydpi=medium-dpi">
<title>Hello, World!</title>
<meta property="og:title" content="Hello, World!" />
<link rel="stylesheet" href="foo.css">
<script src="bar.js"></script>
```

#### A. Charset

문서의 언어셋은 `UTF-8`으로 선언하세요.

```html
<meta charset="utf-8">
```

#### B. X-UA-Compatible

PC용 웹사이트는 최신 버전의 IE로 렌더링하기 위해 문서모드를 `Edge`로 선언하세요.

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

<h3 id="html-elements">1-4. Elements</h3>

#### A. `<body>` 래퍼 엘리먼트

필요에 따라 본문을 숨겨야 하거나, 본문 위에 다른 레이어 엘리먼트가 겹칠 수도 있습니다. 본문의 화면 조작을 위해 본문을 래퍼 엘리먼트에 작성하세요.

```html
<body>
  <div id="app">
    <h1>Hello, World!</h1>
  </div>
  <div role="dialog" class="dialog"></div>
</body>
```

#### B. 스타일 제어가 어려운 엘리먼트

자식 엘리먼트 태그가 한정적이거나(ex. `<table>`) 스타일 제어에 한계를 가진 엘리먼트(ex. `<select>`)가 컴포넌트의 루트 역할로 쓰일 땐 나중에 발생할 유지보수를 고려해 `<div>`나 `<span>` 엘리먼트로 감싸는 것을 권장합니다.

> 이 외의 불필요한 엘리먼트 상속은 반드시 피해야 합니다!

```html
<!-- Not Bad -->
<table class="table"></table>
<select class="combobox"></select>

<!-- Good -->
<div class="table">
  <table></table>
</div>
<span class="combobox">
  <select></select>
</span>
```

#### C. 테이블 제목

`<caption>` 엘리먼트의 뷰를 숨길 때는 새로운 엘리먼트로 감싸서 숨기세요. `<caption>`을 바로 숨긴다면 브라우저에 따라 스타일이 깨질 수도 있습니다.

```html
<!-- Bad -->
<table>
  <caption class="blind">My Caption</caption>
</table>

<!-- Good -->
<table>
  <caption>
    <div class="blind">My Caption</div>
  </caption>
</table>
```

테이블의 제목이 필요없거나 이미 제공되었다면 생략하세요. 컨텐츠를 중복 제공하는 것은 좋지 않습니다. 이 때 `aria-labelledby` 애트리뷰트를 사용하면 더 좋습니다.

```html
<!-- Bad -->
<h4>My Caption</h4>
<table>
  <caption>
    <div class="blind">My Caption</div>
  </caption>
</table>

<!-- Not Bad -->
<h4>My Caption</h4>
<table></table>

<!-- Good -->
<h4 id="_my-caption">My Caption</h4>
<table aria-labelledby="_my-caption"></table>
```

#### D. 입력 필드

회원가입 폼의 입력 필드처럼 너비, 높이가 유동적이라면 인라인 스타일로 제어하세요. 이렇게 하면 불필요한 클래스 생성을 막을 수 있습니다.

```html
<!-- Bad -->
<input type="text" class="input input--width-120">
<input type="text" class="input input--width-180">

<!-- Good -->
<input type="text" class="input" style="width:120px">
<input type="text" class="input" style="width:180px">
```

<h3 id="html-attributes">1-5. Attributes</h3>

애트리뷰트는 변하지 않는 것부터 먼저 선언하세요. 애트리뷰트의 순서가 비슷한 엘리먼트끼리 통일되므로 검색하기 편해집니다.

```html
<input class="input" type="text" id="user-id" name="UserId" title="아이디" style="width:100px">
<input class="input" type="password" id="user-pw" name="UserPw" title="비밀번호" style="width:120px">
```

#### A. Boolean 애트리뷰트

HTML5에서는 Boolean 애트리뷰트를 선언하는 것 만으로도 `true` 값을 가집니다. 필요하지 않다면 값을 작성하지 마세요.

```html
<!-- Not Bad -->
<button disabled="true"></button>

<!-- Good -->
<button disabled></button>
```

#### B. `name` 애트리뷰트

`name` 애트리뷰트 값은 비즈니스 로직을 작성하는 언어의 네이밍 규칙에 맞게 작성하는 것을 권장합니다.

```html
<!-- PascalCase -->
<form class="form" id="my-form" name="MyForm">
  <input class="input" type="text" id="my-user-name" name="MyUserName">
</form>
```

<h3 id="html-import">1-6. Import</h3>

- HTML5에서 CSS와 JS 파일을 불러올 때 `type` 애트리뷰트는 이미 기본값을 가집니다. 필요하지 않다면 선언하지 마세요.
- `<script>` 엘리먼트는 가급적 `<head>` 또는 `<body>` 엘리먼트의 가장 마지막에 작성하세요. 웹브라우저는 `<script>` 엘리먼트를 만나면 처리가 끝날 때까지 HTML 파싱을 멈춥니다.


[↑ Table of Conetnts](#table-of-contents)



<h2 id="css">2. CSS</h2>

CSS와 SASS, LESS, Stylus 등의 CSS 전처리기(CSS Preprocessor) 코드의 작성 규칙을 설명합니다.

<h3 id="css-syntax">2-1. Syntax</h3>

> **<a target="_blank" href="http://editorconfig.org/">EditorConfig</a>와 Lint의 사용을 권장합니다!**

- 들여쓰기는 2개의 공백 문자(소프트탭)을 사용하세요. 다른 규칙으로 통일하여 작성해도 됩니다.
- 프로퍼티는 한 줄에 하나씩 작성하세요. 다른 규칙으로 통일하여 작성해도 됩니다.
- 프로퍼티는 영문 소문자로 작성하세요.
- 일반적으로 작은 따옴표(`'`)를 사용하지만 `@charset` 선언과 타입 선택자는 큰 따옴표(`"`)를 사용하세요. 가능하다면 생략하는 것이 가장 좋습니다.

<h3 id="css-charset">2-2. Charset</h3>

문서의 언어셋은 `UTF-8`으로 최상위에 선언하세요. 언어셋이 정해진 번들링 파일이라면 선언하지 않습니다.

```css
@charset "UTF-8";
```

<h3 id="css-selectors">2-3. Selectors</h3>

- **선택자는 가급적 중첩하지 마세요!**
- **렌더링 성능 최적화를 위해 클래스, 가상 선택자 외의 선택자는 사용을 피하세요!**

> 선택자의 중첩을 피하는 방법은 <a href="#naming">3. Naming</a> 섹션을 참고하세요.

> ###### 참고자료
> - <a target="_blank" href="http://markdotto.com/2012/03/02/stop-the-cascade/">Stop the cascade &middot; @mdo</a>
> - <del><a target="_blank" href="https://developer.mozilla.org/ko/docs/Web/CSS/Writing_Efficient_CSS">효율적인 CSS 작성하기 - CSS | MDN</a></del> (<a target="_blank" href="http://webclub.tistory.com/361"> 번역본</a>)

<h3 id="css-z-index">2-4. z-index</h3>

`z-index` 스택을 `0`부터 규칙 없이 쌓는다면 순서가 꼬일 수 밖에 없습니다. 엘리먼트의 특성에 맞게 계층을 분리하여 체계적으로 관리하는 것이 더 좋은 방법입니다.

> **CSS 전처리기의 믹스인을 활용한다면 간편하게 작성할 수 있습니다.**

```scss
/* scss */
.foo {
  position: absolute;
  @include layer-index('floating', 3000);
}

/* css */
.foo {
  z-index: 16203000
}
```

#### A. Normal

평범한 엘리먼트입니다.

- Value: `-1` ~ `99999`

#### B. `inline-popover`

마우스 오버 또는, 클릭 등의 이벤트 트리거링으로 특정 상황에서 상위에 노출되어야 하는 엘리먼트입니다. 상태 클래스를 이용하여 스택을 유동적으로 관리하세요.

> 부모 엘리먼트의 위치에 영향을 받지 않는 엘리먼트는 `inline-popover` 대신 `popover`을 사용합니다.

- Value: `16100000` ~ `16199999`

```css
.dropdown {
  position: relative;
}
.dropdown.is-expand {
  position: absolute;
  @include layer-index('inline-popover');
}
```

#### C. `floating`

플로팅 레이어는 항상 상위에 떠있어야 합니다.

- Value: `16200000` ~ `16299999`

#### D. `dialog`

다이얼로그는 본문보다 위에 노출되어야 합니다.

- Value: `16300000` ~ `16399999`

#### E. `popover`

이벤트 트리거링으로 상위에 노출되어야 하는 엘리먼트입니다. `inline-popover`와 같은 상황일 때 엘리먼트가 `position: fixed;`거나 `<body>`의 자식으로 존재한다면 사용하세요.

- Value: `16400000` ~ `16499999`

```css
.dropdown {}
.dropdown-menu {
  position: fixed;
  @include layer-index('popover');
}
```

#### F. `toast`

토스트는 사용자가 확인할 수 있도록 페이지의 최상위에 노출되어야 합니다.

- Value: `16500000` ~ `16599999`

#### G. `super`

무조건 최상위에 노출됩니다. 정말 필요할 때만 사용하세요.

- Value: `16600000` ~ `16699999`

#### H. `skip`

스킵 네비게이션은 어디서든 접근 가능해야 하므로 다른 레이어에 절대 가려지지 않아야 합니다.

- Value: `16777271`

<h3 id="css-import">2-5. Import</h3>

**CSS의 기본 문법인 `@import`는 성능 문제를 가지고 있습니다. 절대 사용하지 마세요!** 대신 아래의 방법으로 개발하세요.

- 여러개의 `<link>` 엘리먼트로 작성하기
- 하나의 CSS 파일로 작성하기
  - CSS 전처리기의 `@import` 문법을 사용하기
  - 번들러 등의 도구를 이용하여 하나의 CSS 파일로 병합하기

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

<!-- Very Nice -->
<link rel="stylesheet" href="bundle.css"> <!-- one.css, .. in bundle.css -->
```

<h3 id="css-media-query">2-6. Media Query</h3>

미디어 쿼리는 컴포넌트 단위로 분류하여 관련 규칙 바로 뒤에 작성하세요. 이렇게 하면 파편화된 스타일이 한곳으로 모여져 가독성이 좋아집니다. 불가능하다면 문서의 마지막에 모아서 작성하세요. 

```css
.foo-a {}
.foo-b {}
@media (min-width: 768px) {
  .foo-a {}
  .foo-b {}
}

.bar {}
```

```css
.foo-a {}
.foo-b {}

.bar {}

@media (min-width: 768px) {
  .foo-a {}
  .foo-b {}
}
```

<h3 id="css-nesting">2-7. Nesting</h3>

너무 많은 선택자의 중첩은 피해야 하므로, **CSS 전처리기가 지원하는 Nesting 문법은 주의해서 사용해야 합니다!** 무분별하게 사용하면 컴파일된 CSS가 엉망이 될 수도 있습니다.

> - 선택자의 중첩을 피해야하는 이유는 <a href="#css-selectors">2-3. Selectors</a> 섹션의 참고자료를 참고하세요.
> - 선택자의 중첩을 피하는 방법은 <a href="#naming">3. Naming</a> 섹션을 참고하세요.

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

<h3 id="css-extend">2-8. Extend</h3>

**CSS 전처리기가 지원하는 Extend 문법은 절대 사용하지 마세요! Mixin으로 대체하세요!** 

> ###### 참고자료
> - <a target="_blank" href="https://sass-guidelin.es/ko/#extend">Sass 가이드라인</a>
> - <a target="_blank" href="https://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/">When to use @extend; when to use a mixin - CSS Wizardry</a>

<h3 id="css-reset">2-9. Reset</h3>

초기화 스타일은 서비스에 맞게 정의하세요. 만약 <a target="_blank" href="http://necolas.github.io/normalize.css/">normalize.css</a> 또는 <a target="_blank" href="http://getbootstrap.com/">Bootstrap</a> 등의 프레임워크를 사용한다면 초기화를 생략하세요.

<h3 id="css-vendor-prefix">2-10. Vendor Prefix</h3>

벤더 프리픽스 프로퍼티는 일반 프로퍼티보다 먼저 선언하세요.

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


[↑ Table of Conetnts](#table-of-contents)



<h2 id="naming">3. Naming</h2>

네이밍 규칙을 설명합니다.

<h3 id="naming-selectors">3-1. Selectors</h3>

> 이 규칙은 *<a target="_blank" href="http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/">BEMIT</a> 방법론*(*<a target="_blank" href="https://en.bem.info/methodology/naming-convention/">BEM</a>* + *<a target="_blank" href="http://csswizardry.net/talks/2014/11/itcss-dafed.pdf">ITCSS</a>*)을 기반으로 작성되었습니다.

> ###### 참고자료
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

- **스타일 제어를 위해 아이디 선택자의 사용을 피하세요!**
- **클래스명은 반드시 엘리먼트의 의미를 전부 담아서 네이밍하세요!**
- **클래스명은 페이지에 상속받지 않으며, 디자인보다는 구조, 기능, 목적을 나타내는 이름으로 네이밍하세요!**

#### A. Naming

Syntax: `<BLOCK>[__<ELEMENT>][--<MODIFIER>][.is|has-<STATE>]`

- 기본 네이밍 규칙은 BEM을 따릅니다.  
  ```BLOCK__ELEMENT--MODIFIER```  
- 상태 클래스는 `modifier`에서 분리하여 따로 관리합니다.  
  ```BLOCK__ELEMENT--MODIFIER.is-STATE```

```html
<div class="widget">
  <div class="widget__wrapper widget__wrapper--dark">
    <input class="input" type="text" aria-label="Text Field">
    <button class="btn" type="reset">Reset</button>
    <button class="btn btn--submit is-disabled" type="submit" disabled>Submit</button>
  </div>
</div>
```

```css
.widget {} /* BLOCK */
.widget__wrapper {} /* BLOCK__ELEMENT */
.widget__wrapper--dark {} /* BLOCK__ELEMENT--MODIFIER */
.input {} /* BLOCK */
.btn {} /* BLOCK */
.btn.is-disabled {} /* .BLOCK.is-STATE */
.btn--submit {} /* .BLOCK--MODIFIER */
.btn--submit.is-disabled {} /* .BLOCK--MODIFIER.is-STATE */
```

#### B. Layer

스타일 시트의 계층(Layer)은 9단계로 나뉩니다.

- Settings
- Tools
- Generic
- Base
- Objects
- Components
- Pages
- Themes
- Utilities(Trumps)

###### Example with SASS(scss)

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

@import "pages/_about";
@import "pages/_archive";
@import "pages/_contact";
@import "pages/_error";
@import "pages/_faq";

@import "utilities/_blind";
```

##### a. Settings

전역 변수를 작성하세요.

```scss
$breakpoints: (
  //'xsmall': 'screen',
  'small': 'screen and (min-width: 640px)',
  'medium': 'screen and (min-width: 1024px)',
  'large': 'screen and (min-width: 1280px)',
  'xlarge': 'screen and (min-width: 1440px)',
  'retina': 'screen and (-webkit-min-device-pixel-ratio:1.5)'
);
```

##### b. Tools

CSS 전처리기를 사용한다면 Function과 Mixin을 작성하세요.

```scss
@mixin background-rgba($color, $alpha) {
  $rgba: rgba($color, $alpha);
  $ie-hex-str: ie-hex-str($rgba);
  background-color: $rgba;
  filter: progid:DXImageTransform.Microsoft.gradient(StartColorStr=#{$ie-hex-str},EndColorStr=#{$ie-hex-str});
  &:not([dummy]) {
    filter: progid:DXImageTransform.Microsoft.gradient(enabled='false');
  }
}
```

##### c. Generic

문서의 초기 스타일을 작성하세요.

```scss
html,
body {}
a,
input,
textarea,
button {}
```

##### d. Base

태그 선택자 또는 타입 선택자를 이용하여 각 태그 엘리먼트의 기본 스타일을 작성하세요.

```scss
button,
input[type='button'],
input[type='submit'],
input[type='reset'],
input[type='image'] {}
```

##### e. Objects

반복적이며 재사용이 가능한 디자인 패턴을 작성하세요. 이는 시각적인 효과보단 레이아웃을 위한 스타일을 중점으로 작성합니다. 클래스 대신 CSS 전처리기의 믹스인으로 작성하는 것도 좋은 방법입니다.

```scss
.row {}
.col-s12 {}
.col-m12 {}
.col-l12 {}
```

##### f. Components

컴포넌트 스타일을 작성하세요.

```scss
.combobox {}
.combobox__item {}
.combobox.is-expanded {}
```

##### g. Pages

페이지 스타일을 작성하세요. 컴포넌트 기반 개발 방식을 따르는 경우에도 페이지 스타일이 무수히 많아진다면 설계가 잘못됐을 가능성이 높습니다. (Pages 계층은 *ITCSS* 규칙이 아닙니다)

> ###### 참고자료
> - <a target="_blank" href="http://slowalk.tistory.com/2440">슬로워크 블로그 :: 스타일 가이드로 웹서비스 개발하기</a>

```scss
.about-page {}
```

##### h. Themes

테마 스타일을 작성하세요.

```html
<html class="dark-theme">
  <body>
    <div class="spinner"></div>
  </body>
</html>
```

```scss
.combobox {
  .dark-theme & {}
}
```

```scss
.combobox {}
.dark-theme {
  .combobox {}
}
```

테마 스타일을 새로운 CSS 파일로 분리하여 작성할 수도 있습니다.

```html
<link rel="stylesheet" href="/css/style.css">
<link rel="stylesheet" href="/css/dark-theme.css">
```

##### i. Utilities (Trumps)

스타일을 오버라이드하거나 전역 스타일로 사용할 수 있는 헬퍼를 작성합니다. 때에 따라 프로퍼티에 `!important`를 추가할 수 있습니다.

```scss
.blind {}
```


[↑ Table of Conetnts](#table-of-contents)



<h2 id="license">License</h2>

이 저작물은 <a rel="license" target="ccl" href="http://creativecommons.org/licenses/by-nc-sa/4.0/" style="vertical-align:top">크리에이티브 커먼즈 저작자표시-비영리-동일조건변경허락 4.0 국제 라이선스</a>에 따라 이용할 수 있습니다.

<img alt="크리에이티브 커먼즈 저작자표시-비영리-동일조건변경허락" title="" style="border-width:0;vertical-align:top" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" />


[↑ Table of Conetnts](#table-of-contents)
