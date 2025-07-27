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

# 제어문
# 조건문
## `if` statement
# 반복문
## `for` statement
## `while` statement
## 반복 제어
## 유용한 내장 함수 `map` & `zip`