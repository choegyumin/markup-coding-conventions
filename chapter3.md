# Markup Coding Conventions - 3장. CSS 코드 작성 규칙

<a href="./#article">목차로 이동</a>

## 3. CSS 코드 작성 규칙

CSS 코드의 작성 규칙을 설명한다.

### 3-1. 개요

HTML은 웹 문서를 다양하게 설계하고 수시로 변경하는데 많은 제약이 있다. 이를 보완하기 위해 만들어진 것이 스타일 시트이며, 스타일 시트의 표준안이 바로 CSS이다.  
여기서는 CSS 코드의 전반적인 작성 규칙을 설명한다.

### 3-2. 기본 규칙

CSS 코드 작성 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

- 모든 프로퍼티는 영문 대문자를 사용하지 않는다.
    ```css
    .class{Font-Family:NanumGothic} /* X */
    .class{font-family:NanumGothic} /* O */
    ```
- 기본적으로 프로퍼티 값은 작은 따옴표(')로 묶으며, 따옴표가 필요없는 프로퍼티는 사용하지 않는다.
    ```css
    background:url(bg.gif);
    font-family:Dotum,'돋움';
    content:'exam';
    @charset "utf-8";
    ```
- CSS 코드 블럭은 일반적으로 들여쓰기를 하지 않는다.
- 선택자 기호 · 중괄호 · 프로퍼티 사이의 모든 공백과 마지막 프로퍼티의 세미콜론(;)은 제거한다. (최종 CSS 파일을 압축하여 관리할 경우 예외)
- **선택자의 상속을 최소화하며, 가능하다면 id나 class 하나로 유지한다.**
    ```css
    .exam .exam-wrap .exam-group .exam-box{width:400px} /* X */
    .exam .exam-box{width:400px} /* △ */
    .exam-box{width:400px} /* O */
    ```
- 여러개의 선택자를 선택할 때는 선택자 사이에 줄바꿈을 추가한다.
    ```css
    .section-exam,
    .section-exam2{...}
    ```
- CSS 프로퍼티의 작성 순서는 일반적으로 아래 순서를 따르며, 명시되지 않은 프로퍼티는 적절한 순서에 맞게 사용한다.
    ```shell
    content
    overflow(-x, -y)
    display
    zoom
    visibility
    position
    z-index
    float
    clear
    box-sizing
    width(min-, max-)
    height(min-, max-)
    padding
    border(-style, -color, -width, -radius, -image)
    margin
    background(-color, -image, -repeat, -position, -size, -origin, -clip, -attachment)
    color
    font-family
    font-style
    font-weight
    font-size
    line-height
    letter-spacing
    text-decoration
    white-space
    word-wrap
    word-break
    text-overflow
    text-indent
    text-align
    vertical-align
    cursor
    ```
- 스타일 작성 시 <a href="./appendix.html#2-css-margin-collapsing여백-병합">collapsing margin(여백 병합)</a>을 적극 활용하도록 한다.

#### B. z-index 선언 규칙

- 스킵 네비게이션: ```16777271```
- Dimmed background를 포함하는 레이어: ```16600000``` ~ ```16699999```
- 플로팅 레이어: ```16500000``` ~ ```16599999```
- 사용자와의 상호작용으로 활성화된 엘리먼트 및 레이어 (ex. 커스텀 콤보박스): ```16400000``` ~ ```16499999```
- 그 외 엘리먼트: ```-1``` ~ ```100000```

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

레이아웃 또는, 그루핑된 엘리먼트의 시작을 알리는 주석은 아래의 형식에 맞게 작성한다.

```css
/* 영역 이름 */
.lnb{...}
```

#### C. 작성자 주석

마크업을 진행한 작성자의 정보를 표기하며, 작성자 정보는 소속 회사 및 부서, 영문 이름 이니셜, 작업 시작일을 표시한다.

```css
/* [P] Overtimaman Front-end Development Group CGM 141014 */
```

- 프로젝트인지 유지보수인지에 따라 맨 앞에 '[P]'나 '[S]'를 표기한다. (단발성 프로젝트는 생략 가능)
- 작업 시작일은 YYMMDD 형식을 사용한다.
- 리뉴얼 또는, 유지보수 등으로 서비스의 작업자가 변경되었을 때 아래에 이어서 추가한다.
    ```css
    /* [P] Overtimaman Front-end Development Group CGM 141014 */
    /* [S] Company UI Team PYH 150201 */
    ```

### 3-4. 웹폰트 사용

- 웹폰트는 시스템폰트와 동일한 이름을 사용하거나 프리픽스 'wf'를 추가하여 네이밍한다.
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

CSS 파일의 종류는 기본 CSS, 전역 CSS, 서비스별 CSS, 폰트 CSS로 나뉘며, 필요에 따라 분기한다. 네이밍은 <a href="./chapter1.html#b-css">1-4. 파일 및 폴더 네이밍 &gt; B. CSS</a>를 참고도록 한다.

### 3-6. 기본 CSS 파일

최초의 CSS 파일은 아래의 코드를 기본으로 **불필요한 코드를 제거 후 서비스에 맞게 수정**하여 사용한다.  
CSS 초기화(```/* Reset */```) 대신 <a target="_blank" href="http://necolas.github.io/normalize.css/">normalize.css</a>를 사용하여도 상관없다.

**comm.css (PC)**

```css
@charset "utf-8";
/* [작업구분] 소속 이니셜 작업일 */

/* Font Set */
@font-face{
	font-family:'wf-FONTNAME';
	font-weight:normal;
	src:url(FILENAME.eot);
	src:local('☺'),
		url(FILENAME.woff) format('woff'),
		url(FILENAME.ttf) format('truetype')
}

/* Reset */
article,aside,details,figcaption,figure,footer,header,menu,nav,section{display:block}
html,body{height:100%}
html{overflow-y:scroll;font-family:'FONTNAME','wf-FONTNAME','맑은 고딕','Malgun Gothic','돋움',Dotum,'굴림',Gulim,Helvetica,sans-serif;font-size:12px;line-height:1.2}
body{background:#fff;color:#000;-webkit-text-size-adjust:none}
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,form,fieldset,hr,p,input,textarea,select,button,th,td,blockquote,figure{padding:0;margin:0}
body,h1,h2,h3,h4,h5,h6,input,textarea,select,button,table{font-family:inherit;font-size:1em}
a,input,textarea,button{color:inherit} /* [D] IE7 크로스브라우징 시 body와 동일한 color 지정 */
img,fieldset,iframe{border:0}
hr{border:solid #9a9a9a;border-width:1px 0 0 0}
ul,ol{list-style:none}
img,input,select,button,textarea{vertical-align:middle}
a{text-decoration:none}
a:hover{text-decoration:underline}
a:active{text-decoration:none}
cite,em,address{font-style:normal}
em{font-weight:bold}
small{font-size:.92em}
mark{padding:1px}
code,kbd,pre,samp{font-family:Menlo,Monaco,Consolas,'Courier New',monospace}
input,textarea{-webkit-box-sizing:border-box;box-sizing:border-box} /* [D] IE7 크로스브라우징 시 라인 삭제 */
button,input[type=button],input[type=submit],input[type=reset],input[type=image]{border:0;background:none;cursor:pointer}
textarea{overflow:hidden;overflow-y:auto}
legend{position:absolute;width:1px;height:1px;padding:0;clip:rect(0 0 0 0)}
fieldset{min-width:0}
table{border-collapse:collapse;border-spacing:0}

/* Global */
html>body .blind{overflow:hidden;position:absolute;width:1px;height:1px;padding:0;margin:0;clip:rect(0 0 0 0)}
.show_b{display:block !important}
.show_i{display:inline !important}
.show_ib{display:inline-block !important}
.hide{display:none !important}
.placeholder{color:#a9a9a9}
.ellipsis{overflow:hidden;max-width:100%;white-space:nowrap;text-overflow:ellipsis;word-wrap:normal;word-break:normal}

/* Module */

/* Skip Navigation */
#skipnav{position:fixed;z-index:16777271;top:0;right:0;left:0;height:0}
#skipnav a{overflow:hidden;display:block;position:absolute;top:-45px;right:0;left:0;height:45px;background:#222;color:#fff;font-size:14px;line-height:43px;font-weight:bold;text-decoration:none;white-space:nowrap;text-align:center;clip:rect(0 0 0 0)}
#skipnav a:hover,#skipnav a:focus,#skipnav a:active{top:0;clip:auto}

/* Layout */
#wrap{position:relative;min-height:100%}

/* Component */

/* Print */
@media print{
}

/* Screen Reader */
@media aural, speech{
}
```

**comm.css (Mobile)**

```css
@charset "utf-8";
/* [작업구분] 소속 이니셜 작업일 */

/* Reset */
html,body{height:100%}
html{overflow-y:scroll;font-size:14px;line-height:1.2}
body{background:#fff;color:#000;word-wrap:break-word;word-break:break-all;-webkit-text-size-adjust:none}
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,form,fieldset,p,input,textarea,select,button,th,td,blockquote,figure{padding:0;margin:0}
body,h1,h2,h3,h4,h5,h6,input,textarea,select,button,table{font-family:inherit;font-size:1em}
a,input,textarea,button{color:inherit}
img,fieldset,iframe{border:0}
hr{border:solid #9a9a9a;border-width:1px 0 0 0}
ul,ol{list-style:none}
img,input,select,button,textarea{vertical-align:middle}
a{text-decoration:none}
cite,em,address{font-style:normal}
em{font-weight:bold}
small{font-size:.92em}
mark{padding:1px}
code,kbd,pre,samp{font-family:Menlo,Monaco,Consolas,'Courier New',monospace}
input,textarea{-webkit-box-sizing:border-box;box-sizing:border-box}
input,textarea,select,button,input[type="file"]::-webkit-file-upload-button{border-radius:0;-webkit-appearance:none}
button,input[type=button],input[type=submit],input[type=reset],input[type=image],input[type="file"]::-webkit-file-upload-button{background:none;border:0;cursor:pointer}
textarea{overflow:hidden;overflow-y:auto}
legend{position:absolute;width:1px;height:1px;padding:0;clip:rect(0 0 0 0)}
fieldset{min-width:0}
table{border-collapse:collapse;border-spacing:0}
.placeholder{color:#a9a9a9}
input::-webkit-input-placeholder{color:#a9a9a9}
input:-moz-placeholder{color:#a9a9a9}
input::-moz-placeholder{color:#a9a9a9}
input:-ms-input-placeholder{color:#a9a9a9}

/* Global */
html>body .blind{overflow:hidden;position:absolute;width:1px;height:1px;padding:0;margin:0;clip:rect(0 0 0 0)}
.show_b{display:block !important}
.show_i{display:inline !important}
.show_ib{display:inline-block !important}
.hide{display:none !important}
.ellipsiss{overflow:hidden;max-width:100%;white-space:nowrap;text-overflow:ellipsis;word-wrap:normal;word-break:normal}

/* Module */

/* Layout */
#skipnav{position:absolute;width:1px;height:1px;clip:rect(0 0 0 0)}
#wrap{position:relative;min-height:100%}

/* Component */
```

---

<a href="./chapter2.html#article">이전</a> <a href="./chapter4.html#article">다음</a> <a href="./#article">목차</a> <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/" target="_blank" style="float:right"><img alt="이 저작물은 크리에이티브 커먼즈 저작자표시-비영리-변경금지 4.0 국제 라이선스에 따라 이용할 수 있습니다." title="이 저작물은 크리에이티브 커먼즈 저작자표시-비영리-변경금지 4.0 국제 라이선스에 따라 이용할 수 있습니다." style="border-width:0;vertical-align:top" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a>
