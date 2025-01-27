---
title: "[python] 확장열과 긴 문자열"
excerpt: "#파이썬정복 #한빛미디어 python의 문자열(string) 중 확장열과 긴 문자열 "

categories:
  - Python
tags:
  - [Python]

permalink: /python/string-1/

toc: true
toc_sticky: true

date: 2023-01-10
last_modified_at: 2023-01-10
---

## 🚀 확장열(Escape Sequence)

문자열 안에 담기 힘든 특수한 문자의 경우 \문자 뒤에 특별한 기호로 표시하여 문자로 구분

|&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;확장열&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|설명|
|:-----:|:-----:|
| \n | 개행 |
| \t | 탭 |
| \\" | 큰따옴표 |
| \\' |&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 작은따옴표 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|
| \\\ | 문자 \\ |

```python
a = "old\new"
print(a)

>>> old
    ew
```
- \ 다음의 new 첫 글자인 n이 확장열로 해석되어 이 자리에서 개행(\n)  
- 진짜 \문자를 표기하고 싶은 경우에는 아래와 같이 써야 함

```python
a = "old\\new"
print(a)

>>> old\new
```

### 💡 문자열 앞에 r 접두 사용
확장열을 사용하지 않고, 문자 그대로 출력을 원하는 경우에 사용

```python
print("c:\temp\new.txt")

>>> c: emp
    ew.txt
```

```python
print(r"c:\temp\new.txt")

>>> c:\temp\new.txt
```



## 🚀 긴 문자열
### 💡 따옴표 3개 연달아 사용(''' | """)
- 개행 코드까지 문자열의 일부로 포함되므로 \n을 쓰지 않아도 상관없음
  - 코드상으로 개행한 곳에서 실제 개행이 발생하기 때문에 있는 그대로 적어 넣으면 됨
- 들여쓰기도 문자열의 일부로 인식되므로 2행 이후 들여쓰기 X

```python
s = """강나루 건너서 밀밭 길을 구름에 달 가듯이 가는 나그네
길은 외줄기 남도 삼백리 술 익는 마을마다 타는 저녁놀
구름에 달 가듯이 가는 나그네"""

print(s)

>>> 강나루 건너서 밀밭 길을 구름에 달 가듯이 가는 나그네
    길은 외줄기 남도 삼백리 술 익는 마을마다 타는 저녁놀
    구름에 달 가듯이 가는 나그네
```

### 💡 행 계속 문자 \ 
- 행을 이어줄 뿐이므로 개행 코드를 삽입하지 않는 경우 긴 문자열이 만들어짐
- 개행을 원하는 경우 \n 확장열 사용  

```python
s = "강나루 건너서 밀밭 길을 구름에 달 가듯이 가는 나그네 \
길은 외줄기 남도 삼백리 술 익는 마을마다 타는 저녁놀 \
구름에 달 가듯이 가는 나그네"

print(s)

>>> 강나루 건너서 밀밭 길을 구름에 달 가듯이 가는 나그네 길은 외줄기 남도 삼백리 술 익는 마을마다 타는 저녁놀 구름에 달 가듯이 가는 나그네
```

코드를 다음 행에 계속 써야 하는 경우에도 사용 가능  

```python
totalsec = 365 * 24 * \
           60 * 60
print(totalsec)

>>> 31536000
```

### 💡 인접한 문자열의 경우
- 콤마로 구분하지 않고 짧은 문자열을 쭉 나열하는 경우 하나의 문자열로 합쳐짐
- 중간의 공백은 모두 무시되나, 개행 코드는 무시되지 않고 다음 줄로 내려감

```python
s = "korea" "japan" "2002"
print(s)

>>> koreajapan2002
```

여러 개의 문자열을 개행해서 긴 문자열로 만들고 싶은 경우, 전체를 괄호()로 감싸야 함
```python
s = ("korea"
     "japan"
     "2002")
print(s)

>>> koreajapan2002
```
