### 문제 1

양수를 입력받아 이 수를 반지름으로 하는 원의 넓이를 반환하는 함수를 작성하세요.

### 문제 2

두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수를 작성하세요.

### 문제 3

정수를 입력받아, 5 단위로 올림한 수를 반환하는 함수를 작성하세요.

예:
```
ceilBy5(32); -> 35
ceilBy5(37); -> 40
```

```js
function ceilBy5(input) {
  return Math.ceil(input / 5) * 5
}
```
### 문제 4

배열을 입력받아, 요소들의 순서를 뒤섞은 새 배열을 반환하는 함수를 작성하세요.

### 문제 5

임의의 HTML 색상 코드를 반환하는 함수를 작성하세요.

```js
function randomColor() {
  const candidate = '0123456789ABCDEF'
  let color = '#'
  for (let i = 0; i < 6; i++) {
    const randomIndex = Math.floor(candidate.length * Math.random())
    color += candidate[randomIndex]
  }
  return color
}
```

```js
function randomColor() {
  const r = Math.floor(Math.random() * 256)
  const g = Math.floor(Math.random() * 256)
  const b = Math.floor(Math.random() * 256)
  return `rgb(${r},${g},${b})`
}
```

### 문제 6

양수를 입력받아, 그 수만큼의 길이를 갖는 임의의 문자열을 반환하는 함수를 작성하세요.

```js
function randomString(n) {
  const candidate = '1234567890!@#$%^&*()abcdefg'
  let result = ''
  for (let i = 0; i < n; i++) {
    const randomIndex = Math.floor(Math.random() * candidate.length)
    result += candidate[randomIndex]
  }
  return result
}
```

```js
function randomString(n) {
  let result = ''
  for (let i = 0; i < n; i++) {
    result += String.fromCodePoint(Math.floor(Math.random() * 65536))
  }
  return result
}
```

### 문제 7

수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 표준편차를 구하는 함수를 작성하세요.
