---
title: LV1. 약수의 합
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12928)

## 접근하기

주어진 수의 약수를 모두 더한 값을 반환한다.

<br>

## 내 코드

```js
function solution(n) {
  let sum = 0;
  for (let i = 1; i <= n; i++) {
    if (n % i === 0) sum += i;
  }
  return sum;
}
```

1. 1부터 주어진 수 까지 순회하면서 각 인덱스로 나눠떨어지면 그 인덱스를 더한 값을 반환한다.
