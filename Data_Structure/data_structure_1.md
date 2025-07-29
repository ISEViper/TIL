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
new_text_2 = text.title()
print(new_text_2) # Hello, World

# upper
text = 'heLLo, WorLD'
new_text_3 = text.upper()
print(new_text_3) # HELLO, WORLD

# lower
text = 'heLLo, WorLD'
new_text_4 = text.lower()
print(new_text_4) # hello, world

# swapcase
text = 'heLLo, WorLD'
new_text_5 = text.swapcase()
print(new_text_5) # HEllO, wORld
```
## 리스트
### 리스트 값 추가 및 삭제 메서드
|매서드|설명|
|---|---|
|`L.append(x)`|리스트 마지막에 항목 x를 추가|
|`L.extend(m)`|iterable m의 모든 항목들을 리스트에 추가 (+=와 같은 기능)|
|`L.insert(i, x)`|리스트 i번째 순서에 항목 x를 삽입|
|`L.remove(x)`|리스트 가장 왼쪽에 있는 항목(첫번째) x를 제거 → 항목이 존재하지 않는 경우, ValueError|
|`L.pop()`|리스트의 가장 오른쪽의 값을 반환 후 제거|
|`L.pop(i)`|리스트 i번째 순서에 있는 값을 반환 후 제거|
|`L.clear`|리스트의 모든 항목 제거|
### `.append(x)`
```python
my_list = ['a', 'b', 'c', 'd']
my_list.append('e')

print(my_list) # ['a', 'b', 'c', 'd', 'e']
```
### `.extend(m)`
```python
my_list = ['a', 'b', 'c', 'd']
my_list.extend(['e', 'f', 'g'])

print(my_list) # ['a', 'b', 'c', 'd', 'e', 'f', 'g']
```
> [!WARNING]  
> **`extend` 주의 사항 (`append`와의 비교)**
> ```python
> my_list = ['a', 'b', 'c', 'd']
> my_list.append(['e', 'f', 'g']) # ['a', 'b', 'c', 'd', ['e', 'f', 'g']]
> 
> # 반복 가능한 객체가 아니면 추가 불가
> my_list.extend(100) # TypeError: 'int' object is not iterable
> ```
### `.insert(i, x)`
```python
my_list = ['a', 'b', 'c', 'd']
my_list.insert(1, 'k')

print(my_list) # ['a', 'k', 'b', 'c', 'd']
```
### `.remove(x)`
```python
my_list = ['a', 'b', 'a', 'b', 'c', 'd']
my_list.remove('a')

print(my_list) # ['b', 'a', 'b', 'c', 'd']
```
### `.pop()`, `.pop(i)`
```python
my_list = ['a', 'b', 'a', 'b', 'c', 'd']
item_1 = my_list.pop()
item_2 = my_list.pop(0)

print(item_1) # 'd'
print(item_2) # 'a'
print(my_list) # ['b', 'a', 'b', 'c']
```
### `.clear()`
```python
my_list = ['a', 'b', 'a', 'b', 'c', 'd']
my_list.clear()

print(my_list) # []
```
### 리스트 탐색 및 정렬 매서드
|매서드|설명|
|---|---|
|`L.index(x)`|리스트에서 첫 번째로 일치하는 항목 x의 인덱스를 반환|
|`L.count(x)`|리스트 내 항목 x의 개수 반환|
|`L.reverse()`|리스트 순서를 역순으로 변경 (정렬하는 것은 아님)|
|`L.sort()`|리스트 정렬|
### `.index()`
```python
my_list = ['a', 'b', 'a', 'b', 'c', 'd']
index = my_list.index('a')
print(index) # 0
```
### `.count(x)`
```python
my_list = ['a', 'b', 'a', 'b', 'c', 'd']
count = my_list.count('a')
print(count) # 2
```
### `.reverse()`
```python
my_list = [25, 3, 30, 5, 1]
my_list.reverse()
print(my_list.reverse()) # None (reverse는 None을 반환)
print(my_list) # [1, 5, 30, 3, 25]
```
### `.sort()`
```python
my_list = [25, 3, 30, 5, 1]
my_list.sort()
print(my_list.sort()) # None (sort는 None을 반환)
print(my_list) # [1, 3, 5, 25, 30]
```
# 복사
## 객체와 참조
## 얕은 복사
## 깊은 복사
# List Comprehension
