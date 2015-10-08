Markup Coding Guide - 1장. 네이밍 규칙
===

---

[목차로 이동](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)

1. 네이밍 규칙
---

선택자, 이미지, 파일 및 폴더의 네이밍 규칙을 설명한다.

### 1-1. 개요

네이밍 규칙은 HTML, CSS 파일에서 사용되는 선택자, 그리고 이미지 등의 파일이나 폴더의 이름을 작성하는 규칙이다.  
네이밍을 이해하기 쉽게 작성하여야 사이트의 제작 및 유지보수를 맡은 관리자가 코드를 쉽게 파악할 수 있다.

### 1-2. 기본 규칙

네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

- 이름은 영문 소문자, 숫자, 하이픈(```-```), 언더바(```_```)를 사용하여 작성한다.
- 이름은 일반적으로 영문 소문자로 시작하여야 한다.
- 일반적으로 선택자는 CSS의 Cascade 방식에 알맞은 네이밍을 한다.
```html
<div class="sect-exam">
	<input class="ipt">
</div>
```

#### B. 예약어 사용

- 네이밍하려는 엘리먼트의 의미에 대한 예약어가 있는 경우 예약어를 사용한다.
- 예약어가 없을 경우 엘리먼트의 종류와 의미를 나타낼 수 있도록 네이밍한다.
- 예약어 목록은 부록을 참고한다.

#### C. 네이밍 조합

- 하이픈은 엘리먼트 역할에 따라 네이밍 단어를 역할별로 조합할 때 사용되며, 단순히 띄어쓰기가 필요한 경우 언더바를 사용한다.
```shell
service-naming-exam-wrap (X)
service_naming_exam-wrap (O)
```
- 네이밍의 조합은 '사용자 정의 프리픽스-가이드 정의 프리픽스-컨텐츠명-형태-의미-영역-확장--상태' 최대 8단계로 나뉘며, 필요에 따라 조합할 수 있다.
```shell
comm-ui-name-sect-exam-box-v2--over
```
- 단어와 숫자를 조합하는 경우 하이픈을 사용하지 않으며, 숫자는 특별한 경우가 아니라면 임의로 자릿수를 늘리지 않는다.
```shell
list-3 (X)
list03 (X)
list3 (O)
```
- 상태 네이밍은 하이픈을 두번 사용하여 조합한다.
```html
<input class="ipt-exam ipt-exam--on">
```
- 확장 네이밍은 일반적으로 'v'와 숫자 또는 식별 가능한 이름을 붙여 네이밍하며, 이름을 부여하는 경우 'v'와 단어 사이에 하이픈이 아닌 언더바를 사용한다.
```html
<input class="ipt-exam ipt-exam-v2">
<input class="ipt-exam ipt-exam-v_wide">
```
- 정의된 클래스가 없는 엘리먼트를 확장 또는 상태 제어해야 할 경우 조합없이 네이밍하여 사용한다.
```html
<div class="v_blur"></div>
<div class="fd"></div>
```

#### D. 네이밍 프리픽스

- 일반적으로 모듈화되는 엘리먼트에 사용한다.
- 프리픽스는 모듈의 의미를 나타낸다.
- 프리픽스는 기본적으로 id, class, name 등 엘리먼트를 식별하기 위한 애트리뷰트에 사용 가능하다.
- 프리픽스 목록은 [부록 &gt; 3. 네이밍 예약어 &gt; C. 프리픽스](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Appendix#c-프리픽스)를 참고한다.

### 1-3. 선택자 네이밍

선택자 네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

- 한 페이지에서 동일한 id를 여러번 사용하지 않는다.
- class는 여러번 사용할 수 있다.
- 엘리먼트의 id가 레이아웃을 위해 작성된 것이 아닐 경우 class를 추가하여 스타일을 제공한다.
- 하나의 컨텐츠를 이루는 엘리먼트 모음의 최상위 엘리먼트는 독립성과 재사용성의 증진을 위해 컨텐츠를 확실히 식별할 수 있는 이름으로 네이밍하며, 이는 일반적으로 네이밍 조합 단계 중 컨텐츠명에 해당한다.
```html
<div class="service_naming_exam">
	<ul class="list-box">
		...
	</ul>
</div>
```

#### F. 프리픽스 네이밍

사용자 정의 프리픽스는 네이밍 기본 규칙을 준수하는 선에서 마음대로 사용 가능하며, 가이드 정의 프리픽스의 앞에 사용한다.  
여기서는 가이드 정의 프리픽스만을 설명한다.

##### a. 레이아웃

아래의 표에 해당하는 엘리먼트는 선택자에 프리픽스를 추가한다.

**[D] Include**: /table/003-chapter1-3-F-a.html

```shell
#pop-wrap
#ly-header
#ifr-content
```

##### b. 테이블 셀

```<th>```, ```<td>``` 엘리먼트에 제공되는 ```id```, ```headers``` 애트리뷰트 값 은 프리픽스 ```t```를 추가한다.

```shell
#t-price
```

##### c. 폼

폼과 관련된 ```<input>```, ```<select>``` 등의 엘리먼트에 제공되는 ```id```, ```name``` 애트리뷰트 값 은 프리픽스 ```f```를 추가한다.

```shell
#f-email
```

##### d. WAI-ARIA의 상태 및 속성

WAI-ARIA의 상태 및 속성만을 위해 제공되는 ```id``` 애트리뷰트 값은 프리픽스 ```aria```를 추가한다. (별도로 정의된 값이 있을 때는 예외)

```html
<div id="nav" role="navigation" aria-labelledby="aria-nav-tit">
	<h2 id="aria-nav-tit">네비게이션</h2>
	...
</div>
```

##### e. 앵커 포인트

앵커 포인트는 페이지 내에서 화면의 이동을 위한 지표 역할을 한다.  
앵커 포인트만을 위해 제공되는 선택자는 프리픽스 ```apnt```를 추가한다. (별도로 정의된 값이 있을 때는 예외)

```html
<a href="127.0.0.1/exam.html#apnt-exam">예제 바로가기</a>
...
<h4>
	<span id="apnt-exam"></span>
	예제입니다
</h4>
<p>
	...
</p>
```

##### f. 컴포넌트

컴포넌트란 하나의 독립적인 모듈로 사용되는 유저 인터페이스를 뜻한다.  
컴포넌트에 제공되는 선택자는 프리픽스 ```ui```를 추가하며, [1-5. 모듈화](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter1#1-5-모듈화)의 규칙을 따른다.

```html
<div class="ui-exam">....</div>
```

### 1-4. 파일 및 폴더 네이밍

파일 및 폴더 네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. HTML

- HTML 파일은 페이지명을 토대로 네이밍한다.
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

#### D. 폴더

- 프로젝트 폴더는 '생성일-프로젝트명'으로 네이밍하며, 생성일은 YYMMDD 형식을 사용한다.
```shell
140825-overtimeman
```
- 이미지, CSS, JavaScript 폴더는 'img', 'css', 'js'로 네이밍한다.
- HTML파일을 메뉴별로 분기해야할 경우 서비스명을 토대로 네이밍한다.

### 1-5. 모듈화

모듈화가 필요한 경우 아래의 네이밍 방법을 준수하도록 한다.

#### A. 선택자 네이밍

- 고유한 네임스페이스가 필요하므로 프리픽스를 추가한다.
```html
<div class="ui-tabmenu"></div>
```
- 일반적으로 부모 엘리먼트 선택자의 네이밍을 종속받는다.  
종속 시 부모 엘리먼트 네이밍이 의미를 가지지 않거나 네이밍이 과도하게 길어질 경우 생략 가능하나, 최상위 엘리먼트의 선택자 네이밍은 항상 종속받도록 한다.
```html
<div class="ui-btnshare">
	<div class="ui-btnshare-wrap">
		<button class="ui-btnshare-btn"></button>
	</div>
</div>
```
- 모듈화된 엘리먼트를 각 영역에서 사용함에 따라 부가적인 스타일 변경이 필요할 경우 직접 선택하여 변경하지 않는다.
```html
<div class="thmb ui-imgratio"></div>
```
```css
.ui-imgratio{width:200px} /* X */
.thmb{width:200px} /* O */
.thmb.ui-imgratio{width:200px} /* O */
```
- 이 외의 규칙은 일반적인 선택자 네이밍 규칙과 동일하다.

[이전](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Preface) [다음](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter2) [목차](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)  