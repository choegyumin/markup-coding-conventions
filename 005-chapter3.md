Markup Coding Guide - 3장. CSS 코드 작성 규칙
===

---

<a href="http://overtimeman.tistory.com/entry/Markup-Coding-Guide#article">목차로 이동</a>

3. CSS 코드 작성 규칙
---

CSS 코드의 작성 규칙을 설명한다.

### 3-1. 개요

HTML은 웹 문서를 다양하게 설계하고 수시로 변경하는데 많은 제약이 있다. 이를 보완하기 위해 만들어진 것이 스타일 시트이며, 스타일 시트의 표준안이 바로 CSS이다.  
여기서는 CSS 코드의 전반적인 작성 규칙을 설명한다.

### 3-2. 기본 규칙

CSS 코드 작성 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

- CSS는 Hack과 같이 부득이하게 문법을 지킬수 없는 경우를 제외하고는 W3C Validation을 통과해야 한다.
- 모든 속성은 영문 대문자를 사용하지 않는다.
```css
.class{Font-Family:NanumGothic} /* X */
.class{font-family:NanumGothic} /* O */
```
- 기본적으로 속성 값은 작은 따옴표(')로 묶으며, 따옴표가 필요없는 속성은 사용하지 않는다.
```css
background:url(bg.gif);
font-family:Dotum,'돋움';
content:'example';
@charset "utf-8";
```
- CSS 코드는 일반적으로 들여쓰기를 하지 않는다.
- 선택자 기호 · 중괄호 · 속성 사이의 모든 공백 및 마지막 속성의 세미콜론(;)은 제거한다. (파일 압축 시 예외)
- 여러개의 선택자를 사용할 때는 선택자 사이에 줄바꿈을 추가한다.
```css
.section-exam,
.section-exam2{...}
```
- CSS 속성의 작성 순서는 아래 예시를 따르며, 명시되지 않은 속성은 적절한 순서에 맞게 사용한다.
```css
overflow(-x, -y)
display
zoom
visibility
flex
float
clear
position
z-index
top, right, bottom, left
width(min-, max-)
height(min-, max-)
padding(-top, -right, -bottom, -left)
border(-width, -style, -color, -radius, -image)
margin(-top, -right, -bottom, -left)
box-sizing
background(-color, -image, -repeat, -position, -size, -origin, -clip, -attachment)
font-style
font-variant
font-weight
font-size
line-height
font-family
letter-spacing
color
text-decoration
white-space
word-wrap
word-break
text-overflow
text-indent
text-align
vertical-align
cursor
content
```
- 스타일 작성 시 <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Appendix#2-css-margin-collapsing여백-병합">collapsing margin(여백 병합)</a>을 적극적으로 사용하도록 한다.

### 3-3. 주석 작성

CSS의 주석 작성 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

한줄로 작성할 경우 주석기호와 주석내용 사이에 한칸의 공백을 추가하며, 두줄 이상이 경우 주석기호와 주석내용 사이에 줄바꿈을 추가한다.

```css
/* 한줄 설명 */
/*
두줄 이상의 설명
두줄 이상의 설명
*/
```

#### B. 레이아웃 그룹 주석

레이아웃 또는 그루핑된 엘리먼트의 시작을 알리는 주석은 아래의 형식에 맞게 작성한다.

```css
/* 영역 이름 */
.lnb{...}
```

#### C. 작성자 주석

마크업을 진행한 작성자의 정보를 표기하며, 작성자 정보는 소속 회사 및 부서, 영문 이름 이니셜, 작업 시작일을 표시한다.

- 프로젝트인지 유지보수인지에 따라 맨 앞에 '[P]'나 '[S]'를 표기한다. (단발성 프로젝트는 생략 가능)
- 작업 시작일은 YYMMDD 형식을 사용한다.
- 리뉴얼 또는 유지보수 등으로 서비스의 작업자가 변경되었을 때 아래에 이어서 추가한다.
```css
/* [P] Overtimaman Front-end Development Group CGM 141014 */
/* [S] Company UI Team HGD 150201 */
```

### 3-4. 웹폰트 사용

- 웹폰트는 프리픽스 'wf'를 추가하여 네이밍한다.
- 사용자의 시스템에 이미 폰트가 있을 경우를 고려하여 웹폰트 이전에 시스템폰트를 먼저 선언한다.
```css
@font-face{
font-family:'wf-NanumGothic';
...
}
...
body{font-family:'나눔고딕',NanumGothic,'wf-NanumGothic'}
```

### 3-5. 파일 분기

CSS 파일은 일반적으로 기본 CSS, 전역 CSS, 서비스별 CSS, 폰트 CSS로 분기하도록 하며, 네이밍은 <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter1#b-css">1-4. 파일 및 폴더 네이밍 &gt; B. CSS</a>를 확인하도록 한다.

### 3-6. 기본 CSS 파일

최초의 CSS 파일은 아래의 코드를 기본으로 서비스에 맞게 재정의하여 사용한다.  
CSS 초기화가 필요하지 않다면 <a target="_blank" href="http://necolas.github.io/normalize.css/">normalize.css</a>를 먼저 불러온 후 ```/* Reset */```에 해당하는 스타일을 삭제하거나 수정하여 사용하여야 한다.

**comm.css (PC)**

```css
@charset "utf-8";
/* [작업구분] 소속 이니셜 작업일 */

/* Reset */
article,aside,details,figcaption,figure,footer,header,menu,nav,section{display:block}
html{overflow-y:scroll;height:100%;font-size:12px}
body{min-height:100%;background-color:#fff;line-height:1.2;color:#000;/* word-wrap:break-word;word-break:break-all; */-webkit-text-size-adjust:none} /* IE9 이하 제외 시 주석 해제 */
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,form,fieldset,p,input,textarea,select,button,th,td,blockquote{padding:0;margin:0}
body,h1,h2,h3,h4,h5,h6,input,textarea,select,button,table{font-family:'돋움',Dotum,'굴림',Gulim,Helvetica,sans-serif;font-size:1em}
a,input,textarea,button{color:#000} /* IE7 이하 제외 시 color:inherit */
img,fieldset,iframe{border:0}
ul,ol{list-style:none}
li{list-style:inherit}
img,input,select,button{vertical-align:middle}
a{text-decoration:none}
a:hover{color:inherit;text-decoration:underline}
a:active{color:inherit;text-decoration:none}
cite,em,address{font-style:normal}
em{font-weight:bold}
small{font-size:0.92em}
mark{display:inline;padding:2px 1px 1px;background-color:#ff5566;font-weight:bold;color:#fff}
code,kbd,pre,samp{font-family:Menlo,Monaco,Consolas,'Courier New',monospace}
button,input[type=button],input[type=submit],input[type=reset],input[type=image]{border:0;background:none;cursor:pointer}
textarea{overflow:hidden;overflow-y:auto}
legend{position:absolute;z-index:-1;opacity:0;filter:alpha(opacity=0)}
fieldset{min-width:0}
table{border-collapse:collapse;border-spacing:0}
input[type=search]::-webkit-search-decoration,input[type=search]::-webkit-search-cancel-button,input[type=search]::-webkit-search-results-button,input[type=search]::-webkit-search-results-decoration{-webkit-appearance:none}
input::-ms-clear{display:none}
input::-ms-reveal{display:none}

/* Global */
.show-b{display:block !important}
.show-i{display:inline !important}
.show-ib{display:inline-block !important}
.hide{display:none !important}
.js-modal[tabindex=0]{outline:0 !important}
body .blind{position:absolute;z-index:-1;opacity:0;filter:alpha(opacity=0)}
body .blind-ie7{overflow:hidden;display:block;float:none;clear:both;position:relative;z-index:-1;top:0;right:0;bottom:0;left:0;width:1px;min-width:0;height:1px;min-height:0;margin:0 -1px -1px 0;line-height:1px;white-space:nowrap;opacity:0;filter:alpha(opacity=0)} /* IE7 E(position:absolute) + E(margin-top:) 버그 대응 */
body .ellips{overflow:hidden;width:100%;white-space:nowrap;text-overflow:ellipsis}
body .placeholder{color:#999}

/* UI widget */

/* Skip Navigation */
#sknav{position:fixed;z-index:16777271;top:0;right:0;left:0;height:0}
#sknav a{overflow:hidden;display:block;position:absolute;top:0;right:0;left:0;height:0;background:#222;font-size:14px;line-height:44px;font-weight:bold;color:#fff;white-space:nowrap;text-align:center}
#sknav a:hover,#sknav a:focus,#sknav a:active{top:0;height:44px}

/* Layout */
```

**comm.css (Mobile)**

```css
@charset "utf-8";
/* [작업구분] 소속 이니셜 작업일 */

/* Reset */
html{overflow-y:scroll;height:100%;font-size:14px}
body{min-height:100%;background-color:#fff;line-height:1.2;color:#000;word-wrap:break-word;word-break:break-all;-webkit-text-size-adjust:none}
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,form,fieldset,p,input,textarea,select,button,th,td,blockquote{padding:0;margin:0}
body,h1,h2,h3,h4,h5,h6,input,textarea,select,button,table{font-size:1em}
a,input,textarea,button{color:inherit}
img,fieldset,iframe{border:0}
ul,ol{list-style:none}
li{list-style:inherit}
img,input,select,button{vertical-align:middle}
a{text-decoration:none}
cite,em,address{font-style:normal}
em{font-weight:bold}
small{font-size:0.92em}
mark{display:inline;padding:2px 1px 1px;background-color:#ff5566;font-weight:bold;color:#fff}
code,kbd,pre,samp{font-family:Menlo,Monaco,Consolas,'Courier New',monospace}
input,textarea,select,button,input[type="file"]::-webkit-file-upload-button{border-radius:0;-webkit-appearance:none}
button,input[type=button],input[type=submit],input[type=reset],input[type=image],input[type="file"]::-webkit-file-upload-button{background:none;border:0;cursor:pointer}
textarea{overflow:hidden;overflow-y:auto}
legend{position:absolute;z-index:-1;opacity:0}
fieldset{min-width:0}
table{border-collapse:collapse;border-spacing:0}
input[type=search]::-webkit-search-decoration,input[type=search]::-webkit-search-cancel-button,input[type=search]::-webkit-search-results-button,input[type=search]::-webkit-search-results-decoration{-webkit-appearance:none}
input::-ms-clear{display:none}
input::-ms-reveal{display:none}
input::-webkit-input-placeholder{color:#999}
input:-moz-placeholder{color:#999}
input::-moz-placeholder{color:#999}
input:-ms-input-placeholder{color:#999}
.ua-m textarea::-webkit-scrollbar{width:8px;height:8px}
.ua-m textarea::-webkit-scrollbar-thumb{border:3px solid rgba(0,0,0,0);background-color:rgba(0,0,0,.3);-webkit-background-clip:padding-box;background-clip:padding-box}
.ua-m textarea::-webkit-scrollbar-button{display:none;width:0;height:0}
.ua-m textarea::-webkit-scrollbar-corner{background-color:transparent}
.ua-m-android input,.ua-m-android textarea,.ua-m-android button{outline:none;-webkit-tap-highlight-color:rgba(0,0,0,0);-webkit-tap-highlight-color:transparent}

/* Global */
.show-b{display:block !important}
.show-i{display:inline !important}
.show-ib{display:inline-block !important}
.hide{display:none !important}
.js-modal[tabindex=0]{outline:0 !important}
body .blind,#sknav{position:absolute;z-index:-1;opacity:0}
body .ellips{overflow:hidden;width:100%;white-space:nowrap;text-overflow:ellipsis;word-wrap:normal;word-break:normal}

/* UI widget */

/* Layout */
```

**font.css**

```css
@charset "utf-8";
/* [작업구분] 소속 이니셜 작업일 */

/* Font Set */
@font-face{
font-family:'wf-폰트명';
font-weight:normal;
src:url(파일명.eot);
src:local('☺'),
	url(파일명.eot?#iefix) format('embedded-opentype'),
	url(파일명.woff) format('woff'),
	url(파일명.ttf) format('truetype')
}

/* Reset */
body,h1,h2,h3,h4,h5,h6,input,textarea,select,button,table{font-family:'폰트명','wf-폰트명','돋움',Dotum,'굴림',Gulim,Helvetica,sans-serif}
```

---

<a href="http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter2#article">이전</a> <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter4#article">다음</a> <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Guide#article">목차</a>
