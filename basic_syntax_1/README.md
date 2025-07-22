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
### 인덱싱 (Indexing)
### 슬라이싱 (Slicing)
### 길이 (Length)
### 반복 (Iteration)

# 문자열

# 문자열에 값 삽입하기: f-string
```python
name = 'max_verstappen'
age = 27
team = 'red_bull_racing'

# His name is max_verstappen, he is 27 years old, and his team is red_bull_racing
print(f'His name is {name}, he is {age} years old, and his team is {team}')
```

# 시퀀스로서의 문자열
## 인덱스 (Index)
## 슬라이싱(Slicing)
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