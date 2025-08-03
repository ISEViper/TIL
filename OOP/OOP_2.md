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
## `super()` 메서드
# 에러와 예외
## 디버깅
## 에러
## 예외
# 예외 처리
## `try` & `except`
## 복수 예외 처리
## `else` & `finally`
