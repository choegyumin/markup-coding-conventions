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
    - <a href="#css-prefix">2-8. Prefix</a>
    - <a href="#css-comments">2-9. Comments</a>
- <a href="#naming">3. Naming</a>
    - <a href="#naming-general-rules">3-1. General Rules</a>
    - <a href="#naming-selectors">3-2. Selectors</a>
    - <a href="#naming-files">3-3. Files</a>
    - <a href="#naming-prefix">3-4. Prefix</a>

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
    <dd>하나의 독립된 컨텐츠로써 온전한 기능을 가진 큰 단위의 엘리먼트 모음을 의미한다. 사이트의 메뉴, 쇼핑몰의 상품 목록, 언론 사이트의 댓글 폼 등을 예로 들 수 있다.</dd>
    <dt>모듈(Module)</dt>
    <dd>컴포넌트 내에 삽입할 수 있는 미리 정의된 아주 작은 단위의 UI를 의미한다. 예를 들어 텍스트 박스, 셀렉트 박스, 버튼 등이 있다.</dd>
</dl>



<h2 id="html">1. HTML</h2>

HTML 코드의 작성 규칙을 설명한다.

<h3 id="html-syntax">1-1. Syntax</h3>

- 들여쓰기는 4개의 공백 문자를 가지는 하드탭(<kbd>tab</kbd>)을 사용한다.
- 엘리먼트 명과 애트리뷰트 명은 영문 소문자를 사용한다.
- 모든 애트리뷰트값은 큰 따옴표(```"```)를 사용하여 묶는다.
- 단일 태그 엘리먼트는 슬래시(```/```)를 사용하지 않는다.
- 닫는 태그가 선택적인 경우에도 생략하지 않는다. (ex: ```</li>```, ```</body>```)

<h3 id="html-doctype">1-2. Doctype</h3>

Doctype은 일반적으로 HTML5 DTD로 선언한다.
 
```html
<!DOCTYPE html>
```

<h3 id="html-encoding">1-3. Encoding</h3>

문서의 ```Charset```은 일반적으로 ```UTF-8```으로 선언하며 ```<head>``` 엘리먼트 내에서 최초의 엘리먼트로 작성한다.

```html
<meta charset="utf-8">
```

<h3 id="html-metadata">1-4. Metadata</h3>

- 호환성을 위해 IE의 문서모드를 엣지모드를 선언하여 최신 버전의 IE로 렌더링되도록 하며 ```Charset``` 다음으로 선언한다.
    ```html
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    ```
- ```<title>```은 현재 문서의 내용에 알맞은 제목을 가지며 IE 호환성 코드 다음으로 선언한다.
- 아래의 ```<meta>``` 엘리먼트를 추가하여 브라우저가 전화번호 또는 이메일, 주소 포맷을 가진 문자를 감지하지 못하도록 한다.
    ```html
    <meta name="format-detection" content="telephone=no,address=no,email=no">
    ```
- 필요에 따라 ```keywords```, ```description``` 등의 다른 ```<meta>```를 추가하도록 한다.

<h3 id="html-elements">1-5. Elements</h3>

- 렌더링 엔진 최적화를 위해 스타일 또는 스크립트 제어가 필요한 **모든 엘리먼트에는 ID 또는 클래스를 부여**하도록 한다.

#### A. 스타일 제어가 어려운 엘리먼트

자식 엘리먼트로 사용할 수 있는 태그가 한정적인 엘리먼트(```<table>```, ```<ul>```, ..) 또는 자기 자신의 스타일 제어에 한계를 가진 엘리먼트(```<img>```, ```<select>```, ..)는 의미없는 엘리먼트로 감싸는 것을 권장한다. (이 외의 불필요한 엘리먼트 상속은 피하도록 함)

```html
<!-- Not Bad -->
<table class="table"></table>

<!-- Good -->
<div class="table">
    <table></table>
</div>
```

#### B. 테이블 제목

```<caption>``` 엘리먼트를 숨김 처리할 때는 의미없는 엘리먼트로 감싸서 숨기도록 한다.

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

```<table>``` 엘리먼트를 제작 시 ```<thead>```, ```<tfoot>```의 유무와 관계없이 ```<tbody>```를 사용하도록 한다.

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

회원가입 등의 문서 작성 폼에 사용되는 ```<input>```, ```<select>```, ```<textarea>``` 엘리먼트는 서로 너비 값이 상이하다면 인라인 스타일로 제어한다.

```html
<!-- Bad -->
<input type="text" class="input type-width_120">
<input type="text" class="input type-width_180">

<!-- Good -->
<input type="text" class="input" style="width:120px">
<input type="text" class="input" style="width:180px">
```

#### E. 버튼

```<button>``` 엘리먼트는 ```type``` 애트리뷰트가 선언되지 않으면 ```<form>``` 엘리먼트에서 의도치 않은 액션을 발생시키므로 기본값으로 ```type="button"```을 선언한다.

```html
<!-- Bad -->
<button></button>

<!-- Good -->
<button type="button"></button>
```

<h3 id="html-attributes">1-6. Attributes</h3>

- 엘리먼트 애트리뷰트의 선언 순서는 상황에 맞게 가변 애트리뷰트를 가장 나중에 작성한다.
    ```html
    <input type="password" class="input" name="f-pw" id="f-pw" title="비밀번호" style="width:100px" disabled>
    ```
- HTML5에서 Boolean 애트리뷰트는 값을 지정하지 않은 채 선언되어도 ```true```를 의미하므로 필요치 않다면 값을 지정하지 않는다.

<h3 id="html-import">1-7. Include</h3>

- HTML5는 CSS와 JS 파일을 불러올 때 ```type``` 애트리뷰트는 이미 기본값이 지정되어 있으므로 선언하지 않는다.
- 일반적으로 JS 보다 CSS를 먼저 선언한다.
- 일반적으로 JS 파일은 종류에 따라 ```<head>``` 또는 ```<body>``` 엘리먼트의 마지막에 작성한다.

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

작업 진행에 참고해야 하는 주석은 맨 앞에 ```@desc```를 추가하여 작성한다.

```html
<!-- @desc
    blah, blah, blah...
-->
```

#### B. 엘리먼트 주석

레이아웃 또는 그루핑된 엘리먼트의 시작과 끝을 알리는 주석은 아래의 형식에 맞게 작성하며, 맨 앞에 ```@start``` 또는 ```@end```를 표기한다.

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
- 일반적으로 작은 따옴표(```'```)를 사용하며 @charset 선언과 선택자 안에서만 큰 따옴표(```"```)를 사용한다. 만약 따옴표를 생략할 수 있는 경우에는 반드시 생략한다.
    ```css
    @charset "UTF-8";
    input[type="text"] {
        background: url(bg.gif);
        font-family: Dotum,'돋움';
        content: 'lol';
    }
    ```

<h3 id="css-charset">2-2. Charset</h3>

문서의 ```Charset```은 일반적으로 ```UTF-8```으로 선언하며 최상위에 선언한다.

```css
@charset "UTF-8";
```

<h3 id="css-selectors">2-3. Selectors</h3>

- **선택자는 최대 3개까지만 종속한다. (아예 종속하지 않는 것을 권장)**
- **렌더링 성능 최적화를 위해 ID &middot; 클래스, 가상 선택자 외의 선택자는 사용을 지양한다.**  
- 여러개의 선택자를 사용하는 경우 선택자 사이에 개행을 추가한다.
    ```css
    /* Bad */
    .one, .two, .three { }
    
    /* Good */
    .one,
    .two,
    .three { }
    ```

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

- 16진수 값들은 가능하다면 축약형으로 표현한다. (ex: ```#ffffff``` 대신 ```#fff```)
- 속성값이 0인 값은 단위를 생략한다. (ex: ```0px``` 대신 ```0```)
- ```0.*```의 소수값은 소수점 앞의 0을 생략한다. (ex: ```0.5``` 대신 ```.5```)
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
    - z-index
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

**CSS에서 기본으로 제공하는 ```@import```는 성능 문제로 절대 사용하지 않는다.** 대신 아래의 방법 중 하나를 사용하도록 한다.

- 하나의 CSS 파일만 작성
    - 개발도구를 사용하여 CSS 파일을 하나로 합침
    - CSS 전처리기에서 제공하는 import 기능을 사용
- 여러개의 ```<link>``` 엘리먼트를 사용

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
.element { }
.element-foo { }
.element-bar { }
@media (min-width: 768px) {
  .element { }
  .element-foo { }
  .element-bar { }
}
```

<h3 id="css-prefix">2-8. Prefix</h3>

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

<h3 id="css-comments">2-9. Comments</h3>

주석을 한줄로 작성할 경우 주석기호와 주석내용 사이에 한칸의 공백을 추가하며, 두줄 이상의 경우 아래의 문법을 따른다.

```css
/* This comment is 1 line */
/*
    This comment is
    2 lines
*/
```

#### A. 프로젝트 주석

프로젝트 정보를 나타내는 주석은 아래의 양식에 맞게 ```@charset``` 바로 아래에 작성한다. (```/*! */```)

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

작업 진행에 참고해야 하는 주석은 아래의 양식에 맞게 작성한다. (```/*# */```)
```css
/*#
    @title CSS z-index Guidelines 

    blah, blah, blah...
*/
```

<dl>
    <dt><code>@title</code></dt>
    <dd>주석 내용의 제목.</dd>
</dl>

#### C. 엘리먼트 주석

엘리먼트 그룹의 정보를 나타내는 주석은 아래의 형식에 맞게 작성한다. (```/*= */```)
  
```css
/*=
    @type Base
    @name Reset
*/
article, aside, details, figcaption, figure, footer, header, menu, nav, section { }

/*=
    @type Module
    @name Combobox
    @namespace foo
    @since v1.1.0 2016-04-08
*/
#foo-cbo { }

/*=
    @type Media
    @name Screen Reader
    @author Your Name <email_id@domain.com>
*/
@media aural, speech { }
```

<dl>
    <dt><code>@type</code></dt>
    <dd>엘리먼트 그룹의 타입. <code>Base</code>, <code>Layout</code>, <code>Component</code>, <code>Module</code>, <code>Media</code>로 나뉜다</dd>
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

>**이 문서는 <a href="http://ceecss.github.io/" target="_blank">CEE CSS 방법론</a>의 네이밍 규칙을 따른다.**  
> <a href="http://getbem.com/" target="_blank">BEM 방법론</a>을 사용하여도 상관없으나 이 문서는 CEE CSS를 기준으로 설명한다.

<h3 id="naming-general-rules">3-1. General Rules</h3>

- 이름은 영문 소문자, 숫자, 하이픈(```-```), 언더바(```_```)를 사용하여 작성한다.
- 이름은 일반적으로 영문 소문자로 시작하여야 한다.
- 클래스명은 가능하다면 짧고 간결한 것이 좋으나 반드시 엘리먼트의 의미를 전부 담을 수 있도록 한다.
- 컨텐츠가 메뉴 및 페이지 등에 상속받지 않도록 하며, 디자인 적인 측면보다는 구조, 기능, 목적을 나타내는 이름으로 네이밍한다.
- 네이밍을 역할별로 구분했을 때 '프리픽스', '구조', '엘리먼트', '효과'로 나뉘며, 필요에 따라 사용하며, 그 중 구조는 '레이아웃', '컴포넌트', 모듈'을 말한다.
- 일반적으로 구조는 서로 겹치거나 조합해서는 안되며, 레이아웃 내에 컴포넌트와 모듈, 컴포넌트 내에 모듈을 삽입하는 것만 허용된다.

<h3 id="naming-selectors">3-2. Selectors</h3>

선택자 네이밍은 <a href="http://ceecss.github.io/" target="_blank">CEE CSS 방법론</a>을 참고한다.

<h3 id="naming-files">3-3. Files</h3>

#### A. HTML

HTML 파일은 페이지명을 토대로 네이밍한다.

#### B. CSS

CSS 파일은 컨텐츠를 토대로 네이밍하며, 하나의 CSS만 사용할 경우 ```style.css```로 네이밍한다.

#### C. 이미지

- 이미지 확장자와 관계없이 중복되지 않도록 네이밍한다.
    ```shell
    bg-exam.jpg
    bg-exam2.gif
    bg-exam3.png
    ```
- 임시 이미지의 경우 앞에 언더바(```_```)를 추가한다.
    ```shell
    _img-exam.png
    _bg-exam.png
    ```
- 가상 엘리먼트를 위한 이미지는 두개의 하이픈(```--```)으로 조합하며, 엘리먼트의 효과에 따른 이미지는 <a href="http://ceecss.github.io/#naming_rules-effect" target="_blank">CEE CSS 방법론의 Effect</a> 선택자처럼 점(```.```)으로 조합한다.
    ```shell
    bg-menu
    bg-menu--hover.jpg
    bg-menu.type-compact--hover.jpg
    bg-menu.type-compact.is-scrolled.jpg
    ```

<h3 id="naming-prefix">3-4. Prefix</h3>

프리픽스는 사용자 정의 프리픽스와 내장 프리픽스로 구분된다.  
사용자 정의 프리픽스는 네이밍 기본 규칙을 준수하는 선에서 마음대로 사용 가능하며, 여기서는 내장 프리픽스만을 설명한다.

#### A. 폼

```<input>```, ```<select>``` 등의 사용자 입력을 받는 폼과 관련된 엘리먼트에 제공되는 ```id```, ```name``` 애트리뷰트 값은 프리픽스 ```field```를 추가한다.

```html
<label for="field-car">Select car</label>
<select id="field-car" name="field-car">
    <option value="volvo">Volvo</option>
    <option value="mercedes">Mercedes</option>
    <option value="audi">Audi</option>
</select>
```

#### B. 테이블 셀

```<th>```, ```<td>``` 엘리먼트에 제공되는 ```id```, ```headers``` 애트리뷰트 값은 프리픽스 ```cell```를 추가한다.

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

#### C. WAI-ARIA의 상태 및 속성

**오로지 WAI-ARIA의 상태 및 속성만을 위해 제공**되는 ```id``` 애트리뷰트 값은 프리픽스 ```aria```를 추가한다. 이는 **앵커의 참조 엘리먼트로 절대 사용할 수 없다.**

```html
<div id="lnb" role="navigation" aria-labelledby="aria-lnb_heading">
    <h2 id="aria-lnb_heading">Local Navigation Bar</h2>
</div>
```

#### D. 팝업과 다이얼로그

팝업과 관련된 엘리먼트 중 레이아웃 엘리먼트에 제공되는 선택자는 프리픽스 ```popup```를 추가한다.  
이는 **팝업의 확장성을 위해 레이어 팝업에도 해당**되며, 새 창 팝업과의 구분이 필요할 경우 상태 효과 클래스(```.is-window```, ```is-layer```)를 사용한다.

```css
.popup-event {}
.popup-event.is-window {} /* 새 창 팝업 */
.popup-event.is-layer {} /* 레이어 팝업 */
.popup-event_header {}
```  
  
**레이어 팝업은 단순히 팝업을 레이어의 형태로 띄운 것이므로 다이얼로그와는 엄연히 다른 의미**이며, 다이얼로그의 레이아웃 엘리먼트는 프리픽스 ```dialog```를 추가한다.

```css
.dialog-notice {}
.dialog-notice_header {}
```

#### E. 프레임

```<iframe>```과 관련된 엘리먼트 중 레이아웃 엘리먼트에 제공되는 선택자는 프리픽스 ```frame```을 추가한다.

```css
#frame-aside {}
```

#### F. 모듈

<a href="http://ceecss.github.io/#naming_rules-module" target="_blank">모듈은 CEE CSS 방법론의 규칙</a>이며 모듈은 재사용이 가능한 아주 작은 단위의 UI를 뜻한다.  
모듈에 제공되는 선택자는 미리 정의된 이름을 프리픽스(사용자 정의 프리픽스)로 사용하며, 없다면 프리픽스 ```mod```를 추가한다.

```html
<div class="mod-cbo">
    <button class="mod-cbo-toggle_btn">Select another option</button>
</div>
```



<h2 id="changelogs">Changelogs</h2>

<a target="_blank" href="https://github.com/choi4450/markup-coding-conventions">https:&#47;&#47;github.com&#47;choi4450&#47;markup-coding-conventions</a>

> - 2016.04.08 개편(v2.0)
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

이 저작물은 <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank" style="vertical-align:top">크리에이티브 커먼즈 저작자표시-비영리-동일조건변경허락 4.0 국제 라이선스</a>에 따라 이용할 수 있습니다.

<img alt="" title="" style="border-width:0;vertical-align:top" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" />
