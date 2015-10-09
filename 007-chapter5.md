Markup Coding Guide - 5장. 사이트 성능 향상을 위한 마크업
===

---

[목차로 이동](http://overtimeman.tistory.com/entry/Markup-Coding-Guide#article)

5. 사이트 성능 향상을 위한 마크업
---

사이트의 성능 향상을 위한 마크업 방법을 설명한다.

### 5-1. CSS Image Sprites

Static 이미지들은 스프라이트 기법을 활용하여 파일의 용량과 HTTP Request를 최소화한다.

#### A. 일반 규칙

- 각 이미지의 시작점은 항상 짝수 px이어야 한다.
- 각 이미지 사이의 간격은 최소 2px로 지정한다.
- 캔버스 크기는 항상 짝수 px이어야 하며 1024px 이하로 제작한다.
- 스마트 디바이스 또는 Device pixel ratio가 1을 초과하는 경우 캔버스 크기는 디자인의 가로 폭과 동일한 사이즈로 지정한다. (ex. iPhone 5 → 640px)
- 확장자는 일반적으로 PNG를 사용한다. (PNG-24 포맷)
- 스프라이트 이미지의 분기 구분은 용도별로 그룹핑한다. (ex. 타이틀, 버튼, 아이콘, ...)

#### B. 스프라이트 기법의 예제

<!-- [D] Include --> ./img/003-chapter1-3-F-a.html

```css
/* 컴퓨터 이미지를 예로 들었을 경우 */
.img-exam{
	width:182px;
	height:150px;
	background:url(../img/sp-comm.png) no-repeat 0 -232px;
	background-size:360px auto;
}
```

#### C. 스프라이트 기법의 활용

사용자와의 상호작용이 발생하지 않는 정적 이미지에 대해서만 스프라이트 기법을 활용한다.

#### D. 스프라이트 기법의 주의점

용량이 클 경우 이슈가 발생할 수 있으므로 원본, 압축 이미지를 따로 관리하여 압축된 이미지를 사용하도록 한다.

---

[이전](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Chapter4#article) [다음](http://overtimeman.tistory.com/entry/Markup-Coding-Guide-Appendix#article) [목차](http://overtimeman.tistory.com/entry/Markup-Coding-Guide#article)  
