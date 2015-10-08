Markup Coding Guide - 5장. 사이트 성능 향상을 위한 마크업
===

---

[목차로 이동](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)

	<div class="otmpost-box" id="otmmcg-chapter5">
		<h3>5. 사이트 성능 향상을 위한 마크업</h3>
		<p>사이트의 성능 향상을 위한 마크업 방법을 설명한다.</p>
		<div class="otmpost-indent">
			<h4><span class="otmpost-apnt" id="otmmcg-chapter5-1"></span>5-1. CSS Image Sprites</h4>
			<p>Static 이미지들은 스프라이트 기법을 활용하여 파일의 용량과 HTTP Request를 최소화한다.</p>
			<div class="otmpost-indent">
				<h5>A. 일반 규칙</h5>
				<ul>
					<li>각 이미지의 시작점은 항상 짝수 px이어야 한다.</li>
					<li>각 이미지 사이의 간격은 최소 2px로 지정한다.</li>
					<li>캔버스 크기는 항상 짝수 px이어야 하며 1024px 이하로 제작한다.</li>
					<li>스마트 디바이스 또는 Device pixel ratio가 1을 초과하는 경우 캔버스 크기는 디자인의 가로 폭과 동일한 사이즈로 지정한다. (ex. iPhone 5 → 640px)</li>
					<li>확장자는 일반적으로 PNG를 사용한다. (PNG-24 포맷)</li>
					<li>스프라이트 이미지의 분기 구분은 용도별로 그룹핑한다. (ex. 타이틀, 버튼, 아이콘, ...)</li>
				</ul>
				<h5>B. 스프라이트 기법의 예제</h5>
				<div>[##_1N|cfile6.uf@261B914A552F78B3062ABA.PNG|width="630" height="160" filename="2015-04-16 17;48;59.PNG" filemime="image/jpeg"|_##]</div>
				<pre>
					/* 3번 이미지를 예로 들었을 경우 */
					.img-exam{
					&nbsp;&nbsp;width:218px;
					&nbsp;&nbsp;height:52px;
					&nbsp;&nbsp;background:<span class="otmpost-txt-hilight">url(../img/sp-comm.png)</span> no-repeat <span class="otmpost-txt-hilight">0 -54px;</span>
					&nbsp;&nbsp;background-size:<span class="otmpost-txt-hilight">360px auto;</span>
					}
				</pre>
				<h5>C. 스프라이트 기법의 활용</h5>
				<p>사용자와 상호작용이 일어나지 않는 Static 이미지에 대해서만 스프라이트 기법을 활용한다. (ex. 아이콘, 이미지 텍스트, 메뉴의 마우스오버 효과, ...)</p>
				<h5>D. 스프라이트 기법의 주의점</h5>
				<p>용량이 클 경우 크로스 브라우징에 이슈가 있을 수 있으므로 압축해서 사용하도록 한다.</p>
			</div>
		</div>
	</div>

[이전](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter4) [다음](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Appendix) [목차](http://overtimeman.tistory.com/entry/Markup-Coding-Guide)  