### 문제 1

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

### 문제 2

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

### 문제 3

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

### 문제 4

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

### 문제 5

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

### 문제 6

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

### 문제 7

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

### 문제 8

(Array, 알고리즘)
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
