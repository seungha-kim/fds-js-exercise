# JavaScript 기초 연습문제

(연산자, 조건문)
두 수를 입력받아 큰 수를 반환하는 함수를 작성하세요.

```js
function larger(x, y) {
  if (x > y) {
    return x;
  } else {
    return y;
  }
}
```

```js
function larger(x, y) {
  return x > y ? x : y;
}
```

---

(연산자, 조건문, 예외, Number, NaN)
세 수를 입력받아 그 곱이 양수이면 `true`, 0 혹은 음수이면 `false`, 둘 다 아니면 에러를 발생시키는 함수를 작성하세요.

```js
function isPositive(x, y, z) {
  const result = x * y * z;
  if (typeof result !== 'number' || Number.isNaN(result)) {
    throw new Error('입력값이 잘못되었습니다.');
  }
  return result > 0;
}
```

---

(연산자, 조건문, 알고리즘)
세 수를 입력받아 큰 것부터 차례대로 출력하는 함수를 작성하세요.

```js
function printLargerFirst(x, y, z) {
  if (x < y) {
    const temp = x;
    x = y;
    y = temp;
  }
  if (y < z) {
    const temp = y;
    y = z;
    z = temp;
  }
  if (x < y) {
    const temp = x;
    x = y;
    y = temp;
  }
  console.log(x);
  console.log(y);
  console.log(z);
}
```

```js
function printLargerFirst(x, y, z) {
  if (x < y) [x, y] = [y, x];
  if (y < z) [y, z] = [z, y];
  if (x < y) [x, y] = [y, x];
  console.log(x);
  console.log(y);
  console.log(z);
}
```

```js
function printLargerFirst(...args) {
  args.sort((x, y) => y - x).forEach(x => console.log(x));
}
```

---

(반복문)
어떤 정수가 짝수인지 홀수인지 출력하는 함수를 작성하세요. 이를 이용해서, 1부터 20까지의 수가 각각 짝수인지 홀수인지 출력하는 프로그램을 작성하세요.

```js
function printEvenOdd(x) {
  if (x %  2 === 0) {
    console.log(`${x}는 짝수입니다.`);
  } else {
    console.log(`${x}는 홀수입니다.`);
  }
}

for (let i = 1; i <= 20; i++) {
  printEvenOdd(i);
}
```

---

(반복문, String, Array)
1부터 100까지의 수를 차례대로 출력하되, 자릿수에 3, 6, 9중 하나라도 포함되어 있으면 '짝!'을 대신 출력하는 프로그램을 작성하세요.

```js
for (let i = 1; i <= 100; i++) {
  const s = i.toString();
  if (s.includes('3') || s.includes('6') || s.includes('9')) {
    console.log('짝!');
  } else {
    console.log(i);
  }
}
```

---

(반복문)
양의 정수를 입력받아, 다음과 같은 패턴의 출력을 하는 함수를 작성하세요.

1을 입력받은 경우:
```
*
```

3을 입력받은 경우:
```
*
* *
* * *
```

5를 입력받은 경우:
```
*
* *
* * *
* * * *
* * * * *
```

```js
function pyramid(n) {
  let sum = '';
  for (let i = 0; i < n; i++) {
    if (i !== 0) {
      sum += ' ';
    }
    sum += '*';
    console.log(sum);
  }
}
```

```js
function pyramid(n) {
  for (let i = 0; i < n; i++) {
    console.log(new Array(i+1).fill('*').join(' '));
  }
}
```

---

(반복문)
양의 정수를 입력받아, 다음과 같은 패턴의 출력을 하는 함수를 작성하세요.

1를 입력받은 경우:
```
*
```

3를 입력받은 경우:
```
  *
 * *
* * *
 * *
  *
```

5를 입력받은 경우:
```
    *
   * *
  * * *
 * * * *
* * * * *
 * * * *
  * * *
   * *
    *
```

```js
function diamond(n) {
  for (let i = 1; i <= n; i++) {
    let sum = ' '.repeat(n - i);
    for (let j = 1; j <= i; j++) {
      if (j !== 1) {
        sum += ' ';
      }
      sum += '*';
    }
    console.log(sum);
  }
  for (let i = n - 1; i > 0; i--) {
    let sum = ' '.repeat(n - i);
    for (let j = 1; j <= i; j++) {
      if (j !== 1) {
        sum += ' ';
      }
      sum += '*';
    }
    console.log(sum);
  }
}
```

```js
function line(largest, step) {
  let sum = ' '.repeat(largest - step);
  for (let j = 1; j <= step; j++) {
    if (j !== 1) {
      sum += ' ';
    }
    sum += '*';
  }
  console.log(sum);
}

function diamond(n) {
  for (let i = 1; i <= n; i++) {
    line(n, i);
  }
  for (let i = n - 1; i > 0; i--) {
    line(n, i);
  }
}
```
---

(반복문)
두 수를 입력받아서, 두 수의 최대공약수를 반환하는 함수를 작성하세요. ([유클리드 호제법](https://ko.wikipedia.org/wiki/%EC%9C%A0%ED%81%B4%EB%A6%AC%EB%93%9C_%ED%98%B8%EC%A0%9C%EB%B2%95)을 참고하세요.)

```js
function gcd(x, y) {
  while (y !=== 0) {
    const remainder = x % y;
    x = y;
    y = remainder;
  }
  return x;
}
```

```js
function gcd(x, y) {
  return y === 0 ? x : gcd(y, x % y);
}
```

---

(반복문)
100 이하의 자연수 중 3과 5의 공배수를 모두 출력하는 프로그램을 작성하세요.

```js
for (let i = 1; i <= 100; i++) {
  if (i % 3 === 0 || i % 5 === 0) {
    console.log(i);
  }
}
```

---

(Math)
양수를 입력받아 이 수를 반지름으로 하는 원의 넓이를 반환하는 함수를 작성하세요.

```js
function circleArea(r) {
  return Math.PI * r ** 2;
}
```

---

(배열, 알고리즘)
수 타입의 값만 들어있는 배열을 입력받아, 해당 배열을 오름차순 정렬하는 함수를 작성하세요. (`Array.prototype.sort`를 사용하지 않고 작성해보세요. [선택 정렬](https://ko.wikipedia.org/wiki/%EC%84%A0%ED%83%9D_%EC%A0%95%EB%A0%AC)을 참고하세요.)

```js
function selectionSort(arr) {
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] > arr[j]) {
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
    }
  }
  return arr;
}
```

---

(반복문, String)
문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:

```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```

```js
function allSubString(s) {
  const arr = [];
  for (let i = 0; i < s.length; i++) {
    for (let j = i + 1; j < s.length + 1; j++) {
      arr.push(s.slice(i, j));
    }
  }
  return arr;
}
```

---

(반복문, String)
문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)

```js
function isPalindrome(s) {
  for (let i = 0; i < s.length / 2; i++) {
    if (s[i] !== s[s.length - 1 - i]) return false;
  }
  return true;
}
```

---

(String)
문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

```js
function capitalize(s) {
  let sum = '';
  for (let i = 0; i < s.length; i++) {
    if (s[i-1] === undefined || s[i-1] === ' ') {
      sum += s[i].toUpperCase();
    } else {
      sum += s[i];
    }
  }
  return sum;
}
```

```js
function capitalize(s) {
  return s.split(' ')
    .map(ss => ss[0].toUpperCase() + ss.slice(1, ss.length))
    .join(' ');
}
```

---

(반복문, String)
문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.

```js
function swapCase(s) {
  let sum = '';
  for (let i = 0; i < s.length; i++) {
    if (s[i].toUpperCase() === s[i]) {
      sum += s[i].toLowerCase();
    } else {
      sum += s[i].toUpperCase();
    }
  }
  return sum;
}
```

```js
function swapCase(s) {
  let sum = '';
  for (let c of s) {
    if (c.toUpperCase() === c) {
      sum += c.toLowerCase();
    } else {
      sum += c.toUpperCase();
    }
  }
  return sum;
}
```

---

(반복문, String)
문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

```js
function isEmpty(c) {
  return c === undefined || c === ' ';
}

function longestWord(s) {
  let currentLongestWord = '';
  let currentSum = '';
  for (let i = 0; i < s.length + 1; i++) {
    if (isEmpty(s[i-1]) && !isEmpty(s[i])) {
      currentSum = s[i];
    } else if (isEmpty(s[i])) {
      if (currentSum.length > currentLongestWord.length) {
        currentLongestWord = currentSum;
      }
    } else {
      currentSum += s[i];
    }
  }
  return currentLongestWord;
}
```

```js
function longestWord(s) {
  return s.split(' ').sort((s1, s2) => s2.length - s1.length)[0];
}
```
---

(반복문, 조건문)
문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

```js
function countVowel(s) {
  let count = 0;
  for (let c of s) {
    switch (c) {
      case 'a':
      case 'e':
      case 'i':
      case 'o':
      case 'u':
        count++;
        break;
    }
  }
  return count;
}
```

```js
const VOWELS = ['a', 'e', 'i', 'o', 'u'];

function countVowel(s) {
  return Array.from(s)
    .filter(c => VOWELS.includes(c))
    .length;
}
```

---

(반복문)
자연수를 입력받아, 그 수의 모든 약수를 출력하는 함수를 작성하세요.

```js
function printFactors(n) {
  for (let i = 1; i <= n; i++) {
    if (n % i === 0) {
      console.log(i);
    }
  }
}
```

---

(반복문)
2 이상의 자연수를 입력받아, 그 수가 소수인지 아닌지를 판별하는 함수를 작성하세요.

```js
function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if (n % 2 === 0) {
      return false;
    }
  }
  return true;
}
```

---

(반복문, Array)
'금액'과 '동전의 종류가 들어있는 배열'를 입력받아, 최소한의 동전을 사용해서 금액을 맞출 수 있는 방법을 출력하는 함수를 작성하세요.

예:

```
coins(163, [100, 50, 10, 5, 1]);
// 출력
100
50
10
1
1
1
```

```js
function coins(amount, coinTypes) {
  coinTypes.sort((x, y) => y - x);
  for (let coin of coinTypes) {
    while (amount - coin >= 0) {
      console.log(coin);
      amount -= coin;
    }
  }
}
```

---

(반복문, String)
문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```

```js
function removeDuplicates(s) {
  let sum = '';
  for (let c of s) {
    if (!sum.includes(c)) {
      sum += c;
    }
  }
  return sum;
}
```

```js
function removeDuplicates(s) {
  return Array.from(new Set(s)).join('');
}
```
---

(반복문, Object)
문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:

```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```

```js
function countChar(s) {
  const countObj = {};
  for (let c of s) {
    if (countObj[c] === undefined) {
      countObj[c] = 1;
    } else {
      countObj[c]++;
    }
  }
  return countObj;
}
```

```js
function countChar(s) {
  const countObj = {};
  for (let c of s) {
    countObj[c] = countObj[c] + 1 || 1;
  }
  return countObj;
}
```

---

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

---

(반복문, Array)
배열을 입력받아, 배열의 요소 중 두 개를 선택하는 조합을 모두 포함하는 배열을 작성하세요.

예:

```
combination([1, 2, 3]); -> [[1, 2], [1, 3], [2, 3]]
```

```js
function combination(arr) {
  const result = [];
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      result.push([arr[i], arr[j]]);
    }
  }
  return result;
}
```

---

(반복문, String, Array)
숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```

```js
const EVENS = ['0', '2', '4', '6', '8'];

function insertHyphen(s) {
  let previous;
  let sum = '';
  for (let c of s) {
    if (EVENS.includes(previous) && EVENS.includes(c)) {
      sum += '-';
    }
    sum += c;
    previous = c;
  }
  return sum;
}
```

---

(반복문, Array)
수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 합을 구하는 함수를 작성하세요.

```js
function sum(arr) {
  let result = 0;
  for (let item of arr) {
    result += item;
  }
  return result;
}
```

```js
function sum(arr) {
  return arr.reduce((acc, item) => acc + item, 0);
}
```

---

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

---

(반복문, Array)
배열을 입력받아, 중복된 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.

```js
function removeDuplicates(arr) {
  let result = [];
  for (let item of arr) {
    if (!result.includes(item)) {
      result.push(item)
    }
  }
  return result;
}
```

```js
function removeDuplicates(arr) {
  return Array.from(new Set(arr));
}
```
---

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

---

(반복문, Array)
수 타입의 값으로만 이루어진 두 배열을 입력받아, 다음과 같이 동작하는 함수를 작성하세요.
- 두 배열의 같은 자리에 있는 요소를 더한 결과가 새 배열의 요소가 됩니다.
- 만약 입력받은 두 배열의 길이가 갖지 않다면, 긴 배열에 있는 요소를 새 배열의 같은 위치에 포함시키세요.

예:
```
addArray([1, 2, 3], [4, 5, 6, 7]) -> [5, 7, 9, 7]
```

```js
function addArray(arr1, arr2) {
  const largerLength = arr1.length > arr2.length ? arr1.length : arr2.length;
  const result = [];

  for (let i = 0; i < largerLength; i++) {
    if (arr1[i] !== undefined) {
      if (arr2[i] !== undefined) {
        result.push(arr1[i] + arr2[i]);
      } else {
        result.push(arr1[i])
      }
    } else {
      result.push(arr2[i])
    }
  }

  return result;
}
```

---

(반복문, Array)
배열을 입력받아, falsy인 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.

```js
function filterFalsy(arr) {
  const result = [];
  for (let item of arr) {
    if (!!item) {
      result.push(item);
    }
  }
  return result;
}
```

```js
function filterFalsy(arr) {
  return arr.filter(item => item);
}
```

---

(반복문, Array)
두 정수 `start`, `end`를 입력받아, `start`부터 `end`까지의 모든 정수를 배열로 반환하는 함수를 작성하세요.

예:
```
range(3, 6); -> [3, 4, 5, 6]
```

```js
function range(start, end) {
  const result = [];

  for (let i = start; i <= end; i++) {
    result.push(i);
  }

  return result;
}
```

---

(Math)
두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수를 작성하세요.

```js
function randomInteger(min, max) {
  return min + Math.floor(Math.random() * (max - min));
}
```

---

(반복문, Array, String, 연산자)
2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```

```js
function convertBinary(s) {
  let sum = 0;
  const digits = Array.from(s).reverse();
  for (let i = 0; i < digits.length; i++) {
    const number = (
      digits[i] === '1' ? 1 :
      digits[i] === '0' ? 0 :
      NaN
    );
    sum += number * 2 ** i;
  }
  return sum;
}
```

```js
function convertBinary(s) {
  return Array.from(s)
    .reverse()
    .reduce(
      (acc, digit, index) => acc + digit * 2 ** index,
      0
    );
}
```

```js
function convertBinary(s) {
  return parseInt(s, 2);
}
```

---

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

---

(조건문, 연산자)
세 수 `min`, `max`, `input`을 입력받아, 다음과 같이 동작하는 함수를 작성하세요.
- `min`보다 `input`이 작으면, `min`을 반환합니다.
- `max`보다 `input`이 크면, `max`를 반환합니다.
- 아니면 `input`을 반환합니다.

예:
```
limit(3, 7, 5); -> 5
limit(3, 7, 11); -> 7
limit(3, 7, 0); -> 0
```

```js
function limit(min, max, input) {
  if (min > input) {
    return min;
  } else if (max < input) {
    return max;
  } else {
    return input;
  }
}
```

```js
function limit(min, max, input) {
  return (
    min > input ? min :
    max < input ? max :
    input
  );
}
```

---

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

---

(반복문)
자연수 `n`을 입력받아, `n`번째 피보나치 수를 반환하는 함수를 작성하세요.

```js
function fibonacci(n) {
  let x = 0;
  let y = 1;
  for (let i = 1; i < n; i++) {
    const temp = x;
    x = y;
    y = temp + x;
  }
  return x;
}
```

```js
function fibonacci(n) {
  let x = 0;
  let y = 1;
  for (let i = 1; i < n; i++) {
    [x, y] = [y, x + y];
  }
  return x;
}
```

---

(반복문, String, Array)
`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:

```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```

```js
function split(inputStr, seperator) {
  const resultArr = [];
  let currentWord = '';
  for (let c of inputStr) {
    if (c == seperator) {
      resultArr.push(currentWord);
      currentWord = '';
    } else {
      currentWord += c;
    }
  }
  if (currentWord !== seperator) {
    resultArr.push(currentWord);
  }
  return resultArr;
}
```

---

()
문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.

```js
function sliceHead(s, n) {
  let sum = '';
  for (let i = 0; i < n; i++) {
    if (s[i] === undefined) break;
    sum += s[i];
  }
  return sum;
}
```

```js
function sliceHead(s, n) {
  return s.slice(0, n);
}
```

---

(반복문, String, Array)
이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

```js
function hideId(s) {
  let idLength = 0;
  let domain = '';
  let isAfterAtSign = false;
  for (let c of s) {
    if (c === '@') {
      isAfterAtSign = true;
      continue;
    }
    if (isAfterAtSign) {
      domain += c;
    } else {
      idLength++;
    }
  }
  return '*'.repeat(idLength) + '@' + domain;
}
```

```js
function hideId(s) {
  const [id, domain] = s.split('@');
  return '*'.repeat(id.length) + '@' + domain;
}
```

---

(String, 반복문, 조건문)
Camel case의 문자열을 입력받아, snake case로 바꾸어주는 함수를 작성하세요.

```js
function isUpperCase(s) {
  return s.toUpperCase() === s;
}

function camelToSnake(s) {
  let sum = '';
  for (let i = 0; i < s.length; i++) {
    if (isUpperCase(s[i]) && i !== 0) {
      sum += '_';
    }
    sum += s[i].toLowerCase();
  }
  return sum;
}
```

---

(String, 반복문, 조건문)
Snake case의 문자열을 입력받아, camel case로 바꾸어주는 함수를 작성하세요.

```js
function snakeToCamel(s) {
  let nextIsUpper = false;
  let sum = '';
  for (let c of s) {
    if (c === '_') {
      nextIsUpper = true;
      continue;
    }

    if (nextIsUpper) {
      sum += c.toUpperCase();
    } else {
      sum += c;
    }
    nextIsUpper = false;
  }
  return sum;
}
```

---

(String, 조건문)
문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```

```js
function leftPad(s, len) {
  if (s.length < len) {
    return ' '.repeat(len - s.length) + s;
  } else {
    return s;
  }
}
```

---

(String)
두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```

```js
function insensitiveEqual(s1, s2) {
  return s1.toLowerCase() === s2.toLowerCase();
}
```