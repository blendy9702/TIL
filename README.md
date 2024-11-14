# javaScript 기초

## 1. 함수

### 1.1. 함수를 만들 시점

#### 1.1.1. 코드가 너무 긴 경우(한개의 결과를 만들기 위해서)

- 코드 가독성이 너무 떨어진다고 판단시
- 하나의 과정을 작성하기 위해서 너무 많은 코드가 작성된 경우
- 여러 줄이 작성되어 한개의 결과를 만든다면 함수로 묶어줄 고민

#### 1.1.2. 동일한 기능이 여러번 사용될 때

- 두번이상 동일한 기능이라면 함수를 만들까?
- 두번이상 동일한 기능인데 재료만 다르다? 그러면 함수만들까?

#### 1.1.3. 코드를 누군가에게 주어야 한다면

- 코드를 공유할 때 함수를 만들까?

### 1.2. 함수를 만드는 방법.

- {} 즉, 코드블럭을 이용해서 코드를 묶어준다.
- 이름을 지어준다. 이때 이름은 `동사`로 정한다.
- 이름 뒤에 `()` 를 붙인다.
- JS를 위해서 `function` 이라고 적는다.
- 재료가 필요하면 `(매개 변수, 매개 변수)` 로 전달한다.
- 재료가 필요하면 `(파라메터, 파라메터)` 로 전달한다.
- 재료가 필요하면 `(parameter, parameter)` 로 전달한다.
- 함수를 만들때는 `JS Doc` 을 작성해주는 센스 (아주 고평가)

### 1.3. 함수 사용법

- 함수명() <=== 이것을 호출, 실행, call 한다 라고 함.

### 1.4. 샘플코드

````js
// 너비와 높이를 이용해서 면적 계산하기

/**
 *너비 높이 값을 이용한 면적 계산 함수
 *@param {number} _width
 *@param {number} _height
 *@returns {number}
 *--- 함수 사용 예제 ---
 *```javascript
 *clacRect(100, 30)
 *```
 */

function calcRect(_width, _height) {
  const width = _width;
  const height = _height;
  const result = width * height;
  // 함수 실행 결과를 돌려준다.
  // return 함수 종료
  return result;
}

const now = calcRect(400, 50);
console.log(now);
````

## 2. 화살표 함수 (Arrow Function)

### 2.1. 화살표 함수가 필요한 이유

- 함수가 간략화 됨.
- 함수가 최적화 즉, arguments 를 사용할 수 없도록 최적화 됨. (메모리 절약, 성능 최적화)
- this 의 값 고정 (그때 그때 다르지 않고 늘 한결같이 같다.)
- new 를 사용 못함

### 2.2. 화살표 함수 만들기

- 화살표 함수는 상수 만들듯이 생성한다.
- const 를 활용한다.
- 이름을 `동사`로 만든다.
- `값으로 함수`를 작성한다.
- 함수는 `익명함수`로 한다.
- function 을 없애소 화살표( => )로 표현한다.

### 2.3. 화살표 함수 사용하기

- `이름();` 실행됨.
- 주의 사항은 `호이스팅이 안된다`.

### 2.4. 여러가지 화살표 함수의 예

```js
// 파라메터가 없는 경우는 ()를 반드시 입력.
function say() {
  console.log("안녕");
}
const sayArrow = () => {
  console.log("안녕");
};
// 파라메터가 한개 있는 경우 () 생략 가능
function sayWord(word) {
  console.log(word);
}
const sayWordArrow = (word) => {
  console.log(word);
};
// 파라메터가 두개 이상인 경우 () 를 필수로 입력.
function sayWordText(word, text) {
  console.log(word, text);
}
const sayWordTextArrow = (word, text) => {
  console.log(word, text);
};

// 파라메터가 없고 함수 결과를 리턴하지 않는 경우
function noReturn() {}
const noReturnArrow = () => {};
// 파라메터가 없고 함수 결과를 리턴하는 경우
function yesReturn() {
  return 1;
}
// return 코드에 딱 1줄 코딩 작성됨.
const yesReturnArrow = () => {
  return 1;
};
// return 코드에 딱 1줄 코딩 작성됨. 중괄호 생략 가능
const yesReturnArrowOne = () => 1;

// return 샘플 코드 1줄 짜리 예제

const isLogin = true; // 로그인 상태를 저장함.

// if 문 여러 줄 코드 (중괄호 생략 불가, 4줄이라서)
const userLogin = () => {
  if (isLogin === true) {
    return "로그인";
  } else {
    return "로그아웃";
  }
};

// 3항 연산자 (중괄호 생략 가능, 1줄이라서, return 도 있어서.)
const userLoginArrow = () => {
  return isLogin ? "로그인" : "로그아웃";
};

const userLoginArrowReturn = () => (isLogin ? "로그인" : "로그아웃");

// 3배를 계산한다.
const num = 1;
const countThriple = (_num) => _num * 3;
console.log(countThriple(_num));

// 다음은 정말 조심해야 함.
// 파라메터가 {} 형태라면 반드시 () 필수로 감싸줘야 한다.
const parseJsonArrow = ({}) => {
  console.log("실행");
};
```

## 3. 변수 및 함수의 접근가능 유효 범위 ( Scope )

- 제일 중요한 것이 `{}` 코드 블럭의 이해

### 3.1. Scope 의 종류

- 전체 영역 : 전역 스코프(global scope)
- 특정 영역 : 지역 스코프(local scope)

```js
// 전역변수
const appName = "Todo";
// 지역변수 영역 {}
{
  console.log(appName);
}
// 함수 지역 범우;{}
function showAppName() {
  console.log("함수 안 지역: ", appName);
}

showAppName();
```

### 3.2. 전역 스코프

- 프로그램 어디서든 마음대로 사용하세요.
  변수 든, 함수 든 마음대로 사용하세요.
- 전역 함수의 예

```js
// 전역 함수
function say() {
  console.log("안녕");
}
const sayArrow = () => {
  console.log("반가워");
};

say();
sayArrow();

{
  say();
  sayArrow();
}

function showHi() {
  say();
  sayArrow();
}

showHi();
```

### 3.3. 지역 스코프

- `특정 {}` 안에서만 사용한다.

```js
// 지역 scope 생성
{
  const age = 10;
}

console.log(age);
// 지역 함수 scope 생성
{
  // 호이스팅 됩니다.
  function hi() {
    console.log("안녕 백엔드?");
  }
}

hi();

// 지역 scope 화살표 함수
{
  const go = () => {
    console.log("가자");
  };
}
// 접근 오류
go();
```

- function 함수() { `지역 스코프` }

```js
// 함수 안에 만들어진 함수의 scope 의 고민

function 외부함수() {
  function 내부함수() {
    console.log("내부함수");
  }
  function 화살표함수() {
    console.log("화살표함수");
  }
  내부함수();
  화살표함수();
}
외부함수(); // 정상

내부함수(); // 오류
화살표함수(); // 오류
```

### 3.4. this 요놈.. 오류의 원인이 될 수 있다.

- 글로벌 스코프의 this 는 window

```js
console.log("글로벌 this : ", this); // window
```

- 화살표 함수 안쪽의 this 는 window 가 아닐 수 있다.

- 일반 함수 안쪽의 this 는 window 가 아닐 수 있다.
