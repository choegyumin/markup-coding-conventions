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

<table>
	<colgroup>
		<col width="23.5%">
		<col width="26.5%">
		<col width="23.5%">
		<col width="26.5%">
	</colgroup>
	<thead>
	<tr>
		<th scope="col">예약어</th>
		<th scope="col">의미</th>
		<th scope="col">예약어</th>
		<th scope="col">의미</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<th scope="row">tit</th>
		<td>제목</td>
		<th scope="row">dsc</th>
		<td>설명</td>
	</tr>
	<tr>
		<th scope="row">expl</th>
		<td>부가설명</td>
		<th scope="row">cate</th>
		<td>카테고리</td>
	</tr>
	<tr>
		<th scope="row">txt</th>
		<td>문자</td>
		<th scope="row">btn</th>
		<td>버튼</td>
	</tr>
	<tr>
		<th scope="row">subm</th>
		<td>제출</td>
		<th scope="row">canc</th>
		<td>취소</td>
	</tr>
	<tr>
		<th scope="row">chk</th>
		<td>체크</td>
		<th scope="row">clse</th>
		<td>닫기</td>
	</tr>
	<tr>
		<th scope="row">arr</th>
		<td>화살표</td>
		<th scope="row">srch</th>
		<td>검색</td>
	</tr>
	<tr>
		<th scope="row">nav</th>
		<td>네비게이션</td>
		<th scope="row">tab</th>
		<td>탭</td>
	</tr>
	<tr>
		<th scope="row">list</th>
		<td>목록</td>
		<th scope="row">litem</th>
		<td>목록 내 항목</td>
	</tr>
	<tr>
		<th scope="row">tbl</th>
		<td>테이블</td>
		<th scope="row">banr</th>
		<td>배너</td>
	</tr>
	<tr>
		<th scope="row">widg</th>
		<td>위젯</td>
		<th scope="row">pg</th>
		<td>페이징</td>
	</tr>
	<tr>
		<th scope="row">banr</th>
		<td>배너</td>
		<th scope="row">ad</th>
		<td>광고</td>
	</tr>
	<tr>
		<th scope="row">bg</th>
		<td>배경</td>
		<th scope="row">mask</th>
		<td>마스크</td>
	</tr>
	<tr>
		<th scope="row"><span class="otmpost-show-ib">line</span><span class="otmpost-show-ib">(-position)</span><span class="otmpost-show-ib">(-style)</span><span class="otmpost-show-ib">(-color)</span><span class="otmpost-show-ib">(-alpha)</span></th>
		<td><span class="otmpost-show-ib">선&nbsp;&nbsp;</span><span class="otmpost-show-ib">ex. line</span><span class="otmpost-show-ib">(-ht, -hb, -vl, -vr)</span><span class="otmpost-show-ib">(-dot, -dash, -dbl, ...)</span><span class="otmpost-show-ib">(-fff)</span><span class="otmpost-show-ib">(-a20)</span></td>
		<th scope="row">sprt</th>
		<td>구분자</td>
	</tr>
	<tr>
		<th scope="row">ico</th>
		<td>아이콘</td>
		<th scope="row">bu</th>
		<td>블릿</td>
	</tr>
	<tr>
		<th scope="row">photo</th>
		<td>사진</td>
		<th scope="row">thumb</th>
		<td>썸네일</td>
	</tr>
	<tr>
		<th scope="row">img</th>
		<td>이미지</td>
		<th scope="row">sp-</th>
		<td>스프라이트 이미지</td>
	</tr>
	<tr>
		<th scope="row">flt</th>
		<td>플로팅(Floating)</td>
		<th scope="row">dim</th>
		<td>딤드(Dimmed)</td>
	</tr>
	<tr>
		<th scope="row">ipt</th>
		<td>입력 폼</td>
		<th scope="row">ipt-txt</th>
		<td>텍스트필드(입력 폼)</td>
	</tr>
	<tr>
		<th scope="row">ipt-chk</th>
		<td>체크박스(입력 폼)</td>
		<th scope="row">ipt-rdo</th>
		<td>라디오버튼(입력 폼)</td>
	</tr>
	<tr>
		<th scope="row">ipt-sel</th>
		<td>셀렉트박스(입력 폼)</td>
		<th scope="row">ipt-file</th>
		<td>파일 업로드(입력 폼)</td>
	</tr>
	<tr>
		<th scope="row">highlight</th>
		<td>강조</td>
		<th scope="row">ellipsis</th>
		<td>문장 생략</td>
	</tr>
	<tr>
		<th scope="row">prev</th>
		<td>이전</td>
		<th scope="row">next</th>
		<td>다음</td>
	</tr>
	<tr>
		<th scope="row">top</th>
		<td>위</td>
		<th scope="row">btm</th>
		<td>아래</td>
	</tr>
	<tr>
		<th scope="row">lft</th>
		<td>왼쪽</td>
		<th scope="row">rgt</th>
		<td>오른쪽</td>
	</tr>
	<tr>
		<th scope="row">--on/--off</th>
		<td>상태</td>
		<th scope="row">--able/--dsble</th>
		<td>입력 폼 활성화(상태)</td>
	</tr>
	<tr>
		<th scope="row">--ovr/--unovr</th>
		<td>마우스오버(상태)</td>
		<th scope="row">--fcs/--unfcs</th>
		<td>포커스(상태)</td>
	</tr>
	<tr>
		<th scope="row">--chk/--unchk</th>
		<td>체크(상태)</td>
		<th scope="row">--fd/--unfd</th>
		<td>펼침(상태)</td>
	</tr>
	<tr>
		<th scope="row">fnc</th>
		<td>함수(JS 또는 Back-End 개발용)</td>
		<th scope="row">idx</th>
		<td>인덱스(JS 또는 Back-End 개발용)</td>
	</tr>
	<tr>
		<th scope="row">***-</th>
		<td>마크업 산출물 넘버링</td>
		<th scope="row">@</th>
		<td>임시 이미지 또는 마크업 산출물 외 파일 및 폴더</td>
	</tr>
	<tr>
		<th scope="row">--tmp</th>
		<td>임시 파일(이미지 제외)</td>
		<th scope="row">--bak</th>
		<td>백업 파일</td>
	</tr>
	<tr>
		<th scope="row">--comp/--decomp</th>
		<td>압축 이미지 및 보관 폴더</td>
		<th scope="row">psd</th>
		<td>이미지 PSD 보관 폴더</td>
	</tr>
	</tbody>
</table>

#### B. 레이아웃 예약어

id와 class는 별도로 표기되어 있지 않다면 자유롭게 사용 가능하며, 하이픈(-)은 표기된 부분에만 사용할 수 있다.

<table>
	<colgroup>
		<col width="80px">
		<col>
	</colgroup>
	<thead>
	<tr>
		<th scope="col">예약어</th>
		<th scope="col">의미</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<th scope="row">#-wrap</th>
		<td>사이트 전체</td>
	</tr>
	<tr>
		<th scope="row">#-header</th>
		<td>사이트 머리글</td>
	</tr>
	<tr>
		<th scope="row">#-container</th>
		<td>사이트 내용</td>
	</tr>
	<tr>
		<th scope="row">#-footer</th>
		<td>사이트 꼬리글</td>
	</tr>
	<tr>
		<th scope="row">#-content</th>
		<td>본문</td>
	</tr>
	<tr>
		<th scope="row">-aside-</th>
		<td>본문 보충 설명</td>
	</tr>
	<tr>
		<th scope="row">-gnb-</th>
		<td>Global Navigation Bar(사이트 전역 네비게이션. ex. Home, Login, Sitemap, Admin...)</td>
	</tr>
	<tr>
		<th scope="row">-lnb-</th>
		<td>Local Navigation Bar(메인 네비게이션)</td>
	</tr>
	<tr>
		<th scope="row">-snb-</th>
		<td>Side Navigation Bar(서브 네비게이션)</td>
	</tr>
	<tr>
		<th scope="row">-fnb-</th>
		<td>Footer Navigation Bar</td>
	</tr>
	<tr>
		<th scope="row">-qnb-</th>
		<td>Quick Navigation Bar</td>
	</tr>
	<tr>
		<th scope="row">#-sknv</th>
		<td>SKip NaVigation</td>
	</tr>
	<tr>
		<th scope="row">-nav-</th>
		<td>네비게이션</td>
	</tr>
	<tr>
		<th scope="row">-spot-</th>
		<td>사이트 강조 영역</td>
	</tr>
	<tr>
		<th scope="row">-path-</th>
		<td>사이트 경로</td>
	</tr>
	<tr>
		<th scope="row">-copyr-</th>
		<td>카피라이트</td>
	</tr>
	<tr>
		<th scope="row">-sect-</th>
		<td>제목을 포함한 문서의 섹션</td>
	</tr>
	<tr>
		<th scope="row">-artic-</th>
		<td>글 또는 기사</td>
	</tr>
	<tr>
		<th scope="row">-cont-</th>
		<td>내용</td>
	</tr>
	<tr>
		<th scope="row">-wrap</th>
		<td>그루핑(포장)</td>
	</tr>
	<tr>
		<th scope="row">-group</th>
		<td>그루핑(묶음)</td>
	</tr>
	<tr>
		<th scope="row">-box</th>
		<td>그루핑(상자)</td>
	</tr>
	<tr>
		<th scope="row">-area</th>
		<td>그루핑(특정 영역)</td>
	</tr>
	<tr>
		<th scope="row">-zone</th>
		<td>그루핑(영역의 일부)</td>
	</tr>
	<tr>
		<th scope="row">-fld</th>
		<td>그루핑(폼 양식)</td>
	</tr>
	</tbody>
</table>

#### C. 프리픽스

여기서는 가이드 정의 프리픽스만을 설명하며, 하이픈(-)은 표기된 부분에만 사용할 수 있다.  
애트리뷰트 및 속성 별 사용 여부는 아래 표를 따른다.

<table>
	<colgroup>
		<col width="80px">
		<col>
		<col width="27%">
	</colgroup>
	<thead>
	<tr>
		<th scope="col">예약어</th>
		<th scope="col">의미</th>
		<th scope="col">용도</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<th scope="row">ifr-</th>
		<td>아이프레임</td>
		<td>HTML : id, class</td>
	</tr>
	<tr>
		<th scope="row">ly-</th>
		<td>레이어</td>
		<td>HTML : id, class</td>
	</tr>
	<tr>
		<th scope="row">pop-</th>
		<td>팝업</td>
		<td>HTML : id, class</td>
	</tr>
	<tr>
		<th scope="row">t-</th>
		<td>테이블 셀</td>
		<td>HTML : id, headers</td>
	</tr>
	<tr>
		<th scope="row">f-</th>
		<td>폼</td>
		<td>HTML : id, name</td>
	</tr>
	<tr>
		<th scope="row">aria-</th>
		<td>WAI-ARIA의 상태 및 애트리뷰트</td>
		<td>HTML : id(aria-*)</td>
	</tr>
	<tr>
		<th scope="row">-apnt-</th>
		<td>앵커 포인트</td>
		<td>HTML : id, name, class</td>
	</tr>
	<tr>
		<th scope="row">ui-</th>
		<td>공통 컴포넌트</td>
		<td>HTML : id, class</td>
	</tr>
	<tr>
		<th scope="row">wf-</th>
		<td>웹폰트</td>
		<td>Style : font-family</td>
	</tr>
	</tbody>
</table>

---

[이전](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter5#article) 다음 [목차](http://overtimeman.tistory.com/entry/Markup-Coding-Guide#article#article)  
