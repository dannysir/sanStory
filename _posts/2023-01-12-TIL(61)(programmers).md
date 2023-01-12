---
title: Programmers 코딩테스트 (22)
tags: [Programmers, Coding Test, Lv2]
style: fill
color: light
description: programmers LV2 - 최솟값 만들기 - 문제풀이
---

# 2023-01-12 TIL

<br/>
### • 최솟값 만들기
<br/>
### **문제 설명**

---

길이가 같은 배열 A, B 두개가 있습니다. 각 배열은 자연수로 이루어져 있습니다. 배열 A, B에서 각각 한 개의 숫자를 뽑아 두 수를 곱합니다. 이러한 과정을 배열의 길이만큼 반복하며, 두 수를 곱한 값을 누적하여 더합니다. 이때 최종적으로 누적된 값이 최소가 되도록 만드는 것이 목표입니다. (단, 각 배열에서 k번째 숫자를 뽑았다면 다음에 k번째 숫자는 다시 뽑을 수 없습니다.)

예를 들어 A = `[1, 4, 2]` , B = `[5, 4, 4]` 라면

- A에서 첫번째 숫자인 1, B에서 첫번째 숫자인 5를 뽑아 곱하여 더합니다. (누적된 값 : 0 + 5(1x5) = 5)
- A에서 두번째 숫자인 4, B에서 세번째 숫자인 4를 뽑아 곱하여 더합니다. (누적된 값 : 5 + 16(4x4) = 21)
- A에서 세번째 숫자인 2, B에서 두번째 숫자인 4를 뽑아 곱하여 더합니다. (누적된 값 : 21 + 8(2x4) = 29)

즉, 이 경우가 최소가 되므로 **29**를 return 합니다.

배열 A, B가 주어질 때 최종적으로 누적된 최솟값을 return 하는 solution 함수를 완성해 주세요.

### 제한 조건

---

- 배열 A, B의 크기 : 1,000 이하의 자연수
- 배열 A, B의 원소의 크기 : 1,000 이하의 자연수

### 입출력 예

---

| A         | B         | answer |
| --------- | --------- | ------ |
| [1, 4, 2] | [5, 4, 4] | 29     |
| [1,2]     | [3,4]     | 10     |

### 처음 풀이

---

```jsx
function solution(A, B) {
  var answer = 0;
  let aArr = A.sort((a, b) => b - a);
  let bArr = B.sort((a, b) => a - b);
  let sum = [];
  for (let i = 0; i < A.length; i++) {
    sum.push(a[i] * b[i]);
  }
  answer = sum.reduce((a, b) => a + b);
  return answer;
}
```

## reduce() 를 이용하면 for문이 필요 없을 수도 있다는 사실을 알게 됨

### 수정된 풀이

---

```jsx
function solution(A, B) {
  var answer = 0;
  let aArr = A.sort((a, b) => b - a);
  let bArr = B.sort((a, b) => a - b);
  //let sum = [];
  // for (let i = 0; i < A.length; i++){
  //     sum.push(a[i] * b[i]);
  // }

  //reduce() 에서 매개변수는 각각 다음과 같다
  // a는 누산기
  // b는 현재 값
  // c는 현재 인덱스 값
  //따라서 아래 식은 reduce()를 이용하여 바로 계산을 하여 값을 주고 있다.
  answer = aArr.reduce((a, b, c) => {
    return a + b * bArr[c];
  }, 0);
  return answer;
}
```
