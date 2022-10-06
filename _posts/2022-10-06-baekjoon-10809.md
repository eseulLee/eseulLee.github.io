---
title: "[Baekjoon] 10809: 알파벳 찾기"
excerpt: "Baekjoon Algorithm [Python3]"

categories:
  - Baekjoon
tags:
  - [Backjoon, Algorithm, Python]

permalink: /baekjoon/10809/

toc: true
toc_sticky: true

date: 2022-10-06
last_modified_at: 2022-10-06
---

## ✔️ 문제     [😎링크](https://www.acmicpc.net/problem/10809)
알파벳 소문자로만 이루어진 단어 S가 주어진다. 각각의 알파벳에 대해서, 단어에 포함되어 있는 경우에는 처음 등장하는 위치를, 포함되어 있지 않은 경우에는 -1을 출력하는 프로그램을 작성하시오.  
각각의 알파벳에 대해서, a가 처음 등장하는 위치, b가 처음 등장하는 위치, ... z가 처음 등장하는 위치를 공백으로 구분해서 출력한다.  
만약, 어떤 알파벳이 단어에 포함되어 있지 않다면 -1을 출력한다. 단어의 첫 번째 글자는 0번째 위치이고, 두 번째 글자는 1번째 위치이다.

## ✔️ 예시 (입력: baekjoon)
```python
1 0 -1 -1 2 -1 -1 -1 -1 4 3 -1 -1 7 5 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1
```
## ✔️ SOLUTION
### 문제 접근

- 알파벳 리스트를 만들어야 하므로 두가지 접근 방법 이용: 1) 알파벳으로 리스트 만들기 2) 아스키 코드 사용해서 리스트 만들기
- 2)의 경우 문자와 숫자 간 변환할 수 있는 함수를 각각 사용해야 함(chr, ord)
- for문을 이용해 리스트를 돌면서 문자열 S에 어디에 위치하는지 index number 추출
- string 그대로 사용하는 경우 find 함수 이용 (list로 변환시 index 사용)

```python
S = input()

# 1) 알파벳 소문자 리스트 사용
str_lst = 'abcdefghijklmnopqrstuvwxyz'
for s in str_lst:
    print(S.find(s), end=' ')

# 2) 아스키 코드 리스트 사용
ascii_lst = [i for i in range(97, 123)]
for n in ascii_lst :
    print(S.find(chr(n)), end=' ')
```


