---
title: "[Python 문법] 입력 받기(sys.stdin.readline)"
excerpt: "여러 줄 입력받을 때 써야하는 sys.stdin.readline() 정리"

categories:
  - Python
tags:
  - [python, readline]

permalink: /python/readline/

toc: true
toc_sticky: true

date: 2022-08-30
last_modified_at: 2022-08-30
---

## 🚀 input()
기본적인 입력 방법으로 input() 자체는 문자열을 입력받는 것으로 처리됩니다.  
따라서 숫자로 처리해야 하는 경우 형변환이 필요합니다.
```python
str = input()
num = int(input())
```
### 💡 input().split()
split() 함수는 특정 구분자로 문자열을 나눌 때 사용합니다.  
괄호 안에 특정 구분자를 입력하지 않는 경우, 공백(스페이스, 탭, 엔터 등)에 의한 띄어쓰기 구분으로 적용됩니다.
```python
str = input().split()
>>> ['Nice', 'to', 'meet', 'you']
```
### 💡 map()
input().split()을 통해 입력된 값들을 여러 변수를 생성하여 각각의 값으로 할당하고 싶을 때 사용합니다.   
단, 할당되는 변수와 값의 개수가 동일해야 합니다.
```python
a, b, c = map(int, input().split())    # 입력 : '1 3 5'
print(a, b, c)
>>> 1, 3, 5
```


## 🚀 input() 대신 readline()을 사용하는 경우
한두줄을 입력받는 경우와 달리 여러줄을 입력받아야 하는 경우 input()사용시 시간초과 문제가 발생할 수 있습니다.  
첫 줄에서 test case(size)를 입력받는 경우에는 input()을, 다음 줄부터는(여러줄 입력) `sys.stdin.readline()`을 사용해야 합니다.
```python
import sys

T = int(input())  # test case(size)
for i in range(T) :
    A, B = map(int, sys.stdin.readline().split())
    print(A, B)
```


## 🚀 sys.stdin.readline() 사용법 정리
### 💡 한 개의 정수 입력
```python
import sys
n = int(sys.stdin.readline())
```
sys.stdin.readline()의 경우, 한줄 단위로 입력받기 때문에 개행문자(\n)가 같이 입력받아 집니다.  
따라서, 1) 개행문자 제거, 2) 형변환(str→int)을 위해 위와 같이 사용합니다.

### 💡 둘 이상의 정수 입력
```python
import sys
a, b, c = map(int, sys.stdin.readline().split())     # 각각의 변수(a,b,c)에 할당
lst = list(map(int, sys.stdin.readline().split()))   # 리스트에 저장
```

### 💡 임의의 개수의 정수를 n줄 입력받아 2차원의 array에 저장하는 경우
```python
import sys
lst = []
T   = int(sys.stdin.readline())   # test case(size)
for i in range(T):
    lst.append(list(map(int, sys.stdin.readline().split())))
```

### 💡 n줄의 문자열을 입력받아 리스트에 저장하는 경우
```python
import sys
T = int(sys.stdin.readline())    # test case(size)
lst = [sys.stdin.readline().strip() for i in range(T)]
```
`strip()` 함수 사용하여 맨 앞, 맨 끝의 공백문자를 제거합니다.


## 🚀 참조링크
<https://velog.io/@yeseolee/Python-파이썬-입력-정리sys.stdin.readline>  
<https://velog.io/@tbnsok40/파이썬-다양한-입력방법-input-read-readline>
