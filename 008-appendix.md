Markup Coding Guide - 부록
===

---

[목차로 이동](http://overtimeman.tistory.com/entry/Markup-Coding-Guide#article)

부록
---

마크업에 도움이 되는 부분을 보충 설명한다.

### 1. 마크업 방법론

더욱 편리하고 효용성을 높인 마크업을 위한 방법론 중 마크업 코딩 가이드에 사용된 방법론을 설명한다.

#### A. BEM(Block__Element--Modifier)

하나의 엘리먼트 모음을 독립적이고 재사용이 가능하도록 모듈화하여 제작하는 CSS 방법론이다.

[https://en.bem.info/](https://en.bem.info/)

BEM의 장점

: - HTML, CSS를 모듈화하여 재사용이 가능하다.
- 고유한 네임스페이스(프리픽스)를 사용하여 선택자의 충돌을 방지한다.
- 클래스를 종속할 경우 커스터마이징이 용이하다.
- CSS의 탐색 레벨이 낮아진다.
- 네이밍이 직관적이다.

BEM의 단점

: - CSS(Cascading Style Sheets)의 Cascading 규칙에 부합하지 않는다.
- 네이밍이 길어진다.

#### B. ACSS(Atomic CSS)

모든 스타일을 클래스로 나누어 특정 엘리먼트에 종속되지 않고 어디에서나 사용이 가능하도록 제작하는 CSS 방법론이다.

ACSS의 장점

: - Dom Tree를 거치지 않고 CSS의 탐색 레벨이 낮아 브라우저에서 CSS를 읽는 속도가 빠르다.
- 선택자가 종속되지 않아 어떤 엘리먼트에서든 적용이 가능하다.
- 유지보수 시 다른 HTML 페이지의 스타일 깨짐을 우려할 필요가 없다.

ACSS의 단점

: - HTML 문서가 복잡해진다.
- 대규모 사이트의 경우 오히려 CSS를 읽는 속도가 느려질 수 있다.
- 모듈화가 불가능하다.
- 인라인 스타일과 다를 바가 없다.

#### C. OOCSS(Object Oriented CSS)

사이트의 각 스타일을 템플릿화하여 특정 엘리먼트에 종속되지 않고 어디에서나 재사용이 가능하도록 제작하는 CSS 방법론이다.

[http://oocss.org/](http://oocss.org/)

OOCSS의 장점

: - Dom Tree를 거치지 않고 CSS의 탐색 레벨이 낮아 브라우저에서 CSS를 읽는 속도가 빠르다.
- 서로 동일한 스타일을 각 엘리먼트에 별도로 지정할 필요가 없다.
- CSS만을 모듈화하여 선택자가 종속되지 않아 어떤 엘리먼트에서든 적용이 가능하다.
- Sass의 @extend와 함께 사용할 경우 OOCSS의 장점을 극대화시킬 수 있다.

OOCSS의 단점

: - CSS 모듈화는 가능하나 HTML 엘리먼트의 모듈화는 불가능하다.
- 각 페이지의 디자인 가이드가 규칙적이지 않은 사이트에서는 적합하지 않다.

#### D. SMACSS(Scalable and Modular Architecture for CSS)

마크업 스타일을 기초, 레이아웃, 모듈, 상태, 테마 이 다섯가지로 구분하여 제작하는 CSS 방법론이다.

[https://smacss.com/](https://smacss.com/)

SMACSS의 장점

: - HTML, CSS를 모듈화하여 재사용이 가능하다.
- 네이밍이 직관적이다.

### 2. CSS Collapsing margin(여백 병합)

추후 작성.

### 3. 네이밍 예약어

네이밍 규칙은 HTML, CSS 파일에서 사용되는 선택자, 그리고 이미지 등의 파일이나 폴더의 이름을 작성하는 규칙이다.  
네이밍을 이해하기 쉽게 작성하여야 사이트의 제작 및 유지보수를 맡은 관리자가 코드를 쉽게 파악할 수 있다.

#### A. 공통 예약어

하이픈(-)이 별도로 표기되어 있지 않다면 자유롭게 사용 가능하며, 표기되어 있다면 해당 부분에만 사용할 수 있다.

<!-- [D] Include --> ./table/008-appendix-3-A.html

#### B. 레이아웃 예약어

id와 class는 별도로 표기되어 있지 않다면 자유롭게 사용 가능하며, 하이픈(-)은 표기된 부분에만 사용할 수 있다.

<!-- [D] Include --> ./table/008-appendix-3-B.html

#### C. 프리픽스

여기서는 가이드 정의 프리픽스만을 설명하며, 하이픈(-)은 표기된 부분에만 사용할 수 있다.  
애트리뷰트 및 속성 별 사용 여부는 아래 표를 따른다.

<!-- [D] Include --> ./table/008-appendix-3-C.html

---

[이전](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter5#article) 다음 [목차](http://overtimeman.tistory.com/entry/Markup-Coding-Guide#article#article)  
