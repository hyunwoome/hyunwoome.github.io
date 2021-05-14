---
title: LV1. 핸드폰 번호 가리기
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12948)

## 접근하기

주어진 문자열에서 뒤 네자리를 뺀 나머지는 \*로 반환하고, 나머지 네자리는 주어진 문자열을 반환한다.

<br>

## 내 코드

```js
function solution(phone_number) {
  var answer = '';
  for (let i = 0; i < phone_number.length - 4; i++) {
    answer += '*';
  }
  for (let i = phone_number.length - 4; i < phone_number.length; i++) {
    answer += phone_number[i];
  }
  return answer;
}
```

1. 첫 for문은 주어진 숫자의 길이에서 4를 뺀 위치까지 순회하면서 \*를 삽입하고,
2. 두 번째 for문은 남은 뒤 4자리는 주어진 문자열 그대로 더해서 반환한다.
