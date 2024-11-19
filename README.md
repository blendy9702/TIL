# Node.js

- 웹브라우저가 아닌 PC 에서 실행되는 자바스크립트
- 웹서버, 데이터베이스 연결, 웹서비스 개발 환경 구성등...

## 1. 설치

### 1.1. https://nodejs.org/en 설치하기 (개인 작업시)

### 1.2. NVM (node Version Manage)

- 여러개의 node.js 버전을 골라서 설치 가능.
- https://github.com/coreybutler/nvm-windows/releases
- nvm-setup.exe 다운로드 및 설치
- 설치 환경 확인
  : 터미널

```
  nvm -v
```

- node.js 내 PC에 목록 확인

```
  nvm ls
```

- node.js 전체 목록 확인

```
  nvm list available
```

- 원하는 LTS(안정화 버전) 버전 설치하기

```
  nvm install 20.18.0
  nvm install 20.12.0

  nvm ls
```

- 버전 삭제하기

```
nvm uninstall 20.12.0

nvm ls
```

- 버전 사용하기

```
  nvm use 20.18.0

  nvm ls
```

## 2. node.js 버전 확인하기

```
node -v
```

## 3.npm 버전 확인하기 (node package manage)

```
npm -v
```

## 4. js 프로젝트 구성

- 원하는 소스를 https://www.npmjs.com 에서 다운로드 및 설치. (추후)
- 수작업으로 기본 node.js 프로젝트를 생성해 보자.

### 4.1. Node.js 프로젝트 폴더 및 기본형 생성.

- `07-nodejs` 폴더 생성
- `cd 07-nodejs` 폴더 이동
- node.js 프로젝트 초기화
- `npm init`

### 4.2. Node.js 로 index.js 실행하기

- `index.js` 생성

```js
console.log("반가워 Node.js");
```

- `node index.js` 엔터
- `반가워 Node.js`
- 만약에 `index.js` 가 `src` 폴더에 배치되었다면
- `node src/index.js` 엔터

### 4.3. 매번 입력하기 어려우니 스크립트 명령을 써보자.

- `"dev": "node src/index.js"` 추가

```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "node src/index.js"
  },
```

## 5. 모듈 직접 만들어보자
- 모듈의 개념은 `파일 단위`로 `지역 스코프`를 가짐.
- ES6 모듈방식, commonJS 모듈방식, AMD 모듈방식, UMD 모듈방식
- 지금은 ES6 모듈 방식을 기본으로 쓰고있다.
- package,json 을 셋팅 안하면 commonJS 모듈이 자동으로 적용됨.

### 5.1. commonJS 이해.

```js
// 사용하려는 모듈을 불러들인다.
// 무조건 코드위치가 최상위에서 불러들인다.
const { say, smile } = require("./util.js");
// 너무 많은 기능이 있을 수 있으니 원하는 것만 골라서 사용.(관례)
// 객체 구조 분해 할당 문법을 이용.
// const aaa = require("./util.js") 안 좋은 케이스.
console.log("반가워 Node.js");
say();
lol : hi();
smile : smile();
```

### 5.2. ES6 모듈의 이해 (필수)
- 모듈은 `파일단위` `지역 스코프를` 가짐.
- Node,js를 직접 구성한다면 반드시 명시해야 한다.
- package.json 에 명시.

```json
type: "module"
```

```js
export function say() {
  console.log("안녕하세요 :D");
}
// default로 기본값을 설정했다.
export default function hi() {
  console.log("반가워요 :D");
}
export function smile() {
  console.log("웃어요 :)");
}
export function blame() {
  console.log("화나요 :(");
}
// ES6모듈 에서 외부에 함수를 오픈시킴
export { say, hi, smile };
```

```js
// 사용하려는 모듈을 불러들인다.
// 무조건 코드위치가 최상위에서 불러들인다.
import { say, smile } from "./util.js";
console.log("반가워 Node.js");
say();
// lol();
smile();
```

```js
import hi, { say, smile } from "./util.js";

say();
smile();
hi();
```
- 화살표 함수

```js
export const say = () => {
  console.log("안녕하세요 :D");
};
// hi를 변수로 먼저 선언하고 default로 export하거나, 이름 없는 함수로 export default를 사용해야 합니다.
const hi = () => {
  console.log("반가워요 :D");
};
export default hi;

export const smile = () => {
  console.log("웃어요 :)");
};

export const blame = () => {
  console.log("화나요 :()");
};

```

## 6. 모듈 직접 만들어보자
- 미리 만들어둔 모듈을 다운로드 받아서 활용(오픈소스)
- `프로젝트 폴더 구조 변화` 및 `package.json 변화`를 꼭 체크하자.
- 모듈 소스 관리는 `npm` 또는 `yarn` 으로 한다.
- `npm -v` 설치를 확인해야 함.

### 6.1. `npmjs.com` 에서 모듈 선택시 고려사항
- `TS` 지원, 다운로드 수, 업데이트 주기(2년 이상 미지원은 고민)

### 6.2. 모듈관련 명령어
- 모듈 설치
```
npm i 모듈명
```

-모듈 제거
```
npm uninstall 모듈명
```

- 모듈 초기 셋팅 : package-lock.json, node_modules 폴더 제거.

```
npm i
```
