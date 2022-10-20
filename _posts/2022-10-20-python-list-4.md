---
title: "[python] 2차원 리스트 생성과 접근"
excerpt: "2차원 리스트에 대해 알아보자!"

categories:
  - Python
tags:
  - [Python]

permalink: /python/list-4/

toc: true
toc_sticky: true

date: 2022-10-20
last_modified_at: 2022-10-20
---


## 🚀 1차원 리스트 생성

```python
a = [0] * 3
print(a)

>>> [0, 0, 0]
```

## 🚀 2차원 리스트 생성

```python
a = [[0] * 3 for _ in range(3)]
print(a)

>>> [[0, 0, 0], [0, 0, 0], [0, 0, 0]]
```

## 🚀 2차원 리스트 접근
### 💡 리스트 내 값 접근

```python
a = [[0] * 3 for _ in range(3)]
a[0][1] = 1   # 0행 1열의 값
a[1][1] = 2
print(a)

>>> [[0, 1, 0], [0, 2, 0], [0, 0, 0]]
```

### 💡 표 형태로 출력해보기

```python
a = [[0] * 3 for _ in range(3)]
a[0][1], a[1][1] = 1, 2

for idx, x in enumerate(a):
    for y in x:
        print(y, end=' ')
    print()
```
```python
0 1 0 
0 2 0 
0 0 0 
```
