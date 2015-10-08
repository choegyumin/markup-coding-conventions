**Markup coding guide**
===

http://overtimeman.tistory.com/entry/Markup-Coding-Guide

블로그 업로드 시 작성 가이드
---

> layout.html 참고

### CSS

레퍼런스 문서용 추가 CSS

```html
<link rel="stylesheet" type="text/css" href="http://ts.daumcdn.net/custom/blog/173/1735446/skin/images/markdown-reference.css">
```

레퍼런스 문서 내 목차용 추가 CSS

```html
<link rel="stylesheet" type="text/css" href="http://ts.daumcdn.net/custom/blog/173/1735446/skin/images/markdown-reference-index.css">
```

### HTML

[StackEdit](https://stackedit.io/editor)에서 변환된 HTML을 export하여 얻은 산출물을 아래 엘리먼트 내에 복사

```html
<div class="markdown"></div>
```

> 문서 제목 영역(```<h1>```-```<hr>```)은 생략
>
> ```markdown
> Markup Coding Guide
> ===
> 
> ---
> ```