## 1. css

- 영역에 이미지 모두 보이도록 처리(단점: 공백이 존재)

```css
img {
  object-fit: contain;
}
```

- 영역에 이미지 가운데 정렬되면서 보이도록 처리(단점: 이미지 일부 가림처리)

```css
img {
  object-fit: cover;
}
```

## 2. css 에서 글꼴 읽어오기

- 사이트 작업 진행 전에 반드시 글꼴에 대해서 준비를 해야 함.
- 디자이너에게 글꼴을 명시받아야 함.
- 웹용 폰트 즉, 웹브라우저용 폰트는 온라인 에서 구함.
- 웹용 폰트가 없으면 우리가 만들어서 사용함.

### 2.1. 구글폰트

- https://fonts.google.com/
- 글꼴 배치 순서를 조심하세요.
- Get Font 에서 @import 를 활용한다.

### 2.2. 눈누

- https://noonnu.cc
- 웹포트로 사용에서 소스 코드를 복사해서 활용

### 2.3. 글꼴을 잘 하시는 에이전시 사이트

- https://www.webtro.co.kr
- https://www.gdweb.co.kr/main

## 3. 글꼴은 common.css 에 작성하자.

- 모든 페이지에 적용될 공통 css 작성 파일

```css
@charset "utf-8";
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100..900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Inter&display=swap");

* {
  margin: 0px;
  padding: 0;
  box-sizing: border-box;
  /* outline-style: none; */
}
```

```css
body {
  font-family: "Inter", "Noto Sans KR", sans-serif;
  font-style: normal;
  font-weight: 400;
  font-optical-sizing: auto;
  color: #000000;
}
```
