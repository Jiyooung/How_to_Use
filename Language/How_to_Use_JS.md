# JavaScript

## 변수
|선언|변수 재선언|변수 재할당|
|:---:|:---:|:---:|
|var|O|O|
|let|O|X|
|const|X|X|

### var
```javascript
var a = 1;
var s = "string";
```
선언, 초기화가 동시에 이루어짐

### let
선언 > 초기화 > 할당

### const


## 자료형

### 숫자
```javascript
Math.pow(3,2);       // 9,   3의 2승 
Math.round(10.6);    // 11,  10.6을 반올림
Math.ceil(10.2);     // 11,  10.2를 올림
Math.floor(10.6);    // 10,  10.6을 내림
Math.sqrt(9);        // 3,   3의 제곱근
Math.random();       // 0부터 1.0 사이의 랜덤한 숫자
```

#### type 알기
```javascript
alert(typeof "1")
```

### String
`+` 로 연결 가능
str.length
`==` 로 비교 : 서로 값이 같다면 true 다르다면 false
`===` 로 비교 : '정확'하게 같을 때 true 다르면 false, 데이터형까지 같아야 함

### null / undefined
null == undefined
null : 값이 없음
undefined : 값이 없는 상태

### NaN
NaN은 0/0과 같은 연산의 결과로 만들어지는 특수한 데이터 형인데 숫자가 아니라는 뜻

### 형변환
```js
let num = Number(str)
```


## 함수
```javascript
function 함수명( [인자...[,인자]] ){
   코드
   return 반환값
}
```


## 객체
```javascript
var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};    // (key, value)
var grades = {};    // 생성 방법 1
var grades = new Object();  // 생성 방법 2
grades['egoing'] = 10;  // 값 추가
grades['sorialgi']      // 값 접근 방법 1
grades.sorialgi         // 값 접근 방법 2
``` 

객체에는 객체를 담을수도 있고, 함수도 담을 수 있다
```javascript
var grades = {
    'list': {'egoing': 10, 'k8805': 6, 'sorialgi': 80},
    'show' : function(){
        for(var name in this.list){
            document.write(name+':'+this.list[name]+"<br />");
        }
    }
};
grades.show();
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
```javascript
li.push('f');               // 추가
li = li.concat(['f', 'g']); // 여러개 추가
li.unshift('z');            // 맨 앞에 추가
li.splice(2, 0, 'B');       // 2번째 인자부터 0개 지우고 그자리에 'B'넣기, 뒤에는 밀림
li.shift();                 // 첫번째 원소 제거
li.pop();                   // 마지막 원소 제거
li.sort();                  // 정렬
li.reverse();               // 역순 정렬
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




## 입력

### 사용자 입력 받기
prompt()

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


## 출력
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



## 모듈화
코드의 재활용성 높이기, 유지보수 향상

```js
function welcome(){
    return 'Hello world';
}
```
~~.js 파일에 사용할 함수 저장

```js
<script src="~~.js"></script>
```
html파일 head에 위 코드 추가

### Node.js에서의 모듈 로드
```js
var circle = require('~~.js');
console.log(circle.area(4));
```



## 정규표현식 (regular expression)
문자열에서 특정한 문자를 찾아내는 도구

### 정규표현식 객체 생성

#### 정규표현식 객체 생성자
```js
var pattern = new RegExp('a');  // 찾고자 하는 텍스트는 a
```

#### 정규표현식 리터럴
```js
var pattern = /a/;      // 찾고자 하는 텍스트는 a
var pattern = /a./;     // . 은 어떤 문자든지 한 문자를 의미
var pattern = /a/i;     // 대소문자 구분 X
var pattern = /a/g;     // 검색된 모든 결과를 리턴, a의 개수 알 수 있음

```
pattern : 정규표현식 객체. 패턴이 들어있음 = RegExp

#### 괄호 사용
```js
var pattern = /(\w+)\s(\w+)/;   // (\w+) : 한 단어. 앞에서부터 $1
                                // \s: 띄어쓰기?
var str = "coding everybody";
var result = str.replace(pattern, "$2, $1");
console.log(result);
```
괄호안의 패턴은 마치 변수처럼 재사용

#### 치환
```js
var urlPattern = /\b(?:https?):\/\/[a-z0-9-+&@#\/%?=~_|!:,.;]*/gim;
var content = '생활코딩 : http://opentutorials.org/course/1 입니다. 네이버 : http://naver.com 입니다. ';
var result = content.replace(urlPattern, function(url){
    return '<a href="'+url+'">'+url+'</a>';
});
console.log(result);
```

### 문자 찾기

#### RegExp.exec()
```js
console.log(pattern.exec('abcdef'));    // ["a"]
console.log(pattern.exec('bcdefg'));    // null
console.log('abcdef'.match(pattern));   // ["a"]
console.log('bcdefg'.match(pattern));   // null
```
배열을 리턴. 없으면 null 리턴

#### String.replace()
```js
console.log('abcdef'.replace(pattern, 'A'));  // Abcdef
```
문자열에서 패턴을 검색해서 이를 변경한 후에 변경된 값을 리턴

#### RegExp.test()
```js
console.log(pattern.test('abcdef')); // true
```
test는 인자 안에 패턴에 해당되는 문자열이 있으면 true, 없으면 false를 리턴

