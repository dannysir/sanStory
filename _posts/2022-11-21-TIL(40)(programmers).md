---
title: Programmers 코딩테스트 (5)
tags: [Programmers, Coding Test]
style: fill
color: light
description: programmers - 내적 - 문제 풀이
---

# 2022-11-21 TIL

입출력 예 #1

- a와 b의 내적은 `1*(-3) + 2*(-1) + 3*0 + 4*2 = 3` 입니다.

입출력 예 #2

- a와 b의 내적은 `(-1)*1 + 0*0 + 1*(-1) = -2` 입니다.

## programmers

### 내적

### 문제설명

---

길이가 같은 두 1차원 정수 배열 a, b가 매개변수로 주어집니다. a와 b의 [내적](https://en.wikipedia.org/wiki/Dot_product)을 return 하도록 solution 함수를 완성해주세요.

이때, a와 b의 내적은 `a[0]*b[0] + a[1]*b[1] + ... + a[n-1]*b[n-1]` 입니다. (n은 a, b의 길이)

### 제한사항

---

- a, b의 길이는 1 이상 1,000 이하입니다.
- a, b의 모든 수는 -1,000 이상 1,000 이하입니다.

### 입출력 예

---

| a         | b           | result |
| --------- | ----------- | ------ |
| [1,2,3,4] | [-3,-1,0,2] | 3      |
| [-1,0,1]  | [1,0,-1]    | -2     |

### 입출력 예 설명

---

입출력 예 #1

- a와 b의 내적은 `1*(-3) + 2*(-1) + 3*0 + 4*2 = 3` 입니다.

입출력 예 #2

- a와 b의 내적은 `(-1)*1 + 0*0 + 1*(-1) = -2` 입니다.

### 해결

---

```jsx
function solution(a, b) {
  let arr = [];
  let sum = 0;
  //a,b 배열이 같은 길이라는 것을 생각했을 때
  //a,b 의 길이가 다르다면 이중 for문으로
  for (let i = 0; i < a.length; i++) {
    //곱한 값을 arr 배열에 push
    arr.push(a[i] * b[i]);
  }

  for (let j = 0; j < arr.length; j++) {
    // 배열에 있는 값을 합한다.
    sum += arr[j];
  }
  return sum;
}
```
