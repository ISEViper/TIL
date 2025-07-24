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

# 재귀 함수

# 내장 함수

# 함수와 Scope
## global 키워

# 함수 스타일 가이드
## 함수 이름 작성 원칙
## 단일 책임 원칙

# Packing & Unpacking
## Packing
## Unpacking
