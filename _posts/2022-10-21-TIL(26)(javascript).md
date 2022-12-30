---
title: TIL Javascript (21)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 21일차 chaining 과 catch
---

# 2022-10-21 TIL

### chaining 과 catch

---

- 일반적으로는 catch 를 chaining 맨 마지막에 추가해서, 전체 코드의 에러 케이스를 간결히 핸들링

```jsx
const promise = new Promise((resolve, reject) = >){
	console.log("start");
	resolve(1);
});

promise
	.then((num) => {
		console.log("success1");
	})
	.then((num) => {
		console.log("success2");
		throw new Error("error");
	})
	.then((num) => {
		console.log("success3");
	})
	.catch((err) => {
		console.log("error");
	});
```

### chaining 과 return

---

```jsx
// Promise 객체 생성
const promise = new Promise((resolve, reject) => {
  // 비동기 작업 수행
  setTimeout(() => {
    let num = 10;
    if (num >= 9) {
      /* 비동기 작업 성공 */
      resolve(num);
    } else {
      /* 비동기 작업 실패 */
      reject("this is an error");
    }
  }, 500);
});

promise
  .then((num) => {
    console.log("success1", num);
    return 2; /* return 값이 다음 then 의 인자로 넘겨짐 */
  })
  .then((num) => {
    console.log("success2", num);
  });
```

### finally

---

finally() 는 Promise 가 resolve 되든 reject 되든 마지막에 해당 함수를 실행함

```jsx
// Promise 객체 생성
const promise = new Promise((resolve, reject) => {
  // 비동기 작업 수행
  setTimeout(() => {
    let num = 10;
    if (num >= 9) {
      /* 비동기 작업 성공 */
      resolve(num);
    } else {
      /* 비동기 작업 실패 */
      reject("this is an error");
    }
  }, 500);
});

promise
  .then((num) => {
    console.log("success1", num);
    return 2; /* return 값이 다음 then 의 인자로 넘겨짐 */
  })
  .then((num) => {
    console.log("success2", num);
  })
  .finally(() => {
    console.log("finally");
  });
```

### promise.all

---

- 동기화 처리할 Promise 를 묶어서 한번에 실행
- 즉 여러 함수가 다 실행이 완료된 후에, then 구문을 실행함

```jsx
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("100ms"), 100);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("500ms"), 500);
});

Promise.all([promise1, promise2]).then((data) => {
  console.log(data);
});
```

### Promise.race

---

- 여러 함수 중, 제일 빠르게 실행완료된 함수만 then 구문을 실행함

```jsx
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("100ms"), 100);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("500ms"), 500);
});

Promise.race([promise1, promise2]).then((data) => {
  console.log(data);
});
```
