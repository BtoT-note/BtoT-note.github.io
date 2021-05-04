### 세자리수*세자리수 연산 알고리즘

 세 자리 수) × (세 자리 수)는 다음과 같은 과정을 통하여 이루어진다.

       472 ...1
      *385 ...2

    -----
      2360 ...3
     3776  ...4
    1416   ...5

    -----
    181720 ...6

 (1)과 (2)위치에 들어갈 세 자리 자연수가 주어질 때 (3), (4), (5), (6)위치에 들어갈 값을 구하는 프로그램을 작성하시오.


```python
import time
time.strftime("%Y/%m/%d")
```




    '2021/05/04'



#### Step 1
 1. 함수 이름?  
 2. 입력? 첫째 줄에 (1)의 위치에 들어갈 세 자리 자연수가, 둘째 줄에 (2)의 위치에 들어갈 세자리 자연수가 주어진다.
 3. 출력? 첫째 줄부터 넷째 줄까지 차례대로 (3), (4), (5), (6)에 들어갈 값을 출력한다.
 4. 출력 타입? int


```python
# 5. 입력값 받을 변수 지정

first_ThreeFigure = input()
second_ThreeFigure = input()

```

    472
    385
    


```python
# 6. second_ThreeFigure에서 각 자리 수를 First와 곱하는 코드

int(first_ThreeFigure)*int(second_ThreeFigure[-1])
```




    2360




```python
# 7. for문으로 각 자리 값 곱하고 출력, 계산값까지 출력하는 코드

for i in range(len(first_ThreeFigure)):
    sub = int(first_ThreeFigure)*int(second_ThreeFigure[-i-1])
    print(sub)
    result += sub*10**(i)
print(result)

```

    2360
    3776
    1416
    363440
    


```python
# 7. 세자리수 곱셈 알고리즘
print("input")
first_ThreeFigure = input()
second_ThreeFigure = input()

print("\noutput")
for i in range(len(first_ThreeFigure)):
    sub = int(first_ThreeFigure)*int(second_ThreeFigure[-i-1])
    print(sub)
    result += sub*10**(i)
print(result)

```

    input
    472
    385
    
    output
    2360
    3776
    1416
    908600
    
