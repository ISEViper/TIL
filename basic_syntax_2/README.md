# list
**여러 개의 값을 순서대로 저장**하는, **변경 가능한(mutable)** 시퀀스 자료형
```python
my_list = [1, 'a', 3, 'b', 5]
```
### 리스트 표현
- 대괄호 [] 안에 값들을 쉼표로 구분하여 표현
- 숫자, 문자열, 심지어 다른 리스트까지 모든 종류의 데이터를 담을 수 있음
- 값들을 추가, 수정, 삭제하는 등 자유롭게 변경 가능
## 시퀀스로서의 리스트
리스트는 시퀀스이므로 문자열처럼 인덱싱, 슬라이싱, 길이 확인, 반복 등 공통 기능 모두 사용 가능
```python
my_list = [1, 'a', 3, 'b', 5]

# 인덱싱
my_list[3] # 'b'

# 슬라이싱
my_list[1:4] # ['a', '3', 'b']

# 길이 확인
len(my_list) # 5
```
## 중첩 리스트
```python
my_list = [1, 'two', 3, ['eins', 'zwei', 'drei']]
```
- 리스트 내에 다른 리스트를 중첩해서 넣을 수 있음
- 만약에 리스트 안의 리스트의 내용을 출력하고 싶다면
```python
# ['eins', 'zwei', 'drei']
print(my_list[3])

# 'zwei'
print(my_list[3][1])
```
- 위의 방식대로 리스트가 있는 순서를 먼저 입력하고 그 리스트 내의 원하는 내용이 있는 순서를 입력
## 리스트의 가변성
- 한 번 생성된 리스트는 그 내용을 자유롭게 수정, 추가, 삭제가 가능
```python
my_list = [1, 'a', 3, 'b', 5, 'c']

my_list[1] = 2
print(my_list) # [1, 2, 3, 'b', 5, 'c']

my_list[2:4] = ['hi', 'hello']
print(my_list) #[1, 2, 'hi', 'hello', 5, 'c']

my_list[2:4] = ['안녕', '안녕하세요', '반가워요']
print(my_list) # [1, 'a', '안녕', '안녕하세요', '반가워요', 5, 'c']
```

# tuple
## 시퀀스로서의 튜플
## 튜플의 불변성

# range
## range 기본 구문
## range의 규칙

# dict
**key-value** 쌍으로 이루어진 순서와 중복이 없는 변경 하는한 자료형
```python
my_f1 = {'max':'red_bull', 'oscar':'mclaren', 'luis':'ferrai'}
```
### 딕셔너리 표현
- 중괄호{}안에 값들이 쉼표(,)로 구분
- 값 한 개는 key(키)와 value(값)으로 구성되어 있음  
    `{key : value}`
    - key(키): 값을 식별하기 위한 고유한 '이름표'
    - value(값): 키에 해당하는 실제 데이터
>[!WARNING]  
>**딕셔너리 순서?**
>- 딕셔너리는 순서가 없는 자료형이지만 파이썬 3.7 이상에서는 입력한 순서대로 출력 시 그대로 유지
>- 하지만 여전히 딕셔너리의 핵심은 **순서가 없는 자료형**이라는 점과 **Key를 통한 접근**이라는 점!

## 딕셔너리 규칙
### Key 규칙
- 고유성이 있어야 함 (**Key는 중복 불가!**)
- 변경 불가능한 자료형만 이용 가능
    - 사용 가능: `str`, `int`, `float`, `tupple`
    - 사용 불가능: `list`, `dict`
### Value 규칙
- 어떤 자료형이든 자유롭게 사용 가능
## 딕셔너리 값 접근
- Key를 이용해 해당 Value를 꺼낼 수 있음
- Key에 접근 시 대괄호[] 사용
```python
my_f1 = {'max':'red_bull', 'oscar':'mclaren', 'lewis':'mercedes'}
p
print(my_f1['max']) # 'red_bull'
print(my_f1['lando']) # KeyError: 'lando'
```
### 딕셔너리 값 추가 및 변경
```python
my_f1 = {'max':'red_bull', 'oscar':'mclaren', 'lewis':'mercedes'}

# 값 추가
my_f1['george'] = 'mercedes'
print(my_f1) # {'max': 'red_bull', 'oscar': 'mclaren', 'lewis': 'mercedes', 'george': 'mercedes'}

# 값 변경
my_f1['lewis'] = 'ferrai'
print(my_f1) # {'max': 'red_bull', 'oscar': 'mclaren', 'lewis': 'ferrai', 'george': 'mercedes'}
```
>[!TIP]  
>만약에 `dict`과 `list`가 혼합되어 있는 경우
>```python
> my_f1 = {
>    'max': 'red_bull',
>    'oscar': 'mclaren',
>    'lewis': 'mercedes',
>    'teams': ['red_bull', 'mclaren', 'mercedes'],
>    'positions': [{'driver': 'max', 'position': 1}, {'driver': 'oscar', 'position': 2}]
>}
>```
>여기서 'max'의 'position'을 출력하고 싶다면  
>`print(my_f1['positions'][0]['position']) # 1`

# set
## 세트의 집합 연산

# Other Types
## None
## Boolean

# Collection
## 불변과 가변

# 형변환
## 암시적 형변환
## 명시적 형변환

# 연산자
## 산술 연산자
## 복합 연산자
## 비교 연산자
## 논리 연산자
## 단축 평가
## 멤버십 연산자
## 시퀀스형 연산자
## 연산자 우선순위
