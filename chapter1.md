# Markup Coding Conventions - 1장. 네이밍 규칙

<a href="./#article">목차로 이동</a>

## 1. 네이밍 규칙

선택자, 이미지, 파일 및 폴더의 네이밍 규칙을 설명한다.

### 1-1. 개요

네이밍 규칙은 HTML, CSS 파일에서 사용되는 선택자, 그리고 이미지 등의 파일이나 폴더의 이름을 작성하는 규칙이다.  
네이밍을 이해하기 쉽게 작성하여야 사이트의 제작 및 유지보수를 맡은 관리자가 코드를 쉽게 파악할 수 있다.

### 1-2. 기본 규칙

네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

- 이름은 영문 소문자, 숫자, 하이픈(```-```), 언더바(```_```)를 사용하여 작성한다.
- 이름은 일반적으로 영문 소문자로 시작하여야 한다.
- 컨텐츠가 메뉴 및 페이지 등에 상속받지 않도록 최대한 컴포넌트 또는, 모듈과 같이 기능을 기준으로 구분하여 네이밍한다.
- 각 컴포넌트를 서로 겹치거나 조합해서는 안되며, 컴포넌트 내에 모듈을 삽입하는 것만 가능하다. (레이아웃 내에는 무엇이든 추가 가능)
- 렌더링 엔진 최적화를 위해 스타일 또는, 스크립트 제어가 필요한 **모든 엘리먼트에는 클래스명을 부여**하도록 한다.

#### B. 예약어 사용

- 네이밍하려는 엘리먼트의 의미에 대한 예약어가 있는 경우 예약어를 사용한다.
- 예약어가 없을 경우 엘리먼트의 종류와 의미를 나타낼 수 있도록 네이밍한다.
- 예약어 목록은 부록을 참고한다.

#### C. 네이밍 조합

- 하이픈은 네이밍 단어를 역할별로 조합할 때 사용되며, 단순히 띄어쓰기가 필요한 경우 언더바를 사용한다.
    ```shell
    service-naming-exam-wrap (X)
    service_naming_exam-wrap (O)
    ```
- 네이밍의 조합은 역할별로 분류했을 때 '프리픽스-컴포넌트(모듈)-엘리먼트-효과' 최대 4단계로 나뉘며, 필요에 따라 조합할 수 있다.  
선택자 네이밍의 경우 효과 네이밍은 조합하지 않고 분리되며, 별도의 프리픽스를 가진다.
- 단어와 숫자를 조합하는 경우 하이픈을 사용하지 않으며, 숫자는 특별한 경우가 아니라면 임의로 자릿수를 늘리지 않는다.
    ```shell
    list-3 (X)
    list03 (X)
    list3 (O)
    ```
- 일반적으로 **모든 네이밍에는 컴포넌트명을 상속**받는다.

#### D. 네이밍 프리픽스

- 주로 API 또는, 하나의 모듈이 되는 엘리먼트에 사용되며, 모듈의 의미를 나타낸다.
- 프리픽스는 기본적으로 id, class, name 등 엘리먼트를 식별하기 위한 애트리뷰트에 사용 가능하다.
- 프리픽스 목록은 <a href="./appendix.html#c-프리픽스">부록 &gt; 3. 네이밍 예약어 &gt; C. 프리픽스</a>를 참고한다.

### 1-3. 선택자 네이밍

선택자 네이밍 시 다음과 같은 규칙을 준수하도록 하며, **<a href="http://ceecss.github.io/" target="_blank">CEE CSS</a> 방법론을 참고한다.**

#### A. 일반 규칙

- 한 페이지에서 동일한 id를 여러번 사용하지 않는다.
- class는 여러번 사용할 수 있다.
- 엘리먼트의 id가 레이아웃을 위해 작성된 것이 아닐 경우 class를 추가하여 스타일을 제공한다.
- 컴포넌트명은 독립성과 재사용성의 증진을 위해 확실히 식별할 수 있는 이름으로 네이밍한다.
    ```html
    <div class="component_name">
        <ul class="component_name-element_name">...</ul>
    </div>
    ```
- 네이밍의 조합 시 효과 네이밍은 조합하지 않고 분리한다.
    ```html
    <input class="input_txt type-wide is-focus">
    ```
    ```shell
    .input_txt.type-wide.is-focus
    ```

#### B. 효과 네이밍

효과 선택자는 엘리먼트에 부가적인 효과를 주거나 추가 제어가 필요할 때 사용된다.  
선택자의 효과 네이밍은 다른 네이밍과 조합하지 않으며, 프리픽스를 붙여 어떤 역할을 하는 것인지 나타낸다.

##### a. 타입

엘리먼트의 테마, 스킨, UI의 변경을 위한 효과 네이밍은 프리픽스 ```type```을 추가한다

```html
<div class="posteditor type-theme_black">...</div>
```

##### b. 데이터

엘리먼트의 데이터 또는, 컨텐츠에 따라 제어가 필요한 경우 프리픽스 ```data```를 추가한다.

```html
<a href="#" class="link_shortcut data-search">검색</a>
<a href="#" class="link_shortcut data-shopping">쇼핑</a>
<a href="#" class="link_shortcut data-blog">블로그</a>
<a href="#" class="link_shortcut data-cafe">카페</a>
```

##### c. 상태

엘리먼트의 현재 상태를 나타내는 경우 프리픽스 ```is```를 추가한다.

```html
<input class="input_txt is-focus">
```

##### d. 스프라이트 이미지

스프라이트 이미지를 클래스로 관리할 경우 프리픽스 ```spr```을 추가하며, 스프라이트명과 이미지명을 조합한다. 스프라이트 클래스는 컴포넌트에 상속받지 않도록 글로벌 클래스로 관리한다.

```html
<small class="ico_new spr-comm-ico_new">(새 소식)</small>
```

```css
[class*="spr-comm-"] { background: ... }
.spr-comm-ico_new { background-position: ... }
.ico_new { ... }
```

##### e. 스크립트

스크립트로 동적 제어가 필요한 엘리먼트의 네이밍은 프리픽스 ```js```를 추가한다.

```html
<input class="input_txt js-chk_valid">
```

#### C. 프리픽스 네이밍

프리픽스는 사용자 정의 프리픽스와 내장 프리픽스로 구분된다.  
사용자 정의 프리픽스는 네이밍 기본 규칙을 준수하는 선에서 마음대로 사용 가능하며, 내장 프리픽스의 앞 또는, 단독으로 사용한다.  
여기서는 내장 프리픽스만을 설명한다.

##### a. 테이블 셀

```<th>```, ```<td>``` 엘리먼트에 제공되는 ```id```, ```headers``` 애트리뷰트 값은 프리픽스 ```t```를 추가한다.

```shell
#t-price
```

##### b. 폼

폼과 관련된 ```<input>```, ```<select>``` 등의 엘리먼트에 제공되는 ```id```, ```name``` 애트리뷰트 값은 프리픽스 ```f```를 추가한다.

```shell
#f-email
```

##### c. 프레임

```iframe``` 엘리먼트 또는, ```iframe```으로 불러올 HTML에 종속된 엘리먼트에 제공되는 선택자는 프리픽스 ```ifr```을 추가한다.

```shell
#ifr-aside
```

##### d. 팝업

팝업과 관련된 엘리먼트에 제공되는 선택자는 프리픽스 ```pop```를 추가한다.  
이는 모달 다이얼로그(레이어 팝업)에도 해당되며, 새 창 팝업과의 구분이 필요할 경우 상태 효과 클래스를 사용한다.

```shell
.pop-join
.pop-join.is-win (새 창 팝업)
.pop-join.is-modal (모달 팝업)
```

##### e. WAI-ARIA의 상태 및 속성

WAI-ARIA의 상태 및 속성만을 위해 제공되는 ```id``` 애트리뷰트 값은 프리픽스 ```aria```를 추가한다. (별도로 정의된 값이 있을 때는 예외)

```html
<div id="nav" role="navigation" aria-labelledby="aria-nav_heading">
	<h2 id="aria-nav_heading">네비게이션</h2>
	...
</div>
```

##### f. 앵커 포인트

앵커 포인트는 페이지 내에서 화면의 이동을 위한 지표 역할을 한다.  
의미가 없는 역할의 앵커에만 사용 가능하며, 이 때 제공되는 선택자는 프리픽스 ```apnt```를 추가한다. (별도로 정의된 값이 있을 때는 예외)

```html
<a href="#apnt-exam">예제 바로가기</a>
...
<h4>
	<span id="apnt-exam"></span>
	예제입니다
</h4>
<p>...</p>
```

##### g. 모듈

모듈이란 재사용이 가능한 아주 작은 단위의 UI를 뜻한다.  
모듈에 제공되는 선택자는 미리 정의된 이름을 프리픽스로 사용하며, 없다면 프리픽스 ```mod```를 추가한다.  
모듈 마크업은 <a href="./chapter1.html#1-5-모듈화">1-5. 모듈화</a>의 규칙을 따른다.

```html
<div class="mod-selectbox">
	<button class="mod-selectbox-toggle_btn">...</button>
</div>
```

#### D. 컴포넌트명 축약

컴포넌트명이 너무 길어질 경우 축약하여 사용할 수 있다. 대신 컴포넌트의 최상위 엘리먼트는 기존 컴포넌트명과 축약된 컴포넌트명을 모두 가지며, 스타일 제어 시 기존 컴포넌트명 클래스를 이용하여 제어한다.

```html
<!-- Before -->
<div class="workspace">
	<div class="workspace-canvas">
		<div class="workspace-canvas_tablist">
			<div class="workspace-canvas_tabitem">...</div>
			<div class="workspace-canvas_tabpanel">...</div>
		</div>
	</div>
</div>

<!-- After -->
<div class="workspace ws">
	<div class="ws-canvas">
		<div class="ws-canvas_tablist">
			<div class="ws-canvas_tabitem">...</div>
			<div class="ws-canvas_tabpanel">...</div>
		</div>
	</div>
</div>
```

```css
.workspace { ... }
.ws-canvas_tabitem { ... }
.ws-canvas_tabpanel { ... }
...
```

### 1-4. 파일 및 폴더 네이밍

파일 및 폴더 네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. HTML

HTML 파일은 페이지명을 토대로 네이밍한다.

```shell
news-list.html
customer.html
```

#### B. CSS

- 가장 기본이 되는 CSS는 일반적으로 'comm'으로 네이밍한다.
    ```shell
    comm.css (기본 CSS)
    ```
- 버티컬의 유뮤나 서비스 간의 컨셉 통일 등 다른 서비스와의 연계성을 가지는 경우 기본이 되는 CSS를 서비스명으로 네이밍하며, 여러 서비스에 전역(공통)으로 사용되는 CSS는 'comm'으로 네이밍한다.
    ```shell
    comm.css (전역 CSS)
    front.css, manage.css, ... (기본 CSS)
    ```
- 기본 CSS를 제외한 나머지 CSS는 상황에 맞게 분류하여 네이밍하며, 연계 서비스의 경우 앞에 서비스명을 추가하여 네이밍한다.
    ```shell
    main.css, sub.css, bbs.css, ...
    front-main.css, front-sub.css, front-bbs.css, ...
    ```
- 미디어쿼리와 별개로 환경에 따라 CSS가 필요한 경우 마지막에 환경명을 추가하여 네이밍한다.
    ```shell
    comm-pc.css
    comm-mobile.css
    ```

#### C. 이미지

- 이미지 확장자와 관계없이 중복되지 않도록 네이밍한다.
    ```shell
    bg-exam.jpg
    bg-exam2.gif
    bg-exam3.png
    ```
- 임시 이미지의 경우 앞에 @를 추가한다.
    ```shell
    @img-exam.png
    @bg-exam.png
    ```
- 가상 엘리먼트에 사용되는 이미지는 하이픈을 두번 사용하여 선택자명을 조합하며, 멀티 클래스 엘리먼트는 CSS와 동일한 방식으로 ```.```을 사용하여 조합한다.
    ```shell
    bg-header--hover.jpg
    bg-header.type-compact--hover.jpg
    bg-header.type-compact.is-scrolled.jpg
    ```

#### D. 폴더

- 프로젝트 폴더는 '생성일-프로젝트명'으로 네이밍하며, 생성일은 YYMMDD 형식을 사용한다.
    ```shell
    140825-overtimeman
    ```
- 이미지, CSS, JavaScript 폴더는 'img', 'css', 'js'로 네이밍한다.
- HTML파일을 메뉴별로 분기해야할 경우 서비스명을 토대로 네이밍한다.

### 1-5. 모듈화

모듈을 제작할 경우 아래의 네이밍 방법을 준수하도록 한다.

#### A. 선택자 네이밍

- 고유한 네임스페이스가 필요하므로 프리픽스를 추가한다.
    ```html
    <div class="mod-tabmenu">...</div>
    ```
- **항상 컴포넌트명을 상속**받아 네이밍한다.
    ```html
    <div class="mod-share_btn">
        <div class="mod-share_btn-wrap">
            <button class="mod-share_btn-btn">...</button>
        </div>
    </div>
    ```
- 모듈 내에서 항상 사용되지 않고 케이스에 따라 필요여부가 결정되는 UI 엘리먼트는 프리픽스에 ```_extn```을 붙여 확장형(extension) UI임을 나타낸다. 이것을 '모듈 익스텐션'이라 부른다.
    ```html
    <div role="tablist" class="mod-dropdown_tab">
        ...
        <div role="tabpanel" class="mod-dropdown_tab-panel">
            <div class="mod_extn-dropdown_tab-list">리스트...</div>
        </div>
        <div role="tabpanel" class="mod-dropdown_tab-panel">
            <div class="mod_extn-dropdown_tab-option">옵션...</div>
        </div>
    </div>
    ```
- 모듈을 각 영역에서 사용함에 따라 부가적인 스타일 변경이 필요할 경우 직접 선택하여 변경하지 않는다.
    ```html
    <div class="goods_list">
        <div class="goods_list-thumb mod-imgratio">...</div>
    </div>
    ```
    ```css
    .goods_list .mod-imgratio{width:200px} /* X */
    .goods_list-thumb.mod-imgratio{width:200px} /* △ */
    .goods_list-thumb{width:200px} /* O */
    ```
- 이 외의 규칙은 일반적인 선택자 네이밍 규칙과 동일하다.

---

<a href="./preface.html#article">이전</a> <a href="./chapter2.html#article">다음</a> <a href="./#article">목차</a> <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/" target="_blank" style="float:right"><img alt="이 저작물은 크리에이티브 커먼즈 저작자표시-비영리-변경금지 4.0 국제 라이선스에 따라 이용할 수 있습니다." title="이 저작물은 크리에이티브 커먼즈 저작자표시-비영리-변경금지 4.0 국제 라이선스에 따라 이용할 수 있습니다." style="border-width:0;vertical-align:top" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a>
