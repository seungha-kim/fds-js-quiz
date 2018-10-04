### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```

```js
// 긴 버전
function insensitiveEqual(str1, str2) {
  if (str1.toLowerCase() === str2.toLowerCase()) {
    return true
  } else {
    return false
  }
}
```

```js
// 짧은 버전
function insensitiveEqual(str1, str2) {
  return str1.toLowerCase() === str2.toLowerCase()
}
```
### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백을 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```

```js
function leftPad(s, n) {
  if (s.length < n) {
    const spaceNum = n - s.length
    return ' '.repeat(spaceNum) + s
  } else {
    return s
  }
}

```

### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

```js
function count(str) {
  let num = 0
  for (let i = 0; i < str.length; i++) { 
    if (str[i] === 'a' || str[i] === 'e' || str[i] === 'i' || str[i] === 'o' || str[i] === 'u') {
      num += 1
    }
  }
  return num
}

count('hello')
```

### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 개수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```

```js
function countChar(input) {
  const obj = {}
  for (let i = 0; i < input.length; i++) {
    const char = input[i]
    // 글자를 본적이 없다면 "글자": 1 을 적어준다.
    if ( !(char in obj) ) {
      obj[char] = 1
    } else {
      // 글자를 본적이 있다면 개수를 1 증가시켜준다.
      obj[char]++
    }
  }
  return obj
}
```

### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)

### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```

```js
const isPalindrome = (input) => {
  for (let i = 0; i <= input.length / 2 - 1; i++) {
    const left = i;
    const right = input.length - 1 - i;
    if (input[left] !== input[right]) {
      return false
    }
  }
  return true
}
```

### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```

### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.
- `split` 메소드를 이용해서 풀어보세요.

```js
const removeId = (input) => {
  let seen = false
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    // 내가 지금 보고 있는 글자가 '@' 이면
    if (input[i] === '@') {
      // seen의 값을 true로 바꾼다.
      seen = true
    }

    // seen이 true이면
    if (seen) {
      // 내가 지금 보고 있는 글자를 그대로 memory에 덧붙인다.
      memory += input[i]  
    } else {
      // 아니면, 별표를 대신 덧붙인다.
      memory += '*'
    }
  }
  // 변환한 결과를 반환한다.
  return memory
}

const removeId2 = (input) => {
  // '@'을 기준으로 쪼갠 후
  const splitted = input.split('@')
  // id 부분과 같은 길이를 갖는 별표 문자열을 만든다.
  const stars = '*'.repeat(splitted[0].length)
  // 별표를 @, 도메인 부분과 이어붙인 후 반환한다.
  return stars + '@' + splitted[1]
}
```

### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.

```js
// 배열을 사용하지 않고, 루프를 사용해서 풀기
function swapCase(input) {
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    if (input[i].toUpperCase() === input[i]) {
      memory += input[i].toLowerCase()
    } else {
      memory += input[i].toUpperCase()
    }
  }
  return memory
}

swapCase('JavaScript')
```

```js
// 배열 메소드를 사용해서 풀기
const swapCase = input => Array.from(input)
  .map(c => c.toUpperCase() === c ? c.toLowerCase() : c.toUpperCase())
  .join('')

swapCase('JavaScript')
```

### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

```js
// 배열을 사용하지 않고, 루프를 사용해서 풀기
function capitalize(input) {
  let seenBlank = true
  let memory = ''

  for (let i = 0; i < input.length; i++) {
    if (seenBlank) {
      memory += input[i].toUpperCase()
    } else {
      memory += input[i]
    }

    if (input[i] === ' ') {
      seenBlank = true
    } else {
      seenBlank = false
    }
  }

  return memory
}

capitalize('i am hungry')
```

```js
// 배열 메소드를 사용해서 풀기
const capitalize = input => input.split(' ')
  .map(word => word.slice(0, 1).toUpperCase() + word.slice(1))
  .join(' ')

capitalize('i am hungry')
```

### 문제 11

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

```js
// 아이디어: 한 글자씩 보면서, 지금까지 봤던 단어중에 "제일 긴" "단어"를 기억해둔다.
function longestWord(input) {
  let longest = '' // 지금까지 봤던 단어 중에 제일 긴 단어
  let current = '' // 내가 지금 보고 있는 단어

  // 한 글자씩 보기
  for (let i = 0; i < input.length; i++) {

    // 내가 지금 보고 있는 글자가 공백이 아니면
    if (input[i] !== ' ') {
      current += input[i]
      if (current.length >= longest.length) {
        longest = current
      }
    } else {
      // 내가 지금 보고 있는 글자가 공백이면
      // current를 처음부터 다시 시작
      current = ''
    }
  }

  return longest
}

longestWord('java haha hehe') // -> 'javascript'
```

```js

// 배열 메소드 사용한 버전
function longestWord(input) {
  const splitted = input.split(' ')
  splitted.sort((x, y) => y.length - x.length)
  return splitted[0]
}

longestWord('hello fun javascript') // -> 'javascript'
```

### 문제 12

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.

```js

function firstLetters(s, n) {
  if (s.length < n) {
    return s
  }
  let memory = ''
  for (let i = 0; i < s.length; i++) {
    memory += s[i]
    if (memory.length === n) {
      return memory
    }
  }
}

```

### 문제 13

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

```js
function toSnakeCase(input) {
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    // 만약, 첫 글자가 아닌 대문자를 만났을 경우
    if (i !== 0 && (input[i].toUpperCase() === input[i])) {
      memory += '_'
    }
    memory += input[i].toLowerCase()
  }
  return memory
}
```

### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

### 문제 15

`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```

```js
// 한 글자 짜리 separator만 지원하는 함수
function split(input, sep) { // 'separator'
  // 현재 보고 있는 단어
  let memory = ''
  let arr = []
  for (let i = 0; i < input.length; i++) {
    if (input[i] !== sep) {
      memory += input[i]
    } else {
      arr.push(memory)
      memory = ''
    }
  }
  arr.push(memory)
  return arr 
}
```

```js
// 길이가 1 이상인 separator에 대해서도 동작하는 split 함수
// 단순 루프를 사용한 버전
// 아이디어: 한 글자씩 보면서, separator를 발견하면 그 이전 부분까지의 문자열을 배열에 추가한다.
function split(input, separator) {
  let memory = ''
  // sepIndex: separator 일지도 모르는 부분의 첫 인덱스를 저장하는 변수.
  // separator가 아닌 것 같은 부분을 보고 있을 때는 null을 저장한다.
  let sepIndex = null
  let arr = []
  for (let i = 0; i < input.length; i++) {
    memory += input[i]
    // separator를 보고 있는 중이 아니라면
    if (sepIndex == null) {

      // separator와 첫글자가 일치하는 경우라면 (separator일지도 모른다!)
      if (input[i] === separator[0]) {
        sepIndex = i
      }
    }

    // separator일지도 모르는 부분을 보고 있는 중이고, separator과 글자가 일치한다면
    if (sepIndex != null && input[i] === separator[i - sepIndex]) {
      // separator의 끝부분까지 모두 일치해서, 지금까지 본 것이 separator라는 결론을 내릴 수 있다면
      if (i - sepIndex === separator.length - 1) {
        arr.push(memory.slice(0, memory.length - separator.length))
        memory = ''
        sepIndex = null
      }
    } else {
      // 'separator인가?' 하고 보고 있었지만 보다보니 separator와 글자가 일치하지 않는다면
      sepIndex = null
    }
  }
  arr.push(memory)
  return arr
}

console.log(split('javascript,python,java', ','))
console.log(split('javascriptAndpythonAndjava', 'And'))
```

### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```

### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```
