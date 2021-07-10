---
title: Programmers - LV2. 피보나치 수
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12945)

## 접근하기

주어진 정수 `n`의 피보나치 수를 구할 때 마다 1234567로 나눈 나머지 값을 구한 값 중 n번째 수를 반환한다.

<br>

## 참고 코드

```js
function solution(n) {
  let answer = [];
  for (let i = 0; i <= n; i++) {
    if (i == 0) answer.push(0);
    if (i == 1) answer.push(1);
    if (i >= 2) {
      let sum = answer[i - 1] + answer[i - 2];
      answer.push(sum % 1234567);
    }
  }
  let result = answer[n];
  return result;
}
```

1. 주어진 정수 `n`까지 순회하면서 피보나치 수열을 `answer`에 담는다.
2. for문이 2이상부턴 구한 피보나치 수열에 `1234567`을 나눈 나머지를 삽입한다.
3. 그렇게 구한 피보나치 수열에서 `n`번째 수를 반환한다.
