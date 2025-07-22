# 표현식과 값

# 변수와 메모리
## 할당문 동작 순서
## 재할당

# Data Types
## 숫자형 데이터
## 숫자형의 '행동': 산술 연산
### 산술 연산자
|연산자|설명|
|----|----|
|+|덧셈|
|-|뺄셈|
|*|곱셈|
|/|나눗셈|
|//|몫 나눗셈|
|%|나머지|
|**|거듭제곱|
|-|음수 부호|
### 연산자 우선순위
|우선순위|연산자|
|-------|-------|
|높음|** (거듭제곱)|
||- (음수 부호)|
||* (곱셈), / (나눗셈), // (몫 나눗셈), % (나머지)|
|낮음|+ (덧셈), - (뺄셈)|

```python
# 계산 결과 비교
print(-2 ** 4)   # -16
print(-(2 ** 4)) # -16
print((-2) ** 4) # 16
```


# Sequence Types
## 시퀀스 타입의 5가지 공통 특징
### 순서 (Order)
값들이 순서대로 저장 (정렬 X)
### 인덱싱 (Indexing)
각 값에 고유 번호(인덱스)를 가지고 있으며, 인덱스를 사용하여 특정 위치의 값을 선택하거나 수정할 수있음
### 슬라이싱 (Slicing)
인덱스 범위를 조절해 전체 데이터 중 원하는 부분만 값을 잘라내서 사용 가능
### 길이 (Length)
`len()`함수를 사용하여 저장된 값의 개수(길이)를 구할 수 있음
### 반복 (Iteration)
반복문을 사용하여 각 값을 하나씩 순서대로 꺼낼 수 있음  

### 시퀀스 타입 특징 예시
`my_data = 'Hello'`  
|특징|사용예시|결과|
|-----|-----|-----|
|인덱싱|`my_data[0]`|`'H'`|
|슬라이싱|`my_data[1:4]`|`'ell'`|
|길이|`len(my_data)`|`5`|
|반복|`for char in my_data`|`H, e, l, l, o`를 차례대로 출력|

# 문자열

# 문자열에 값 삽입하기: f-string
문자열 내에 변수나 표현식의 결과를 손쉽게 삽입하는 강력한 방법
- 문자 시작 전에 f를 붙이고 '{표현식}' 형태로 적기
```python
name = 'max_verstappen'
age = 27
team = 'red_bull_racing'

# His name is max_verstappen, he is 27 years old, and his team is red_bull_racing
print(f'His name is {name}, he is {age} years old, and his team is {team}')
```

# 시퀀스로서의 문자열
## 인덱스 (Index)
시퀀스에서 각 값의 위치를 구별하기 위해 붙이는 고유 번호
>[!NOTE]
>**왜 인덱스는 0번부터 시작할까?**  
>순서라고 생각하지 말고 거리라고 생각하면 편하다. 즉, **시작지점에서 얼마나 멀리 떨어져 있나**로 생각해야 한다.  

||h|e|l|l|o|
|-|-|-|-|-|-|
|순방향|0|1|2|3|4|
|역방향|-5|-4|-3|-2|-1|

## 슬라이싱(Slicing)
```python
my_sequence[start:stop:step]
```
`start`: 슬라이싱 시작 지점(이상)  
`stop`: 슬라이싱 끝나는 지점(미만)  
`step`: 숫자를 몇 개씩 건너뛰면서 반복할건지  

### 슬라이싱 예시
```python
my_str = 'hello'
```
```python
my_str[1:] # 'ello'
my_str[:3] # 'hel'
my_str[::2] # 'hlo'
my_str[::-1] # 'olleh'
my_str[1:3] # 'el'
my_str[1:4:2] # 'el'
my_str[5:2:-1] # 'ol'
```

# 문자열의 불변성
```python
my_str = 'hello'
# TypeError: 'str' object does not support item assignment
my_str[2] = 'r'

my_str = my_str[:2] + 'r' + my_str[3:]
# herlo
print(my_str)
```

>[!WARNING]
>한 번 생성된 문자열 객체는 더 이상 수정할 수 없다.  
>현재 위에 보이는 예시는 수정된 것처럼 보이지만 슬라이싱을 이용해 새로운 값으로 재할당 한 것이지, 수정된 것이 아니다!