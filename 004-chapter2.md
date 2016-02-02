Markup Coding Conventions - 2장. HTML 코드 작성 규칙
===

---

<a href="http://overtimeman.tistory.com/entry/Markup-Coding-Conventions#article">목차로 이동</a>

2. HTML 코드 작성 규칙
---

HTML 코드의 작성 규칙을 설명한다.

### 2-1. 개요

HTML은 사용자에게 내용을 전달하는 문서이며, 따라서 HTML 코드를 논리적으로 작성하여야 사이트를 더 효율적으로 사용할 수 있다.  
여기서는 HTML 코드의 전반적인 작성 규칙을 설명한다.

### 2-2. 기본 규칙

HTML 코드 작성 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

- HTML은 선언한 DTD 명세에 맞게 작성되어야 하며, 부득이하게 문법을 지킬수 없는 경우를 제외하고는 W3C Validation을 통과해야 한다.
- 특정 케이스(DTD 선언)를 제외한 모든 엘리먼트와 애트리뷰트는 영문 대문자를 사용하지 않는다.
```html
<IMG SRC=".."> <!-- X -->
<img src=".."> <!-- O -->
```
- 모든 애트리뷰트 값은 큰 따옴표(```"```)로 묶는다.
```html
<img src='..'> <!-- X -->
<img src=".."> <!-- O -->
```
- 모든 마크업 엘리먼트는 중첩 시 1탭 들여쓴다. (```<html>```, ```<head>```, ```<body>```의 자식 엘리먼트는 예외)
- HTML 코드 내 스크립트는 사용을 지양하며, ```<body>```의 마지막에 작성하거나 또는, js 파일로 분리한다.
```html
<input type="text" onfocus="this.className='on'"> <!-- X -->
```
- 엘리먼트 애트리뷰트의 선언 순서는 상황에 맞게 가변 애트리뷰트를 가장 나중에 작성한다.
```html
<input type="password" class="input_exam" name="f-pw" id="f-pw" title="비밀번호" style="width:100px" disabled>
```
- 렌더링 엔진 최적화를 위해 스타일 또는, 스크립트 제어가 필요한 **모든 엘리먼트에는 클래스명을 부여**하도록 한다.

### 2-3. DTD 선언 및 head 엘리먼트 내부 마크업

DTD 선언 및 HTML의 head 엘리먼트 내부 마크업 시 다음과 같은 규칙을 준수하도록 한다.

#### A. DTD 선언

HTML 문서 작성 시 DTD는 아래의 예시를 따르며, DTD 선언 앞에는 서버사이드 언어를 제외한 다른 문자를 허용하지 않는다.

<table>
	<colgroup>
		<col width="22%">
		<col>
	</colgroup>
	<tbody>
	<tr>
		<th scope="row">HTML 5</th>
		<td>
			<code>&lt;!DOCTYPE html&gt;</code>
		</td>
	</tr>
	<tr>
		<th scope="row">HTML 4.01<br>Transitional</th>
		<td>
			<code>&lt;!DOCTYPE HTML PUBLIC &quot;-//W3C//DTD HTML 4.01 Transitional//EN&quot; &quot;http://www.w3.org/TR/html4/loose.dtd&quot;&gt;</code>
		</td>
	</tr>
	<tr>
		<th scope="row">XHTML 1.0<br>Transitional</th>
		<td>
			<code>&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;</code>
		</td>
	</tr>
	</tbody>
</table>

#### B. 인코딩

HTML 문서 작성 시 다음과 같은 규칙을 준수하여 인코딩을 선언하도록 한다.

<table>
	<colgroup>
		<col width="22%">
		<col>
	</colgroup>
	<tbody>
	<tr>
		<th scope="row">HTML 5</th>
		<td>
			<code>&lt;meta charset=&quot;utf-8&quot;&gt;</code>
		</td>
	</tr>
	<tr>
		<th scope="row">Other</th>
		<td>
			<code>&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html;charset=utf-8&quot;&gt;</code>
		</td>
	</tr>
	</tbody>
</table>

- UTF-8 인코딩을 사용할 수 없다면 다른 인코딩을 사용한다. (한글은 euc-kr)
- 인코딩 선언은 head 엘리먼트 내부의 최초 엘리먼트로 작성한다.

#### C. Viewport

HTML 문서 작성 시 다음과 같은 규칙을 준수하여 Viewport를 설정하도록 한다.

<table>
	<colgroup>
		<col width="22%">
		<col>
	</colgroup>
	<tbody>
	<tr>
		<th scope="row">iOS</th>
		<td>
			<code>&lt;meta name=&quot;viewport&quot; content=&quot;width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no&quot;&gt;</code>
		</td>
	</tr>
	<tr>
		<th scope="row">Other</th>
		<td>
			<code>&lt;meta name=&quot;viewport&quot; content=&quot;width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no,target-densitydpi=medium-dpi&quot;&gt;</code>
		</td>
	</tr>
	</tbody>
</table>

#### D. User Agent

HTML 문서 작성 시 필요할 경우 User Agent별로 body에 클래스를 추가하며, 다음과 같은 규칙을 기본으로 한다.

<table>
	<colgroup>
		<col width="22%">
		<col width="22%">
		<col>
	</colgroup>
	<tbody>
	<tr>
		<th scope="rowgroup" rowspan="3">Mobile</th>
		<th scope="row">-</th>
		<td>ua-m</td>
	</tr>
	<tr>
		<th scope="row">iOS</th>
		<td>ua-m ua-m-ios</td>
	</tr>
	<tr>
		<th scope="row">Android</th>
		<td>ua-m ua-m-android</td>
	</tr>
	<tr>
		<th scope="rowgroup" rowspan="4">PC</th>
		<th scope="row">-</th>
		<td>ua-pc</td>
	</tr>
	<tr>
		<th scope="row">Windows</th>
		<td>ua-pc ua-pc-windows</td>
	</tr>
	<tr>
		<th scope="row">Mac</th>
		<td>ua-pc ua-pc-mac</td>
	</tr>
	<tr>
		<th scope="row">Linux</th>
		<td>ua-pc ua-pc-linux</td>
	</tr>
	<tr>
		<th scope="rowgroup">Other</th>
		<th scope="row">-</th>
		<td>ua-other</td>
	</tr>
	</tbody>
</table>

### 2-4. 주석 작성

HTML의 주석 작성 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

한줄로 작성할 경우 주석기호와 주석내용 사이에 한칸의 공백을 추가하며, 두줄 이상이 경우 주석기호와 주석내용 사이에 줄바꿈을 추가한다.

```html
<!-- 한줄 설명 -->
<!--
두줄 이상의 설명
두줄 이상의 설명
-->
```

#### B. 레이아웃 그룹 주석

레이아웃 또는, 그루핑된 엘리먼트의 시작과 끝을 알리는 주석은 아래의 형식에 맞게 작성하며, 시작인지 끝인지에 따라 맨 앞에 '[S]'나 '[E]'를 표기한다.

```html
<!-- [S] 영역 이름 -->
<div>
	...
</div>
<!-- [E] 영역 이름 -->
```

#### C. 개발참고 주석

개발 적용 시에 참고해야하는 주석은 맨 앞에 '[D]'를 추가하여 작성한다.

```html
<!-- [D] 개발 적용 시 참고해야 할 내용 -->
```

### 2-5. 엘리먼트별 작성

HTML 작성 시 엘리먼트 별로 코드작성 유의사항을 준수하도록 한다.  
여기서는 DTD 명세와 W3C Validation과는 별도로 엘리먼트 작성 시 추가로 지켜야할 사항만을 설명한다.

#### A. 일반 규칙

HTML은 부득이하게 문법을 지킬수 없는 경우를 제외하고는 W3C Validation을 통과해야 한다.

#### B. ```<table>```, ```<ul>```, ```<ol>```, ```<dl>```

자식 엘리먼트로 사용할 수 있는 태그가 한정적인 엘리먼트는 일반적으로 ```<div>```로 묶어서 사용한다.

```html
<!-- X -->
<table class="tbl">
	...
</table>

<!-- O -->
<div class="tbl">
	<table>
		...
	</table>
</div>
```

#### C. ```<table>```, ```<thead>```, ```<tfoot>```, ```<tbody>```

```<table>``` 엘리먼트를 제작 시 ```<thead>```, ```<tfoot>```의 유무와 관계없이 ```<tbody>```를 사용하도록 한다.

```html
<!-- X -->
<table>
	<tr>...</tr>
	...
</table>

<!-- O -->
<table>
	<tbody>
		<tr>...</tr>
	</tbody>
	...
</table>
```

#### D. ```<caption>```

```<caption>``` 엘리먼트를 숨김 처리할 때는 ```<caption>``` 내부의 컨텐츠를 묶어서 숨기도록 한다.

```html
<!-- X -->
<table>
	<caption class="blind">...</caption>
	...
</table>

<!-- O -->
<table>
	<caption>
		<div class="blind">...</div>
	</caption>
	...
</table>
```

#### E. ```<input>```, ```<select>```, ```<textarea>```

회원가입 등의 문서 작성 폼의 경우 각 엘리먼트별로 너비 값이 다르다면 인라인 스타일로 제어한다.

```html
<!-- X -->
<input type="text" class="input-txt input-txt-w120">
<input type="text" class="input-txt input-txt-w180">

<!-- O -->
<input type="text" class="input-txt" style="width:120px">
<input type="text" class="input-txt" style="width:180px">
```

#### E. ```<button>```

버튼에 별도의 type 애트리뷰트가 지정되어있지 않을 경우 반드시 ```type="button"```을 선언한다.

```html
<button>버튼</button> <!-- X -->
<button type="button">버튼</button> <!-- O -->
```

### 2-6. 기본 HTML 파일

최초의 HTML 파일은 아래의 구조를 토대로 수정하여 사용한다.

**PC**

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>페이지명 | 사이트명</title>
<meta name="keywords" content="..">
<meta name="description" content="..">
<meta name="author" content="..">
<meta name="format-detection" content="telephone=no,address=no,email=no">
<link rel="stylesheet" type="text/css" href="..">
</head>
<body>
<div id="wrap">
<!-- [S] Skip Navigation -->
<div id="skipnav">
</div>
<!-- [E] Skip Navigation -->
<!-- [S] Header -->
<div id="header" role="banner">
</div>
<!-- [E] Header -->
<hr>
<!-- [S] Container -->
<div id="container" role="main">
	<!-- [S] Content -->
	<div id="content">
	</div>
	<!-- [E] Content -->
</div>
<!-- [E] Container -->
<hr>
<!-- [S] Footer -->
<div id="footer" role="contentinfo">
</div>
<!-- [E] Footer -->
</div>
</body>
</html>
```

**PC (html5shiv)**

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>페이지명 | 사이트명</title>
<meta name="keywords" content="..">
<meta name="description" content="..">
<meta name="author" content="..">
<meta name="format-detection" content="telephone=no,address=no,email=no">
<link rel="stylesheet" type="text/css" href="..">
<!--[if lt IE 9]>
<script type="text/javascript" src="html5shiv-printshiv.min.js"></script>
<![endif]-->
</head>
<body>
<div id="wrap">
<!-- [S] Skip Navigation -->
<div id="skipnav">
</div>
<!-- [E] Skip Navigation -->
<!-- [S] Header -->
<header id="header">
</header>
<!-- [E] Header -->
<hr>
<!-- [S] Container -->
<div id="container" role="main">
	<!-- [S] Content -->
	<div id="content">
	</div>
	<!-- [E] Content -->
</div>
<!-- [E] Container -->
<hr>
<!-- [S] Footer -->
<footer id="footer">
</footer>
<!-- [E] Footer -->
</div>
</body>
</html>
```

**Mobile**

```html
<!doctype html>
<html lang="ko">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no,target-densitydpi=medium-dpi">
<title>페이지명 | 사이트명</title>
<meta name="keywords" content="..">
<meta name="description" content="..">
<meta name="author" content="..">
<meta name="format-detection" content="telephone=no,address=no,email=no">
<link rel="stylesheet" type="text/css" href="..">
</head>
<body class="..">
<div id="wrap">
<!-- [S] Skip Navigation -->
<div id="skipnav">
</div>
<!-- [E] Skip Navigation -->
<!-- [S] Header -->
<header id="header">
</header>
<!-- [E] Header -->
<hr>
<!-- [S] Container -->
<div id="container" role="main">
	<!-- [S] Content -->
	<div id="content">
	</div>
	<!-- [E] Content -->
</div>
<!-- [E] Container -->
<hr>
<!-- [S] Footer -->
<footer id="footer">
</footer>
<!-- [E] Footer -->
</div>
</body>
</html>
```

---

<a href="http://overtimeman.tistory.com/entry/Markup-Coding-Conventions-Chapter1#article">이전</a> <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Conventions-Chapter3#article">다음</a> <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Conventions#article">목차</a>
