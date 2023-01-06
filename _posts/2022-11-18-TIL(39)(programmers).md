---
title: Programmers 코딩테스트 (4)
tags: [Programmers, Coding Test]
style: fill
color: light
description: programmers - 콜라츠 추측 - 문제 풀이
---

# 2022-11-18 TIL

<br/>

### 나누어 떨어지는 숫자 배열

### 문제설명

---

array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.

divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.

### 제한사항

---

- arr은 자연수를 담은 배열입니다.
- 정수 i, j에 대해 i ≠ j 이면 arr[i] ≠ arr[j] 입니다.
- divisor는 자연수입니다.
- array는 길이 1 이상인 배열입니다.

### 입출력 예

---

| arr           | divisor | return        |
| ------------- | ------- | ------------- |
| [5, 9, 7, 10] | 5       | [5, 10]       |
| [2, 36, 1, 3] | 1       | [1, 2, 3, 36] |
| [3,2,6]       | 10      | [-1]          |

### 입출력 설명

---

입출력 예#1arr의 원소 중 5로 나누어 떨어지는 원소는 5와 10입니다. 따라서 [5, 10]을 리턴합니다.

입출력 예#2arr의 모든 원소는 1으로 나누어 떨어집니다. 원소를 오름차순으로 정렬해 [1, 2, 3, 36]을 리턴합니다.

입출력 예#33, 2, 6은 10으로 나누어 떨어지지 않습니다. 나누어 떨어지는 원소가 없으므로 [-1]을 리턴합니다.

### 해결

---

```jsx
function solution(arr, divisor) {
  var answer = [];
  //나누어 떨어지면 배열 answer 에 Push
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] % divisor == 0) {
      answer.push(arr[i]);
    }
  }
  //배열 answer가 비어있으면 -1을 push
  if (answer.length == 0) {
    answer.push(-1);
  }
  // 배열을 오름차순으로 해주기 위함
  // sort()만 쓰면 10,5 순서로 나옴 이것은 10의 앞에 있는 1이 5보다 작기 때문
  return answer.sort(function (a, b) {
    return a - b;
  });
}
```
