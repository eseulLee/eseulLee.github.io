---
title: "[python] 문자열과 내장함수"
excerpt: "python의 문자열(string)과 내장함수"

categories:
  - Python
tags:
  - [Python]

permalink: /python/string-func/

toc: true
toc_sticky: true

date: 2022-10-20
last_modified_at: 2022-10-20
---

## 🚀 upper()

문자열을 대문자로 변환  
문자열 자체를 대문자로 바꾸는 것이 아니므로 원 변수를 출력하는 경우 그대로 출력됨  

```python
msg = 'It is Time'
print(msg.upper())
print(msg)

>>> IT IS TIME
>>> It is Time
```
대문자로 변환된 문자열을 새로운 변수로 정의해야 함  

```python
tmp = msg.upper()
print(tmp)

>>> IT IS TIME
```


## 🚀 lower()

문자열을 소문자로 변환

```python
msg = 'It is Time'
print(msg.lower())
print(msg)

>>> it is time
>>> It is Time
```

## 🚀 find
- 문자열에서 특정 문자의 index number를 리턴
- 문자가 중복되는 경우 0번째 부터 첫번째로 나오는 문자의 index를 가져오게 됨

```python
msg = 'It is Time'
tmp = msg.upper()
print(tmp.find('T'))

>>> 1
```

## 🚀 count
- 문자열에서 특정 문자의 개수 리턴

```python
msg = 'It is Time'
tmp = msg.upper()
print(tmp.count('T'))

>>> 2
```

## 🚀 문자마다 접근(for문 사용)
### 💡 len(str) 이용

문자열의 문자 개수를 구해서 그 숫자만큼 for문 반복

```python
msg = 'It is Time'

print(len(msg))   # 공백까지 포함하여 수 count
for i in range(len(msg)):
    print(msg[i], end='  ')

>>> 10
>>> I  t     i  s     T  i  m  e
```

### 💡 문자 그대로 접근

```python
msg = 'It is Time'

for x in msg:
    print(x, end='  ')

>>> I  t     i  s     T  i  m  e
```

## 🚀 isupper()

대문자면 True, 아니면 False 리턴

```python
msg = 'It is Time'

for x in msg:
    if x.isupper():
        print(x, end='  ')

>>> I  T
```

## 🚀 islower()

소문자면 True, 아니면 False 리턴

```python
msg = 'It is Time'

for x in msg:
    if x.islower():
        print(x, end='  ')

>>> t  i  s  i  m  e  
```

## 🚀 알파벳/숫자 여부 판별
### 💡 isalpha()
알파벳인 경우 True, 아닌 경우 False 리턴  
알파벳을 제외한 숫자, 공백 등의 경우에는 모두 False

```python
msg = 'It is Time'

for x in msg:
    if x.isalpha():
        print(x, end='')

>>> ItisTime
```

### 💡 isdigit()
숫자인 경우 True, 아닌 경우 False 리턴  

```python
alnum = "ab!cd#ef$g 1h^^ij23"

for y in alnum:
    if y.isdigit():
        print(y, end='')

>>> 123
```

### 💡 isalnum()
알파벳/숫자인 경우 True, 아닌 경우 False 리턴  
특수문자와 공백 모두 제거(False)되고 출력

```python
alnum = "ab!cd#ef$g 1h^^ij23"

for y in alnum:
    if y.isalnum():
        print(y, end='')

>>> abcdefg1hij23
```
