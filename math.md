### 문제 1

(Math)
양수를 입력받아 이 수를 반지름으로 하는 원의 넓이를 반환하는 함수를 작성하세요.

```js
function circleArea(r) {
  return Math.PI * r ** 2;
}
```

### 문제 2

(Math)
두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수를 작성하세요.

```js
function randomInteger(min, max) {
  return min + Math.floor(Math.random() * (max - min));
}
```

### 문제 3

(Math)
정수를 입력받아, 5 단위로 올림한 수를 반환하는 함수를 작성하세요.

예:
```
ceilBy5(32); -> 35
ceilBy5(37); -> 40
```

```js
function ceilBy5(n) {
  return Math.ceil(n / 5) * 5;
}
```

### 문제 4

(반복문, Array, Math)
배열을 입력받아, 요소들의 순서를 뒤섞은 새 배열을 반환하는 함수를 작성하세요.

```js
function shuffle(arr) {
  let result = [];
  
  while(arr.length > 0) {
    const randomIndex = Math.floor(Math.random() * arr.length);
    result = result.concat(arr.splice(randomIndex, 1));
  }

  return result;
}
```

```js
function shuffle(arr) {
  const result = [];
  
  while(arr.length > 0) {
    const randomIndex = Math.floor(Math.random() * arr.length);
    result.push(...arr.splice(randomIndex, 1));
  }

  return result;
}
```

### 문제 5

(반복문, Math)
임의의 HTML 색상 코드를 반환하는 함수를 작성하세요.

```js
const DIGITS = '0123456789abcdef';

function randomColorCode() {
  let result = '#';
  for (let i = 0; i < 6; i++) {
    result += DIGITS[Math.floor(Math.random() * DIGITS.length)];
  }
  return result;
}
```

```js
function randomColorCode() {
  return '#' + Math.floor(Math.random() * 256 ** 3).toString(16);
}
```

### 문제 6

(Math, 반복문)
양수를 입력받아, 그 수만큼의 길이를 갖는 임의의 문자열을 반환하는 함수를 작성하세요.

```js
function randomString(n) {
  const chars = ' !@#$%^&*()_+abcdefghijklmnopqrstuvwxyz1234567890';
  let sum = '';
  for (let i = 0; i < n; i++) {
    sum += chars[Math.floor(Math.random() * chars.length)];
  }
  return sum;
}
```

### 문제 7

(반복문, Array, Math)
수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 표준편차를 구하는 함수를 작성하세요.

```js
// 평균
function mean(arr) {
  let sum = 0;
  for (let item of arr) {
    sum += item;
  }
  return sum / arr.length;
}

// 표준편차
function stddev(arr) {
  const meanOfArr = mean(arr);
  const devArr = [];
  for (let item of arr) {
    devArr.push((item - meanOfArr) ** 2);
  }
  return Math.sqrt(mean(devArr));
}
```

```js
function mean(arr) {
  return arr.reduce((acc, item) => acc + item, 0) / arr.length;
}

function stddev(arr) {
  const meanOfArr = mean(arr);
  return Math.sqrt(mean(arr.map(x => (x - meanOfArr) ** 2)))
}
```
