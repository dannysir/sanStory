---
title: TIL Javascript (8)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 8일차 프로토타입과 클래스
---

# 2022-09-23 TIL

### 프로토타입

---

- 생성자 함수에 프로퍼티 또는 메서드 정의 가능
- ‘객체이름.prototype.프로퍼티명 = 코드’ 와 같이 사용 가능

```jsx
function User(age, name) {
  this.age = age;
  this.name = name;
}
User.prototype.mesage = function () {
  return "I'm SanE";
};
User.prototype.hobby = "baseketball";
const San = new User(26, "SeoSan");
console.log(San.hobby);
console.log(San);
```

### 클래스

---

- ES6에서 다른 언어의 객체 지향 문법과 유사한 class 키워드 기반 객체 생성 문법이 표준화됨
- 하지만, 지금까지도 javascript 개발자들은 객체 리터럴을 주로 사용하기도 함
  - javascrip 로 그렇게까지 복잡한 코드를 작성할 일이 없기도 하고, 기존 객체 리터럴 방식에 익숙한 개발자가 많음

클래스 정의

- class 클래스명{} 으로 클래스 정의 가능

```jsx
class User{
 ...
}
```

constructor(): 클래스 생성자 함수

- 클래스 내부에 constructor() 라는 이름으로 하나의 생성자 함수를 작성할 수 있다.

```jsx
class User {
	constructor() {
		...
	}
}
```

- class 로 정의된 클래스는 new 클래스명() 으로 객체로 생성될 수 있음
- 클래스 프로퍼티는 constructor 내부에서 this 키워드로 선언될 수도 있다.

```jsx
class User {
  constructor() {
    this.name = "SanE";
  }
}
const san = new User();
console.log(san);
```

- 객체 생성시 인자 정의는 constructor 에서 할 수 있음

```jsx
class User {
  constructor(name) {
    this.name = name;
  }
}
const san = new User("SanE");
console.log(san.name);
```

- 클래스 내부에서 메서드 생성 가능

```jsx
class User {
  constructor(name) {
    this.name = name;
  }
  get_message() {
    return "Hello";
  }
}
const san = new User("SanE");
console.log(san.get_message());
```

- 상속도 일반적인 객체지향 문법과 유사함
  - extends 를 사용해서, 상속할 클래스를 선언할 수 있다.
  - 자식 클래스에서는 super()(부모클래스의 constructor() 를 호출함 ) 을 constructor() 안에서 호출해야함

```jsx
class Animal {
  constructor() {
    this.name = name;
  }
}
class User extends Animal {
  consturctor(name, brand) {
    super(name);
    this.brand = brand;
  }
}
const san = new User("SanE", "jnu");
console.log(san);
```

- 객체지향의 다형성 또한 지원

```jsx
class Test1 {
  constructor(name) {
    this.name = name;
  }
  get_message() {
    return "Hello";
  }
}

class Test2 extends Test1 {
  constructor(name, brand) {
    super(name);
    this.brand = brand;
  }
  get_message() {
    return "Hello, World!";
  }
}
const san = new Test2("SanE", "JNU");
console.log(san.get_message());
```

### hasOwnProperty() 사용법

- 클래스명.property.프로퍼티 = 프로퍼티 값 으로도 클래스 외부에서 프로퍼티 값 추가 가능( 그래도 클래스 내부에서 선언하는 것을 권장 )
- 클래스 내부에서 선언한 프로퍼티임을 확인하기 위해 hasOwnProperty(프로퍼티명)을 사용

```jsx
class User {
  constructor(name) {
    this.name = name;
  }
  get_message() {
    return "Hello";
  }
}

User.prototype.age = 26;
const san = new User("SanE");
console.log(san.name);
console.log(san.OwnProperty.name);
console.log(san.OwnProperty.age);
```

- 결과

```jsx
SanE;
true;
false;
```
