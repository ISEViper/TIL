# 함수
특정 작업을 수행하기 위한 **재사용 가능한 코드 묶음**
### 함수를 사용하는 이유
- 두 수의 합을 구하는 함수를 정의하고 사용함으로써 코드의 중복을 방지
- **재사용성**이 높아지고, 코드의 **가독성**과 **유지보수성** 향상
### 함수 호출(function call)
`function_name(arguments)`
```python
def get_sum(num1, num2):
    return num1 + num2

x = 5
y = 3
print(get_sum(5, 3)) # 8
```
## 함수 구조
```python
def greet(name):   # --> Input (name: parameter)
  """이 함수는 입력된 이름으로 인사말을 출력합니다.""" # --> Docstring
  message = f"안녕하세요, {name}님!"  # --> function body
  print(message) # --> Output

greet("철수")  # 출력: 안녕하세요, 영희님! 
```
1. 함수 정의
   - 함수 정의는 `def`(define) 키워드로 시작
   - `def` 이후에는 함수 이름 작성
   - 괄호 안에는 매개변수를 정의하고, 매개변수(parameter)는 함수에 전달되는 값
2. 함수 body
   - 콜론(:) 다음에 들여쓰기 된 코드 블록
   - 함수가 실행 될 때 수행되는 코드
3. Docstring
   - 함수 body 앞에 함수가 어떻게 작동하는 설명하는 주석
4. 함수 반환값
   - body에서 실행한 값 결과를 반환
   - `return`이 있는 경우 반환하는 값을 명시
   - `return`문은 함수를 종료시키고, 결과를 호출 부분에 반환
   - `return` 이후에 적는 코드는 실행이 안됨
5. 함수 호출
   - 함수 사용을 위해 호출이 필요
   - 함수 이름과 인자를 조건에 맞게 적으면 값이 반
## 함수와 반환 값
>[!WARNING]
>**`print()`는 반환값이 없음**
>`print()`는 말그대로 괄호 안에 있는 값을 출력해줄뿐, 값을 반환해주는 것이 아님  
> →확성기처럼 소리를 전달하지만 확성기는 다시 말을 돌려주지는 않음
>```python
>result = print(1)
>print(result)  # None
>```
>`return`과 헷갈리기 쉬운 내용이므로 `print`는 메뉴판의 음식이고,`return`은 서빙된 음식이라 생각하면 편함  


# 매개변수와 인자
### 매개변수(parameter)
함수 정의 시, 함수가 받을 값을 나타내는 변수
### 인자(argument)
함수를 호출할 때, 실제로 전달되는 값
```python
def make_mul(num1, num2):
    return num1 * num2

x, y = 5, 3
print(make_mul(x, y)) # 15 
```
여기서 num1, num2는 매개변수, x, y는 인자
## 다양한 인자 종류
### 위치 인자 (Positional Argument)
- 함수 호출 시 위치에 따라 전달되는 인자
- 위치 인자는 함수 호출시 반드시 인자를 전달해야 함
```python
def greet(name, age):
   print(f'{name}님 안녕하세요. 현재 {age}세 입니다.')

greet('Alice', 25) # 안녕하세요 'Alice'님. 현재 25세 입니다.
greet(25, 'Alice') # 안녕하세요 25님. 현재 'Alice'세 입니다.
greet(25) # TypeError: greet() missing 1 required positional argument: 'age'
```
### 기본 인자값 (Default Argument Values)
- 함수 호출 시 해당 인자에 따로 적은 내용이 없으면 매개변수에 설정한 기본값이 전달되는 인자
```python
def greet(name, age = 30):
   print(f'{name}님 안녕하세요. 현재 {age}세 입니다.')

greet('Dave') # 안녕하세요 'Dave'님. 현재 30세 입니다.
greet('Alice', 25) # 안녕하세요 'Alice'님. 현재 25세 입니다.
```
### 키워드 인자 (Keyword Arguement)
- 함수 호출 시 인자의 이름과 값을 함께 적는 인자
- 매개변수와 인자를 일치시키지 않고 특정 인자에 전달 가능
- 단, 키워드 인자는 위치 인자 뒤에 위치해야 함 (키워드 인자가 값만 있는 것보다 뒤에 있으면 안됨)
```python
def greet(name, age):
   print(f'{name}님 안녕하세요. 현재 {age}세 입니다.')

greet(name = 'Dave', age = 30) # 안녕하세요 'Dave'님. 현재 30세 입니다.
greet(age = 25, name = 'Alice') # 안녕하세요 'Alice'님. 현재 25세 입니다.
greet(age = 25, 'Alice') # SyntaxError: positional argument follows keyword argument
```
### 임의의 인자 목록 (Arbitrary Argument Lists)
- 함수 호출 시 인자가 얼마나 들어가야 할 지 모를때 설정하는 인자
- `*` 뒤에 이름을 붙이면 되는데 보통은 `args`를 많이 활용
- 여러 개의 인자를 튜플로 처리
```python
def calculate_sum(*args):
   print(args) # (1, 100, 200, 500)
   print(type(args)) # <class 'tuple'>

calculate_sum(1, 100, 200, 500)
```
### 임의의 키워드 인자 목록 (Arbitrary Keyword Argument Lists)
- 정해지지 않은 키워드 인자를 처리하는 인자
- `*` 뒤에 이름을 붙이면 되는데 보통은 `kwargs`를 많이 활용
- 여러 개의 인자를 딕셔너리로 처리
```python
def users_info(*kwargs):
   print(kwargs) # {name : 'Eva', age: '30'}

users_info(name = 'Eva', age = '30')
```
### 함수 인자 권장 작성 순서
위치 → 기본 → 가변 → 가변 순으로 작성  
- 호출 시 인자 순서의 혼란을 줄이기 위함
- 다만 무조건 지켜야 하는 것은 아니고 상황에 따라 유연하게 작성

# 재귀 함수 (Recursion function)
함수 내부에서 자기 자신을 반복하는 함수 (factorial이 대표적인 case!)
```python
def factorial(x):
    if x == 0:
        return 1
    else:
        return x * factorial(x - 1)

print(factorial(5)) # 120
```
### 재귀함수 특징
- 특정 알고리즘 식을 표현할 때 변수 사용이 줄어들고 가독성이 높아짐
- 1개 이상의 base case(종료되는 상황)이 존재하고 수렴하도록 작성
- 다만, 종료 조건을 명확하게 하지 않으면 스택 오버플로우 발생

# 내장 함수 (Built-in function)
Python에서 기본적으로 제공하는 내장 함수(`import` 없이 사용 가능)
```python
my_list = [1, 2, 3, 4, 5]

print(len(my_list)) # 5
print(sum(my_list)) # 15
print(max(my_list)) # 5
print(min(my_list)) # 1
print(sorted(my_list, reverse = True)) # [5, 4, 3, 2, 1]
```
# 함수와 Scope
### Python의 범위 (Scope)
함수는 코드 내부에 **local scope**를 생성하며, 그 외 공간인 **global scope**로 구분
### 범위와 변수 관계
- scope
   - global scope: 코드 어디에서는 참조할 수 있는 공간
   - local scope: 함수가 만든 scope (함수 내부에서만 참조 가능)
- variable
   - global variable: global scope에 정의된 함수
   - local variable: local scope에 정의된 함수
### 변수의 수명 주기
- 변수의 수명 주기는 변수가 선언되는 위치와 scope에 따라 결정
- built-in scope
   - 파이썬이 실행된 이후부터 영원히 유지
- global scope
   - 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
- local scope
   - 함수가 호출될 때, 생성되고, 함수가 종료될 때까지 유지  
### 이름 검색 규칙
**LEGB Rule** 이라고도 하며 아래와 같은 순서로 이름을 찾아나감
1. Local Scope: 지역범위 (현재 작엽 중인 범위)
2. Enclosed Scope: 지역 범위 한 단계 위 범위
3. Global Scope: 최상단에 위치한 범위
4. Built-in scope: 모든 것을 담고 있는 범위
```python
x = 'global'

def outer():
    x = 'enclosed'
    
    def inner():
        x = 'local'
        print(x)
    
    inner()

outer()

print(x) # local global
'''
inner() 함수 안에서 x = 'local' 이라는 지역 변수(Local Scope) 가 정의되어 있는 것을 먼저 출력하고
outer() 함수에 있는 x = 'enclosed'는 return이나 print가 없기 때문에 따로 출력할 수 있는 방법이 없고
그 이후에 global scope에 있는 'global'이 출력
'''
```
## global 키워드
- 변수의 스코프를 전역 범위로 지정하기 위해 사용
- 단, global 키워드 선언 전에 참조 불가하고, 매개변수에도 사용 불가
```python
num = 0 # 전역 변수

def increment():
		global num  # num를 전역 변수로 선언
		num += 1

print(num) # 0
increment()
print(num) # 1
```

# 함수 스타일 가이드
## 함수 이름 작성 원칙
### 기본 규칙
- 소문자와 언더스코어(_) 사용
- 동사로 시작하여 함수 동작 설정
- 약어 사용 지양
### 함수 이름 구성 요소
- 동사 + 명사 : `save_user()`
- 동사 + 형용사 + 명사 : `calculate_total_users()`
- get/set 접두사 : `set_username()`
>[!Note]
>- 이름만으로 함수가 어떤 역할을 하고 있는지 알아야 함
>- `True`/`False`를 반환한다면 `is` 또는 `has`로 시작하는 것이 좋음
>- 프로젝트 전체에 일관성을 유지하는 것이 좋음
## 단일 책임 원칙
모든 객체는 하나의 명확한 목적과 책임을 가져야 함
### 함수 설계 원칙
1. 명확한 목적
   - 이 함수가 어떤 목적을 가지고 한 가지 작업을 수행하는지 명확하게 표현
2. 책임 분리
    - 함수 내부에서 여러 역할을 가지고 있는 것이 아닌 독립적으로 작동할 수 있도록 설계
3. 유지보수성
   - 함수를 유지보수할 때 작은 범위로 나누어 관리할 수 있도록 하는 것이 좋음 (여기저기 꼬여있으면 하나를 고치면 다른 것이 안되는 경우가 많음 → 본인 경험담)

# Packing & Unpacking
## Packing
여러 개의 데이터를 하나의 컬렉션으로 모아 담는 과정
### 기본 원리
- 여러 개의 값을 하나의 튜플로 묶는 파이썬의 기본 동작
- 한 변수에 콤마(,)로 구분된 값을 넣으면 자동으로 튜플을 처리
1. '*'을 활용한 패킹 (함수 매개변수 작성 시)
   - 남은 위치 인자들을 튜플로 묶기
   ```python
   def my_func(*args):
      print(args) # (1, 2, 3, 4, 5)
      print(type(args)) # <class 'tuple'>

   my_func(1, 2, 3, 4, 5)
   ```
2. '**'을 활용한 패킹 (함수 매개변수 작성시)
   - 남은 키워드 인자들을 딕셔너리로 묶기
   ```python
   def my_func(**kwargs):
      print(kwargs) # {'a' : 1, 'b' : 2, 'c' : 3}
      print(type(kwargs)) # <class 'dict'>

   my_func(a = 1, b = 2, c = 3)
   ```
## Unpacking
컬렉션에 담겨있는 데이터들을 개별 요소로 펼쳐 놓는 과정
### 기본 원리
- 튜플이나 리스트 등의 객체의 요소들을 개별 변수에 할당
- 시퀀스 언패킹 또는 다중 할당이라고도 부름
1. '*'을 활용한 언패킹 (함수 인자 전달)
   - 리스트나 튜플 앞에 *을 붙여 각 요소를 함수의 개별 위치 인자로 전달
   ```python
   def my_function(x, y, z):
		print(x, y, z)

   names = ['alice', 'jane', 'peter']
   my_function(*names) # alice jane peter
   ```
2. '**'을 활용한 언패킹 (딕셔너리 → 함수 키워드 인자)
   - 딕셔너리 앞에 **를 붙여 {키 : 값} 쌍을 키=값 형태의 키워드 인자로 전달
   ```python
   def my_function(x, y, z):
		print(x, y, z)

   my_dict = {'a' : 1, 'b' : 2, 'c' : 3}
   my_function(**my_dict) # 1 2 3