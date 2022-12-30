---
title: Programmers 코딩테스트 (3)
tags: [Programmers, Coding Test]
style: fill
color: light
description: programmers - 핸드폰 번호 가리기 - 문제 풀이
---

# 2022-11-11 TIL

## programmers

### 핸드폰 번호 가리기

### 문제설명

---

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 `*`으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

### 제한사항

---

• phone_number는 길이 4 이상, 20이하인 문자열입니다.

### 입출력 예

---

| phone_number  | return           |
| ------------- | ---------------- |
| "01033334444" | "**\*\*\***4444" |
| "027778888"   | "**\***8888"     |

### 해결

---

```jsx
function solution(phone_number) {
  var answer = "";

  // 전화번호를 배열로 나눠준다.
  const numSplit = phone_number.split("");

  //전화번호 뒤 4자리는 *로
  for (let i = 0; i < numSplit.length - 4; i++) {
    numSplit[i] = "*";
  }
  // 배열로 만든것을 다시 String 으로
  const hideNum = numSplit.join("");
  answer = hideNum;
  return answer;
}
```
