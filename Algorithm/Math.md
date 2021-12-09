# 수학 공식 모음

## GCD (최대공약수, Greatest Common Divisor)
유클리드호제법<br>
a,b 수 크기 상관 없음<br>
```c++
a%b = 0// 최대 공약수 = b
a%b = c
b%c = 0//최대공약수 = c
int gcd(int a, int b) {
	if (b==0) return a;
	return gcd(b, a%b);
}
```

## LCM (최소공배수, Least Common Multiple)
```c++
a*b/gcd = lcm
```

## 빠른 제곱
일반적으로 : a^b => b번<br>
a^10000000000 => 1억만 넘어도 1초 넘는데 100억은 너무 오래 걸림<br>
2^8 => 2*2=4 => 4*4=16 …...<br>
log n번에 가능해짐<br>

### a의 b승
```c++
long long ans = 1; 
while(b!=0) {
	if (b%2==1)	// (b&1); b가 홀수면 참
		ans *= a;
	a *= a;
	b /= 2;		// (b >>=1);
}
return ans;
```

### 피보나치
```
(a0 a1)
(a1 a2)
```
위의 행렬을 n제곱 하면 아래가 나옴<br>
```
(an    an+1)
(an+1  an+2)
```
행렬과 빠른제곱을 사용하면 n번째 피보나치 수를 구할 때 유용<br>

## 1부터 n까지의 합 구하기
n * (n + 1) // 2

## 1부터 n까지의 연속한 숫자의 제곱의 합 구하기
n * (n+1) * (2n+1) // 6

## 에라토스테네스의 체 - 소수 찾기
```python
def find(num):  # num이 소수이면 True 반환
    i = 2
    while i*i <= num:
        if num % i == 0:
            return False
        i += 1
    return True
```
