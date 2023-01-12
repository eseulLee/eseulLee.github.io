---
title: "[python] 함수, 인수, 변수"
excerpt: "#파이썬정복 #한빛미디어 함수와 인수, 인수의 형식, 변수의 범위"

categories:
  - Python
tags:
  - [Python]

permalink: /python/func-1/

toc: true
toc_sticky: true

date: 2023-01-12
last_modified_at: 2023-01-12
---

## 🚀 7.1 함수와 인수

```python
def 함수명(인수 목록):
    본체
```

n까지의 합을 구하는 반복되는 코드를 함수로 구현
```python
def calcsum(n):
    summ = 0
    for num in range(n + 1):
        summ += num
    return summ

print("~ 4 =", calcsum(4))
print("~ 10 =", calcsum(10))

>>> ~ 4 = 10
    ~ 10 = 55
```

### 💡 인수
- 호출원에서 함수로 전달되는 작업거리, 매개변수
- 형식 인수(함수 정의문의 인수)와 실인수(함수 호출문에서 전달하는 인수)로 나뉨
  - 위의 코드상에서 n이 형식 인수, 호출문의 4와 10이 실인수에 해당
- 개수 제한이 없어 얼마든지 많이 전달할 수도 있고, 아예 없을 수도 있음

```python
def calcrange(begin, end):
    summ = 0
    for num in range(begin, end + 1):
        summ += num
    return summ
```

### 💡 리턴값
- 함수의 실행 결과를 호출원으로 돌려주는 값
- 인수는 여러 개 있을 수 있지만, 리턴값은 딱 하나밖에 없음
- 리턴값이 꼭 있어야 하는 것은 아니며, 반환할 값이 없는 경우도 있음

```python
def printsum(n):
    summ = 0
    for num in range(n + 1):
        summ += num
    print("~", n, "=", summ)
  
printsum(4)
printsum(10)

>>> ~ 4 = 10
    ~ 10 = 55
```
- 위의 printsum 함수는 합계를 구해주는 것이 아니라 직접 출력하는 형태
- 리턴값이 없는 함수의 경우, 동작만 처리할 뿐 값이 아니기 때문에 단독으로 호출해야 함
  - 변수에 대입하거나 수식 내에서 사용하면 안됨

```python
a = printsum(4)        # None
print(printsum(4) * 2) # error
```

### 💡 PASS 명령
- pass 명령을 만나면 그냥 무시하고 건너 뜀
- 함수를 만들어 두고 본체를 천천히 만드는 경우 pass 키워드 입력 (그대로 비워두면 에러)
- 앞으로 작성할 코드에 대해 자리만 잡아 놓는 역할

## 🚀 7.2 인수의 형식

### 💡 가변 인수
- 일반적인 함수의 경우, 정의문에 필요한 인수의 개수가 명시되어 있고 호출할 때 이 개수에 맞게 실인수를 넘겨야 함
- 가변 인수는 임의 개수의 인수를 받기 때문에 개수가 미리 정해져 있지 않음
- 인수 이름 앞에 * 기호를 붙이면 이 자리에 여러 개의 인수가 올 수 있음
- 여러 개의 실인수를 튜플로 묶어 전달하게 되고, for 루프를 돌며 튜플의 요소를 하나씩 꺼내 사용
- 가변 인수를 사용하는 대표적이고 실용적인 함수 : 기본 출력문인 print

```python
def intsum(*ints):
    summ = 0
    for num in ints:
        summ += num
    return summ

print(intsum(1, 2, 3), end=' ')
print(intsum(5, 7, 9, 11, 13), end=' ')
print(intsum(8, 9, 6, 2, 9, 7, 5, 8))

>>> 6 45 54
```

- 가변 인수는 **이후의 모든 인수를 다 포함**하기 때문에 **인수 목록의 마지막**에 와야 함
- 가변 인수 앞에는 일반 인수가 올 수 있지만 뒤쪽에는 올 수 없음

```python
intsum(s, *ints)      # possible :)
intsum(*ints, s)      # error :/
intsum(*ints, *nums)  # error :/
```

### 💡 인수의 기본값

```python
# step 인수로 증감값 추가하여 범위 내의 수를 건너뛰며 합계 구하는 기능 추가

def calcstep(begin, end, step):
    summ = 0
    for num in range(begin, end + 1, step):
        summ += num
    return summ

print("1 ~ 10 =", calcstep(1, 10, 2))
print("2 ~ 10 =", calcstep(2, 10, 2))

>>> 1 ~ 10 = 25
    2 ~ 10 = 30
```

#### 👀 잘 바뀌지 않는 인수인 경우에도 일일이 인수를 전달해야 하는 불편함 발생

- 증감값의 경우, 웬만하면 1인 경우가 대부분이라 일일이 전달하는 경우 오히려 불편해짐
- 잘 바뀌지 않는 인수의 경우 인수 목록에 기본값 지정 가능
- 기본값이 있는 인수는 일종의 옵션으로 취급되어 **생략 가능**
- 실인수를 생략하는 경우, 기본값을 전달한 것으로 가정

```python
def calcstep(begin, end, step = 1):
    summ = 0
    for num in range(begin, end + 1, step):
        summ += num
    return summ

print("1 ~ 10 =", calcstep(1, 10, 2))
print("1 ~ 100 =", calcstep(1, 100))

>>> 1 ~ 10 = 25
    1 ~ 100 = 5050
```

- 그러나 기본값을 가지는 인수 뒤에 일반 인수 올 수 없음
  - 중간 인수의 경우 호출문에서 생략할 수 없기 때문
- 중간을 생략할 수 없고 끝부분만 생략할 수 있으므로 **기본값을 가지는 인수는 목록의 뒤쪽**에 적어야 함

### 💡 키워드 인수
- 위치 인수(Positional Argument): 순서대로 인수를 전달하는 방식
- - 함수를 호출할 때 함수 정의문에 선언된 순서대로 실인수를 전달하며, 호출문에 나타나는 순서에 따라 형식 인수에 차례대로 대입
  - 호출문이 짧고 간단하지만, 인수의 수가 많아지면 헷갈릴 수 있음
- 키워드 인수(Keyword Argument): 인수의 이름을 지정하여 대입 형식으로 전달하는 방식
  - 순서와 무관하게 인수 전달 가능

```python
def calcstep(begin, end, step):
    summ = 0
    for num in range(begin, end + 1, step):
        summ += num
    return summ

print("3 ~ 5 =", calcstep(3, 5, 1)) 
print("3 ~ 5 =", calcstep(begin = 3, end = 5, step = 1))
print("3 ~ 5 =", calcstep(step = 1, end = 5, begin = 3))
print("3 ~ 5 =", calcstep(3, 5, step = 1))
print("3 ~ 5 =", calcstep(3, step = 1, end = 5))

>>> 3 ~ 5 = 12
    3 ~ 5 = 12
    3 ~ 5 = 12
    3 ~ 5 = 12
    3 ~ 5 = 12
```

- 위치 인수와 키워드 인수를 섞어서 호출하는 경우, 위치 인수가 항상 먼저 와야 하며 앞쪽에 키워드 인수가 온 경우 뒤쪽에는 위치 인수가 올 수 없음
- print 함수의 sep, end 가 대표적인 키워드 인수

```python
print(value, ..., sep = ' ', end = '\n', file = sys.stdout, flush = False)
```

### 💡 키워드 가변 인수
- 키워드 인수를 가변 개수로 전달하는 경우, 인수 목록에 ** 기호 붙임
- 여러 개의 키워드 인수 전달시 인수의 이름과 값의 쌍을 사전으로 만들어 전달, 함수 내부에서 사전을 읽듯 인수값을 꺼내 사용하게 됨

```python
def calcstep(**args):
    begin = args['begin']
    end   = args['end']
    step  = args['step']
    
    summ = 0
    for num in range(begin, end + 1, step):
        summ += num
    return summ

print("3 ~ 5 =", calcstep(begin = 3, end = 5, step = 1))
print("3 ~ 5 =", calcstep(step = 1, end = 5, begin = 3))

>>> 3 ~ 5 = 12
    3 ~ 5 = 12
```

- 사전은 순서가 없는 집합이므로, 인수의 전달 순서는 상관없으며 함수 내부에서도 전달 순서 알 수 없음
- 위 예시의 calcstep 함수는 키워드 인수만 받겠다고 선언하였기 떄문에 반드시 키워드 인수만 받아야 함
  - calcstep(3, 5, 1) 식으로 위치 인수를 넘길 경우 에러 처리
- 또한 세 개의 인수를 다 사용하고 있으므로 세 인수를 모두 전달해야 함

#### 👀 위치 인수와 키워드 인수를 동시에 가변으로 취하는 경우
- `일반 인수 > 위치 인수 > 키워드 인수` 순으로 위치

```python
def calcscore(name, *score, **option):
    print(name)
    summ = 0
    for s in score:
        summ += s
    print('총점 :', summ)
    if (option['avg'] == True):
        print("평균 :", summ / len(score))

calcscore('student1', 88, 99, 77, avg = True)
calcscore('student2', 66, 68, 75, avg = False)

>>> student1
    총점 : 264
    평균 : 88.0
    student2
    총점 : 209
```

## 🚀 7.3 변수의 범위

### 💡 지역 변수
- 함수 내부에서 선언하는 변수 (사용 범위 또한 함수 내부로 국한)
- 함수의 동작을 처리하기 위해 잠시 사용하는 변수로 함수가 종료되면 사라짐
- 이름 충돌을 피하고, 함수의 동작에 필요한 모든 것을 내부에 포함시켜 독립성, 재활용성 향상
- 지속 시간이 함수 실행 중으로 제한되어 메모리 절약 (필요할 때만 기억장소 차지)
- 사용 범위가 좁기 때문에 디버깅이 쉬움

### 💡 전역 변수

```python
salerate = 0.9     # 전역변수(global)

def kim():
    print('오늘의 할인율 :', salerate)

def lee(price):
    print('가격 :', price * salerate)
    
kim()
salerate = 1.1
lee(1000)

>>> 오늘의 할인율 : 0.9
    가격 : 1100.0
```


- 함수 내부에서 처음 대입하는 변수는 항상 지역 변수로 간주
- 파이썬의 경우 명시적인 선언이 없고 대입에 의해 변수를 생성하기 때문에 초기화하는 장소에 따라 범위 결정

```python
price = 1000     # 전역 변수 (price)

def sale():
    price = 500  # 지역 변수 (price)

sale()
print(price)

>>> 1000
```

```python
price = 1000    

def sale():
    price = 500 
    print('sale', id(price))

sale()
print('global', id(price))

>>> sale 2002926032176
    global 2002926034480
```
- 위와 같이 같은 이름을 가지고 있지만 주소가 다름 == 아예 다른 변수
- 그래서 지역, 전역끼리는 이름이 같아도 상관없으나 함수 내부에서는 지역 변수가 우선이라는 규칙 적용!
- 그럼 위 예시에서 새로운 지역 변수를 의미한 게 아니라 전역 변수 price의 값을 변경하고자 한 거라면?
  - 명령어 global 사용

```python
price = 1000

def sale():
    global price
    price = 500

sale()
print(price)

>>> 500
```

그러나 global 명령어는 가급적 사용하지 않는 것이 좋고, 정 필요한 경우 g_price 식으로 이름에 전역임을 표시하여 충돌 원천 방지가 합리적

### 💡 docstring

- 함수의 재활용성을 높이기 위해 자세한 함수 사용법이나 인수의 의미, 주의 사항 등을 문서로 남김
- 함수 선언문과 본체 사이에 작성하는 문자열
- 한 줄일 때는 단순 따옴표를 쓸 수도 있지만, 보통 삼겹 따옴표(""")로 여러 줄의 긴 설명을 작성하고 서식도 지정 가능
- 단순 설명일 뿐 코드가 아니기 때문에 실행에는 아무런 영향을 미치지 않음
- docstring 읽을 때 help 함수를 사용, 인수로 함수명 전달

```python
def calcsum(n):
    """1 ~ n 까지의 합계를 구해 리턴한다."""
    summ = 0
    for i in range(n + 1):
        summ += i
    return summ

help(calcsum)

>>> Help on function calcsum in module __main__:

    calcsum(n)
        1 ~ n 까지의 합계를 구해 리턴한다.
```
