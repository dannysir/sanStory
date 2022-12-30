---
title: TIL Javascript (2)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 2일차 자료형
---

# 2022-09-13 TIL

## javascript

### NUMBER

---

python에서는 int, float으로 부동 소숫점을 표현하지만, javascript에서는 정수와 부동소숫점을 모두 NUMBER 데이터 타입으로 표현한다.

❉ typeof 를 사용해서 변수의 데이터타입을 표현한다.

> const SanE = 1;
> console.log(typeof SanE)

---

### Boolean

---

true 혹은 false 값을 가질 수 있음

> let SanE = 1 > 2;
> console.log(SanE);
> console.log(typeof SanE);

결과

> false
> boolean

---

### null & undefined

---

- null은 값이 없음을 나타내고 undefined는 값을 아직 할당하지 않았음을 나타낸다.
- null은 null 이라는 이름의 값 하나만 가질 수 있다. ( 모두 소문자로 정확하게 null )
- undefined 도 undefined 라는 값 하나만 가질 수 있다. ( 모두 소문자로 정확하게 undefined )

> let SanUndefined;
> console.log(SanUndefined, typeof SanUndefined);
> let SanNull = null;
> console.log(SanNull, typeof SanNull);

-결과-

> undefined undefined
> null null

---
