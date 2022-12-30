---
title: TIL Javascript (1)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 1일차 변수 선언
---

### 기초내용

---

javascript에서는 주석을 달 때 한줄에서는 // 여러줄에서는

/\*

내용

\*/

이렇게 사용한다. 또한 자바스크립트는 코드 라인이 끝날 때마다 세미콜론(;)을 붙여줘야하며 console.log()를 통해 일반적인 print를 할 수 있다. (ex: console.log(”Hello, World!”)

---

### 변수 선언

---

> let 변수명;
> let 변수명 = 변수값;

let으로 선언한 변수는 나중에 다른 변수값을 넣을 수 있다

> let SanE;
> SanE = 2;
> console.log(SanE);
> SanE = 10;
> console.log(SanE);

result

> 2
> 10

let으로 선언한 변수는 다시 선언을 할 수 없다.

> let SanE = 1;
> let SanE = 10;
> //에러 발생

---

### 상수선언

---

- 파이썬과 달리 특정 상수를 저장하는 변수를 선언할 수 있다.
- 한번 상수로 선언된 변수에는 새로운 값을 넣을 수 있다.
- 선언할 때 특정 상수값까지 넣어서 선언해야한다.

> const SanE = 2;
> const SanE = ‘학생’
> const SanE = ‘ ‘ //null 값을 넣을 수도 있다

- 선언할 때 특정 값을 넣지 않으면 에러가 발생

> const SanE;
> //에러발생

---

### 데이터타입

---

- Number
- String
- Boolean
- null
- undefined
- object
- Symbol
