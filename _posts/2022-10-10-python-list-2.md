---
title: "[python] List 활용하기(2)- 리스트 정렬"
excerpt: "list 정렬하기: sort, reverse"

categories:
  - Python
tags:
  - [Python]

permalink: /python/list-2/

toc: true
toc_sticky: true

date: 2022-10-10
last_modified_at: 2022-10-10
---

리스트는 다른 자료형을 담을 수 있지만, sort 함수를 사용하기 위해서는 리스트 내부에 **같은** 자료형이 들어있어야 함

## 🚀 list 자체 정렬
### 💡 list.sort()
1. (default) 숫자형은 **오름차순**, 문자열은 **사전순**

```python
a = [6, 2, 4, 1]
b = ['carrot', 'apple', 'banana']
a.sort()
b.sort()
print(a, b)

>>> [1, 2, 4, 6] ['apple', 'banana', 'carrot']
```

2. (option) reverse=True : **내림차순** 정렬

```python
c = [1, 10, 5, 7, 6]
c.sort(reverse=True)
print(c)

>>> [10, 7, 6, 5, 1]
```

3. (option) key= : key 옵션을 통해 정렬 기준을 정할 수 있음

```python
d = ['pizza', 'chicken', 'coke']
d.sort(key=len)
print(d)

>>> ['coke', 'pizza', 'chicken']
```

### 💡 list.reverse()
- 리스트를 거꾸로 뒤집음
- Not desc 정렬 주의

```python
e = [2, 15, 8, 7, 9]
e.reverse()
print(e)

>>> [9, 7, 8, 15, 2]
```

## 🚀 list의 정렬된 결과만 반환
- list 자체를 변형하지 않음

### 💡 sorted()
- list의 원소를 순서대로 정렬하여 반환

```python
f = [1, 10, 3, 6, 8]
g = sorted(f)
print(f, g)

>>> [1, 10, 3, 6, 8] [1, 3, 6, 8, 10]
```

### 💡 reversed()
- 거꾸로 뒤집기(정렬의 역순이 아님 주의)
- **iterable한 객체**를 반환하므로 확인하기 위해서는 **list로 변형** 필요함

```python
h = [1, 11, 2, 5, 6]
i = reversed(h)
print(h)

>>> [1, 11, 2, 5, 6]   # 원래 리스트의 원소 순서 그대로
```

```python
print(i)

>>> <list_reverseiterator object at 0x7f79e5b142d0>
```
```python
i_ = list(i)   # list로 형변환
print(i_)

>>> [6, 5, 2, 11, 1]
```
