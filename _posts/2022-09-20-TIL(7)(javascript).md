---
title: TIL Javascript (5)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 5일차 함수선언
---

# 2022-09-20 TIL

###

## 함수

---

기본문법

```jsx
function 함수이름(인자) {
  코드;
}
```

예시

```jsx
function SanE(name) {
  console.log("Hi" + name + "!");
}
SanE(dannysir);
```

### ES6 화살표 함수 ( Arrow function ) 선언

---

- 함수 선언은 보다 간편하게 하기 위해 고안된 문법
- 화살표 함수는 익명임
  - 따라서 익명 함수를 호출하기 위해 변수를 대입한다.

```jsx
let SanE = (name) => {
  console.log("Hi" + name + "!");
};
//위의 함수는 다음과 같다
let SanE = function (name) {
  console.log("Hi" + name + "!");
};
```

- 다음과 같은 세가지 단축 문법을 지원한다.
  - function 키워드 생략 가능
  - 함수 인자가 하나 뿐이면, 괄호() 생략 가능
  - 함수 코드가 한 라인이라면, 코드 블록 기호 및 return 키워드 생략 가능

예시1

```jsx
//기존 함수 선언
let exa1 = function () {
  return "Hello, World!";
};

//arrow function
let exa1 = () => "Hello, World!";
```

예시2

```jsx
let exa2 = function (sample) {
  return sample * 2;
};

//동일한 선언
let exa2 = (sample) => sample * 2;
```

예시3

```jsx
let exa3 = function (item1, item2) {
  return item1 * item2;
};

//동일한 선언
let exa3 = (item1, item2) => item1 * item2;
```

### 객체

---

- javascript 은 대부분의 기능은 내부적으로 객체로 다루어진다.
- javascript 객체는 프로퍼티와 메서드로 이루어질 수 있다고 이해하면 된다.
  - javascript 객체의 프로퍼티는 보통 프로퍼티 키(key) 와 프로퍼티 값(value) 로 이루어져 있다.
  - CSS 는 프로퍼티로 이루어져 있고 각 프로퍼티에 대응하는 프로퍼티 값으로 이러어져 있다.
  - HTML 은 속성과 속성 값을 가질 수 있다.

### javascript 객체 프로퍼티(property)와 메서드(method)

- 프로퍼티는 프로퍼티 키( key )와 프로퍼티 값( value )으로 구성된다.
- 프로퍼티 키는 보통 문자열 또는 심볼( Symbol ) 값으로 구성되고, 프로퍼티 값은 해당 키에 저장하고자 하는 데이터가 들어가 있다.
- 메서드는 일반 함수와 구분하여, 객체가 가지고 있는 함수를 말한다.
- javascript 객체 생성 방법
  - 객체 리터럴 방식
  - new Object() 로 생성하는 방식
  - 생성자 함수로 생성하는 방식

```jsx
const 객체이름 = {
	프로퍼티 키 : 프로프터 값
};
```

참고

- 객체이름 선언 시에는 보통 const를 사용한다.
- const 선언시 객체 이름은 다른 객체로 재할당되지 않음 (객체에 할당된 주소값이 변경될 수 없기 때문)
- 객체 주소값도 변경이 될 수 있다면 let 을 사용

예시

```jsx
const MainUser = {
  age: 26,
  name: "SanE",
};
```
