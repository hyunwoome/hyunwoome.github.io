---
title: Programmers - LV2. 멀쩡한 사각형
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/62048)

## 접근하기

숫자형 `w`와 `h`가 주어진다. `w`와 `h`는 너비와 높이를 나타내며, 해당 크기만큼 직사각형이 존재하고, 1칸당 1cm를 나타낸다. 한 칸식 잘라서 사용하려 했는데 대각선이 잘려있어서 잘린 부분을 제외한 멀쩡한 사각형의 개수를 반환한다.

<br>

## 참고 코드

```js
function solution(w, h) {
  function gcd(a, b) {
    const mod = a % b;
    if (mod === 0) {
      return b;
    }
    return gcd(b, mod);
  }
  const gcdValue = gcd(w, h);
  return w * h - (w + h - gcdValue);
}
```
