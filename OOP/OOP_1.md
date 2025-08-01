# 절차 지향과 객체 지향
|절차 지향|객체 지향|
|-----|-----|
|데이터와 해당 데이터를 처리하는 함수(절차)가 분리|데이터와 해당 데이터를 처리하는 메서드를 하나의 객체로 묶음|
|함수 호출의 흐름이 중요|객체 간 상호작용과 메시지 전달이 중요|
|어떤 순서로 처리할까|어떤 객체가 이 문제를 해결할까? / 이 객체는 어떤 속성과 기능을 가질까?|
## 절차 지향 프로그래밍 (Procedural Programming)
- 함수와 로직 중심 작성
- 데이터를 순차적으로 처리
```python
name = 'Alice'
age = 25

def introduce(name, age):
    print(f'안녕하세요, {name}입니다. 나이는 {age}살입니다.')

introduce(name, age)
```
### 절차 지향 프로그래밍 특징
- 입력을 받고, 처리하고 결과를 내는 과정이 위에서 순차적으로 흐르는 형태
- 순차적인 명령어 수행
- 데이터와 함수 (절차)의 분리
- 함수 호출의 흐름이 중요
### 절차 지향 프로그래밍 한계
- 복잡성 증가
    - 프로그램 규모가 커질수록 데이터와 함수의 관리가 어려움
    - 전역 변수의 증가로 인한 관리 어려움
- 유지보수 문제
    - 코드 수정 시 영향 범위 파악이 어려움
## 객체 지향 프로그래밍 (Object Oriented Programming)
- 클래스(청사진;blueprint)는 설계도
- 인스턴스는 실제 물건 → 서로 독립적 (이제는 데이터를 중심으로 보겠다!)
- 파이썬에서도 클래스를 정의한 뒤 그 클래스를 바탕으로 여러 개의 인스턴스 생성 가능
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(name, age):
        print(f'안녕하세요, {name}입니다. 나이는 {age}살입니다.')

alice = Person('Alice', 25) # 인스턴스
alice.introduce() # 객체가 자신의 정보를 출력
```
## 객체 지향 프로그래밍 특징
- 프로그램을 데이터(변수)와 그 데이터를 처리하는 함수(메서드)를 하나의 단위(객체)로 묶어서 조직적으로 관리
- 데이터와 메서드의 결합
# 객체와 클래스
## 객체 (Object)
- 실제 존재하는 사물을 추상화 한 것
- 속성과 동작을 가짐
- 예를 들어 개를 품종과 나이라는 속성과 짖기, 뛰기와 같은 동작으로 표현 가능
### 객체의 특징
- 속성(Attribute): 객체의 상태와 데이터
- 메서드(Method): 객체의 행동과 기능
- 고유성: 각 객체는 고유한 특성을 가짐
## 클래스 (Class)
- 객체를 만들기 위한 설계도
- 데이터와 기능을 함께 묶는 방법을 제공
- 파이썬에서 타입을 표현하기 위한 방법
- 예를 들어 서류 양식이 클래스이면 양식을 채운 서류는 인스턴스
### 클래스 정의
클래스 이름은 파스칼 케이스(Pascal Case) 방식으로 작성 → 다른 변수/함수와 구분하기 위해
```python
class MyClass:
    pass
```
`__init__`메서드는 **생성자 메서드**로 불리며, 새로운 객체를 만들 때 필요한 초기값을 설정
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(name, age):
        print(f'안녕하세요, {name}입니다. 나이는 {age}살입니다.')
```
### 인스턴스 (Instance)
클래스를 통해 생성된 객체
- 클래스를 사용해 실제로 만들어진 객체
- 같은 클래스로 여러 인스턴스 생성 가능
- 각 인스턴스는 클래스 구조를 따라 동작하지만 서로 독립적인 데이터를 가질 수 있음
- 클래스가 설계도라면, 인스턴스는 그 클래스를 바탕으로 만들어진 실제 물건
```python
bob = Person('Bob', 25)
bob.introduce() # 안녕하세요. Bob입니다. 나이는 25살 입니다.
alice = Person('Alice', 21)
alice.introduce() # 안녕하세요. Alice입니다. 나이는 21살 입니다.
```
### 클래스와 인스턴스
F1Driver 클래스에 생성된 Max_Verstappen 인스턴스
- Max_Verstappen은 객체이다. ✅
- Max_Verstappen은 인스턴스이다. ❌
- Max_Verstappen은 F1Driver클래스의 인스턴스이다. ✅
### 클래스 구성 요소
**생성자 메서드**
- 인스턴스 생성 시 자동 호출되는 특별 메서드
- `__init__`이라는 메서드로 정의
- 인스턴스 초기화 담당
```python
class Person:
    def __init__(self, name, age):
        ...
```
**인스턴스 변수**
- 각 인스턴스별 고유한 특성
- `self.변수명`으로 정의
- 인스턴스마다 독립적인 값 유지
```python
class Person:
    def __init__(self, name, age):
        # 인스턴스 변수 정의
        self.name = name
        self.age = age
```
**클래스 변수**
- 모든 인스턴스가 공유하는 속성
- 클래스 내부에서 직접 정의
```python
class Person:
    # 클래스 변수 정의
    population = 0

    def __init__(self, name, age):
        self.name = name
        self.age = age
```
### 클래스 변수와 인스턴스 변수
- 클래스 변수와 동일한 이름으로 인스턴스 변수 생성 시 클래스 변수가 아닌 변수 먼저 참조
- `class.class_variable`로 참조 가능
```python
class Circle:
    pi = 3.14
    def __init__(self, radius):
        self.radius = radius

c1 = Circle(5)
c1.pi = 10
print(c1.pi) # 10
```
## 메서드 (Method)
### 메서드 종류
|인스턴스 메서드|클래스 메서드|스태틱 메서드|
|-------------|-----------|-----------|
|인스턴스의 상태를 변경하거나 해당 인스턴스의 특정 동작을 수행|인스턴스의 상태에 의존하지 않는 기능을 정의|클래스 및 인스턴스과 관계 없는 일반적인 기능을 수행|
||클래스 변수를 조작하거나 클래스 레벨의 동작을 수행||
### 인스턴스 메서드
- 인스턴스의 상태를 조작하거나 동작을 수행
- 인스턴스가 호출!
### 인스턴스 메서드 구조
- 클래스 내부에 정의되는 메서드 기본
- **반드시 첫번째 인자로 인스턴스 자신(`self`)을 받음
- 인스턴스 속성에 접근하거나 변경 가능
```python
class MyClass:
    def instance_method(self, arg1, ...):
        pass
```
>[!NOTE]
>**`self` 동작 원리**  
>`upper` 메서드를 사용해 문자열 `'hello'`를 대문자로 변경  
>`'hello'.upper()`  
>실제 파이썬 내부에서 작동하는 방식  
>`str.upper('hello')`
>- `str`클래스가 `upper`메서드를 호출했고, 그 첫번째 인자가 문자열 인스턴스가 호출한 것
>    - 인스턴스 메서드의 첫번째 인자가 반드시 자기 자신인 이유
>- `'hello'.upper()`은 `str.upper('hello')`를 객체 지향 방식의 메서드로 호출하는 표현 (단축형 표현)
>    - 'hello'라는 문자열 객체가 단순히 어딘가의 함수로 들어가는 인자로 활용되는 것이 아님
>    - 객체 스스로 메서드를 호출하고 코드를 동작하는 객체 지향적인 표현
### 생성자 메서드 (Constructor Method)
인스턴스 객체가 생성될 때 자동으로 호출되는 메서드 → 인스턴스 변수들의 초기값을 초기화
```python
class Person:
    def __init__(self, name):
        # 왼쪽 name : 인스턴스 변수 name
        # 오른쪽 name : 생성자 메서드의 매개변수 이름
        self.name = name
        print("인스턴스가 생성되었습니다.")
     

    def greeting(self):
        print(f'안녕하세요 {self.name}입니다.')

person1 = Person('아이유') # 인스턴스가 생성되었습니다.
person1.greeting() # 안녕하세요 아이유입니다.
# Person.greeting(person1)
```
### 클래스 메서드
- 클래스 변수(공통 속성)를 조작하거나 클래스 레밸의 동작을 수행
- `@classmethod`를 사용하면 클래스 자체를 호출 가능
- 그 안에서 클래스 변수를 변경하거나 전체 동작 정의 가능
```python
class MyClass:
    ...
    @classmethod
    def class_method(cls, arg1, ...):
        pass
```
→ `cls`는 매개변수의 이름일 뿐이며 다른 이름으로 설정 가능하지만 다른 이름으로 사용하지 않을 것을 강력하게 권장 (불문율 같은 것임!)
```python
class Person:
    population = 0

    def __init__(self, name):
        self.name = name
        Person.increase_population()
    
    @classmethod
    def increase_population(cls):
        cls.poplulation += 1
```
### 스태틱(정적) 메서드 (Static Method)
- 클래스 인스턴스와 상관없이 독립적으로 동작하는 메서드
- `@staticmethod`를 사용하면 클래스 내부에 있지만 어떤 객체와도 관계없이 동작하는 메서드 생성 가능
```python
class MyClass:
    ...
    @staticmethod
    def static_method(arg1, arg2, ...):
        pass
```
```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

print(MathUtils.add(3, 5)) # 8
```
# 객체 지향 프로그래밍 연습: 입출금이 가능한 은행 계좌 클래스 만들기
1. `def __init__(self, owner, balance = 0)`
2. `interest_rate = 0.03`
```python
class BankAccount:
    interrest_rate = 0.03

    def __init__(self, owner, balance = 0):
       self.owner = owner
       self.balance = balance 
```  
3. `deposit(self, amount)`
4. `withdraw(self, amount)`
```python
    def deposit(self, amount):
        self.balance += amount

    def withdraw(self, amount):
        if amount > balance:
            print('잔액 부족으로 출금을 진행할 수 없습니다.')
        else:
            self.balance -= amount
```
6. `set_interest_rate(cls, rate)`
```python
    @classmethod
    def set_interest_rate(cls, rate):
        cls.interest_rate = rate
```
8. `is_positive(amount)`
```python
    @staticmethod
    def is_positive(amount):
        return amount > 0
```
