Markup coding guide
===

http://overtimeman.tistory.com/entry/Markup-Coding-Guide

> 마크다운 문법은 [StackEdit](https://stackedit.io/editor)의 지원 여부를 기준으로 작성한다.

문서 작성 가이드
---

### Markdown

#### 인클루드

- 마크다운 코드를 HTML로 컴파일 시 이슈가 발생하거나 마크다운 문법으로 작성할 수 없는 코드의 경우 인클루드 파일로 분리하여 보관한다.
- 인클루드 영역은 아래와 같이 주석과 파일 경로를 표기하여 HTML로 컴파일 후 직접 덮어쓸 수 있도록 한다.
```markdown
<!-- [D] Include --> ./img/exam_sprite.html
```

##### 엘리먼트별 작성 규칙

###### 테이블

- 테이블은 마크다운에서 지원하지 않는 구조가 많아 제약이 크므로 HTML 문법으로 작성한다.
- 마크다운 코드를 HTML로 컴파일 시 ```style``` 애트리뷰트를 무시하므로 doctype과 관계없이 컬럼의 가로 폭은 ```style``` 애트리뷰트 대신 ```width``` 애트리뷰트를 사용하여 지정한다.
```html
<col style="width:20%"> <!-- X -->
<col width="20%"> <!-- O -->
```
- 작성하고자 하는 테이블의 구조가 마크다운에서도 완벽히 지원하며 각 컬럼의 가로 폭 지정이 필요 없을 경우 마크다운 문법으로 제작 가능하다.

###### 이미지

- 이미지는 티스토리에서 지원하는 'Light TT EX (이미지 크게보기)' 플러그인을 사용함에 따라 ```img``` 엘리먼트 대신 티스토리에서 지원하는 이미지 치환자를 사용하여야 하며, 치환된 코드는 HTML 파일로 제작하여 원본 이미지와 같이 ```img```폴더에 보관한다.

블로그 업로드 시 작성 가이드
---

> [layout.html](https://github.com/choi4450/markup-coding-guide/blob/master/layout.html) 참고

### CSS

레퍼런스 문서용 추가 CSS

```html
<link rel="stylesheet" type="text/css" href="http://ts.daumcdn.net/custom/blog/173/1735446/skin/images/markdown-reference.css">
```

### HTML

[StackEdit](https://stackedit.io/editor)에서 변환한 HTML을 export하여 아래 엘리먼트 내에 붙여넣는다.

```html
<div class="markdown"></div>
```

- 문서 제목 영역(```<h1>```-```<hr>```)은 생략한다.
```markdown
Markup Coding Guide
===

---
```
- 인클루드 영역(```<!-- [D] Include -->```)에 추가 작성된 URL의 코드를 변환된 HTML 코드의 해당 영역에 덮어쓴다.
```markdown
<!-- [D] Include --> ./img/exam_sprite.html
```