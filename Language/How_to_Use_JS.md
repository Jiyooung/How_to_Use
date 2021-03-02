# Node.js

## 변수

|선언|변수 재선언|변수 재할당|
|:---:|:---:|:---:|
|var|O|O|
|let|O|X|
|const|X|X|

### var
선언, 초기화가 동시에 이루어짐

### let
선언 > 초기화 > 할당

### const



## 자료형



### 형변환
```js
let num = Number(str)
```

## 자료구조

### Array
```js
let arr = [1, 2, 3]; 

arr.length();       // 요소 개수 반환
arr[0];             // 인덱스로 접근 가능 => 1
arr.forEach(function(data, idx, array) {    // 요소 모두 출력
    console.log(data, idx);
})
arr.indexOf(2)      // 데이터를 가진 인덱스 출력 => 1
arr.push(4);        // 요소 마지막에 추가   [1, 2, 3, 4]
arr.unshift(0);     // 요소 맨 앞에 추가    [0, 1, 2, 3, 4]
arr.pop();          // 마지막 요소 삭제     [0, 1, 2, 3]
arr.shift();        // 첫번째 요소 삭제     [1, 2, 3]
arr.splice(idx, 1); // idx부터 1개 요소 삭제[1, 3]
arr.includes(2)     // 해당 요소가 있는지 확인 => false
```

#### includes
대소문자 구분
```js
arr.includes(valueToFind[, fromIndex])
```
arr의 fromIndex부터 valueToFind가 존재하는 지 확인.
fromIndex는 생략 가능 (default = 0)
fromIndex이 음수라면 arr.length + fromIndex의 인덱스부터 시작


```js
arr = ['aa', 'bb', 'cc'];
arr[5] = 'ee';          // ['aa', 'bb', 'cc', 'ee']
arr.length              // => 6
Object.keys(arr)        // => ['0', '1', '2', '5']

arr.length = 10;        // ['aa', 'bb', 'cc', empty X 2, 'ee', empty X 4]
arr[8]                  // => undefined

arr.length = 2;         // ['aa', 'bb']
```

#### 차집합, 교집합, 합집합, 배타적논리합
```js
let arr1 = [1, 2, 3]; 
let arr2 = [2, 3, 4, 5];

let diff = arr1.filter(x => !arr2.includes(x));     // 차집합
let inter = arr1.filter(x => arr2.includes(x));     // 교집합
let inter = arr1.filter(x => arr2.includes(x))      // 합집합
                .concat(arr2.filter(x => !arr1.includes(x)));
let inter = arr1.filter(x => !arr2.includes(x))      // 배타적논리합
                .concat(arr2.filter(x => !arr1.includes(x)));
```

### Set 객체
```js
let mySet = new Set();  // 선언
mySet.add(1);           // 요소 추가
mySet.has(1);           // 요소 존재 확인. 있으면 true, 없으면 false 반환
mySet.delete(1);        // 요소 삭제
mySet.clear();          // 모든 요소 제거
mySet.size();           // 요소 개수 반환
```

## 입출력

### readline 모듈 사용

#### 한 줄 입력
```js
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});
rl.on('line', function(line) {
    console.log(line);

    rl.close();
}).on("close", function() {
    process.exit();
});
```

#### 여러줄 입력

```js
let input = [];
rl.on('line', function (line) {
    input.push(line)
}).on('close', function () {
    console.log(input);
    process.exit();
});


```

### fs 모듈 사용

#### 한 줄 입력
```js
var fs = require('fs');
var input = fs.readFileSync("/dev/stdin").toString();    // 하나 입력
```
#### 여러개 입력
```js
var fs = require('fs');
var input = fs.readFileSync("/dev/stdin").toString().split(" "); // 여러개 입력, input[idx]로 접근
var input = fs.readFileSync("/dev/stdin").toString().split(" ")
                .map(function(a) { return +a }); // 입력을 숫자로 받기
```

#### 여러 줄 입력
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let numbers = [];

for (let i = 1; i < input.length; i++) {
    if (input[i] !== '') {
        numbers.push(input[i].split(' '));
    }
}
for (let i = 0; i < numbers.length; i++){
    let num1 = Number(numbers[i][0]);
    let num2 = Number(numbers[i][1]);

    console.log(num1 + num2);
}
```


### 출력
```js
console.log(~~)     // 백준 알고리즘에 정답 출력 시 사용
```

## 정렬

### 문자 정렬
```js
array.sort()    // ASCII 문자 순서로 오름차순
```

### 슷자 정렬
```js
array.sort(function(a, b) {
    return a - b;   // 숫자 오름차순
//  return b - a;   // 숫자 내림차순
});
```

### 슷자 정렬
```js
array.sort(function(a, b) {
    return a - b;   // 숫자 오름차순
//  return b - a;   // 숫자 내림차순
});
```

### Object 정렬
```js
var veg = [
    {name : "마늘", price : 28},
    {name : "감자", price : 66},
    {name : "버섯", price : 42}
]

/* 이름순으로 정렬 */
veg.sort(function(a, b) { 
    return a.name < b.name ? -1 : a.name > b.name ? 1 : 0;  // 오름차순
//  return a.name > b.name ? -1 : a.name < b.name ? 1 : 0;  // 내림차순
});

/* 나이순으로 정렬 */
var sort_field = "price";

veg.sort(function(a, b) { 
    return a[sort_field] - b[sort_field];   // 오름차순
//  return b[sort_field] - a[sort_field];   // 내림차순
});

```


