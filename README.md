# javaScript 기초

## 1. 객체

### 1.1. 가장 간단한 객체 만드는 법

- 우리는 `명칭을 약속`합니다.
- 무조건 `객체리터럴` 이라고 읽어야 합니다.
- 다음 형식은 무조건 명칭을 지켜주세요.

```js
const 객체 = {
  객체키명1: 객체키값1,
  객체키명2: 객체키값2,
};
```

- 만약 `1 개의 객체`를 `생성하는 리터럴`이라면 `카멜케이스`로 이름짓기

```js
const person = {
  nickName: "홍길동",
  age: 15,
  member: false,
};
```

- 주의 할 것은 만약 `여러 개의 객체`를 `생성하는 함수`라면 `파스칼케이스`로 이름짓기
- `new 생성자함수` 공식명칭이 있다.

```js
function Person() {
  this.nickName = "홍길동";
  this.age = 15;
  this.member = false;
}
```

- 응용 예

```js
const student_1 = {
  age: 20,
  member: false,
};
student_1.age;
student_1.member;

const student_2 = {
  age: 30,
  member: true,
};
student_2.age;
student_2.member;

const student_3 = {
  age: 10,
  member: false,
};
student_3.age;
student_3.member;

// 참 힘들어요. ㅠㅠ;
function Student(_age, _member) {
  this.age = _age;
  this.member = _member;
  console.log(this);
}

const gogo = Student(10, true);
//console.log(gogo);

const student_4 = new Student(12, false);
console.log(student_4);
```

### 1.2. 객체에 기능 추가하기

- `메소드 - method`, `행위 - behavior` 라고 합니다.

#### 1.2.1. 객체 `리터럴`

```js
const student_1 = {
  age: 15,
  member: true,
  say: function () {
    // 누가 실행했니 통과
    // student_1 가 실행함 say();
    console.log(this.age); // 15
  },
  cry: () => {
    // this는 window의 member 를 찾음
    // 화살표 함수라서.
    console.log(this.member); // undefined
  },
  hi() {
    // 왜 정상이지? 메소드 축약형, 추가된 새로운 문법
    // 정상적으로 실행
    console.log(this);
  },
};
student_1.say();
student_1.cry();
student_1.hi();
```

#### 1.2.2. `객체의 인스턴스 생성자 함수`

```js
function Student(_age, _member) {
  this.age = _age;
  this.member = _member;
  // 메소드 추가
  this.say = function () {};
  this.cry = () => {};
  this.hi = () => {};
}
// 아래처럼 하면 안되요. 용도를 잘못 생각하고 코딩한것
// Student(10, true);

// 함수만 보아도 new 를 사용하려는 용도임을 앎.
new Student(15, true);
```

## 2. 배열(Array)

- 데이터 종류와 상관없이 여러개를 `순서(인덱싱)` 대로 저장하는 데이터객체

### 2.1. 배열 만드는 법

```js
// 아래를 주로 활용(배열 리터럴)
 const 배열명 = [요소1, 요소2, 요소3, ...];

 // 아래는 제 경험상 쓸일이 없어던 같아요.
 // 배열 객체 생성함수로 만들기
 const 배열명 = new Array(5); // [,,,,]

 // 배열을 함수를 통해서 만들 수 있음.
 const 새로운배열 = 기존배열.map();

```

### 2.2. 배열에 요소(각 인덱스 자리)의 값을 찾아서 사용하는 법

```js
const arr = [10, 20, "hello", function () {}, null, undefined, true];
consle.log(arr[2]);
```

### 2.3. 배열도 객체라서 속성(프로퍼티)이 있어요.

```js
const obj = { 속성명: 속성값, 속성명: 기능 };
const obj = { property명: property값, property명: method };
// 배열도 객체라서
const arr = [];
arr.length 속성이 있어요. : 0 이라고 출력됨.
```

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
const total = lunchArr.length;
console.log(total);
for (let i = 0; i < total; i++) {
  console.log(`${i} 번째의 요소는 ${lunchArr[i]}`);
}
```

### 2.4. 배열을 다루는 함수에서 원본을 훼손하는 배열함수

- push() : 배열 `끝`에 추가

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.push("커피");
console.log(lunchArr);
// 커피 추가 (원본 훼손)
// [  "사과",  "딸기",  "과자",  "햄버거",  "커피"]
```

- pop() : `끝` 요소 제거 및 제거된 요소 반환

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.pop();
console.log(lunchArr);
// 햄버거 제거 (원본 훼손)
// [  "사과",  "딸기",  "과자"]
```

- unshift() : `앞` 요소 추가

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.unshift("커피");
console.log(lunchArr);
// 햄버거 앞자리 추가 (원본 훼손)
// ["커피", "사과",  "딸기",  "과자", "햄버거"]
```

- shift() : `앞 첫번째` 요소 제거

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.shift();
console.log(lunchArr);
// 햄버거 앞자리 제거 (원본 훼손)
// ["딸기",  "과자", "햄버거"]
```

- splice() : `원하는 인덱스` 부터 추가, 제거

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.splice(1, 2);
console.log(lunchArr);
// 인덱스로 부터 개수만큼 제거 (원본 훼손)
// ["사과", "햄버거"]
```

- sort() : 배열의 순서를 정렬하기

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.sort();
console.log(lunchArr);
// ['과자', '딸기', '사과', '햄버거']
const enArr = ["k", "o", "r", "e", "A", "j", "p", "a", "n"];

// 원본훼손
enArr.sort();
console.log(enArr);
// ['A', 'a', 'e', 'j', 'k', 'n', 'o', 'p', 'r']
const numArr = [1, 2, 12, 25, 37, 30];
// 원본훼손
numArr.sort();
console.log(numArr);
// 단순히 sort() 를 사용하면 앞 글자를 기준으로 정렬됨.
// [1, 12, 2, 25, 30, 37]

// 내림 차순으로 정렬해 보자.
// numArr.sort((a, b) => b - a);
// [37, 30, 25, 12, 2, 1]

// 올림 차순
numArr.sort((a, b) => a - b);
console.log(numArr);
// [1, 2, 12, 25, 30, 37]
```

- reverse() : `역순` 순서를 뒤집어 저장

```js
const numArr = [1, 2, 12, 25, 37, 30];
// 원본 훼손
numArr.reverse();
console.log(numArr);
// [30, 37, 25, 12, 2, 1]
```

- fill() : 요소에 값을 채운다.

```js
const numArr = [1, 2, 12, 25, 37, 30];
// 원본 훼손
// numArr.fill(0);
console.log(numArr);
// [0, 0, 0, 0, 0, 0]
// 값 1 을 채워라
// 인덱스 3번으로 부터
// 인덱스 5번 전까지
numArr.fill(1, 3, 5);
console.log(numArr);
// [1, 2, 12, 1, 1, 30]
```

- flat() : `배열을 평탄화` 사용합니다.
  : flat 을 위한 별도의 라이브러가 존재합니다.
  : react 에서 모듈을 설치해서 사용합니다.

```js
const numArr = [1, 2, 3, ["a", "b", "c"], 8, 9];
// flat(배열의 단계)
const result = numArr.flat(1);
console.log(result);
// [1, 2, 3, 'a', 'b', 'c', 8, 9]
const num2Arr = [1, 2, [3, [4, [5, 6]]], 100];
const result2 = num2Arr.flat(1);
console.log(result2);
// [1, 2, 3, Array(2), 100]
const result3 = result2.flat(1);
console.log(result3);
// [1, 2, 3, 4, Array(2), 100]
const result4 = result3.flat(1);
console.log(result4);
// [1, 2, 3, 4, 5, 6, 100]
```

### 2.5. 배열을 다루는 함수에서 원본을 훼손하지 않고 `새로운 배열을 만들어 주는 함수`

- `데이터 불변성(immutability)` 유지하셨나요?

### 2.5.1. map()

- `star가 1000만개` 가치가 있고, 자주활용
- 원본 배열의 요소에 동일한 함수 실행 후 새로운 배열로 생성

```js
const originArr = ["홍길동", "고길동", "김수한무"];
const copyArr = originArr.map(function (item, index, arr) {
  // console.log(`item : ${item}, index: ${index}`);
  const tag = `<div class="user-info">${item}</div>`;
  console.log(tag);
  // 리턴해야 배열이 담깁니다.
  return tag;
});
console.log(`원본 originArr : ${originArr}`);
console.log(`복제본 copyArr : ${copyArr}`);

const copyArrowArr = originArr.map((item, index) => {
  return `<a href="${index}">${item}</a>`;
});
console.log(`복제본 copyArrowArr : ${copyArrowArr}`);
```

### 2.5.2. filter()

- 조건에 참인 것만 모아서 배열 리턴
- 자주 사용은 합니다.

```js
const memberHong = {
  age: 10,
  name: "홍길동",
  role: "GUEST",
};
const memberKim = {
  age: 18,
  name: "김수한무",
  role: "MEMBER",
};
const memberPark = {
  age: 25,
  name: "박둘리",
  role: "ADMIN",
};

const originArr = [memberHong, memberKim, memberPark];

const result = originArr.filter((item, index) => {
  // return item.role === "ADMIN";
  return item.age <= 20;
});
console.log(result);
```

### 2.5.3. slice()

- 배열의 일부를 복사한다.

```js
const numArr = [1, "a", "b", 4];
// 시작 인덱스로 부터 도착 인덱스 미만 요소 출력
const nowArr = numArr.slice(1, 3);
console.log(numArr);
console.log(nowArr); //  ['a', 'b']
```

### 2.5.4. concat();

- 배열을 `합쳐서` 하나의 배열을 리턴.

```js
const numArr1 = [1, "a", "b", 4];
const numArr2 = [8, 100];
const result = numArr1.concat(numArr2);
console.log(result);
// [1, 'a', 'b', 4, 8, 100]
```

### 2.5.5. reduce();

- 배열의 요소를 탐색하면서 누적 연산함.
- 누적된 결과를 출력함.

```js
const numArr1 = [1, 2, 3, 4];
// 문법이 좀 다릅니다.
// 보통은 ===>  (item, index, arr)
// const total = numArr1.reduce(함수, 초기값)
const total = numArr1.reduce((acc, cur) => {
  console.log("acc : ", acc);
  console.log("cur : ", cur);
  return acc + cur;
}, 0);

console.log("total : ", total);
```

### 2.5.6. join();

- 문자열로 배열을 연결한 결과를 만든다.

```js
const numArr1 = [1, 2, 3, 4];
// 기본은 ,  연결된 글자
const result = numArr1.join("#");
// 결과는 string
console.log(`typeof ${typeof result} , ${result}`);
// typeof string , 1#2#3#4
```

### 2.5.7. indexOf();

- 찾는 요소가 몇번째 인덱스 인지를 파악

```js
const numArr1 = [1, 2, 3, 4];
// 기본은 ,  연결된 글자
const result = numArr1.indexOf(3);
console.log(`typeof ${typeof result} , ${result}`);
// typeof number , 인덱스 2
```

### 2.5.8. includes();

- 요소가 포함되었는지 아닌지

```js
const numArr1 = [1, 2, 3, 4];
// 기본은 ,  연결된 글자
const result = numArr1.includes(3);
console.log(`typeof ${typeof result} , ${result}`);
// typeof boolean , true
```

## 3. 객체 즉 {} 와 배열 [] 에 필수 이해

### 3.1. 반복문

- 배열 : map, forEach, for, for of, for in (???)

```js
const numArr = [1, 2, 3, 4];

// 배열에서 요소에 접근하는 전통적 방식
console.log("for 구문");
for (let i = 0; i < numArr.length; i++) {
  console.log(numArr[i]);
}

console.log("forEach 구문");
// 다음 버전
// numArr.forEach((item, index, arr) => { })
numArr.forEach((item) => {
  console.log(item);
});

console.log("for of 구문");
// 최신 (for  of 문)
for (const item of numArr) {
  console.log(item);
}

numArr.map((item) => {
  console.log(item);
});

console.log("for  in 구문 참조용, 실전에서는 고민해보자.");
const strArr = ["a", "b", "c"];
for (const item in strArr) {
  console.log(strArr[item]);
}
```

- 객체 : for in 추천

```js
const person = {
  age: 10,
  nickName: "hong",
  isMember: false,
};
person.hi = "반가워";

// for in 객체 속성 반복 구문
for (item in person) {
  console.log(item); // 속성명
  console.log(person[item]); // 속성값
}

console.log("Object.vlaues ==== ");
// 나는 값만 출력하고 싶다. (추천하지 않습니다만...)
Object.values(person).forEach((key) => {
  console.log(key);
});

console.log("Object.keys ==== ");
// 나는 이름만 출력하고 싶다. (추천하지 않습니다만...)
Object.keys(person).forEach((key) => {
  console.log(key);
});

console.log("Object.entries ==== ");
// 나는 이름과 값을 출력하고 싶다. (추천하지 않습니다만...)
Object.entries(person).forEach(([key, value]) => {
  console.log(key, value);
});
```

- 정리

```
  배열 : for, forEach, map
  객체 : for in
```

### 3.2. 값 추출하여 보관

- 배열

```js
const arr = ["사과", "딸기", "바나나"];

// 아래의 문장들을 잘 사용하지 않습니다.
//const apple = arr[0];
//const straw = arr[1];
//const banana = arr[2];

// Spread 문법 ... 작성 필요
const [apple, straw, banana] = [...arr];
console.log(apple, straw, banana);

// Spread 문법으로 배열 합치기
const newArrOld = ["감자", arr[0], arr[1], arr[2], "고구마", "상추"];
const newArr = ["감자", ...arr, "고구마", "상추"];
console.log(newArr);

// Rest 파라메터 문법
function go(a, b, ...rest) {
  // a 는 1
  // b 는 2,
  // rest ===> [3,4,5,6,7]
}

go(1, 2, 3, 4, 5, 6, 7);
```

- 객체

```js
const person = {
  age: 10,
  nickName: "홍길동",
  level: 5,
};

// const a = person.age;
// const b = person.nickName;

// 객체의 구조를 분해해서 할당한다.
// 객체 구조 분해 할당
const { age, nickName, level } = person;
```
