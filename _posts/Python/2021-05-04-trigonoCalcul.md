---
layout: post
title: "[Python]프로그래밍 1. 삼각함수 계산"
---

### 삼각함수 계산
1. 임의의 수 x를 입력으로 받고, sin x + cos x를 출력하는 프로그램을 만드시오.
2. 단, sin x와 cos x를 구하는 함수를 직접 만들어야 합니다.
3. sin x = x - x^3 / 3! + x^5 / 5! - x^7 / 7! + ...입니다.
4. cos x = 1 - x^2 / 2! + x^4 / 4! - x^6 / 6! + ...입니다.
5. 삼각함수 연산은 호도법을 이용합니다.
6. p.s. 정밀한 계산을 원할 경우 오버플로 문제를 해결하는 법도 찾아야 하겠네요. (팩토리얼 연산 이용하기 때문) 예시 입력: 0 예시 출력: 1


```python
import time
time.strftime("%Y/%m/%d")
```




    '2021/05/04'



step 1.
 1. 함수 이름은? trigonometric_Calculator
 2. 입력은? 실수
 3. 출력은? sin x + cos x
 4. 출력 타입은? float
 5. 연산 방법은? 호도법


```python
# 6. 테일러 급수로 sin x 근사 
# sin x = 시그마 n이 1에서 무한대 ( (-1)**(n+1) * x**(2n-1)/(2n-1)! )
from math import factorial, pi

def sin(x):
    x = float(x)
    result = 0
    n = 1
    term = x**(2*n-1)/factorial(2*n-1)
    
    while abs(term) > 1.0e-10: # 1.0e-1.0 이하에서는 컴퓨터에서 허용하는 오차 범위 외
        if n%2:
            result += term
        else:
            result -= term
        n += 1
        term = x**(2*n-1)/factorial(2*n-1)
        
    return result
```


```python
sin(pi)
```




    1.0348185903053497e-11




```python
# 7. 테일러 급수로 cos x 근사
# cos x = 시그마 n이 1에서 무한대 ( 1 - (-1)**(n+1) * x**(2n)/(2n)! )

def cos(x):
    x = float(x)
    result = 1
    n = 1
    term = x**(2*n)/factorial(2*n)
    
    while abs(term) > 1.0e-10: # 1.0e-1.0 이하에서는 컴퓨터에서 허용하는 오차 범위 외
        if n%2:
            result -= term
        else:
            result += term
        n += 1
        term = x**(2*n)/factorial(2*n)
        
    return result
```


```python
cos(pi)
```




    -0.9999999999243493




```python
# 8. sin x + cos x 값 리턴 함수
def trigonometric_Calculator(x):
    return sin(x)+cos(x)

```


```python
print(trigonometric_Calculator(pi))
```

    -0.9999999999140011
    


```python
print(trigonometric_Calculator(2*pi))
```

    0.9999999999801273
    
