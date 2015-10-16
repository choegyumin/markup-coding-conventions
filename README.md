Markup Coding Guide
===

http://overtimeman.tistory.com/entry/Markup-Coding-Guide

문서 작성 규칙
---

### 기본 규칙

- 테이블의 열(col: column)은 6개를 넘을 수 없다.
- 이미지는 티스토리에서 지원하는 'Light TT EX (이미지 크게보기)' 플러그인을 사용함에 따라 ```img``` 엘리먼트 대신 티스토리에서 지원하는 이미지 치환자를 사용한다.
- 마크다운 문법은 [StackEdit](https://stackedit.io/editor)의 지원 여부를 기준으로 작성한다.

### 제목

- 제목 영역은 아래와 같이 작성하며, 블로그에는 제외하여 업로드한다.

```markdown
Markup Coding Guide - 1장. 네이밍 규칙
===

---
```

### 인클루드

- 마크다운 코드를 HTML 변환 시 이슈가 발생하거나 마크다운 문법으로 작성할 수 없는 코드의 경우 별도의 html 파일로 분리하여 보관한다.
- 인클루드 영역은 아래와 같이 주석과 파일 경로를 표기하여 HTML 변환 후 직접 덮어쓸 수 있도록 한다.

```markdown
<!-- [D] Include --> ./img/exam_sprite.html
```

### 엘리먼트별 작성 규칙

##### 앵커(링크)

- 앵커는 새창 열림을 유도하기 위하여 HTML 문법으로 작성한다.

```html
<a href="http://overtimeman.tistory.com/" target="_blank">야근맨</a>
```

#### 테이블

- 테이블은 마크다운에서 지원하지 않는 구조가 많아 제약이 크므로 HTML 문법으로 작성한다.
- HTML 변환 시 ```style``` 애트리뷰트를 무시하므로 doctype과 관계없이 ```style``` 애트리뷰트 대신 ```width```, ```align``` 애트리뷰트를 사용한다.

```html
<col style="width:20%"> <!-- X -->
<col width="20%"> <!-- O -->
```

```html
<td style="text-align:center">...</td> <!-- X -->
<td align="center">...</td> <!-- O -->
```

- 작성하고자 하는 테이블의 구조가 마크다운에서 정상적으로 지원할 경우 마크다운 문법으로 제작 가능하다.

#### 이미지 치환자

- 이미지 치환자는 HTML 변환 시 이슈가 발생할 수 있으므로 인클루드 영역으로 구분하며, 원본 이미지와 같이 ```img```폴더에 보관한다.

블로그 업로드 규칙
---

### 기본 설정

| 항목 | 설정값 |
| :--- | :--- |
| 공개 형태 | 발행 |
| 주제 | IT 인터넷 |
| 권한 | 댓글 허용 X, 트랙백 허용 X |
| CCL | 저작물 사용 허가 표시, 상업적 이용 X, 콘텐츠 변경 X |
| 태그 | coding, Convention, CSS, Guide, HTML, Markup, ui, ux, 가이드, 마크업, 컨벤션, 코딩 |
| 서식 | Markup Coding Guide |

### 본문

> [레이아웃](https://github.com/choi4450/markup-coding-guide/blob/master/layout.html) 참고

- 최상단에 레퍼런스 문서용 추가 CSS를 불러온다.

```html
<link rel="stylesheet" type="text/css" href="http://ts.daumcdn.net/custom/blog/173/1735446/skin/images/markdown-reference.css">
```

- [StackEdit](https://stackedit.io/editor)에서 변환한 HTML을 export하여 얻은 코드를 아래 엘리먼트 내에 붙여넣는다. (제목 영역은 생략)

```html
<div class="markdown"></div>
```

- 인클루드 영역에 작성된 URL의 코드를 해당 영역에 덮어쓴다.

```markdown
<!-- [D] Include --> ./img/exam_sprite.html
```