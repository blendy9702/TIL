# Vite

## 1. Vite 와 CRA 의 차이

### 1.1. 프로젝트 생성법 차이

```
npx create-react-app@latest 소문자 프로젝트명
npm create vite@latest 소문자 프로젝트명
```

### 1.2. 간략한 장단점.

- Vite 는 차세대 프론트엔드 빌드 도구, 빠른 개발환경 제공.
- CRA 는 Webpack 을 활용, Vite 는 Rollup, esbuild 을 사용.
- `HMR (Hot Module Replacement)` 를 Vite 에서는 빠르게 제공.
  : 모듈 교체 시 빠르게 업데이트가 가능.
  : ES 모듈 교체를 이용해 필요한 부분만 새로고치기 때문에 빠름.
  : CRA 는 Webpack 으로 번들링하는 시간 및 적용시간이 길어서 테스트시 시간 소비가 큼.
- CRA 는 모든 환경을 제공하므로 초보자가 활용하기 좋음.
- Vite 는 개발환경을 이해한 개발자가 활용하기 좋음.
- 결론 : Vite 가 그냥 좋다.

## 2. VSCode Extenstion 설치

- ESLint 설치
- ES7+ React/Redux/React-Native snippets
- Simple React Snippets
- Error Lens
- Simple React Snippets
- Prettier - Code Formatter
  -setting.json 코드 추가

```json
"editor.formatOnSave": true,

"editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
},
```

## 3. 프로젝트 구성

- 반드시 소문자(단어-단어) 처럼 특수기호 `-` 허용
- 자동으로 `git init` 됨
- `git remote add origin 깃허브주소` 는 직접 셋팅

## 4. Vite 프로젝트 생성 후 과정

```
npm install
```

- 만약 yarn 으로 관리할 경우 주의가 필요.

## 5. 프로젝트 살펴보기

- 자동으로 기본 eslint 셋팅됨. (버전 고민)
- package.json

```
dependency {}
devDependency {}
```

### 5.1. .gitignore 수정

```
* env
.env
```

### 5.2. index.html 수정

- lang 과 title 만 수정
- main.jsx로 시작.

```html
<!doctype html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite 프로젝트</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

### 5.3. public 폴더

- 리소스 배치장소(images, mp4...)

### 5.4. src 폴드

- assets 폴더는 src 에 있는 js 들이 사용하는 리소스

### 5.5. index.css

- 참고 사항 : (:root 사용의 예)
- :root 는 html 보다 힘이 강함.
- html {} 과 :root {} 적용시 :root 가 우선권을 가짐.
- :root css는 html 에 css를 적용한 것과 같다.
- html 을 커스터마이징 할 때 :root 를 쓴다.
- 전역으로 사용하고 싶을 때 활용함.

```css
:root {
  --primary-color: #000;
  --secondary-color: #f5e565;
  --font-size-base: 16px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

a {
  text-decoration: none;
  color: #000;
}

ul,
li {
  list-style: none;
}

html {
  font-size: 16px;
}

body {
  font-size: var(--font-size-base);
  color: var(--primary-color);
}
/* 웹서비스 개발시 권장함. (개인적으로) */
html,
body,
:root {
  width: 100%;
  height: 100%;
  overflow-x: hidden;
}
```

### 5.6. eslint.config.js

```js
import js from "@eslint/js";
import globals from "globals";
import react from "eslint-plugin-react";
import reactHooks from "eslint-plugin-react-hooks";
import reactRefresh from "eslint-plugin-react-refresh";

export default [
  // dist 폴더는 eslint 에서 제외
  { ignores: ["dist"] },
  {
    // eslint 검사 대상, 파일명의 확장자
    files: ["**/*.{js,jsx}"],
    // js 및 jsx 옵션
    languageOptions: {
      // js 검사 기준 버전
      ecmaVersion: 2020,
      // globals 웹브라우저 : windows, Node.js : local
      // 웹브라우저에 사용되는 windows, document
      globals: globals.browser,
      // parser (파서) : 복잡한 입력 데이터를 해석
      parserOptions: {
        // latest (최신버전) : ECMA 중에 최근 버전을 활용하겠다.
        ecmaVersion: "latest",
        // jsx 를 사용하겠다.
        ecmaFeatures: { jsx: true },
        // 모듈 방식중에 ESModule 을 쓰겠다.
        sourceType: "module",
      },
    },
    // React 버전
    settings: { react: { version: "18.3" } },
    // ESLint 플러그인
    plugins: {
      // 리액트 문법 규칙 맞는지 검사하는 도구
      react,
      // 리액트 hooks 의 규칙이 맞는지 검사하는 도구
      "react-hooks": reactHooks,
      // 리액트 refresh
      "react-refresh": reactRefresh,
    },
    rules: {
      ...js.configs.recommended.rules,
      ...react.configs.recommended.rules,
      ...react.configs["jsx-runtime"].rules,
      ...reactHooks.configs.recommended.rules,
      "react/jsx-no-target-blank": "off",
      "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
    },
  },
];
```

## 6. Prettier 셋팅

- 코드 포맷터
- setting.json 확인

```json
 // 확장 규칙
      extends: [
        "eslint:recommended",
        "plugin:react/recommended",
        "plugin:react-hooks/recommended",
        "plugin:prettier/recommended",
      ],
      // prettier 경고는 에러가 아님.
      "prettier/prettier": "warn",
```

### 6.1. 설치

```
npm install --save-dev prettier eslint-config-prettier eslint-plugin-prettier
```

### 6.2. `.prettierrc` 파일 생성

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

## 7. ESLint 와 Prettier 통합 설정

- ESLint 에서 Prettier 도 처리필요

```js
import js from "@eslint/js";
import globals from "globals";
import react from "eslint-plugin-react";
import reactHooks from "eslint-plugin-react-hooks";
import reactRefresh from "eslint-plugin-react-refresh";
import prettier from "eslint-plugin-prettier";

export default [
  // dist 폴더는 검사 제외
  { ignores: ["dist"] },
  {
    // 검사할 파일 확장자
    files: ["**/*.{js,jsx}"],
    // 언어 옵션
    languageOptions: {
      ecmaVersion: "latest", // 최신 ECMAScript 문법 사용
      globals: globals.browser, // 브라우저 환경 글로벌 변수 사용
      parserOptions: {
        ecmaFeatures: { jsx: true }, // JSX 문법 활성화
        sourceType: "module", // ES 모듈 사용
      },
    },
    // React 버전 설정
    settings: { react: { version: "18.3" } },
    // 플러그인 설정
    plugins: {
      react, // React 관련 규칙 플러그인
      "react-hooks": reactHooks, // React Hooks 규칙 플러그인
      "react-refresh": reactRefresh, // React Refresh 규칙 플러그인
      prettier, // Prettier 플러그인
    },
    // 규칙 정의
    rules: {
      ...js.configs.recommended.rules, // 기본 JavaScript 권장 규칙
      ...react.configs.recommended.rules, // React 권장 규칙
      ...react.configs["jsx-runtime"].rules, // JSX Runtime 규칙
      ...reactHooks.configs.recommended.rules, // React Hooks 권장 규칙
      "react/jsx-no-target-blank": "off", // target="_blank" 관련 규칙 비활성화
      "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ], // React Fast Refresh 규칙
      "prettier/prettier": "warn", // Prettier 규칙 (포매팅 오류를 에러로 표시)
    },
  },
];
```
