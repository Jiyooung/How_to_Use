# Java Code 사용법

## 입출력

### scanner
```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);

int num1 = scanner.nextInt();       // int 값 하나만 저장
scanner.nextLine();                 // 없으면 아래 s1에 엔터값이 들어감
String s1 = scanner.nextLine();     // 엔터 전까지 한 줄을 받음

System.out.println(s1); 

scanner.close();    // 사용 후 반환
scanner = null;
```

### BufferedReader
scanner보다 빠름
```java

static int[] arr;
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
t = Integer.parseInt(br.readLine());    // int 값 하나만 저장
String[] data = br.readLine().split(" ");   // input : 5 7
r = Integer.parseInt(data[0]);      // 5
c = Integer.parseInt(data[1]);      // 7

arr = new int[r];
String line = br.readLine();        // input : 123456789
for (int j = 0; j < line.length(); j++) {
    arr[j] = line.charAt(j)-'0';    // int형으로 넣기 위해 -'0' 수행
}
```


## 자료형

## String

### String 값 비교
```java
s1.equals(s2)   // true, false
s2.equalsIgnoreCase("yes")  // YES, YeS 등 대소문자 구분없이 비교, true, false
```

### String 대소문자 변환
```java
st.toUpperCase()    // 모두 대문자로
```

### String > 숫자
```java
int num = Integer.parseInt("100");
double d = Double.parseDouble("33.56");
```

### 길이얻기
```java
s1.length()
```

### String 접근 index
```java
s1.charAt(index)    // 0부터 시작
```

### 공백제거
```java
s1.trim()
```
문자열 좌우의 공백만 제거
```java
s1.replace(" ", "");
```
문자열 사이 공백 모두 제거는 replace() 활용

### StringBuffer, StringBuilder
둘이 사용법은 똑같음
```java
// StringBuffer sb = new StringBuffer();
StringBuilder sb = new StringBuilder();

sb.append(~~); 
```
String에 + 해서 문자열 만들수도 있지만 효율적으로 좋지 않음 \> 쓰지 않기를 권장

### 문자열 뽑아내기
```java
// 문자열 start 위치부터 num개 뽑아내기
String msg = new String("~~".toCharArray(), start, num);  
```

## char

### 값이 숫자인지 확인
```java
Character.isDigit(c)    // true, false
```

## int

### 숫자 > String
```java
String st = Integer.toString(100);
```

### 길이얻기
```java
num.length
```

## 자료형 min, max 크기 확인
```java
Byte.MIN_VALUE, Byte.MAX_VALUE
Integer.MIN_VALUE, Integer.MAX_VALUE
```


## 반복문

### 지정한 for문 break 하기

```java
OUT:    for (int i = 0; i < 10; i++) {
            for(int j = 0; j < 10; j++) {
                if (j == 5) break OUT;
            }
        }
```

## 배열

### 선언, 생성, 초기화, 출력
```java
int[] num = {1, 2}
String s[] = {"ha", "hi"}

System.out.println(Arrays.toString(num));   // [1, 2]	
System.out.println(Arrays.toString(s));     // [ha, hi]
```

## 업캐스팅 (UpCasting)
```java
Dog d1 = new Dog();
Animal a2 = d1; // Dog > Animal로 자동 형변환 
```

## 다운캐스팅 (DownCasting)
```java
Animal a1 = new Dog(); 
System.out.println(((Dog)a1).name);			// downcasting

Ahimal a2 = new Fish();
if (a2 instanceof Fish) ((Fish)a2).print();	// downcasting
```
method는 downcasting 전에 instanceof 로 객체 타입 확인한 후에 진행해야 함!<br>


<!-- 
```java

``` 
-->