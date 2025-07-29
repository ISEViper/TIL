# 모듈
- 한 파일로 묶인 변수와 함수의 모음
- 특정한 기능을 하는 코드가 작성된 파이썬 파일 (`.py`)
### 모듈 예시
- `math` 내장 모듈
    - 파이썬이 미리 작성해 둔 수학 관련 변수와 함수가 작성된 모듈
## 모듈 활용
### `import`문 활용
- 같은 이름의 함수가 여러 모듈에 있을 때 충돌 방지 가능
- '.(dot)'연산자
    - 점의 왼쪽 객체에서 점의 오른쪽 이름을 찾으라는 의미
    - `module_name.variable_name`
```python
import math

print(math.pi) # 3.141592653589793
print(math.sqrt(4)) # 2
```
### `from`절 활용
코드가 짧고 간결해짐
```python
from math import pi, sqrt

print(pi) # 변수명
print(sqrt(16)) #함수명
```
- 단점
    - 정의된 모듈의 위치를 알기 어려워 명시적이지 않을 수 있음
    - 사용자가 선언한 변수 또는 함수가 겹치면 모듈에서 정의한 값이나 동작이 이루어지지 않을 수 있음
```python
from math import math
math_result = sqrt(16) # 실수형 4.0

def sqrt(x):
    return str(x ** 0,5) # 사용자 정의 sqrt 함수

math_result = sqrt(16) # 문자열 4.0
```
### `from`절 사용 시 주의사항
서로 다른 모듈에서 `import`된 변수나 함수의 이름이 같은 경우 이름 충돌 발생
→ 마지막에 `import` 된 것이 이전 것을 덮어쓰기 때문에, 나중에 `import` 한 것만 유효
```python
from math import sqrt  # math.sqrt 먼저 import
from my_math import sqrt # my_math.sqrt가 math.sqrt를 덮어씀

result = sqrt(9) # math.sqrt가 아닌 my_math.sqrt가 사용
```
모든 요소를 한 번에 `import` 하는 *은 권장하지 않음
```python
from math import *
from my_math import sqrt, tangent # 이러면 어떤 것이 겹치는지 알 수 없음

a = 100
b = 200
e = 400 # math 모듈에 있는 자연상수 e를 활용할 수 없음
```
### `as` 키워드
`as` 키워드를 사용해 별칭(alias)을 부여
→ 두 개 이상의 모듈에서 동일한 이름의 변수, 함수 클래스 등을 가져올 때 발생하는 이름 충돌 방지
```python
from math import sqrt
from my_math import sqrt as my_sqrt

sqrt(4)
my_sqrt(4)
```
`import`되는 함수나 변수명이 너무 길거나 자주 사용하는 경우 `as` 키워드로 별칭 정의해 쉽게 사용
```python
import pandas as pd
import matplotlib.pyplot as plt

# 별칭을 부여하지 않으면 길고 불편함
df = pandas.DataFrame()
matplotlib.pyplot.plot(x, y)

# 별칭을 사용하면 짧고 편리
df = pd.DataFrame()
plt.plot(x, y)
```
## 사용자 정의 모듈
### 직접 정의한 모듈 사용
`my_math.py` 생성하여 두 수의 합을 구하는 add 함수 생성
```python
def add(x, y):
    return x + y
```
같은 위치에 `sample.py` 파일을 생성하고 my_math 모듈의 add 함수 `import` 후 add 함수 추출
```python
import my_math

print(my_math.add(30, 10)) # 40
```
# 파이썬 표준 라이브러리
**Python Standard Library**
파이썬 언어와 함께 제공되는 다양한 모듈과 패키지의 모음  
참고사이트: [PSL](https://docs.python.org/ko/3.11/library/index.html)
## 패키지
연관된 모듈들을 하나의 디렉토리에 모아놓은 것
### 패키지의 활용 목적
모듈 들의 이름 공간을 구분하여 충돌을 방지하고 모듈들을 관리하고 할 수 있도록 돕는 역할
> **본인이 패키지를 만들 때 주의사항**
> - 너무 많은 기능이 한 파일에 몰려있으면 사용자가 헷갈릴 수 있음
> - 비슷한 기능은 묶고, 없는 것은 나누는 것이 사용하기 편함
> - 폴더/파일명은 소문자 + 언더스코어(_)를 쓰는게 깔끔하고 표준적
### 패키지의 종류
1. PSL(Python Standard Library) 내부 패키지
    - 파이썬을 설치하면 자동으로 사용할 수 있는 기본 패키지
    - `math`, `os`, `sys`, `random` 등이 있음
    - 따로 설치할 필요 없이 `import`하여 바로 사용 가능
2. 파이썬 외부 패키지
    - 필요한 기능을 사용하기 위해 직접 설치해 쓰는 패키지
    - 사용할 패키지를 설치할 떄 `pip`를 활용
>[!NOTE]  
>**`pip`란?**  
>외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템  
>- PyPI(Python Package Index)에 저장된 외부 패키지를 설치하는 것
>- 직접 만든 패키지도 여기에 등록해서 활용 가능
### `pip`를 활용한 패키지 설치
```bash
$ pip install SomePackage
$ pip install SomePackage == 1.0.5
$ pip install SomePackage >= 1.0.4
```
> - 다양한 패키지 버전이 존재하기 때문에 호환성 이슈에 대한 확인 필요
> - `requirements.txt`로 개발환경을 통일시키는 것이 좋음
### 외부 패키지 설치 및 사용 예시
`request` 패키지 활용 예시
- 먼저 패키지 설치 진행
```bash
$ pip install requests
```
- 이후 패키지를 `import` 하여 활용
```python
# HTTP 요청을 보내기 위한 requests 패키지를 불러옵니다.
import requests

# 데이터를 요청할 API의 주소(URL)를 문자열로 정의합니다.
# Nager.Date API를 사용하여 2025년 대한민국의 공휴일 정보를 요청합니다.
url = "https://date.nager.at/api/v3/publicholidays/2025/KR"

# requests.get(url)을 통해 해당 URL에 GET 요청을 보냅니다.
# .json() 메서드를 사용하여 서버로부터 받은 JSON 형식의 응답(response)을
# 파이썬 딕셔너리 또는 리스트 형태로 변환하여 response 변수에 저장합니다.
response = requests.get(url).json()

# 파이썬 객체로 변환된 공휴일 정보를 화면에 출력합니다.
print(response)
```

# 제어문 (Control Statement)
코드의 실행 흐름의 제어하는데 사용되는 구문
- **조건**에 따라 코드 블록을 실행하거나 **반복**적으로 코드 실행
- 조건문 : `if`, `else`, `else`
- 반복문: `for`, `while` (`break`, `continue`로 반복 제어)
# 조건문
## `if` statement
### 조건문의 기본 구조
- `if` 문
    - 조건문의 기본 형태
    - `if`문 내부의 코드가 실행 
- `elif` 문
    - 이전 조건을 만족하지 못하고 추가 조건이 필요할 때 사용
    - 여러 `elif` 활용 가능
- `else` 문
    - 모든 조건을 만족하지 않을 때 실행
```python
# 조건 작성은 반드시 표현식
if 조건1:
	조건 1을 만족할 때 실행할 코드
elif 조건2:
	조건 2을 만족할 때 실행할 코드
elif 조건3:
	조건 3을 만족할 때 실행할 코드
else:
	모든 조건을 만족하지 않으면 실행할 코드
```
### 조건문 예시
```python
score = 97

if score > 95:
	print('축하합니다.')
else:
	print('수고하셨습니다.')

print(score) # 축하합니다.
```
```python
score = 87

if score > 95:
	print('축하합니다.')
else:
	print('수고하셨습니다.')

print(score) # 수고하셨습니다.
```
### 복수 조건문
조건식을 동시에 검사하는 것이 아니라 순차적으로 비교
```python
## 결과: 매우 나쁨
dust = 155

if dust > 150:
    print('매우 나쁨')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
```
### 중첩 조건문
`if`문 내에 또 다른 `if`문 작성 가능
```python
# 출력: 매우 나쁨
#      위험해요! 나가지 마세요!
dust = 480

if dust > 150:
    print('매우 나쁨')
    if dust > 300:
        print('위험해요! 나가지 마세요!')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
```

# 반복문
주어진 코드 블록을 여러 번 반복해서 실행하는 구문
### 반복문의 종류
1. `for`문  
반복 가능(iterable)한 객체의 요소를 반복하는 데 사용
2. `while` 문  
`while`이 참일 동안에 반복하는 함수(끝나려면 언젠가 `False`가 되어야 함)
## `for` statement
반복 가능(iterable)한 객체의 요소를 반복하는 데 사용
```python
for 변수 in 반복 가능한 객체:
    코드 블록
```
> [!NOTE]  
> **반복 가능한 객체(iterable)**  
> 요소를 하나씩 반환할 수 있는 모든 객체  
> `list`, `tuple`, `str` 같은 시퀀스 자료형 뿐만 아니라 `dict`, `set`과 같은 비 시퀀스 자료형도 반복 가능한 객체
### `for`문 작동 원리
1. 리스트 내 첫 항목이 반복변수(num)에 할당되고 코드 블록이 실행
2. 순서대로 코드블록이 실행
3. 더 이상 반복 변수가 없다면 종료
```python
my_list = [1, 2, 3]
for num in my_list: # num: 반복 변수
    print(num)
"""
1
2
3
"""
```
### 문자열 순회
```python
country = 'Korea'

for char in country:
	print(char)

# 출력
"""
K
o
r
e
a
"""
```
### `range` 순회 (**for문에서 가장 많이 활용**)
```python
for i in range(1, 5):
    print(i)
"""
1
2
3
4
"""
```
### 딕셔너리 순회
```python
my_dict = {'max' : 'red_bull', 'lewis' : 'ferrai', 'oscar' : 'mclaren'}
for driver in my_dict:
    print(driver)
    print(my_dict[driver])
"""
'max'
'red_bull'
'lewis'
'ferrai'
'oscar'
'mclaren'
"""
```
### 인덱스로 리스트 순회
```python
my_list = [20, 30, -50, 3, 134]

for i in range(len(my_list)):
    my_list[i] *= 2

print(my_list) # [40, 60, -100, 6, 268]
```
### 중첩된 반복문
첫 바깥쪽 중첩에 접근하고 먼저 안쪽의 중첩이 다 돌고 다음 과정을 반복하는 과정을 수행 
```python
outers = ['a', 'b']
inners = ['1', '2']

for outer in outers:
    for inner in inners:
        print(outer, inner)

"""
'a', '1'
'a', '2'
'b', '1'
'b', '2'
"""
```
### 중첩 리스트 순회
```python
my_list = [['a', 'b'], ['c', 'd']]

for elem in my_list:
    print(elem)
"""
['a', 'b']
['c', 'd']
"""

for elem in my_list:
    for element in elem:
        print(element)
"""
'a'
'b'
'c'
'd'
"""
```  
## `while` statement
주어진 조건식이 참(True)인 동안 코드를 반복해서 실행 == 주어진 조건식이 거짓(False)인 경우 반복 종료
```python
while 조건식:
    코드 블록
```
### `while`문 작동 원리
1. `while`문 조건식 확인
    - 조건식이 True인 경우 코드 블록 실행
    - 조건식이 False인 경우 반복 종료
2. 코드 블록 실행이 마무리 되면 다시 `while` 조건문 확인
```python
a = 0

while a < 3:
    print(a)
    a += 1

print('끝')

"""
0
1
2
끝
"""
```
> [!WARNING]
> **`while`문 주의사항**  
> `while`문은 종료조건이 없으면 무한 반복에 빠지게 되기 때문에 반드시 종료 조건을 설정해야 함
> - `while` 문 시작 전 조건에 사용할 변수를 초기화 하는 것이 좋음
> - 혹시 모를 상황에 대비해 `break`를 활용

>[!NOTE]  
> `for`문 vs `while`문  
> **`for`문**
> - 반복 가능한 데이터 구조(iterable)를 하나씩 순회하며 반복
> - 반복 횟수가 명확히 정해져 있는 경우에 유용함
> 
> **`while`문**  
> - 주어진 조건식이 True인 동안 반복
> - 반복 횟수가 불명확하거나 조건에 따라 반복을 종료해야 하는 경우에 사용
## 반복 제어
`for`문과 `while`문은 매 반복마다 모든 코드를 실행하지만 때때로 일부만 실행하느 ㄴ것이 필요한 경우가 있음
- 반복 제어문은 반드시 반복문 내에 사용
- 중첩 반복문인 경우 해당 키워드가 작성된 코드 블록의 반복 흐름만 제어
- 과도하게 사용하면 가독성이 떨어지므로 필요한 상황에서만 사용
### `break`
- 해당 키워드를 만나게 되면 남은 코드를 무시하고 반복 종료
- 반복이 종료되기 위한 명확한 조건이 있어야 함
```python
for i in range(10):
    if i == 5:
        break
    print(i) # 0 1 2 3 4
```
### `continue`
- 해당 키워드를 만나게 되면 다음 코드를 무시하고 다음 반복을 수행
```python
for i in range(10):
    if i % 2 == 0:
        continue
    print(i) # 1 3 5 7 9
```
## 유용한 내장 함수 `map` & `zip`
### `map` 함수
`map(function, iterable)`  
반복 가능한 데이터 구조(iterable)의 모든 요소에 함수(function)을 조회하고 그걸 map object로 묶어서 반환
```python
numbers = [1, 2, 3]
result = map(str, numbers)

print(result) # <map object at 0x00000239C915D760>
print(list(result))  # ['1', '2', '3']
```
> [!TIP]  
> `map` 함수 활용법
> ```python
> numbers = input().split()
> print(numbers) # ['1', '2', '3']
> test = list(map(int, input().split()))
> print(test) # [1, 2, 3]
> ```
### `zip` 함수
`zip(*iterable)`  
여러 개의 반복 가능한 데이터 구조(*iterable)을 묶어 같은 위치에 있는 값들을 하나의 튜플로 만든 뒤 그걸 zip object로 묶어서 반환
- 반복 가능한 자료형만 넣을 수 잇음
- 반복 가능한 자료형의 길이가 다른 경우 짧은 것을 기준으로 묶음
```python
team = ['red_bull', 'mercedes', 'mclaren']
driver = ['max', 'george', 'lando']

f1 = zip(team, driver)

print(f1) # <zip object at 0x000001FE5ADB38C0>
print(list(f1)) # [('red_bull', 'max'), ('mercedes', 'george'), ('mclaren', 'lando')]
```
> [!TIP]  
> `zip` 함수 활용법
> ```python
> kr_scores = [10, 20, 30 ,40]
> math_scores = [30, 10, 40 ,20]
> eng_scores = [20, 40, 10, 30]
> 
> for test_score in zip(kr_socres, math_scores, eng_scores):
>   print(test_score)
> 
> """
> (10, 20, 40)
> (20, 40, 20)
> (30, 50, 30)
> (50, 70, 50)
> """
> ```