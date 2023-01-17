---
title: Programmers 코딩테스트 (23)
tags: [Programmers, Coding Test, Lv2, 효율성테스트 에러]
style: fill
color: light
description: programmers LV2 - 최솟값 만들기(효율성 테스트 에러)
---

# 2023-01-12 TIL

<br/>
### • 올바른 괄호
<br/>
### **문제 설명**

---

괄호가 바르게 짝지어졌다는 것은 '(' 문자로 열렸으면 반드시 짝지어서 ')' 문자로 닫혀야 한다는 뜻입니다. 예를 들어

- "()()" 또는 "(())()" 는 올바른 괄호입니다.
- ")()(" 또는 "(()(" 는 올바르지 않은 괄호입니다.

'(' 또는 ')' 로만 이루어진 문자열 s가 주어졌을 때, 문자열 s가 올바른 괄호이면 true를 return 하고, 올바르지 않은 괄호이면 false를 return 하는 solution 함수를 완성해 주세요.

### 제한 조건

---

- 문자열 s의 길이 : 100,000 이하의 자연수
- 문자열 s는 '(' 또는 ')' 로만 이루어져 있습니다.

### 입출력 예

---

| s        | answer |
| -------- | ------ |
| "()()"   | true   |
| "(())()" | true   |
| ")()("   | false  |
| "(()("   | false  |

### 처음 풀이

---

아래와 같이 풀었을 경우 테스트는 전부 통과하지만, **효율성 검사에서 시간초과를 받게 되었다.**

- 알아본 바로는 매번 ‘()’ 가 있는지 확인하는 과정이 너무 많이 때문에 에러가 난 것으로 확인

```jsx
let sArr = s.split("");
let newArr = [];

for (let i = 0; i < sArr.length; i++) {
  if (sArr[i] == "(") {
    newArr.push(0);
  } else if (sArr[i] == ")") {
    newArr.push(1);
  }
}

let numStr = newArr.join("");
let strLeng = numStr.length;

for (let i = 0; i < strLeng; i++) {
  numStr = numStr.replace("01", "");
  i++;
}
if (numStr.length == 0) {
  answer = true;
} else {
  answer = false;
}
```

## 따라서 풀이 과정을 수정

‘()’을 매번 찾기 ⇒ String 각 인덱스를 순차적으로 확인

### 수정된 풀이

---

```jsx
function solution(s) {
  var answer = true;
  let strLeng = s.length;
  let count = 0;
  //만약 길이가 1이거나 )로 시작하면 바로 false 출력
  if (strLeng == 1 || s.startsWith(")")) {
    return (answer = false);
  }

  for (let i = 0; i < s.length; i++) {
    // (로 시작할 경우 count 1 증가
    if (s[i] == "(") {
      count++;
    } else {
      // 만약 카운트가 0 아래로 떨어지면 )가 더 많이 나왔다는 뜻
      // 따라서 false 출력
      if (count < 1) return false;
      count--;
    }
  }

  if (count == 0) {
    answer = true;
  } else {
    answer = false;
  }
  return answer;
}
```
