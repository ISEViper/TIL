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
여러 개의 값을 순서대로 저장하는, 변경 불가능한 시퀀스 자료형
### 튜플 표현
- 소괄호()안에 값들이 쉼표(,)로 구분
- 모든 종류의 데이터를 담을 수 있음
- 리스트와 비슷하지만, 한번 입력하면 변경할 수 없다는 점에서 차이점 발생
```python
my_tuple_1 = ()
my_tuple_2 = (1,) # 값이 1개인 경우 뒤에 쉼표를 꼭 붙여줘야 함
my_tuple_3 = (1, 'a', 3, 'b', 5)
my_tuple_4 = 1, 'hello', 3.14, True
```
## 시퀀스로서의 튜플
튜플도 시퀀스형 자료형이기 때문에 인덱싱, 슬라이싱, 길이 확인, 반복등이 가능
```python
my_tuple = (1, 'a', 3, 'b', 5)

#인덱싱
my_tuple[2] # 3

#슬라이싱
my_tuple[1:] # ('a', 3, 'b', 5)
my_tuple[:3] # (1, 'a', 3)
my_tuple[1:4] # ('a', 3, 'b')
my_tuple[::2] # (1, 3, 5)

# 길이 확인
len(my_tuple) # 5
```

## 튜플의 불변성
한 번 생성된 튜플은 절대 수정, 추가, 삭제가 불가능!
```python
my_tuple = (1, 'a', 3, 'b', 5)

# TypeError: 'tuple' object does not support item assignment
my_tuple[1] = 'z'
```
### 튜플이 활용되는 곳은 어디일까?
**데이터를 안전하게 전달해야 하는 내부 동작에서 주로 활용!**

# range
연속된 정수 시퀀스에 사용되는, 변경 불가능한 시퀀스 자료형
## range 기본 구문
`range(start, stop, step)`  
`start`: 정수 시퀀스가 시작하는 지점 (이상)  
`stop`: 정수 시퀀스가 끝나는데 포함이 안되는 지점 (미만)  
`step`: 정수 시퀀스가 건너뛰는 숫자의 크기  

`range`는 `list`에 넣으면 확인 가능!
## range의 규칙
1. 값의 범위 규칙
   - `stop`에 들어가는 값은 절대 값에 포함되지 않음
2. 증가/감소 규칙
   - 증가할 때: `start`와 `stop`의 방향이 순방향이여야 함
   - 감소할 때: `start`와 `stop`의 방향이 역방향이여야 하고, `step`에는 음수가 들어가야 함

### range 활용 예시
`for`문과 같이 활용이 많이 됨
```python
arr = []
for i in range(10):
    arr.append(i)
print(arr) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
# dict
**key-value** 쌍으로 이루어진 순서와 중복이 없는 변경 하는 자료형
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
순서와 중복이 없는 변경 가능한 자료형
### set 표현
소괄호{}안에 있는 값들이 쉼표(,)로 구분
### 특징
1. 중복을 허용하지 않음
2. 순서가 없음
```python
my_set_1 = set() # 소괄호만 입력하는 것은 dict이 우선이기 때문에 빈 set을 구성하는 경우 set()으로 설정
my_set_2 = {1, 2, 3, 4}
my_set_3 = {1, 1, 1, 1} # print(my_set_3) 하면 결과는 {1}로 출력
```
## 세트의 집합 연산
세트는 집합연산을 그대로 사용이 가능함
`my_set_1 = {1, 2, 3}`, `my_set_2 = {3, 5, 6}`
1. 합집합
`print(my_set_1 | my_set_2)` `# {1, 2, 3, 5, 6}`   
2. 교집합
`print(my_set_1 & my_set_2)` `# {3}` 
3. 차집합
`print(my_set_1 - my_set_2)` `# {1, 2}` 

# Other Types
## None
파이썬에서 **값이 없음**을 표현하는 특별한 데이터 타입 (아직 값이 정해지지 않음을 나타내는 것)
## Boolean
True/False 두가지 값만 가지는 데이터 타입

# Collection
여러 개의 값을 하나로 묶어 관리하는 자료형을 통칭하는 말 (여러 물건을 담는 보관함 같은 것)
|컬렉션명|변경가능여부|순서존재여부||
|--------|----------|-----------|------|
|`str`|X|O|시퀀스형|
|`list`|O|O|시퀀스형|
|`tuple`|X|O|시퀀스형|
|`dict`|O|X|비시퀀스형|
|`set`|O|X|비시퀀스형|
## 불변과 가변
컬렉션 타입은 생성 후 값을 변환할 수 있냐 없냐로도 나눌 수 있음
- 불변형: `str`, `tuple`
- 가변형: `list`, `dict`, `set`
  
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
