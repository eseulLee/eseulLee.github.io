---
title: "[python] List 활용하기(1)- append, insert, extend, del, remove"
excerpt: "list에 자료추가 및 제거 #elice coding #python"

categories:
  - Python
tags:
  - [Python]

permalink: /python/list-1/

toc: true
toc_sticky: true

date: 2022-10-10
last_modified_at: 2022-10-10
---

list에 자료를 추가하거나 삭제하는 등 활용하는 경우 **dot access** 사용  

## 💡 list.append(d)
- **자료 d**를 리스트 **마지막 원소 뒤**에 추가
- 오직 **한 개의 자료**만 넣을 수 있음

```python
a = []
b = ['a', 'b', 'c']
a.append(10)
b.append('d')
print(a, b)

>>> [10] ['a', 'b', 'c', 'd']
```

## 💡 list.insert(i, d)
- **인덱스 i**(추가될 위치)에 **자료 d**를 추가
- 오직 **한 개의 자료**만 넣을 수 있음

```python
c = [1, 2, 4, 5]
c.insert(2, 3)   # (위치, 값)
print(c)

>>> [1, 2, 3, 4, 5]
```

## 💡 list.extend(list)
- list에 list를 추가
- \+ 연산자 사용하는 경우와 동일

```python
List = [1, 3, 5, 6]
List.extend([8, 10, 11])
print(List)

>>> [1, 3, 5, 6, 8, 10, 11]
```

### 🌟 + 연산자 사용

```python
lstA = [1, 3, 5]
lstB = [2, 4, 6]
lstC = lstA + lstB    # list 끼리 연산
print(lstC)

>>> [1, 3, 5, 2, 4, 6]
```

```python
lstC += [7, 8]
print(lstC)

>>> [1, 3, 5, 2, 4, 6, 7, 8]
```

## 💡 list.remove(d)
- **처음 나오는** 자료 d를 제거
- 원소 중복 시 인덱스가 작은 원소를 제거

```python
d = [3, 1, 2, 3]
d.remove(3)
print(d)

>>> [1, 2, 3]
```

## 💡 del list[i]
- list의 인덱스 i의 원소를 제거

```python
d_ = [1, 3, 5, 7, 9]
del d_[1]   # 1: index number
print(d_)

>>> [1, 5, 7, 9]
```
