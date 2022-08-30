---
title: "[Python] 아스키 코드 문자 변환 ord(), chr()"
excerpt: "python char to ascii code"

categories:
  - Python
tags:
  - [python, ascii]

permalink: /python/ascii/

toc: true
toc_sticky: true

date: 2022-08-30
last_modified_at: 2022-08-30
---

## 🚀 아스키코드(ascii)
아스키(ASCII)는 미국 정보 교환 표준 부호(American Standard Code for Information Interchange)로, 말 그대로 정보를 교환하는 부호입니다.
아스키 코드는 영문알파벳과 기호에 적합한 문자 인코딩으로 0부터 127까지 총 128개의 부호가 사용됩니다.
아래는 나무위키에서 가져온 아스키코드표 입니다.
![아스키코드표](/assets/images/posts_img/ascii/ascii_code_table.jpg)
출처: [나무위키](https://namu.wiki/w/%EC%95%84%EC%8A%A4%ED%82%A4%20%EC%BD%94%EB%93%9C)

### 💡 문자의 아스키 코드 확인(반환) : ord(str)
문자열을 아스키코드로 반환할 수 있는 함수로, 괄호() 안에 문자를 넣으면 그 문자에 해당하는 아스키코드를 숫자로 반환합니다.
```python
ord('A')
>>> 65  

ord('6')
>>> 54  

ord(6)
>>> TypeError : ord() expected string of length 1, but int found

print(ord('b') - ord('a'))   # 아스키코드로 변환된 숫자 간 연산 가능
>>> 1
```

### 💡 아스키코드를 문자열로 반환 : chr(int)
아스키코드를 문자로 반환하는 함수로, 괄호() 안에 숫자를 넣으면 그 숫자의 아스키코드에 대응하는 문자를 반환합니다.
```python
chr(65)
>>> 'A'

chr(90)
>>> 'Z'

chr(44032)
>>> '가'

for i in range(97,123):
    print(chr(i), end=' ')
>>> a b c d e f g h i j k l m n o p q r s t u v w x y z 
```
