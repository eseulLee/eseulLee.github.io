---
title: "[python] List 활용하기(3)- 기타 내장함수"
excerpt: "list의 내장함수에 대해 알아보자!"

categories:
  - Python
tags:
  - [Python]

permalink: /python/list-3/

toc: true
toc_sticky: true

date: 2022-10-20
last_modified_at: 2022-10-20
---


## 🚀 index()
특정 원소의 index number 리턴  

```python
a = list(range(1, 11))   # 1~10으로 구성된 리스트 생성
print(a.index(5))

>>> 4
```

## 🚀 최대/최소 찾기
### 💡 최대(max)

```python
a = list(range(1, 11))
print(max(a))

>>> 10
```

### 💡 최소(min)

```python
a = list(range(1, 11))
print(min(a))

>>> 1
```

## 🚀 리스트 무작위로 섞기

```python
import random as r

a = list(range(1, 11))
print(a)
r.shuffle(a)
print(a)

>>> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> [1, 6, 4, 10, 8, 7, 2, 3, 5, 9]
```
[리스트 정렬 관련 포스트](/python/list-2/)

## 🚀 clear()
리스트 내 원소 모두 삭제

```python
a = list(range(1, 11))
a.clear()
print(a)

>>> []
```


## 🚀 all/any
### 💡 all

모든 경우가 True인 경우 True 리턴  
하나라도 False가 나오면 False

```python
a = [11, 22, 33, 44, 55, 66]

if all(50 > x for x in a):
    print("YES")
else:
    print("NO")
    
>>> NO
```

### 💡 any
하나라도 True인 경우 True 리턴  
모두 False여야 False 리턴

```python
a = [11, 22, 33, 44, 55, 66]

if any(50 > x for x in a):
    print("YES")
else:
    print("NO")
    
>>> YES
```

