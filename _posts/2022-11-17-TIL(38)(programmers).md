---
title: Programmers 코딩테스트 (3)
tags: [Programmers, Coding Test]
style: fill
color: light
description: programmers - 자연수 뒤집어 배열로 만들기 - 문제 풀이
---

# 2022-11-17 TIL

## programmers

### 자연수 뒤집어 배열로 만들기

### 문제설명

---

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

### 제한사항

---

• n은 10,000,000,000이하인 자연수입니다.

### 입출력 예

---

| n     | return      |
| ----- | ----------- |
| 12345 | [5,4,3,2,1] |

### 해결

---

```jsx
function solution(n) {
  var answer = [];
  const numToString = String(n); //숫자를 String타입으로 바꿔줌
  const numArr = numToString.split(""); // 배열로 나누어준다.
  const realArr = numArr.reverse(); // 배열을 거꾸로
  for (let i = 0; i < numArr.length; i++) {
    answer.push(parseInt(realArr[i])); // 하나씩 답에 Push
  }

  return answer;
}
```
