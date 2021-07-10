---
title: Programmers - LV2. 전화번호목록
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/42577)

> 자바스크립트 언어를 지원하지 않아 예제 테스트만 진행한 상태입니다. 실행 시 정확하지 않을 수 있습니다.

## 접근하기

문자열이 담긴 배열 `phone_book`이 주어진다. `phone_book`에서 한 문자열이라도 겹치는 접두어가 있다면 `false`를, 아니면 `true`를 반환한다.

<br>

## 참고 코드

```js
function solution(phone_book) {
  let asc = phone_book.sort((a, b) => a.length - b.length);
  let minLength = asc[0];

  let arr = [];
  for (let i = 1; i < phone_book.length; i++) {
    arr.push(phone_book[i].slice(0, minLength.length));
  }

  for (let i = 0; i < arr.length; i++) {
    if (minLength === arr[i]) return false;
  }
  return true;
}
```

1. 카테고리는 해시인데 배열을 이용해 풀었다.
2. 먼저 배열에서 가장 작은 문자열을 가져온다.
3. 배열의 모든 요소를 0부터 가장 작은 문자열까지 잘라낸다.
4. 처음 가장 작은 문자열과 잘라낸 문자열이 하나라도 일치하면 `false`를, 아니면 `true`를 반환한다.
