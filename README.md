# 리액트 CRA 프로젝트

- 기존 리액트 프로젝트 생성의 기준
- ESLint 설정과 Prettire 통합이 목표

## 1. VSCode Extention 설치

- ESLint : JavaScript 를 위해서 코드 오류 및 코드 가이드를 Help 도구
- React 템플릿 도구

- Error Lens
  : JS 코드 에러 체크

- Prettire - Code Formatter
  : 문서 포맷터

## 2. 리액트 프로젝트 기본형 설치

- 프로젝트 명은 반드시 `소문자`로 작성
- 특수기호는 `-` 만 허용
- 현제 폴더에 프로젝트 생성은 `.`을 작성
- 기본적으로 `git init`이 자동으로 셋팅

```
npx create-react-app@latest 프로젝트명
```

- 프로젝트 생성하기

```
npx create-react-app@latest .
```

## 3. 생성된 프로젝트 살펴보기

- 회사에서 진행중인 프로젝트가 있다면 package.json 부터 파악.

### 3.1. package.json 살펴보기

- 개발자가 `npm install 모듈명`
- 개발시에 활용한 기술 파악
- 아래는 웹소스에 포함되는 모듈 목록

```json
// 아래는 웹소스에 포함되는 모듈 목록
"dependencies": {}
// 아래는 개발에만 사용하고 서비스 소스에는 포함 안됨
"devDependencies": {}
```

- scripts 항목(실행 명령어)

```
npm run 명령어
npm run start : 미리보기 (Ctrl + C 종료)
npm run build : 최종 전달하는 소스 번들링(압축)
npm run text : 개발 중 원하는 결과 나오는지 테스트
npm run eject : 숨겨진 소스에서 추출하기
```

```json
 "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
```

### 3.2. 불필요한 라이브러리 삭제

- package.json 원본

```json
"dependencies": {
    "@testing-library/jest-dom": "^5.17.0",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-scripts": "5.0.1",
    "web-vitals": "^2.1.4"
  },
```

- package.json 수정본

```json
 "dependencies": {
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-scripts": "5.0.1"
  },
```

- package-lock-json 삭제
- node_modules 폴더 삭제

```
npm i
```

### 3.3. .gitignore 살펴보기

- GitHub 에 업로드 되면 안되는 파일과 폴더들
- 실습 `/.env` 파일만들기

-.gitignore 내용 수정

```
# env
.env
```

### 3.4. public 폴더 살펴보기

- favicon.ico : 즐겨찾기 및 주소 공유시 보일 이미지
- logo192.png.. : 휴대폰 바로가기 등에 보여질 섬네일
- manifest.json : react는 웹 어플리케이션 이라서 앱의 설명 부여 가능.
- robots.txt : 검색엔진 노출 여부 작성, 크롤링 여부
- sitemap.xml : 직접 추가(네이버, 구글 검색 등록시 요구 파일)
- 웹페이지에 추가할 모든 리소스(이미지, 영상, 음악, 폰트 등) 배치
  : images 폴더, assets 폴더 배치
- index.html : 첫화면

```html
<!doctype html>
<html lang="ko">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <meta
      name="description"
      content="Web site created using create-react-app"
    />
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <title>서비스 타이틀</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```

### 3.5. src 폴더 살펴보기

- 제거할 파일들
  : App.test.js (`test`가 있으면 제거)
  : logo.svg (사용하지 않음)
  : reportWebVitals.js (사용하지 않음)
  : setupTests.js (test 하지않음)

- index.js
  : 최초 실행되는 js 파일 (약속)

```js
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";

// 아이디 root 에 js 내용을 js 실행 결과를 입력.
// index.html 에 있는 <div id="root"></div> 변경금지
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
);
```

-App.js
: 화면에 html(jsx) 을 출력한다면 `반드시 대문자`로 파일명 작성

```js
import "./App.css";

function App() {
  return <div>안녕</div>;
}

export default App;
```

- index.css : 수정

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
a {
  text-decoration: none;
  color: black;
}

ul,
li {
  list-style: none;
}
html {
  font-size: 16px;
}

body {
  font-size: 16px;
}
```

- App.css : 내용만 모두 삭제

## 4. 협업 프로젝트 개발 환경 설정

### 4.1. ESLint

- 반드시 익스텐션 ESLint 설치하고 진행.

- 회사에 물어보고 ESLint 버전 확인이 필요함.
  : `.eslintrc.js` 또는 `.eslintrc.json`
  : 최신 ESLint 8 버전부터는 eslint.config.mjs가 기본으로 생성됨
  : `.mjs` 확장자는 ESM을 뜻함

- ESLint 7 버전으로 셋팅 `npm install eslint@7 -D
- 이후 설정

```
npx eslint --init
```

### 4.2. Prettier 설치

- Prettier VSCode 익스텐션 설치 후 진행
- `npm i prettier -D`
- 파일로 문서포맷을 관리하도록 한다.
- `.prettierrc.json` 생성
- 셋팅하기

```json
{
  "singleQuote": false,
  "semi": true,
  "useTabs": false,
  "tabWidth": 2,
  "trailingComma": "all",
  "printWidth": 80,
  "arrowParens": "avoid",
  "endOfLine": "auto"
}
```

### 4.3. ESLint 와 Prettier 통합 관리

- ESLint 에서 Prettier 에 관련된 규칙 체크
- `npm i eslint-config-prettier -D`
- `npm i eslint-plugin-prettier -D`
- `npm i eslint-plugin-prettier -D --force`

- ESLint 에서 Prettier 를 관리하는 내용을 추가
- .eslintrc.js 코드 추가

```js
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:prettier/recommended",
  ],
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 12,
    sourceType: "module",
  },
  plugins: ["react"],
  rules: {},
};
```

### 4.4. ESLint `rules` 설정

- .eslintrc.js 를 관리하자.

```js
rules: {
    "no-unused-vars": "off",
  },
```
