---
title: "[python] 리스트(List)"
excerpt: "#파이썬정복 #한빛미디어 리스트 원소 대체(Replace), 리스트 컴프리헨션(List Comprehension), 리스트 관리(삽입, 삭제, 검색, 정렬)"

categories:
  - Python
tags:
  - [Python]

permalink: /python/list-5/

toc: true
toc_sticky: true

date: 2023-01-18
last_modified_at: 2023-01-18
---


## 🚀 리스트(List)

- 리스트에 소속되는 각각의 값을 요소(Element) 또는 원소라고 함
- 문자열(변경 불가능)과는 달리 요소 변경 및 대체 가능

### 💡 리스트 요소 대체(replace)

```python
nums = list(range(10))   # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
nums[2:5] = [20, 30, 40]
print(nums)
nums[6:8] = [90, 91, 92, 93, 94]   # 개수 다른 경우도 대체 가능
print(nums)
```

```python
[0, 1, 20, 30, 40, 5, 6, 7, 8, 9]
[0, 1, 20, 30, 40, 5, 90, 91, 92, 93, 94, 8, 9]
```

### 💡 리스트 요소 삭제

```python
nums = list(range(10))
nums[2:5] = []  # 값을 빈 리스트[]로 대체시 삭제 효과
print(nums)
del nums[4]     # 요소 한 개 삭제
print(nums)
```

```python
[0, 1, 5, 6, 7, 8, 9]
[0, 1, 5, 6, 8, 9]
```

### 💡 리스트 요소 연결(concat)

```python
list1 = [1, 2, 3, 4, 5]
list2 = [10, 11]
listadd = list1 + list2
print(listadd)
listmulti = list2 * 3
print(listmulti)
```

```python
[1, 2, 3, 4, 5, 10, 11]
[10, 11, 10, 11, 10, 11]
```

## 🚀 2차원 리스트

**연습) 학생 성적처리**  

각 학생의 총점, 평균과 전체 학생의 평균 구하기

```python
score = [
    [88, 76, 92, 98],
    [65, 70, 58, 82],
    [82, 80, 78, 88]
]

total = 0
totalsub = 0

for student in score:
    sum_ = 0
    for subject in student:
        sum_ += subject
    subjects = len(student)
    print("총점 %4d, 평균 %6.2f" % (sum_, sum_/subjects))
    total += sum_
    totalsub += subjects
print("\n전체평균 %.2f" % (total/totalsub))
```

```python
총점  354, 평균  88.50
총점  275, 평균  68.75
총점  328, 평균  82.00

전체평균 79.75
```


## 🚀 List Comprehension

```python
[수식 for 변수 in 리스트 if 조건]
```

**연습) 1~10의 값 중 3의 배수만 골라 그 제곱 값으로 구성된 리스트 만들기**  

```python
lst = [n**2 for n in range(1, 11) if n % 3 == 0]
print(lst)

>>> [9, 36, 81]
```

## 🚀 리스트 관리

### 💡 삽입

```python
# 예시 1
nums = [1, 2, 3, 4]
nums[2:2] = [90, 91, 92]
print(nums)

>>> [1, 2, 90, 91, 92, 3, 4]
```

```python
# 예시 2
nums = [1, 2, 3, 4]
nums[2] = [90, 91, 92]
print(nums)

>>> [1, 2, [90, 91, 92], 4]
```

위의 예시 1의 경우, [2:2] 범위의 길이는 0이지만 삽입할 위치를 알려주는 역할을 하게 되어 길이 0의 범위에 길이 3의 리스트를 대입, 즉 세 개의 요소를 삽입하는 것과 같음  
반면 예시 2에서 [2]번째 위치의 요소에 리스트를 대입하는 것은 대입에 의해 2번째 요소값이 길이 3의 리스트로 대체되어 요소 개수에는 변화가 없으나 리스트끼리 중첩이 가능하므로 요소 자리에 리스트가 들어가게 됨  
리스트에 리스트를 추가하여 병합하고 싶을 때는? **extend** 사용!

```python
list1 = [1, 2, 3, 4, 5]
list2 = [10, 11]
list1.extend(list2)   # list1 += list2 와 같은 결과
print(list1)

>>> [1, 2, 3, 4, 5, 10, 11]
```

### 💡 삭제

```python
score = [88, 95, 70, 100, 99, 80, 78, 50]
score.remove(100)  # 요소값 직접 삭제
print(score)
del(score[2])      # 순서값 지정하여 삭제. del score[2]로도 호출 가능
print(score)
score[1:4] = []
print(score)       # 요소 여러 개 삭제. del score[1:4] 로도 가능
```

```python
[88, 95, 70, 99, 80, 78, 50]
[88, 95, 99, 80, 78, 50]
[88, 78, 50]
```

#### 👀 pop()

- remove와 del은 요소를 지우기만 하는 데에 비해 pop은 삭제한 요소를 꺼내 리턴
- 첨자를 지정하여 지울 대상을 지정하되 인수가 없으면 **마지막** 요소 pop
- 인수 생략시 pop(-1)을 호출하는 것과 같음
- 리스트의 끝에서 append로 추가하고 pop으로 제거하면 선입선출(FIFO) 방식으로 동작하는 스택(Stack)

```python
score = [88, 95, 70, 100, 99]
print(score.pop())
print(score.pop())
print(score.pop(1))
print(score)
```

```python
99
100
95
[88, 70]
```

### 💡 검색

- index: 특정 요소의 위치를 찾으며 발견되지 않을 경우 예외 발생
- count: 특정 요소값의 개수 조사

```python
score = [88, 95, 70, 100, 99, 80, 78, 50]
perfect = score.index(100)
print("만점 받은 학생은 %d번입니다." % perfect)
pernum = score.count(100)
print("만점자 수는 %d명입니다." % pernum)
```

```python
만점 받은 학생은 3번입니다.
만점자 수는 1명입니다.
```

- 리스트 내 요소 유무 판별: in/ not in 연산자 사용

```python
ans = input("결제하시겠습니까? ")
if ans in ['yes', 'y', 'ok', '네', '좋아요']:
    print("구입해주셔서 감사합니다!")
else:
    print('안녕히 가세요.')
```

```python
결제하시겠습니까? yes
구입해주셔서 감사합니다!
```

### 💡 정렬

#### 👀 sort/reverse 메서드

```python
score = [88, 95, 70, 100, 99]
score.sort()     # default: reverse=False > 오름차순 정렬 reverse=True시 내림차순 정렬
print(score)

score = [88, 95, 70, 100, 99]
score.reverse()  # 원 리스트의 요소의 순서를 반대로 뒤집음
print(score)
```

```python
[70, 88, 95, 99, 100]
[99, 100, 70, 95, 88]
```

#### 👀 key 인수

정렬 시 요소를 비교할 키를 추출하는 함수로 키를 변형하여 비교 기준으로 사용

```python
country = ["Korea", "japan", "CHINA", "america"]
country.sort()
print(country)
country.sort(key = str.lower) # 비교할 때만 잠시 소문자로 바뀔 뿐 요소 자체가 바뀌는 것은 아님
print(country)
```

```python
['CHINA', 'Korea', 'america', 'japan']
['america', 'CHINA', 'japan', 'Korea']
```

#### 👀 sorted 함수

- 리스트는 그대로 두고 정렬된 새로운 리스트를 만들어 리턴
- 원본은 유지되므로 정렬된 결과를 별도의 변수에 대입받아야 함
- sort 메서드와 마찬가지로 **reverse, key 키워드 인수**를 통해 내림차순으로 정렬하거나 비교방식 지정 

```python
score = [88, 95, 70, 100, 99]
score2 = sorted(score)
print(score)
print(score2)
```

```python
[88, 95, 70, 100, 99]
[70, 88, 95, 99, 100]
```
