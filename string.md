
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

(String, 반복문, 조건문)
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

(String, 반복문, Object)
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

(반복문, String)
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
