# JavaScript 기초

## 1. 객체

- 우리는 `명칭을 약속` 해야한다.
- 다음 형식은 무조건 명칭을 지켜야 한다.
- 무조건 `객체리터럴` 이라고 읽어야 한다.

```js
const 객체 = {
  객체키명1: 객체키값1,
  객체키명2: 객체키값2,
};
```

- 만약 `1개의 객체`를 `생성하는 리터널`이라면 `카멜케이스`로 이름짓기.

```js
const person = {
  nickName: "홍길동",
  age: 15,
  member: false,
};
```

- 주의 할 것은 만약 `여러개의 객체`를 `생성하는 함수`라면 `파스칼케이스`로 이름짓기.
- `new 생성자함수` 공식명칭이 있다.

```js
function Person() {
  this.nickName = "홍길동";
  this.age = 15;
  this.memver = false;
}
```

- 응용 예제

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

//  어렵다..
function Student(_age, _member) {
  this.age = _age;
  this.member = _member;
  console.log(this);
}

Student(10, true);

const student_4 = new Student(12, false);
console.log(student_4);
```

### 1.2. 객체에 기능 추가 하기(메소드 라고 함.)

- `메소드 - method`, `행위 - behavior` 라고 합니다.

#### 1.2.1. 객체 `리터럴`

```js
const student_1 = {
  age: 15,
  member: true,
  say: function () {
    // student_1.say() 가 실행을 하게 됨
    console.log(this.age); // 15
  },
  cry: () => {
    //  화살표 함수라 this가 window의 member를 찾게 됨
    console.log(this.member);
  },
  hi() {
    // 메소드 축약형 이라 하는데 새로 추가된 문법.
    console.log(this);
  },
};

student_1.say();
student_1.cry();
student_1.hi();
```

#### 1.2.1. 객체 `객체의 인스턴스 생성자 함수`

```js
class Student {
  constructor(_age, _member) {
    this.age = _age;
    this.member = _member;
  }
  // 메소드 추가
  say() {}
  cry() {}
  hi() {}
}
// 용도를 잘못 생각하고 코딩을 하면 안됨.
// Student(10, true);

// 함수만 봐도 new 를 사용하려는 용도를 알 수 있음.
new Student(15, true);
```

## 2. 배열(Array)

- 데이터 종류와 상관없이 여러개를 `순서(인덱싱)` 대로 저장하는 데이터객체.

### 2.1. 배열 만드는 법

```js
// 아래를 주로 활용 (배열 리터럴 )
const 배열명 = [요소1, 요소2, 요소3 ...];

// 아래는 별로 쓸 일이 없다.
// 배열 객체 생성함수로 만들기.
const 배열명 = new Array(5); //[,,,,]

// 배열을 함수를 통해서 만들 수 있음.
const 새로운배열 = 기존배열.map();
```

### 2.2. 배열의 요소(각 인덱스 자리)의 값을 찾아 쓰는법

```js
const arr = [10, 20, "hello", function () {}, null, undefined, true];
console.log(arr[2]);
```

### 2.3. 배열도 객체라서 속성(프로퍼티)이 있음.

```js
const obj = {속성명: 속성값, 속성명: 기능};
const obj = {property명: property값, property명: method };
// 배열도 객체임
const arr = [];
arr.length 속성이 있어요 : 0 이라고 출력됨
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
// 커피 추가(원본 훼손)
// ['사과', '딸기', '과자', '햄버거', '커피']
```

- pop() : `끝` 요소 제거 및 제거된 요소 반환

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.pop("");
console.log(lunchArr);
// 햄버거 제거(원본 훼손)
// ['사과', '딸기', '과자',]
```

- unshift(); : `앞 첫번째` 요소 추가

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.unshift("커피");
console.log(lunchArr);
// 앞자리 커피 추가(원본 훼손)
// [커피', '사과', '딸기', '과자', '햄버거']
```

- shift() : `앞 첫번째` 요소 제거

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.shift("커피");
console.log(lunchArr);
// 앞자리 사과 제거 (원본 훼손)
// ['사과', '딸기', '과자', '햄버거']
```

- splice() : `원하는 인덱스` 부터 추가, 제거

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.splice(1, 2);
console.log(lunchArr);
// 1번으로 부터 2개를 제거 (원본 훼손)
// 0, 1, 2, 3 에서 1, 2를 제거 했다.
// ['사과', '햄버거']

// 1 번으로 부터 0개를 제거하고, "커피", "우유" 추가
// (원본 훼손)
lunchArr.splice(1, 0, "커피", "우유");
console.log(lunchArr);
// ['사과', '커피', '우유', '딸기', '과자', '햄버거']

// 1번으로 부터 2개를 제거하고, "도너츠", "콜라" 추가
// (원본 훼손)
lunchArr.splice(1, 2, "도너츠", "콜라");
console.log(lunchArr);
// [사과', '도너츠', '콜라', '딸기', '과자', '햄버거']

// 1본 포함 모두 다 제거
// (원본 훼손)
lunchArr.splice(1);
console.log(lunchArr);
// ['사과']
```

- sort() : 배열의 순서를 정렬하기

```js
const lunchArr = ["사과", "딸기", "과자", "햄버거"];
lunchArr.sort();
console.log(lunchArr);
// ["과자", "딸기", "사과", "햄버거"]
const enArr = ["k", "o", "r", "e", "a", "j", "p", "A"];
enArr.sort();
console.log(enArr);
// ['A', 'a', 'e', 'j', 'k', 'o', 'p', 'r']
const numArr = [1, 2, 12, 25, 37, 30];
numArr.sort();
console.log(numArr);
// 단순히 sort() 를 사용하면 앞 글자 기준으로 정렬됨.
// [1, 12, 2, 25, 30, 37]

// 내림 차순으로 정렬.
numArr.sort((a, b) => b - a);
console.log(numArr);
// [37, 30, 25, 12, 2, 1]

// 올림 차순으로 정렬.
numArr.sort((a, b) => a - b);
console.log(numArr);
// [1, 2, 12, 25, 30, 37]
```

- reverse() : `역순` 정렬

```js
const numArr = [1, 2, 12, 25, 37, 30];
numArr.reverse();
console.log(numArr);
// [30, 37, 25, 12, 2, 1]
```

- fill() : 요소에 값을 채운다.

```js
const numArr = [1, 2, 12, 25, 37, 30];
// numArr.fill(0);
console.log(numArr);
// [0, 0, 0, 0, 0, 0]

// 9를 3번자리 부터 5번 전까지 체우기.
numArr.fill(9, 3, 5);
console.log(numArr);
// [0, 0, 0, 9, 9, 0]
```

- flat() : `배열을 평탄화` 사용.
  : flet을 위한 별도의 라이브러리가 존재한다.
- react 에서 모듈을 설치해서 사용한다.

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

- `데이터 불면성(immutability)` 유지.

#### 2.5.1. map()

- map() : `매우매우 중요하다` 자주 활용함.
- 원본 배열의 요소에 동일한 함수 실행 후 새로운 배열로 생성

```js
const originArr = ["홍길동", "고길동", "김수한무"];
const copyArr = originArr.map(function (item, index, arr) {
  // console.log(`item : ${item}, index : ${index}, arr : ${arr}`);

  const tag = `<div class="user-info">${item}</div>`;
  console.log(tag);
  return tag;
});

console.log(`원본 originArr : ${originArr}`);
console.log(`원본 copyArr : ${copyArr}`);

const copyArrowArr = originArr.map(
  (item, index, arr) => `<a href="${index}">${item}</a>`
);
console.log(`복제본 copyArrowArr : ${copyArrowArr}`);
```

### 2.5.2. filter()

- 조건에 참인 것만 모아서 배열 리턴
- 자주 사용은 함.

```js
const memberHong = {
  age: 10,
  name: "홍길동",
  role: "guest",
};
const memberKim = {
  age: 18,
  name: "김수한무",
  role: "member",
};
const memberPark = {
  age: 25,
  name: "박둘리",
  role: "admin",
};

const originArr = [memberHong, memberKim, memberPark];

const result = originArr.filter((item, index) => {
  // return item.role === "admin";
  return item.age <= 20;
});

console.log(result);
```

### 2.5.3. slice()

- 배열의 일부를 복사함.

```js
const numArr = [1, 2, 3, 4];
// 시작 인덱스에서 도착 인덱스까지 출력
const nowArr = numArr.slice(1, 3);
console.log(numArr);
console.log(nowArr);
```
