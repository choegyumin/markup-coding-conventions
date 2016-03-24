# Markup Coding Conventions<small>(Markup Coding Style Guide)</small>

## 목차

### [머리글](./preface.html#article)

먼저 마크업 코딩 컨벤션의 목적과 사용되는 용어를 설명한다.

- <a href="./preface.html#1-서론">1. 서론</a>
- <a href="./preface.html#2-용어-설명">2. 용어 설명</a>

### [1장. 네이밍 규칙](./chapter1.html#article)

선택자, 이미지, 파일 및 폴더의 네이밍 규칙을 설명한다.

- <a href="./chapter1.html#1-1-개요">1. 개요</a>
- <a href="./chapter1.html#1-2-기본-규칙">2. 기본 규칙</a>
- <a href="./chapter1.html#1-3-선택자-네이밍">3. 선택자 네이밍</a>
- <a href="./chapter1.html#1-4-파일-및-폴더-네이밍">4. 파일 및 폴더 네이밍</a>
- <a href="./chapter1.html#1-5-모듈화">5. 모듈화</a>

### [2장. HTML 코드 작성 규칙](./chapter2.html#article)

HTML 코드의 작성 규칙을 설명한다.

- <a href="./chapter2.html#2-1-개요">1. 개요</a>
- <a href="./chapter2.html#2-2-기본-규칙">2. 기본 규칙</a>
- <a href="./chapter2.html#2-3-dtd-선언-및-head-엘리먼트-내부-마크업">3. DTD 선언 및 head 엘리먼트 내부 마크업</a>
- <a href="./chapter2.html#2-4-주석-작성">4. 주석 작성</a>
- <a href="./chapter2.html#2-5-엘리먼트별-작성">5. 엘리먼트별 작성</a>
- <a href="./chapter2.html#2-6-기본-html-파일">6. 기본 HTML 파일</a>

### [3장. CSS 코드 작성 규칙](./chapter3.html#article)

CSS 코드의 작성 규칙을 설명한다.

- <a href="./chapter3.html#3-1-개요">1. 개요</a>
- <a href="./chapter3.html#3-2-기본-규칙">2. 기본 규칙</a>
- <a href="./chapter3.html#3-3-주석-작성">3. 주석 작성</a>
- <a href="./chapter3.html#3-4-웹폰트-사용">4. 웹폰트 사용</a>
- <a href="./chapter3.html#3-5-파일-분기">5. 파일 분기</a>
- <a href="./chapter3.html#3-6-기본-css-파일">6. 기본 CSS 파일</a>

### [4장. 웹 접근성 준수 방법](./chapter4.html#article)

웹 접근성을 준수하여 마크업하는 방법을 설명한다.

- <a href="./chapter4.html#4-1-개요">1. 개요</a>
- <a href="./chapter4.html#4-2-의미있는-마크업시멘틱-마크업">2. 의미있는 마크업(시멘틱 마크업)</a>
- <a href="./chapter4.html#4-3-논리적인-순서의-마크업">3. 논리적인 순서의 마크업</a>
- <a href="./chapter4.html#4-4-대체-텍스트-제공">4. 대체 텍스트 제공</a>
- <a href="./chapter4.html#4-5-스킵-네비게이션-제공">5. 스킵 네비게이션 제공</a>
- <a href="./chapter4.html#4-6-키보드-접근성-보장">6. 키보드 접근성 보장</a>

### [5장. 사이트 성능 향상을 위한 마크업](./chapter5.html#article)

사이트의 성능 향상을 위한 마크업 방법을 설명한다.

- <a href="./chapter5.html#5-1-css-image-sprites">1. CSS Image Sprites</a>
- <a href="./chapter5.html#5-2-reflow의-최소화">2. Reflow의 최소화</a>

### [부록](./appendix.html#article)

마크업에 도움이 되는 부분을 보충 설명한다.

- <a href="./appendix.html#1-마크업-방법론">1. 마크업 방법론</a>
- <a href="./appendix.html#2-css-collapsing-margin여백-병합">2. CSS Collapsing margin(여백 병합)</a>
- <a href="./appendix.html#3-네이밍-예약어">3. 네이밍 예약어</a>

문서 수정 이력
---

<a target="_blank" href="https://github.com/choi4450/markup-coding-conventions">https:&#47;&#47;github.com&#47;choi4450&#47;markup-coding-conventions</a>

> - 2015.04.15 작성 완료
> - 2015.05.18 글로벌 컴포넌트 네이밍 방법 정의 - 최규민
> - 2015.05.29 전역 및 컨텐츠 네이밍 내용 보충 - 최규민
> - 2015.09.10 네이밍 규칙 개선 - 최규민
> - 2015.10.28 프리픽스 네이밍 수정, 키보드 접근성 내용 추가 - 최규민
> - 2015.12.14 글로벌 컴포넌트 익스텐션 정의 - 최규민
> - 2016.01.07 렌더링 엔진 최적화를 위한 클래스 사용 방법 정의 - 최규민
> - 2016.01.23 확장 네이밍 분류 정의 및 조합 방법 변경 - 최규민
> - 2016.02.02 컴포넌트 관련 용어 재정의, 프리픽스 네이밍 변경(글로벌 컴포넌트, ui → 모듈, mod) - 최규민

<div style="margin-top:25px;text-align:right"><a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/" target="_blank" style="vertical-align:top"><img alt="이 저작물은 크리에이티브 커먼즈 저작자표시-비영리-변경금지 4.0 국제 라이선스에 따라 이용할 수 있습니다." title="이 저작물은 크리에이티브 커먼즈 저작자표시-비영리-변경금지 4.0 국제 라이선스에 따라 이용할 수 있습니다." style="border-width:0;vertical-align:top" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a></div>
