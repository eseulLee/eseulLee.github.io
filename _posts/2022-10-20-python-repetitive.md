---
title: "[python] 반복문 - for, while, break, continue"
excerpt: "python 반복문 문법 정리: for, while, break, continue"

categories:
  - Python
tags:
  - [Python]

permalink: /python/repetitive/

toc: true
toc_sticky: true

date: 2022-10-20
last_modified_at: 2022-10-20
---

## 🚀 range 사용
```python
a = range(10)
print(a)

>>> range(0, 10)
```
range(10)을 그대로 출력하는 경우 range 자체가 출력되므로 리스트 형태를 원하는 경우 리스트로 형변환 필요
```python
print(list(a))

>>> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## 🚀 반복문 for
### 💡 for ~ range

```python
for i in range(1, 11):
    print(i)  # 1부터 10까지 순서대로 출력
```
```python
1
2
3
4
5
6
7
8
9
10
```
10부터 1까지 거꾸로 출력해야 하는 경우 range() 내의 세번째 인자로 -1 입력 **(-2 입력시 2씩 작아짐)**
- 1~10의 숫자를 출력하는 것은 동일하나, 시작 숫자가 다르기 때문에 range() 내에 들어가는 숫자가 다름 주의

```python
for i in range(10, 0, -1):
    print(i)
```
```python
10
9
8
7
6
5
4
3
2
1
```

### 💡 for ~ else
- for문이 정상적으로 모두 반복되는 경우에만 else문 실행
- break에 의한 비정상적인 종료 등 반복문이 모두 실행되지 않았을 경우에는 else문 실행X  


i가 5보다 큰 경우 print함수로 출력 후 break 이므로 중간에 반복문이 중단되면서 종료됨  
👉 else문은 실행되지 않음

```python
for i in range(1, 11):
    print(i)
    if i >= 5:
        break
else:
    print(11)
    print('Success!')
```
```python
1
2
3
4
5
```

반복문이 1부터 10까지 모두 실행된 후에 else문 실행됨 
 

```python
for i in range(1, 11):
    print(i)
    if i >= 12:
        break
else:
    print(11)
    print('Success!')
```
```python
1
2
3
4
5
6
7
8
9
10
11
Success!
```
 
## 🚀 반복문 while
- 초기값 설정 필수
- while 조건문이 True인 경우 반복해서 실행됨
- 초기값 혹은 조건문을 False로 바꿔주는 코드가 없는 경우 무한루프를 돌 수 있음 주의

```python
i = 1     # 초기값 설정
while i <= 10 :
    print(i)
    i += 1
```
```python
1
2
3
4
5
6
7
8
9
10
```

## 🚀 break
- 반복문의 반복을 멈추게 하는 역할
- 아래의 예시처럼 조건문이 True인 경우 무한루프를 돌게 됨
- break는 이러한 while문의 무한 반복을 멈추게 함
- 혹은 특정 조건일 때(if문) 멈추게 함

```python
i = 1
while True :
    print(i)
    if i == 10 :
        break
    i += 1
```
```python
1
2
3
4
5
6
7
8
9
10
```

## 🚀 continue
- continue 아래의 반복문이 실행되지 않고 다음 반복으로 넘어가게 됨

```python
for i in range(1, 11):
    if i % 2 == 0 :     # 홀수만 출력
        continue
    print(i)
```

```python
1
3
5
7
9
```
