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
### 기본 인자값 (Default Argument Values)
### 키워드 인자 (Keyword Arguement)
### 임의의 인자 목록 (Arbitrary Argument Lists)
### 임의의 키워드 인자 목록 (Arbitrary Keyword Argument Lists)
### 함수 인자 권장 작성 순서

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
## global 키워드

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
## Unpacking
