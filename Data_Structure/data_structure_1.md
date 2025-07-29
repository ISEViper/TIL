# Data Structure
### 자료구조
- 각 데이터의 효율적인 저장, 관리를 위한 구조를 나눠 놓은 것
- 단순히 데이터를 묶는 것을 넘어, 프로그램의 성능과 효율성, 유지보수성에 큰 영향을 미치는 핵심적인 개념
## 매서드 (Method)
객체에 속한 함수
- 프로그래밍에서 메서드는 객체가 특정 작업을 수행하도록 정의된 함수
- 문자열, 리스트, 딕셔너리 등 각 데이터 구조의 매서드를 호출하여 다양한 기능 활용
- 매서드는 클래스(`class`)내부에 정의되는 함수
### 매서드 호출 방법
`데이터 타입 객체.메서드()`
```python
# 문자열 매서드 예시
print('hello'.captialize()) # Hello

# 리스트 메서드 예시
num = [1, 2, 3]
num.append(4)

print(num) # [1, 2, 3, 4]
```
# 시퀀스 데이터 구조
## 문자열
### 문자열 조회/탐색 및 검증 매서드
|매서드|설명|
|---|---|
|`s.find(x)`|x의 첫 번째 위치를 반환, 없으면 -1을 반환|
|`s.index(x)`|x의 첫 번째 위치를 반환, 없으면 오류 발생|
|`s.isupper(x)`|문자열 내의 모든 문자가 대문자인지 확인|
|`s.islower(x)`|문자열 내의 모든 문자가 소문자인지 확인|
|`s.isalpha(x)`|문자열 내의 모든 문자가 알파벳인지 확인 → 단순 알파벳이 아닌 유니코드 상 Letter(한국어도 포함)|
### `.find(x)`
```python
my_letter = 'Banana'
print(my_letter.find('a')) # 1
print(my_letter.find('z')) # -1
```
### `.index(x)`
```python
my_letter = 'Banana'
print(my_letter.find('a')) # 1
print(my_letter.find('z')) # ValueError: substring not found
```
### `.isupper()`, `.islower()`
```python
my_letter = 'BANANA'
print(my_letter.isupper()) # True
print(my_letter.islower()) # False
```
### `.isalpha()`
```python
my_letter_1 = 'banana123'
my_letter_@ = 'Banana'
print(my_letter_1.isalpha()) # False
print(my_letter_1.isalpha()) # True
```
### 문자열 조작 메서드 (새로운 문자열 반환)
|매서드|설명|
|---|---|
|`s.replace(old, new[, count])`|바꿀 대상 글자를 새로운 글자로 바꿔서 전환|
|`s.strip([chars])`|문자열의 시작과 끝에 있ㄱ는 공백 혹은 지정한 문자를 제거|
|`s.split(sep=None, maxsplit=-1)`|`sep`을 구분자 문자열로 사용해서 문자열에 있는 단어들의 리스트를 반환|
|`'separator'.join(iterable)`|구분자로 iterable의 문자열을 연결한 문자열을 반환|
|`s.capitalize()`|가장 첫 번째 글자를 대문자로 변경|
|`s.title()`|문자열 내 띄어쓰기 기준으로 각 단어의 첫 글자는 대문자로, 나머지는 소문자로 진행|
|`s.upper()`|모두 대문자로 변경|
|`s.lower()`|모두 소문자로 변경|
|`s.swapcase()`|대↔소문자 서로 변경|
### `.replace(old, new[, count])`
```python
my_letter = "Hello, world world world!"
print(my_letter.replace('world', 'Python')) # Hello, Python Python Python!
print(my_letter.replace('world', 'Python', 2)) # Hello, Python Python world!
```
### `.strip([chars])`
```python
my_letter = '   Hello world   '
print(my_letter.strip()) # Hello world
```
### `.split(sep=None, maxsplit=-1)`
```python
my_letter = "Hello, Python, world!"
print(my_letter.split(',')) # ['Hello', ' Python', ' world!']
print(my_letter.split()) # ['Hello,', 'Python,', 'world!']
```
### `'seperator'.join(iterable)`
```python
my_letter = ['Hello', 'world']
print(', '.join(my_letter)) # Hello, world
```
### 기타 문자열 조작 메서드
```python
# capitalize
text = 'heLLo, WorLD'
new_text_1 = text.capitalize()
print(new_text_1) # Hello, world

# title
text = 'heLLo, WorLD'
new_text_1 = text.title()
print(new_text_1) # Hello, World

# upper
text = 'heLLo, WorLD'
new_text_1 = text.upper()
print(new_text_1) # HELLO, WORLD

# lower
text = 'heLLo, WorLD'
new_text_1 = text.lower()
print(new_text_1) # hello, world

# swapcase
text = 'heLLo, WorLD'
new_text_1 = text.swapcase()
print(new_text_1) # HEllO, wORld
```
## 리스트
# 복사
## 객체와 참조
## 얕은 복사
## 깊은 복사
# List Comprehension
