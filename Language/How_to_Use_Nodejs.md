# Node.js

## 변수


## 자료형

### 형변환
```js
let num = Number(str)
```

## 자료구조


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


