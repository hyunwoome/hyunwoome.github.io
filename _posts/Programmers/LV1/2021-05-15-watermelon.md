---
title: Programmers - LV1. 수박수박수박수박수박수?
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12922)

## 접근하기

주어진 숫자가 "수박수박수박수...."와 같은 패턴을 유지할 때 일치하는 문자열을 반환한다.

<br>

## 내 코드

```js
function solution(n) {
  let answer = '';
  let one = '수';
  let two = '수박';
  if (n % 2 === 0) {
    let div = n / 2;
    answer += two.repeat(div);
  } else {
    let div = parseInt(n / 2);
    answer += two.repeat(div) + one;
  }
  return answer;
}
```

1. 주어진 숫자가 짝수라면, 해당 수를 2로 나눈 값만큼 `'수박'`을 반복한다.
2. 주어진 숫자가 홀수라면, 해당 수를 2로 나눈 값만큼 `'수박'`을 반복하고 마지막에 `'수'`를 더한다.
