# 상속
한 클래스(부모)의 속성과 메서드를 다른 클래스(자식)가 물려받는 것
### 상속이 필요한 이유
1. 코드 재사용
   - 상속을 통해 기존 클래스의 속성에 메서드 재사용
   - 기존 클래스를 수정하지 않고도 기능 확장 가능
2. 계층 구조
   - 상속을 통해 기존 클래스들 간의 계층 구조 형성 가능
   - 부모 클래스와 자식 클래스 간의 관계 표현하고, 더 구체적인 클래스 만들기 가능
3. 유지 보수 용이성
   - 상속을 통해 기존 클래스 수정이 필요한 경우, 해당 클래스만 수정하면 되므로 유지보수가 용이해짐
   - 코드의 일관성을 유지하고 범위 최소화 가능
## 클래스 상속
### 상속 없이 구현하는 경우
- 상속 없이 구현하는 경우 학생/교수 정보를 별도로 표현하기 어려움
- `Person class`만을 사용하는 경우 학생과 교수가 가지는 고유 속성을 표현하기 어려움
- 나이와 이름만으로는 직업 정보를 판단하기 어려움
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):
        print(f'안녕하세요. {self.name}입니다.')

s1 = Person('김교수', 45)
s2 = Person('홍길동', 22)

s1.talk() # 안녕하세요. 김교수 입니다.
s2.talk() # 안녕하세요. 홍길동 입니다.
```
- 클래스를 분리했지만 메서드가 중복으로 정의될 수 있음
- 중복되고 있는 속성 `name`, `age`와 메서드 `talk`를 부모 클래스에서 한 번만 정의
- 필요한 클래스들이 이 부모 클래스에서 물려받아 사용 가능
```python
class Professor:
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department

    def talk(self): # 중복
        print(f'안녕하세요. {self.name}입니다.')
```
```python
class Student:
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa

    def talk(self): # 중복
        print(f'안녕하세요. {self.name}입니다.')
```
### 상속을 사용한 계층 구조 변경
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):
        print(f'안녕하세요. {self.name}입니다.')

class Student(Person):
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa

class Professor(Person):
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department

s1 = ('홍길동', 22, 3.8)
s2 = ('김교수', 45, '산업공학과')

s1.talk() # 안녕하세요. 홍길동입니다.
s2.talk() # 안녕하세요. 김교수입니다.
```
## 메서드 오버라이딩
부모 클래스의 메서드를 같은 이름, 같은 파라미터 구조로 다시 정의하는 것
- 자식 클래스에서 메서드를 다시 정의하면 부모 클래스 메서드 대신 자식 클래스 메서드가 실행
- 오버라이딩은 동일한 이름과 매개변수를 사용하지만, 내부 동작을 원하는대로 바꿀 수 있게 함
- 부모 클래스의 기능을 유지하면서도 일부 동작을 맞춤형으로 바꾸고 싶을 때 유용
```python
class Animal:
    def eat(self):
        print('동물이 먹는 중')

class Dog(Animal):
    # 부모 클래스(Animal)의 eat 메서드를 오버라이딩(재정의)
    def eat(self):
        print('개가 먹는 중')

my_dog = Dog()
my_dog.eat() # 개가 먹는 중
```
> [!NOTE]
> **오버로딩(Overloading)**
> - 같은 이름 다른 파라미터를 가진 여러 메서드를 정의하는 것 (파이썬은 미지원)
> - 파이썬은 실제로 하나의 메서드만 인식하며, 인자의 형태가 다르다는 이유로 메서드를 여러 개 불러주지 않음
> - 파이썬은 `*args`, `**kwargs` 같이 임의의 인자를 받을 수 있기 때문에 필요성이 낮아 미지원한다고 생각하면 편함
> - 자바의 오버로딩 예시 코드
> ```java
> class Calculator {
>    public int add(int a, int b) {
>        return a + b;
>    }
>
>    public double add(double a, double b) {
>        return a + b;
>    }
>
>    public int add(int a, int b, int c) {
>        return a + b + c;
>    }
> }
>
> public class Main {
>    public static void main(String[] args) {
>        Calculator calc = new Calculator();
>        System.out.println(calc.add(1, 2));        // 3
>        System.out.println(calc.add(1.5, 2.5));    // 4.0
>        System.out.println(calc.add(1, 2, 3));     // 6
>    }
> }
> ```
## 다중 상속
- 둘 이상의 상위 클래스로부터 여러 행동이나 특징을 상속받을 수 있음
- 상속받은 모든 클래스의 요소 활용 가능
- 중복된 속성이나 메서드가 있는 경우 **상속 순서에 의해 결정**
```python
class Person:
   def __init__(self, name):
      self.name = name

   def greeting(self):
      return f'안녕, {self.name}'

class Mom(Person):
   gene = 'XX'

   def swim(self):
      return '엄마가 수영'

class Dad(Person):
   gene = 'XY'

   def walk(self):
      return '아빠가 걷기'

class FirstChild(Dad, Mom):
    def swim(self):
        return '첫째가 수영'

    def cry(self):
        return '첫째가 응애'

baby1 = FirstChild()
print(baby1.swim()) # 첫째가 수영
print(baby1.walk()) # 아빠가 걷기
print(baby1.cry()) # 첫째가 응애
print(baby1.gene) # XY
```
### 다이아몬드 문제 (The diamond problem)
-  두 클래스  B와 C가 A에서 상속되고 클래스 D가 B와 C 모두에서 상속될 때 발생하는 모호함
-  B와 C를 재정의한 메서드가 A에 있고 D가 이를 재정의하지 않는 경우
   - D는 B의 메서드 중 어떤 버전을 상속하는가?
   - 아니면 C의 메서드 버전을 상속하는가?
### MRO(Method Resolution Order)
파이썬이 메서드를 찾는 순서에 대한 규칙이자 메서드 결정 방법
- MRO는 다중 상속에서 어떤 부모 클래스의 메서드를 먼저 사용할지 순서를 정의
- 파이썬은 미리 정해진 MRO를 통해 다중 상속 환경에서도 예측 가능한 방식으로 메서드 탐색이 이루어질 수 있도록 함
### MRO가 필요한 이유
- 부모 클래스들이 여러번 액세스 되지 않도록 각 클래스에서 지정된 왼쪽에서 오른쪽으로 가는 순서 보존
- 각 부모를 오직 한 번만 호출하고, 부모들의 우선순위에 영향을 주지 않으면서 서브 클래스를 만드는 단조적인 구조 형성
## `super()` 메서드
MRO에 따라 현재 클래스의 부모(상위) 클래스의 메서드나 속성에 접근할 수 있게 해주는 내장 함수
- `super()`를 사용하면 직접 부모 클래스 이름을 적지 않아도 MRO에 따라 자동으로 올바른 메서드를 찾아 실행
- 다중 상속에서 `super()`를 호출하면 상속 순서에 맞춰 여러 부모 클래스의 메서드를 순차적으로 실행 가능
- 생성자나 오버라이딩된 메서드에서 `super()`를 호출하면 부모 클래스의 초기화나 로직을 그대로 활용 가능
### `super()`의 특징
단순히 부모 클래스의 메서드를 호출하기 위한 용도 뿐만 아니라 다중 상속이 있을 때도 MRO에 따라 상위 클래스의 메서드를 찾아 실행하기 위해 `super()`를 사용
### `super()` 예시
**단일 상속**
- `super()` 이용 전
```python
class Person:
   def __init__(self, name, age):
      self.name = name
      self.age = age

class Student(Person):
   def __init__(self, name, age, gpa):
      self.name = name
      self.age = age
      self.gpa = gpa
```
- `super()` 이용 후
```python
class Person:
   def __init__(self, name, age):
      self.name = name
      self.age = age

class Student(Person):
   def __init__(self, name, age, gpa):
      super().__init__(name, age)
      self.gpa = gpa
```
**다중 상속**
```python
class ParentA:
   def __init__(self):
      # 상속의 안정적인 호출을 위한 super()
      # 만약에 이게 없다면 Child가 value_b 호출 시 KeyError 발생
      super().__init__()
      self.value_a = 'ParentA'

   def show_value(self):
      print(f'Value from ParentA: {self.value_a}')

class ParentB:
   def __init__(self):
      self.value_b = 'ParentB'

   def show_value(self):
      print(f'Value from ParentB: {self.value_b}')

class Child(ParentA, ParentB):
   def __init__(self):
      super().__init__()
      self.value_c = 'Child'

   def show_value(self):
        super().show_value()  # ParentA 클래스의 show_value 메서드 호출
        print(f'Value from Child: {self.value_c}')

print(child.value_c)  # Child
print(child.value_b)  # ParentB
print(child.value_a)  # ParentA
```
> [!IMPORTANT]
> **단일 상속 구조에서의 `super()`함수**
> - 부모 클래스의 생성자 또는 메서드를 호출하기 위해 사용
> - 명시적으로 이름을 지정하지 않고 부모 클래스를 참조할 수 있으므로 코드 유지 관리에 용이
> - 클래스 이름이 변경되거나 부모 클래스가 교체되어도 `super()`를 사용하면 코드 수정이 더 적게 필요
>
> **다중 상속 구조에서의 `super()`함수**
> - MRO(메서드 해석 순서)에 따라 각 클래스의 메서드를 찾아가기 때문에 단순히 직계 부모만이 아니라 다중 상속 관게에서도 적절한 상위 클래스의 메서드를 안전하게 호출 가능
> - 이를 통해 복잡한 상속 구조에서도 코드를 유연하고 깔끔하게 유지 가능
# 에러와 예외
## 디버깅
소프트웨어에서 발생하는 버그를 찾아내고 수정하는 과정
→ `print`함수 또는 IDE 등에서 제공하는 기능으로 디버깅 가능
## 에러
프로그램 실행 중에 발생하는 예외 상황
## 예외
프로그램 실행 중에 감지되는 에러
### 내장 예외 (Built-in Exception)
- `ZeroDivisionError`: 나누기 또는 모듈로 0으로 나누려고 할 때
- `TypeError`: 타입 불일치/인자 누락/인자 초과/인자 타입 불일치
- `ValueError`: 연산이나 함수에는 문제가 없지만 부적절한 값으로 인자를 받는 경우
- `NameError`: 지역 또는 전역 이름을 찾을 수 없을 때
- `IndexError`: 시퀀스 인덱스가 범위를 벗어났을 때
- `KeyError`: 딕셔너리에 해당 키가 존재하지 않을 때
- `ImportError`: 임포트하려는 이름을 찾을 수 없을 때
- `ModuleNotFoundError`: 모듈을 찾을 수 없을 때
- `KeyboardInterrupt`: 사용자가 ctrl-c 또는 delete를 누를 때 발생 (강제 종료 시)
- `IndentationError`: 잘못된 들여쓰기
# 예외 처리
예외가 발생했을 때 프로그램이 비정상적으로 종료되지 않고, 적절하게 처리할 수 있도록 하는 방법
## `try` & `except`
- `try`: 예외가 발생할 수 있는 코드
- `except`: 예외 발생 시 실행할 코드
```python
try:
   예외가 발생할 수 있는 코드
except 예외 조건:
   예외 처리 코드
```
```python
try:
   x = int(input('숫자를 입력하세요: '))
   y = 10/x
except ZeroDivisonError:
   print('0으로 나눌 수 없습니다.')
except ValueError:
   print('유효한 숫자가 아닙니다.')
```
## 복수 예외 처리
## `else` & `finally`
- `else`: 예외가 발생하지 않았을 때 추가 작업 진행
- `finally`: 예외 발생여부와 상관없이 항상 실행할 코드 작성
```python
try:
   x = int(input('숫자를 입력하세요: '))
   y = 10/x
except ZeroDivisonError:
   print('0으로 나눌 수 없습니다.')
except ValueError:
   print('유효한 숫자가 아닙니다.')
else:
   print(f'결과: {y}')
finally:
   print('프로그램이 종료되었습니다')
```




