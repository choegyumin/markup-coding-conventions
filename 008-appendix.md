Markup Coding Conventions - 부록
===

---

<a href="http://overtimeman.tistory.com/entry/Markup-Coding-Conventions#article">목차로 이동</a>

부록
---

마크업에 도움이 되는 부분을 보충 설명한다.

### 1. 마크업 방법론

더욱 편리하고 효용성을 높인 마크업을 위한 방법론 중 마크업 코딩 컨벤션에 사용된 방법론을 설명한다.

#### A. BEM(Block__Element--Modifier)

하나의 엘리먼트 모음을 독립적이고 재사용이 가능하도록 모듈화하여 제작하는 CSS 방법론이다.

<a target="_blank" href="http://getbem.com/">http:&#47;&#47;getbem.com&#47;</a>

BEM의 장점

: - 네이밍이 직관적이다.
- 고유한 네임스페이스를 사용하여 컴포넌트 간의 선택자 충돌을 방지한다.
- Dom Tree를 거치지 않고 CSS의 탐색 레벨이 낮아 브라우저에서 CSS를 읽는 속도가 빠르다.
- 클래스 종속으로 커스터마이징이 용이하다.
- HTML, CSS를 모듈화하여 재사용이 가능하다.

BEM의 단점

: - 네이밍이 길어 HTML의 가독성이 떨어진다.

#### B. ACSS(Atomic CSS)

모든 스타일을 클래스로 나누어 특정 엘리먼트에 종속되지 않고 어디에서나 사용 가능하도록 제작하는 CSS 방법론이다.

ACSS의 장점

: - Dom Tree를 거치지 않고 CSS의 탐색 레벨이 낮아 브라우저에서 CSS를 읽는 속도가 빠르다.
- 선택자가 종속되지 않아 어떤 엘리먼트에서든 적용이 가능하다.
- 유지보수 시 다른 HTML 페이지의 스타일 깨짐을 우려할 필요가 없다.

ACSS의 단점

: - 인라인 스타일과 크게 다를 바가 없어 HTML 문서가 복잡해진다.
- 대규모 사이트의 경우 관리가 매우 어려우며, 오히려 CSS를 읽는 속도가 느려질 수 있다.
- 모듈화가 불가능하다.

#### C. OOCSS(Object Oriented CSS)

사이트의 각 스타일을 템플릿화하여 특정 엘리먼트에 종속되지 않고 어디에서나 재사용이 가능하도록 제작하는 CSS 방법론이다.  
Sass의 @extend를 HTML에 옮겨놓은 느낌이다.

<a target="_blank" href="http://oocss.org/">http:&#47;&#47;oocss.org&#47;</a>

OOCSS의 장점

: - Dom Tree를 거치지 않고 CSS의 탐색 레벨이 낮아 브라우저에서 CSS를 읽는 속도가 빠르다.
- CSS를 모듈화하여 어떤 엘리먼트에서든 재사용이 가능하다.

OOCSS의 단점

: - CSS 모듈화는 가능하나 HTML 엘리먼트의 모듈화는 불가능하다.
- 디자인의 재사용 빈도가 적은 사이트의 경우 적합하지 않다.

#### D. SMACSS(Scalable and Modular Architecture for CSS)

마크업 스타일을 기초, 레이아웃, 모듈, 상태, 테마 이 다섯가지로 구분하여 제작하는 CSS 방법론이다.

<a target="_blank" href="https://smacss.com/">https:&#47;&#47;smacss.com&#47;</a>

SMACSS의 장점

: - 네이밍이 직관적이다.
- 모듈 카테고리에 한하여 HTML, CSS 재사용이 가능하다.

SMACSS의 단점

: - 모듈의 스타일이 수정될 경우 사이트 전체에 일으킬 수 있는 위험 부담이 크다.

### 2. CSS Collapsing margin(여백 병합)

추후 작성.

### 3. 네이밍 예약어

네이밍 규칙은 HTML, CSS 파일에서 사용되는 선택자, 그리고 이미지 등의 파일이나 폴더의 이름을 작성하는 규칙이다.  
네이밍을 이해하기 쉽게 작성하여야 사이트의 제작 및 유지보수를 맡은 관리자가 코드를 쉽게 파악할 수 있다.

#### A. 공통 예약어

<table>
	<colgroup>
		<col width="23%">
		<col width="27%">
		<col width="23%">
		<col width="27%">
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
		<th scope="row">desc</th>
		<td>설명</td>
	</tr>
	<tr>
		<th scope="row">subsc</th>
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
		<th scope="row">submit</th>
		<td>제출</td>
		<th scope="row">cancel</th>
		<td>취소</td>
	</tr>
	<tr>
		<th scope="row">chk</th>
		<td>체크</td>
		<th scope="row">close</th>
		<td>닫기</td>
	</tr>
	<tr>
		<th scope="row">arr</th>
		<td>화살표</td>
		<th scope="row">search</th>
		<td>검색</td>
	</tr>
	<tr>
		<th scope="row">nav</th>
		<td>네비게이션</td>
		<th scope="row">tab</th>
		<td>탭</td>
	</tr>
	<tr>
		<th scope="row">listbox</th>
		<td>목록</td>
		<th scope="row">listitem</th>
		<td>목록 내 항목</td>
	</tr>
	<tr>
		<th scope="row">table</th>
		<td>테이블</td>
		<th scope="row">paginate</th>
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
		<th scope="row">line<br>(-position)<br>(-style)<br>(-color)<br>(-alpha)</th>
		<td colspan="3">선<br>ex. line(-ht, -hb, -vl, -vr)(-dot, -dash, -dbl, ...)(-fff, -...)(-a20, -...)</td>
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
		<th scope="row">bak</th>
		<td>백업 파일</td>
	</tr>
	<tr>
		<th scope="row">separ</th>
		<td>구분자</td>
		<th scope="row">dim</th>
		<td>딤드(Dimmed)</td>
	</tr>
	<tr>
		<th scope="row">input</th>
		<td>입력 폼</td>
		<th scope="row">input_txt</th>
		<td>텍스트필드(입력 폼)</td>
	</tr>
	<tr>
		<th scope="row">input_chk</th>
		<td>체크박스(입력 폼)</td>
		<th scope="row">input_rdo</th>
		<td>라디오버튼(입력 폼)</td>
	</tr>
	<tr>
		<th scope="row">input_sel</th>
		<td>셀렉트박스(입력 폼)</td>
		<th scope="row">input_file</th>
		<td>파일 업로드(입력 폼)</td>
	</tr>
	<tr>
		<th scope="row">highlight</th>
		<td>강조</td>
		<th scope="row">ellipsis</th>
		<td>문장 생략</td>
	</tr>
	<tr>
		<th scope="row">win</th>
		<td>창(새 창)</td>
		<th scope="row">modal</th>
		<td>모달 다이얼로그(레이어 팝업)</td>
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
		<th scope="row">bottom</th>
		<td>아래</td>
	</tr>
	<tr>
		<th scope="row">left</th>
		<td>왼쪽</td>
		<th scope="row">right</th>
		<td>오른쪽</td>
	</tr>
	<tr>
		<th scope="row">on/off</th>
		<td>켜짐/꺼짐(상태)</td>
		<th scope="row">able/disable</th>
		<td>활성화(상태)</td>
	</tr>
	<tr>
		<th scope="row">over/unover</th>
		<td>마우스오버(상태)</td>
		<th scope="row">focus/unfocus</th>
		<td>포커스(상태)</td>
	</tr>
	<tr>
		<th scope="row">chk/unchk</th>
		<td>체크(상태)</td>
		<th scope="row">expand/unexpand</th>
		<td>펼침/접힘(상태)</td>
	</tr>
	<tr>
		<th scope="row">@</th>
		<td>임시 이미지 또는 마크업 산출물 외 파일 및 폴더</td>
		<th scope="row">tmp</th>
		<td>이미지 제외를 제외한 임시 파일</td>
	</tr>
	<tr>
		<th scope="row">decomp</th>
		<td>압축 전 파일 보관 폴더</td>
		<th scope="row">psd</th>
		<td>PSD 보관 폴더</td>
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
		<th scope="row">#-skipnav</th>
		<td>SKip NAVigation(스킵 네비게이션)</td>
	</tr>
	<tr>
		<th scope="row">-aside-</th>
		<td>본문 보충 설명</td>
	</tr>
	<tr>
		<th scope="row">-gnb-</th>
		<td>Global Navigation Bar(서비스 전역 네비게이션)</td>
	</tr>
	<tr>
		<th scope="row">-lnb-</th>
		<td>Local Navigation Bar(현재 서비스 네비게이션)</td>
	</tr>
	<tr>
		<th scope="row">-snb-</th>
		<td>Sub Navigation Bar</td>
	</tr>
	<tr>
		<th scope="row">-fnb-</th>
		<td>Foot Navigation Bar</td>
	</tr>
	<tr>
		<th scope="row">-qnb-</th>
		<td>Quick Navigation Bar</td>
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
		<th scope="row">-fld</th>
		<td>그루핑(폼 양식)</td>
	</tr>
	</tbody>
</table>

#### C. 프리픽스

여기서는 내장 프리픽스만을 설명하며, 하이픈(-)은 표기된 부분에만 사용할 수 있다.  
애트리뷰트 및 프로퍼티 별 사용 여부는 아래 표를 따른다.

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
		<td>프레임</td>
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
		<td>글로벌 컴포넌트</td>
		<td>HTML : id, class</td>
	</tr>
	<tr>
		<th scope="row">wf-</th>
		<td>웹폰트</td>
		<td>Style : font-family</td>
	</tr>
	<tr>
		<th scope="row">js-</th>
		<td>스크립트 개발용 선택자</td>
		<td>HTML : id, class</td>
	</tr>
	</tbody>
</table>

---

<a href="http://overtimeman.tistory.com/entry/Markup-Coding-Conventions-Chapter5#article">이전</a> 다음 <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Conventions#article">목차</a>
