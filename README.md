**Markup coding guide**
===

http://overtimeman.tistory.com/entry/Markup-Coding-Guide

블로그 업로드 시 작성 가이드
---

> [layout.html](./blob/master/layout.html) 참고

### CSS

레퍼런스 문서용 추가 CSS

```html
<link rel="stylesheet" type="text/css" href="http://ts.daumcdn.net/custom/blog/173/1735446/skin/images/markdown-reference.css">
```

### HTML

[StackEdit](https://stackedit.io/editor)에서 변환한 HTML을 export하여 아래 엘리먼트 내에 붙여넣기

```html
<div class="markdown"></div>
```

- 문서 제목 영역(```<h1>```-```<hr>```)은 생략
```markdown
Markup Coding Guide
===

---
```
- ```**[D] Include**:``` 영역에 추가 작성된 URL의 코드를 변환된 HTML 코드의 해당 영역에 덮어쓰기
```markdown
**[D] Include**: /table/003-chapter1-3-F-a.html
```