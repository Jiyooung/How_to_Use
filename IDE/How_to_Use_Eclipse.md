# Eclipse 사용법

## Java로 세팅
> Window \> Perspective \> Open Perspective \> java <br>

Java 개발에 맞게 기본적으로 세팅된 화면을 제공<br>

## 사용하던 뷰가 사라졌을 때
> window \> show view \> 원하는 거 선택<br>

## Java 파일 생성
> src 우클릭 \> new \> class <br>

일반적으로 패키지 이름은 도메인 주소를 거꾸로 해서 사용 (com.사이트.파일특징)<br>
ex) com.mulcam.hello<br>

## 파일명 변경
> 해당 파일 우클릭 \> refactor \> rename<br>

## 변수명 바꾸기
동일 이름 변수 모두 바꿈<br>
> 해당 변수 드래그 \> 우클릭 \> refactor > rename<br>

## 단축키

### 실행(run)
`ctrl + F11`

### 자동 완성
`ctrl + space` \> 원하는 형식 엔터 <br>
- main      > public static void main(String[] args) { }
- sysout    > System.out.println();

### 자동 정렬
`ctrl + shift + f`

### 초록색 커서
`tab` 키를 누르면 초록색 포인터로 커서가 이동

### 커서 줄 복사
`ctrl + alt + 위/아래 화살표`<br>
해당 방향으로 커서줄 복사

### 커서 줄 삭제
`ctrl + d`<br>
해당 줄 삭제

### 커서 줄 이동
`alt + 위/아래 화살표`<br>
해당 방향으로 커서줄 이동

### 들여쓰기
드래그 + `tab`

### 들여쓰기 삭제
드래그 + `shift + tab`

## 주석
- // : 한줄 주석
- /* ~ */ : 여러줄 주석
- /** ~ */ : document 주석

## private 변수 생성자, getter, setter 만들기

### 생성자 만들기
> source \> Generate Constructor using fields \> 변수 체크 \> 생성자 생성<br>
변수 체크 안하면 빈 생성자 생성 가능<br>
this

### getter, setter 만들기
> source \> Generate Getters and Setters \>  변수 체크 \> Generate \> get~, set~ 생성


## import
`ctrl + shift + o` <br>
필요한 클래스 자동 import
















