---
title: TIL Javascript (10)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 10일차 while문과 배열 CRUD
---

# 2022-09-27 TIL

### while 문

---

- 일반적인 프로그래밍 언어에서 지원하는 while 문도 지원한다.

```jsx
int i = 0;
while(i <6 ){
	console.log(i);
	i++;
}
```

### break 와 continue

---

- break : 반복문 안에서 더이상 반복문을 실행하지 말고 반복문 밖으로 빠져나오기
- continue : 현재 반복 코드에서 continue 다음 반복 코드를 수행하지 않고 다음 반복 횟수로 넘어 감

```jsx
for (let i = 0; i < 5; i++) {
  if (i === 3) {
    continue;
  }
  console.log(i);
}
```

```jsx
for (let i = 0; i < 5; i++) {
  if (i === 3) {
    break;
  }
  console.log(i);
}
```

## javascript 배열 CRUD

---

- 데이터 구조를 다루는 문법을 공부할 때 기본적으로 CRUD 문법을 익히면 된다.
  - C(create), R(read), U(update), D(delete)

### javascript 배열 생성 ( Create )

- [ ] 괄호를 사용하고 내부에서 아이템을 콤마 (,) 로 구분한다.
- 객체와 마찬가지로 새로운 배열로 배열 변수의 배열을 덮어버리는 경우는 적기 때문에 배열 선언시 const 로 선언을 한다.

```jsx
const SanArray = [1, 2, "SanE", 10];
console.log(SanArray);
```

- 배열 길이는 length 로 확인 가능

```jsx
const SanArray = [1, 2, "SanE", 10];
console.log(SanArray.length);
```

- 다른 언어와 달리 객체처럼 생성도 가능

```jsx
const SanArray = new Array();

SanArray[0] = 1;
SanArray[1] = 2;
SanArray[2] = "SanE";
console.log(SanArray);
```

### javascript 배열 읽기 ( Read )

- 0번부터 시작하는 인덱스 번호로 각 아이템을 읽을 수 있음

```jsx
const SanArray = [1, 2, "SanE", 10];
console.log(SanArray[2]);
console.log(SanArray[SanArray.length - 1]); //마지막 아이템
```

### javascript 배열 수정 ( Update )

- 인덱스 번호로 각 아이템을 수정 할 수 있다.

```jsx
const SanArray = [1, 2, "SanE", 10];
SanArray[1] = "JNU";
console.log(SanArray);
```

### javascript 배열 삭제 ( Delete )

- 배열변수 .splice(삭제를 시작할 인덱스 번호, 삭제를 시작할 인덱스부터 몇개를 지울지)

```jsx
const SanArray[1,2,"SanE", 10];
SanArray.splice(0,2);
console.log(SanArray);
```

- 결과

```jsx
["SanE", 10];
```

---
