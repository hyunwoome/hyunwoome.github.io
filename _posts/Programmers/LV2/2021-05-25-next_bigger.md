---
title: LV2. 다음 큰 숫자
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12911)

## 접근하기

정수 `n`이 주어진다. `n`의 다음 큰 숫자를 반환하는데, `n`보다 커야하고, `n`의 비트개수와 같아야 하며, 두 조건을 모두 만족하면서 가장 작은 수를 반환한다.

<br>

## 참고 코드

```js
function solution(n) {
  function countBit(num) {
    let answer = 0;
    let binary = num.toString(2);
    for (let i = 0; i < binary.length; i++) {
      if (binary[i] === '1') answer++;
    }
    return answer;
  }

  for (let i = n + 1; i < 1000000; i++) {
    let bits = countBit(n);
    if (bits === countBit(i)) return i;
  }
}
```

1. 먼저 정수를 2진수로 변환후 1의 개수, 즉 비트 수를 반환하는 함수 `countBit`를 정의했다.
2. `n` 이상 순회하면서, `n`의 비트수와 같은 숫자를 찾아내 반환한다.
