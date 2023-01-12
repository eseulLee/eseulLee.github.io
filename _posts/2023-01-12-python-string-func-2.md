---
title: "[python] 문자열과 내장함수/메서드 (2)"
excerpt: "#파이썬정복 #한빛미디어 python의 문자열(string)과 내장함수/메서드"

categories:
  - Python
tags:
  - [Python]

permalink: /python/string-func-2/

toc: true
toc_sticky: true

date: 2023-01-12
last_modified_at: 2023-01-12
---

## 🚀 검색

```python
s = 'python programming'
print(len(s))         # 내장함수
print(s.find('o'))    # 메서드
print(s.rfind('o'))   # r : rear
print(s.index('r'))
print(s.rindex('r'))
print(s.count('n'))
```
```python
18
4
9
8
11
2
```

- rfind, rindex의 r은 rear의 약자로 뒤에서 검색을 시작
- find, rfind의 경우 해당 문자가 없을 때 -1 리턴
- index, rindex의 경우 해당 문자가 없을 때 예외(에러) 발생
  - 반드시 예외 처리 구문으로 감싸야 함

## 🚀 조사
### 💡 in/ not in

```python
s = 'python programming'
print('a' in s)
print('z' in s)
print('pro' in s)
print('x' not in s)
```
```python
True
False
True
True
```

### 💡 startswith/ endswith

```python
name = '홍길동'
if name.startswith('홍'):
    print('홍가입니다.')
if name.startswith('길'):
    print('가입니다.')
    
file = 'girl.jpg'
if file.endswith('.jpg'):
    print('그림 파일입니다.')
```
```python
홍가입니다.
그림 파일입니다.
```

|함수|설명|
|----|----|
|isalpha|모든 문자가 **알파벳**인지 조사|
|islower|모든 문자가 **소문자**인지 조사|
|isupper|모든 문자가 **대문자**인지 조사|
|isspace|모든 문자가 **공백**인지 조사|
|isalnum|모든 문자가 **알파벳 또는 숫자**인지 조사|
|isdecimal|모든 문자가 **숫자(0~9)**인지 조사|
|isdigit|모든 문자가 **숫자**인지 조사|
|isnumeric|모든 문자가 **숫자**인지 조사|
|isidentifier&emsp;&emsp;&emsp;|**명칭으로 쓸 수 있는 문자**로만 구성되어 있는지 조사&emsp;&emsp;&emsp;&emsp;|
|isprintable|**인쇄 가능한 문자**로만 구성되어 있는지 조사|


## 🚀 변경

```python
s = 'good mOrning, my love KIM.'
print(s.lower())
print(s.upper())
print(s)

print(s.swapcase())
print(s.capitalize())
print(s.title())
```
```python
good morning, my love kim.
GOOD MORNING, MY LOVE KIM.
good mOrning, my love KIM.
GOOD MoRNING, MY LOVE kim.
Good morning, my love kim.
Good Morning, My Love Kim.
```

변경한 문자열을 변수에 대입해 저장할 수도 있지만, 한번만 필요한 경우 메서드 호출문을 바로 사용하는 것이 더 편리!

```python
quiz = input('사과를 영어로 하면? : ')
if quiz.lower() == 'apple':
    print('맞췄습니다!')
    
>>> 사과를 영어로 하면? : Apple
    맞췄습니다!
```

### 💡 공백 제거(strip)

```python
s = "   eseul   "
print(s + '님')
print(s.lstrip() + '님')
print(s.rstrip() + '님')
print(s.strip() + '님')
```
```python
   eseul   님
eseul   님
   eseul님
eseul님
```

## 🚀 분할
### 💡 split

```python
s1 = '짜장면 짬뽕 탕수육'
print(s1.split())       # 디폴트 구분자: 공백

s2 = '서울>>대전>>대구>>부산'
city = s2.split('>>')
print(city)
for c in city:
    print(c, '찍고', end=' ')
```
```python
['짜장면', '짬뽕', '탕수육']
['서울', '대전', '대구', '부산']
서울 찍고 대전 찍고 대구 찍고 부산 찍고 
```

### 💡 splitlines
- 개행 문자나 파일 구분자, 그룹 구분자 등을 기준으로 문자열을 잘라 리스트화
- 주로 개행 코드를 기준으로 한 행씩 잘라내며 긴 문서를 각 행별로 쪼개 관리할 때 편리

```python
traveler = """강나루 건너서\n밀밭 길을\n\n구름에 달 가듯이\n가는 나그네\n
길은 외줄기\n남도 삼백리\n\n술 익는 마을마다\n타는 저녁놀\n
구름에 달 가듯이\n가는 나그네"""

poet = traveler.splitlines()
print(poet)

for line in poet:
    print(line)
```
```python
['강나루 건너서', '밀밭 길을', '', '구름에 달 가듯이', '가는 나그네', '', '길은 외줄기', '남도 삼백리', '', '술 익는 마을마다', '타는 저녁놀', '', '구름에 달 가듯이', '가는 나그네']
강나루 건너서
밀밭 길을

구름에 달 가듯이
가는 나그네

길은 외줄기
남도 삼백리

술 익는 마을마다
타는 저녁놀

구름에 달 가듯이
가는 나그네
```

### 💡 join
- 문자열의 각 문자 사이에 다른 문자열을 끼워 넣음
- join 메서드를 호출하는 문자열이 삽입 대상임을 유의!

```python
s = '._.'
print(s.join('안녕하세요'))

>>> 안._.녕._.하._.세._.요
```

## 🚀 대체
### 💡 replace
- 특정 문자열을 찾아 다른 문자열로 대체
- 문자열 전체에서 원본 문자열을 모두 찾아 대체 문자열로 바꿈
- replace(old, new, [count])
  - old : 현재 문자열에서 변경하고 싶은 문자
  - new: 새로 바꿀 문자
  - count: 변경할 횟수. 횟수는 입력하지 않으면 old의 문자열 전체를 변경. 기본값은 전체를 의미하는 count=-1

```python
a = 'hello world'
print(a)
print(a.replace('hello','hi'))
```
```python
hello world
hi world
```

### 💡 just
- 문자열을 특정 폭에 맞추어 정렬

```python
message = '안녕하세요~'
print(message.ljust(30))
print(message.rjust(30))
print(message.center(30))
```
```python
안녕하세요~                        
                        안녕하세요~
            안녕하세요~            
```






