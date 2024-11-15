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
