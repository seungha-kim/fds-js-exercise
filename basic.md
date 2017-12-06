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

(조건문, 반복문)
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
