Markup Coding Conventions
===

<a href="http://overtimeman.github.io/conventions/markup/">http:&#47;&#47;overtimeman.github.io/conventions/markup/</a>

문서 작성 규칙
---

### 제목

제목 영역은 아래와 같이 작성한다.

```markdown
Markup Coding Conventions - 1장. 네이밍 규칙
===

---
```

### 엘리먼트별 작성 규칙

##### 앵커(링크)

- 앵커는 새창 열림을 유도하기 위하여 HTML 문법으로 작성한다.
- 앵커 엘리먼트 안의 URL이 별도의 앵커 엘리먼트로 컴파일되지 않도록 슬래시(```/```)를 엔티티 코드 ```&#47;```로 작성한다.

```html
<a href="http://overtimeman.github.io/" target="_blank">http:&#47;&#47;overtimeman.github.io&#47;</a>
```

#### 테이블

- 테이블은 마크다운에서 지원하지 않는 구조가 많아 제약이 크므로 HTML 문법으로 작성한다.
- 테이블의 열(col: column)은 6개를 넘을 수 없다.
- HTML 변환 시 ```style``` 애트리뷰트를 무시될 수 있으므로 doctype과 관계없이 ```width```, ```align``` 애트리뷰트를 사용한다.
    ```html
    <col style="width:20%"> <!-- X -->
    <col width="20%"> <!-- O -->
    ```
    ```html
    <td style="text-align:center">...</td> <!-- X -->
    <td align="center">...</td> <!-- O -->
    ```
- 작성하고자 하는 테이블의 구조가 마크다운에서 정상적으로 지원할 경우 마크다운 문법으로 제작 가능하다.
