---
title: "[python] 문자열 포맷팅"
excerpt: "#파이썬정복 #한빛미디어 python의 문자열(string) 포맷팅"

categories:
  - Python
tags:
  - [Python]

permalink: /python/string-2/

toc: true
toc_sticky: true

date: 2023-01-18
last_modified_at: 2023-01-18
---

## 🚀 + 연산자 연결

```python
price = 500
print("이 물건의 가격은 " + str(price) + "원 입니다.")

>>> 이 물건의 가격은 500원 입니다.
```


## 🚀 % 표식 사용

문자열에 다음과 같은 표식을 넣고 뒤에 대응하는 변수를 밝히면 표식 자리에 정보 삽입

|&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;표식&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|설명|
|:-----:|:-----:|
| %d | 정수 |
| %f | 실수 |
| %s | 문자열 |
| %c |&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 문자 하나 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|
| %h | 16진수 |
| %o | 8진수 |
| %% | %자문자 |

```python
price = 500
print("이 물건의 가격은 %d원 입니다." % price)

>>> 이 물건의 가격은 500원 입니다.
```

서식이 두 개 이상인 경우, (값1, 값2) 식으로 실제값을 괄호로 묶어 나열

```python
month = 8
day = 15
anni = "광복절"
print("%d월 %d일은 %s이다." % (month, day, anni))

>>> 8월 15일은 광복절이다.
```


### 💡 출력 형식 지정

```
%[-]폭[.유효자리수]서식
```


#### 👀 Width

서식이 지정하는 폭은 강제 폭이 아닌 **최소 폭**으로, 자리수보다 작은 폭을 주어도 최소한 숫자의 자리수만큼은 차지  
  - 아래의 %1d의 경우, 강제로 1자리로 맞춰 잘리지 않고 3자리 모두 출력


```python
value = 123
print('###%d###' % value)
print('###%5d###' % value)
print('###%10d###' % value)
print('###%1d###' % value)
```

```python
###123###
###  123###
###       123###
###123###
```

#### 👀 Align

일정한 폭을 강제로 할당하여 출력시 변수의 값에 상관없이 숫자의 자리수를 가지런히 맞출 수 있어 숫자 파악에 용이  
 

```python
price = [30, 13500, 2000]

for p in price:
    print("가격:%d원"  % p)
for p in price:
    print("가격:%7d원" % p)
```

```python
가격:30원
가격:13500원
가격:2000원
가격:     30원
가격:  13500원
가격:   2000원
```

#### 👀 Numalign

- 서식 기본값은 오른쪽 정렬
- 폭에 -를 지정하면 왼쪽으로 정렬 (문자열의 경우, 왼쪽 정렬이 보기에 좋음!)

```python
price = [30, 13500, 2000]
for p in price:
    print("가격:%-7d원" % p)
```

```python
가격:30     원
가격:13500  원
가격:2000   원
```


#### 👀 Precision

. 기호와 함께 유효 자리수를 밝혀 소수점 이하 얼마까지 표시할 것인지 정밀도 지정 가능

```python
pie = 3.14159265
print("%10f" % pie)   # 별 다른 지정이 없는 겨우, 소수점 6자리까지 반올림하여 표시
print("%10.8f" % pie)
print("%10.5f" % pie)
print("%10.2f" % pie)
```

```python
  3.141593
3.14159265
   3.14159
      3.14
```


## 🚀 {}.format 메서드 사용

- 신형 포맷팅, 파이썬 2.6 이후부터 

```python
name = 'Jack'
age = 16
height = 162.5
print("이름:{}, 나이:{}, 키:{}".format(name, age, height))

>>> 이름:Jack, 나이:16, 키:162.5
```

{} 괄호 안에 0부터 시작하는 순서값을 지정하는데, 순서값 생략시 0부터 차례대로 번호를 매기게 됨
  - 번호를 사용하면 순서를 임의대로 바꿀 수 있음

```python
name = 'Jack'
age = 16
height = 162.5
print("이름:{2}, 나이:{0}, 키:{1}".format(age, height, name))

>>> 이름:Jack, 나이:16, 키:162.5
```

{} 괄호 안에 변수 이름을 적어 두고 format의 인수열에 변수의 값 나열 가능  
이 때, 키워드 인수로 값을 지정하므로 인수의 순서 상관 없음

```python
print("이름:{name}, 나이:{age}, 키:{height}".format(name = 'Woo', age = 20, height = 160.9))

>>> 이름:Woo, 나이:20, 키:160.9
```

#### 👀 사전에 저장된 값 출력

- 사전을 인수로 주고 []괄호 안에 키 입력
- 사전의 키로부터 값을 검색하여 문자열 중간에 삽입

```python
boy = {"name":"Han", "age":15, "height":158.7}
print("이름:{0[name]}, 나이:{0[age]}, 키:{0[height]}".format(boy))

>>> 이름:Han, 나이:15, 키:158.7
```

#### 👀 인수 타입 지정

- {} 괄호 안의 : 다음에 인수의 타입 지정
- 문자열은 s, 정수는 d, 실수는 f의 타입 사용

```python
name = "Han"
age = 15
height = 158.7
print("이름:{0:s}, 나이:{1:d}, 키:{2:f}".format(name, age, height))

>>> 이름:Han, 나이:15, 키:158.700000
```

### 💡 출력 형식 지정

#### 👀 Width, Precision

:과 타입 문자 사이에 폭/ 정밀도 지정

```python
name = "Han"
age = 15
height = 158.7
print("이름:{0:10s}, 나이:{1:5d}, 키:{2:8.2f}".format(name, age, height))

>>> 이름:Han       , 나이:   15, 키:  158.70
```

#### 👀 Align

- 기본값은 문자열 왼쪽 정렬, 수치값 오른쪽 정렬
- 정렬 지정할 때는 < 왼쪽, > 오른쪽, **^ 중앙 정렬** 기호를 폭 앞에 붙임

```python
name = "Han"
age = 15
height = 158.7
print("이름:{0:^10s}, 나이:{1:>5d}, 키:{2:<8.2f}".format(name, age, height))

>>> 이름:   Han    , 나이:   15, 키:158.70  
```

정렬 문자 이전에 채움 문자 지정시, 공백 대신 채움 문자 출력 가능

```python
name = "Han"
age = 15
height = 158.7
print("이름:{0:$^10s}, 나이:{1:0>5d}, 키:{2:!<8.2f}".format(name, age, height))

>>> 이름:$$$Han$$$$, 나이:00015, 키:158.70!!
```

