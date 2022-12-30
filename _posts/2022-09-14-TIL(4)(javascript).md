---
title: TIL Javascript (3)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 3일차 자료형과 연산자
---

# 2022-09-14 TIL

### 데이터타입 변환

---

- Number()

=Number 타입으로 변환을 해준다.

> console.log(typeof Number(”1”) , Number(”1”);

-결과

> Number 1

- parseInt

=Number 타입으로 변환하되 정수형으로 변환한다.

> console.log( typeof parseInt(”2.2”), parseInt(”2.2”);

-결과

> Number 2

- parseFloat

= 부동소숫점까지 그대로 변환

> console.log( typeof parseFloat(”2.2”), parseFloat(”2.2”);

-결과

> Number 2.2

- String()

=String 타입으로 변환

> console.log( typeof String(”0”), String(”0”);

-결과

> String 0

- Boolean()

=Boolean 타입으로 변환

> console.log( typeof Boolean(”0”), Boolean(”0”);

-결과

> boolean true

---

### 동등 연산자 ( == )와 일치 연산자 ( ===)

---

- 동등 연산자 ( == , != ) : 관대한 연산자로 기본적으로 값만 같은지를 확인한다.
- 일치 연산자 ( ===, !== ) : 엄격한 연산자로 값과 데이터 타입 모두 같은지 확인한다.

---

### 주요 연산자

---

- - : 덧셈
- - : 뺄셈
- - : 곱셈
- / : 나눗셈

### ++연산자

변수++ : 변수에서 먼저 값을 꺼내고 1을 더함

++변수 : 변수에 1을 더한 값을 꺼냄

> let SanE = 1;
> console.log(SanE++ === 2);
> console.log(++SanE ===3);

결과

> false
> true

### 대입 연산자

- =으로 데이터를 변수에 대입할 수 있음

> let SanE = 1;
> console.log(SanE);
> SanE += 10;
> console.log(SanE);

결과

> 1
> 11

### 논리 연산자

- ! : NOT
- && : AND
- || : OR
- 예제
