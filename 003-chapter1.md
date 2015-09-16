Markup Coding Guide - 1장. 네이밍 규칙
===

---

[목차로 이동](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)

1. 네이밍 규칙
---

선택자, 이미지, 파일 및 폴더의 네이밍 규칙을 설명한다.

### 1-1. 개요

네이밍 규칙은 HTML, CSS 파일에서 사용되는 선택자, 그리고 이미지 등의 파일이나 폴더의 이름을 작성하는 규칙이다.  
네이밍을 이해하기 쉽게 작성하여야 사이트의 제작 및 유지보수를 맡은 관리자가 코드를 쉽게 파악할 수 있다.

### 1-2. 기본 규칙

네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

- 이름은 영문 소문자, 숫자, 하이픈(-), 언더바(_)를 사용하여 작성한다.
- 이름은 일반적으로 영문 소문자로 시작하여야 한다.
- 일반적으로 선택자는 CSS의 Cascade 방식에 알맞은 네이밍을 한다.
```html
<div class="sect-exam">
	<input class="ipt">
</div>
```

#### B. 예약어 사용

- 네이밍하려는 엘리먼트의 의미에 대한 예약어가 있는 경우 예약어를 사용한다.
- 예약어가 없을 경우 엘리먼트의 종류와 의미를 나타낼 수 있도록 네이밍한다.
- 예약어 목록은 부록을 참고한다.

#### C. 네이밍 조합

- 하이픈(-)은 엘리먼트 역할에 따라 네이밍 단어를 역할별로 조합할 때 사용되며, 단순히 띄어쓰기가 필요한 경우 언더바를 사용한다.
```
service-naming-exam-wrap (X)
→ service_naming_exam-wrap (O)
```
- 네이밍의 조합은 '프리픽스-컨텐츠명-형태-의미-영역-확장--상태' 최대 7단계로 나뉘며, 필요에 따라 조합할 수 있다.
```
comm-contname-sect-exam-box-v2--over, sect-exam-box-v2, sect-exam
```
- 단어와 숫자를 조합하는 경우 하이픈을 사용하지 않으며, 숫자는 특별한 경우가 아니라면 임의로 자릿수를 늘리지 않는다.
```
list-3 (X) → list3< (O)
list03 (X) → list3< (O)
```
- 상태 네이밍은 하이픈을 두번 사용하여 조합한다.
```html
<input class="ipt-exam ipt-exam--on">
```
- 확장 네이밍은 일반적으로 'v'와 숫자 또는 식별 가능한 이름을 붙여 네이밍하며, 이름을 부여하는 경우 'v'와 단어 사이에 하이픈이 아닌 언더바를 사용한다.
```html
<input class="ipt-exam ipt-exam-v2">
<input class="ipt-exam ipt-exam-v_wide">
```
- 정의된 클래스가 없는 엘리먼트를 확장 또는 상태 제어해야 할 경우 조합없이 네이밍하여 사용한다.
```html
<div class="v_blur"></div>
<div class="fd"></div>
```

#### D. 네이밍 프리픽스

					<li>일반적으로 모듈화되는 엘리먼트에 사용한다.</li>
					<li>프리픽스는 모듈의 의미를 나타낸다.</li>
					<li>모듈에 의미를 부여하기 위해 명시된 프리픽스 외 사용자가 원하는 프리픽스를 추가하여 사용할 수 있다.</li>
					<li>특정한 이름 없이 사용되는 프리픽스는 <a href="http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Appendix#otmmcg-appendix2">부록 &gt; 2. 네이밍 예약어 &gt; C. 프리픽스</a>에서 확인할  수 있다.</li>
					<li>프리픽스는 기본적으로 id, class, name 등 엘리먼트를 식별하기 위한 애트리뷰트에 사용 가능하다.</li>
					<li>
						각각 다른 서비스 또는 서비스 내의 여러 버티컬에 전역(공통)으로 사용되는 엘리먼트는 사용자 정의 프리픽스가 없을 경우 프리픽스 'comm'을 추가한다.
						<pre>
							<span class="otmpost-txt-hilight">comm-</span>header
						</pre>
					</li>
					<li>
						사이트 내 어디에서나 사용 가능한 하나의 모듈(위젯)이 되는 엘리먼트는 사용자 정의 프리픽스가 없을 경우 프리픽스 'ui'를 추가한다.
						<pre>
							<span class="otmpost-txt-hilight">ui-</span>selbox
						</pre>
					</li>
					<li>
						일반적으로 프리픽스는 각 이름에 한번만 사용될 수 있으며, 프리픽스 'ui'는 다른 프리픽스와 중복 사용이 가능하다.
						<pre>
							<span class="otmpost-txt-hilight">comm-ui-</span>exam
							<span class="otmpost-txt-hilight">snsshare-ui-</span>btn
						</pre>
					</li>
					<li>프리픽스 목록은 부록을 참고한다.</li>

### 1-3. 선택자 네이밍

선택자 네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. 일반 규칙

					<li>한 페이지에서 동일한 id를 여러번 사용하지 않는다.</li>
					<li>class는 여러번 사용할 수 있다.</li>
					<li>엘리먼트의 id가 레이아웃을 위해 작성된 것이 아닐 경우 class를 추가하여 스타일을 제공한다.</li>
					<li>
						하나의 컨텐츠를 이루는 엘리먼트 모음의 최상위 엘리먼트는 독립성과 재사용성의 증진을 위해 컨텐츠를 확실히 식별할 수 있는 이름으로 네이밍하며, 이는 일반적으로 네이밍 조합 단계 중 컨텐츠명에 해당한다.
						<pre>
							&lt;div class=&quot;<span class="otmpost-txt-hilight">service_naming_exam</span>&quot;&gt;
							&nbsp;&nbsp;&lt;ul class=&quot;list-box&quot;&gt;
							&nbsp;&nbsp;&nbsp;&nbsp;...
							&nbsp;&nbsp;&lt;/ul&gt;
							&lt;/div&gt;
						</pre>
					</li>

#### B. 레이아웃 네이밍

HTML에서 레이아웃에 사용되는 가장 일반적인 선택자 네이밍은 아래와 같다. (PC 기준)

```html
<div style="position:relative;max-width:508px;padding:15px 110px 15px 15px;border:1px solid #444">
	#wrap : 사이트 전체
	<div style="margin-top:5px;padding:15px;border:1px solid #444">
		<div>#header : 사이트 머리글</div>
		<div style="margin-top:5px;padding:15px;border:1px solid #444">
			#gnb : Global Navigation Bar
		</div>
		<div style="margin-top:5px;padding:15px;border:1px solid #444">
			#lnb : Local Navigation Bar
		</div>
	</div>
	<div style="margin-top:5px">&lt;hr&gt;</div>
	<div style="overflow:hidden;margin-top:5px;padding:15px;border:1px solid #444">
		<div>#container : 사이트 내용</div>
		<div style="float:left;width:30%;margin-top:5px">
			<div style="padding:15px;border:1px solid #444">
				#snb : Side Navigation Bar
			</div>
		</div>
		<div style="float:left;width:38%;margin-top:5px">
			<div style="margin-left:5px;padding:15px;border:1px solid #444">
				#content : 본문
			</div>
		</div>
		<div style="float:left;width:32%;margin-top:5px">
			<div style="margin-left:5px;padding:15px;border:1px solid #444">
				#aside : 본문 보충 설명
			</div>
		</div>
	</div>
	<div style="position:absolute;top:50px;right:15px;width:53px;padding:15px;border:1px solid #444">
		#qnb : Quick Navigation Bar
	</div>
	<div style="margin-top:5px">&lt;hr&gt;</div>
	<div style="overflow:hidden;margin-top:5px;padding:15px;border:1px solid #444">
		<div>#footer : 사이트 꼬리글</div>
		<div style="margin-top:5px;padding:15px;border:1px solid #444">
			.fnb : Footer Navigation Bar
		</div>
		<div style="margin-top:5px;padding:15px;border:1px solid #444">
			.copyr : 카피라이트
		</div>
	</div>
</div>
```

[예제 1-3-B. HTML 기본 레이아웃 구조]

팝업 레이아웃의 경우 프리픽스 'pop', 레이어 레이아웃의 경우 프리픽스 'ly', 프레임 레이아웃의 경우 프리픽스 'ifr'을 추가한다.

```
#pop-wrap, #ly-header, #ifr-content
```

#### C. 테이블 셀 네이밍

&lt;th&gt;, &lt;td&gt; 엘리먼트에 제공되는 id, headers 값 은 프리픽스 't'를 추가한다.

```
#t-price
```

#### D. 폼 네이밍

폼과 관련된 &lt;input&gt;, &lt;select&gt; 등의 엘리먼트에 제공되는 id, name 값 은 프리픽스 'f'를 추가한다.

```
#f-email
```

#### E. WAI-ARIA의 상태 및 속성 네이밍

WAI-ARIA의 상태 및 속성만을 위해 제공되는 id 값은 프리픽스 'aria'를 추가한다. (별도로 정의된 값이 있을 때는 예외)

```html
<div id="nav" role="navigation" aria-labelledby="aria-nav-tit">
	<h2 id="aria-nav-tit">네비게이션</h2>
	...
</div>
```

#### F. 앵커 포인트 네이밍

앵커 포인트는 페이지 내에서 화면의 이동을 위한 지표 역할을 한다.  앵커 포인트만을 위해 제공되는 선택자 값은 프리픽스 'apnt'를 추가한다. (별도로 정의된 값이 있을 때는 예외)

```html
<a href="127.0.0.1/exam.html#apnt-exam">바로가기</a>
...
<h4>
	<span id="apnt-exam"></span>
	...
</h4>
```

### 1-4. 파일 및 폴더 네이밍

파일 및 폴더 네이밍 시 다음과 같은 규칙을 준수하도록 한다.

#### A. HTML

					<li>
						HTML 파일은 페이지명을 토대로 네이밍한다.
						<pre>
							news-list.html, customer.html
						</pre>
					</li>


#### B. CSS

					<li>
						가장 기본이 되는 CSS는 일반적으로 'comm'으로 네이밍한다.
						<pre>
							comm.css (기본 CSS)
						</pre>
					</li>
					<li>
						버티컬의 유뮤나 서비스 간의 컨셉 통일 등 다른 서비스와의 연계성을 가지는 경우 기본이 되는 CSS를 서비스명으로 네이밍하며, 여러 서비스에 전역(공통)으로 사용되는 CSS는 'comm'으로 네이밍한다.
						<pre>
							comm.css (전역 CSS)
							front.css, manage.css, ... (기본 CSS)
						</pre>
					</li>
					<li>
						기본 CSS를 제외한 나머지 CSS는 상황에 맞게 분류하여 네이밍하며, 연계 서비스의 경우 앞에 서비스명을 추가하여 네이밍한다.
						<pre>
							main.css, sub.css, bbs.css, ...
							front-main.css, front-sub.css, front-bbs.css, ...
						</pre>
					</li>
					<li>
						미디어쿼리와 별개로 디바이스별 CSS가 필요한 경우 마지막에 디바이스명을 추가하여 네이밍한다.
						<pre>
							comm-pc.css, comm-mobile.css
						</pre>
					</li>


#### C. 이미지

					<li>
						이미지 확장자와 관계없이 중복되지 않도록 네이밍한다.
						<pre>
							bg-exam.jpg, bg-exam2.gif, bg-exam3.png
						</pre>
					</li>
					<li>
						임시 이미지의 경우 앞에 @를 추가한다.
						<pre>
							@img-exap.png, @bg-exam.png
						</pre>
					</li>


#### D. 폴더

					<li>
						프로젝트 폴더는 '생성일-프로젝트명'으로 네이밍하며, 생성일은 YYMMDD 형식을 사용한다.
						<pre>
							140825-overtimeman
						</pre>
					</li>
					<li>이미지, CSS, JavaScript 폴더는 'img', 'css', 'js'로 네이밍한다.</li>
					<li>HTML파일을 메뉴별로 분기해야할 경우 서비스명을 토대로 네이밍한다.</li>

### 1-5. 모듈화

모듈화가 필요한 경우 아래의 네이밍 방법을 준수하도록 한다.

#### A. 선택자 네이밍

					<li>
						고유한 네임스페이스가 필요하므로 프리픽스를 추가한다.
						<pre>
							&lt;div class=&quot;<span class="otmpost-txt-hilight">ui-</span>tabmenu&quot;&gt;&lt;/div&gt;
						</pre>
					</li>
					<li>
						일반적으로 부모 엘리먼트 선택자의 네이밍을 종속받는다.  
						부모 엘리먼트의 선택자의 네이밍이 의미를 가지지 않는거나 높은 엘리먼트 상속 레벨로 인해 네이밍이 길어짐과 같은 HTML 구조적 이슈가 발생한 경우 반드시 종속받을 필요는 없으나, 다만 최상위 엘리먼트의 선택자 네이밍은 무조건 종속받도록 한다.
						<pre>
							&lt;div class=&quot;ui-btnshare&quot;&gt;
							&nbsp;&nbsp;&lt;div class=&quot;<span class="otmpost-txt-hilight">ui-btnshare</span>-wrap</span>&quot;&gt;
							&nbsp;&nbsp;&nbsp;&nbsp;&lt;button class=&quot;<span class="otmpost-txt-hilight">ui-btnshare</span>-btn</span>&quot;&gt;&lt;/button&gt;
							&nbsp;&nbsp;&lt;/div&gt;
							&lt;/div&gt;
						</pre>
					</li>
					<li>
						모듈화된 엘리먼트를 각 영역에서 사용함에 따라 부가적인 스타일 변경이 필요할 경우 직접 선택하여 변경하지 않는다.
						<pre>
							[HTML]
							&lt;div class=&quot;thmb <span class="otmpost-txt-hilight">ui-imgratio</span>&quot;&gt;&lt;/div&gt;
						</pre>
						<pre>
							[CSS]
							.ui-imgratio{width:200px} (X)
							.thmb{width:200px} (O)
							.thmb.ui-imgratio{width:200px} (O)
						</pre>
					</li>
					<li>
						이 외의 규칙은 일반적인 선택자 네이밍 규칙과 동일하다.
					</li>

[이전](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Preface) [다음](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter2) [목차](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)  