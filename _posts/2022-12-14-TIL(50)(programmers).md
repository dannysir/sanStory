---
title: Programmers 코딩테스트 (12)
tags: [Programmers, Coding Test]
style: fill
color: light
description: programmers - 음양 더하기 - 문제 풀이
---

# 2022-12-14 TIL

<br/>

### 음양 더하기

### **문제 설명**

---

- absolutes의 길이는 1 이상 1,000 이하입니다.
  - absolutes의 모든 수는 각각 1 이상 1,000 이하입니다.
- signs의 길이는 absolutes의 길이와 같습니다.
  - `signs[i]` 가 참이면 `absolutes[i]` 의 실제 정수가 양수임을, 그렇지 않으면 음수임을 의미합니다.

### 입출력 예

---

| absolutes | signs              | result |
| --------- | ------------------ | ------ |
| [4,7,12]  | [true,false,true]  | 9      |
| [1,2,3]   | [false,false,true] | 0      |

### 입출력 예 설명

---

**입출력 예 #1**

- signs가 `[true,false,true]` 이므로, 실제 수들의 값은 각각 4, -7, 12입니다.
- 따라서 세 수의 합인 9를 return 해야 합니다.

**입출력 예 #2**

- signs가 `[false,false,true]` 이므로, 실제 수들의 값은 각각 -1, -2, 3입니다.
- 따라서 세 수의 합인 0을 return 해야 합니다.

### 풀이

---

```jsx
function solution(absolutes, signs) {
  var answer = 123456789;
  let result = 0;
  for (let i = 0; i < signs.length; i++) {
    if (signs[i]) {
      result += absolutes[i];
    } else {
      result -= absolutes[i];
    }
  }
  answer = result;
  return answer;
}
```
