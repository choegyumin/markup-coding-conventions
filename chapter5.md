---
title: Markup Coding Conventions - 5장. 사이트 성능 향상을 위한 마크업
markdown_page: true
---

Markup Coding Conventions - 5장. 사이트 성능 향상을 위한 마크업
===

<a href="./#article">목차로 이동</a>

5. 사이트 성능 향상을 위한 마크업
---

사이트의 성능 향상을 위한 마크업 방법을 설명한다.

### 5-1. CSS Image Sprites

Static 이미지들은 스프라이트 기법을 활용하여 파일의 용량과 HTTP Request를 최소화한다.

#### A. 일반 규칙

- 각 이미지의 시작점은 항상 짝수 px이어야 한다.
- 각 이미지 사이의 간격은 최소 2px로 지정한다.
- 캔버스 크기는 항상 짝수 px이어야 하며 1024px 이하로 제작한다.
- 스마트 디바이스 또는, Device pixel ratio가 1을 초과하는 경우 캔버스 크기는 디자인의 가로 폭과 동일한 사이즈로 지정한다. (ex. iPhone 5 → 640px)
- 확장자는 일반적으로 PNG를 사용한다. (PNG-24 포맷)
- 스프라이트 이미지의 분기 구분은 용도별로 그룹핑한다. (ex. 타이틀, 버튼, 아이콘 등)

#### B. 스프라이트 기법의 예제

<img src="./img/007-chapter5-1-B.jpg" alt="예제 이미지">

```css
/* GitLab 이미지를 예로 들었을 경우 */
.ico-gitlab{
	width:35px;
	height:32px;
	background:url(../img/sp-ico.png) no-repeat -68px 0;
}
```

#### C. 스프라이트 기법의 활용

사용자와의 상호작용이 발생하지 않는 정적 이미지에 대해서만 스프라이트 기법을 활용한다.

#### D. 스프라이트 기법의 주의점

용량이 클 경우 이슈가 발생할 수 있으므로 원본, 압축 이미지를 따로 관리하여 압축된 이미지를 사용하도록 한다.

### 5-2. Reflow의 최소화

추후 작성.

---

<a href="./chapter4.html#article">이전</a> <a href="./appendix.html#article">다음</a> <a href="./#article">목차</a>
