---
title: "[Tableau] 신병훈련소 17기 2일차"
excerpt: "#Tableau #신병훈련소 #데이터_시각화 #계산식 #워드클라우드 #박스플롯"

categories:
  - tableau
tags:
  - [tableau, data_visualization]

permalink: /tableau/bootcamp-17-2/

toc: true
toc_sticky: true

date: 2023-02-06
last_modified_at: 2023-02-06
---

##  ✏️ 2일차

> 📖 2일차 학습 안내  
> - **워드 클라우드** : 칼로리가 높은 메뉴를 한 눈에 살펴보기
> - **박스 플롯(상자수염 차트)**: 여러 카테고리의 커피 메뉴를 여러 가지 선택 기준 적용해서 비교하기
> - **계산식** 맛보기


### 💡 행 수준 vs 집계 수준

- 태블로에서는 화면에 포함된 차원에 따라 측정값 혹은 차원을 집계하여 볼 수 있음
- 화면 차원 세팅시 이미 집계된 값이 보여지는 이유?
  - 이미 태블로에 **측정값 집계라는 옵션이 기본적으로 사용**되기 때문

| 행 수준 계산식                                                     | 집계 수준 계산식                                                             |
|--------------------------------------------------------------|-----------------------------------------------------------------------|
| 모든 행에 대해 계산 후 결과 값을 집계                                       | 각 필드 값을 집계한 후에 계산                                                     |
| [수익] / [매출]                                                  | SUM([수익])/SUM([매출])                                                   |
| 모든 행에 대해 결과 값이 실체화(materializaed)되기 때문에 처리 로직을 다시 실행할 필요가 없음 | 뷰에 사용된 차원에 따라 집계 값이 달라지기 때문에 Tableau 데이터 추출에서 실체화(materialized)될 수 없음 |
| - 열끼리의 사칙연산 <br> - 문자열 처리 <br> - 형 변환 <br> - 날짜/ 시간 계산 |                                                                       |

`집계 인수 및 집계되지 않은 임수를 이 함수와 혼합할 수 없습니다`라는 에러가 뜨는 이유?
- 그냥 필드 값과 집계된 필드 값을 같이 사용하게 되는 경우 생기는 오류
- 행 수준 계산식은 행수준끼리, 집계 수준 계산식은 집계 수준 계산식끼리 사용해야 함


![image](/assets/images/posts_img/tableau_bootcamp/20230206_tableau_bootcamp_17_2_1.png){: .align-center}

<br>

### 💡 계산식 사용하기

- 엑셀에서 수식을 사용하는 것처럼 계산식을 사용해 계산된 필드를 만들어 사용
- <span style="color:orange">참고)</span> [Tableau의 계산 이해](https://help.tableau.com/current/pro/desktop/ko-kr/calculations_calculatedfields_understand.htm)
- <span style="color:orange">참고)</span> [Tableau의 함수](https://help.tableau.com/current/pro/desktop/ko-kr/functions.htm)


![image](/assets/images/posts_img/tableau_bootcamp/20230206_tableau_bootcamp_17_2_2.png){: .align-center}



<br>

### 💡 워드클라우드(WordCloud)

- 많은 키워드 속에서 분석 목적에 따라 핵심 키워드를 표현하는 데 유용한 시각화
- 값의 자세한 비교보다는 데이터의 트렌드를 나타내는 데 좀 더 유용

<br>

### 💡 박스 플롯(Box Plot)

- 데이터의 분포 상태와 이상치를 동시에 보여주면서 서로 다른 데이터 군을 쉽게 비교할 수 있는 시각화
- 여러 개의 데이터를 한 눈에 표현할 수 있어 값을 비교하기에 유용

<br>

## ✏️ 2일차 과제

> "스타벅스 메뉴 데이터"와 "매장 정보 데이터"를 이용해 다양한 시각화, 분석 해보기  

### 1️⃣ 워드클라우드

```
워드클라우드로 가장"칼로리"가 높은 "메뉴명"을 한 눈에 살펴보자
```

1. **메뉴명**을 마크 유형의 **텍스트**에 가져다 놓기
2. **마크의 크기, 색상**을 모두 **칼로리**로 표현(가져다 놓기, Drag & Drop) 
3. 색상을  **칼로리가 높을수록 붉은 색, 칼로리가 낮을수록 푸른색**을 나타내도록 편집
5. 피해야 할 메뉴는? (= 가장 칼로리가 높은 메뉴명은?)  
   - 제주 까망 크림 프라푸치노!! 

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230206_tableau_bootcamp_17_2_3.png){: .align-center}  

</div>
</details>

<br>

### 2️⃣ 박스플롯

```
카테고리별 메뉴들의 칼로리 분포 표현 및 비교(+ 카페인)
```

1. 열 선반에 **카테고리**, 행 선반에 **칼로리** 추가
2. 마크 선반의 **세부정보**에 **메뉴명** Drag & Drop
   - 막대차트가 메뉴별로 쪼개지면서 세부 기준을 잡게 됨
   - 메뉴명 표현방식을 **원**으로 변경
3. 메뉴별 카페인도 함께 비교하기 위해 마크의 **색상**에 **카페인** Drag & Drop (원 크기 조절 필요) 
   - 카페인이 높을수록 붉은색, 낮을수록 푸른색으로
4. "**분석 탭**"에 있는 **박스 플롯** Drag & Drop

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230206_tableau_bootcamp_17_2_4.png){: .align-center}  

</div>
</details>

> [Day 1] 질문인 '칼로리가 낮고 카페인이 높지 않은 메뉴'를 마시고 싶다면?
- **티바나**가 상대적으로 칼로리와 카페인이 모두 낮은 메뉴
- 티바나 카테고리에서 칼로리가 낮은 마크 영역을 드래그 한 후에 **데이터 보기를 실행**
  - 해당 마크 영역에 존재하는 메뉴명(데이터) 확인 가능

<br>

### 3️⃣ 계산된 필드 만들기

```
평균 카페인 함유량이 80mg 보다 높은 카테고리와 아닌 카테고리를 분류하는 필드 만들기
```

1. 카테고리별 평균 칼로리 시각화
   - 열 선반에 평균 칼로리, 행 선반에 카테고리 추가
2. [계산된 필드 만들기] 선택 후 아래와 같이 계산식 입력
   ```
    IF AVG([카페인(Mg)]) > 80
    THEN "카페인 > 80mg"
    ELSE "카페인 <= 80mg"
    END
    ```
3. 만들어진 "**지정 카페인 용량**" 필드를 마크 선반의 색상에 Drag & Drop
   - 색상 편집 진행

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230206_tableau_bootcamp_17_2_5.png){: .align-center}  

</div>
</details>

<br>

### 🔥 추가 도전 과제

```
매장명 별로 매장운영시간을 표현하고, 시도를 필터로 걸어 각 시도의 매장 별 운영 시간 확인하기
```

1. "**매장운영시간**"이라는 계산 필드 생성
   - 날짜 함수 중 **DATEDIFF** 함수 사용하여 두 날짜 간 "시간(hour)" 차이 계산
   - [Tableau 날짜 함수](https://help.tableau.com/current/pro/desktop/ko-kr/functions_functions_date.htm)
2. date_part 인수 

|DATE_PART|	값|
|----|----|
|'year'|	4자리 연도|
|'quarter'|	1-4|
|'month'	|1-12 또는 "1월", "2월" 등|
|'dayofyear'|	일년 중 몇째 날. 1월 1일은 1, 2월 1일은 32 등으로 계산됩니다.|
|'day'|	1-31|
|'weekday'|	1-7 또는 "일요일", "월요일" 등|
|'week'|	1-52|
|'hour'|	0-23|
|'minute'|	0-59|
|'second'|	0-60|
|'iso-year'|	4자리 ISO 8601 연도|
|'iso-quarter'|	1-4|
|'iso-week'|	1-52, 주의 시작은 항상 월요일|
|'iso-weekday'|	1-7, 주의 시작은 항상 월요일|

<https://help.tableau.com/current/pro/desktop/ko-kr/functions_functions_date.htm#datepart-%EA%B0%92>



<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230206_tableau_bootcamp_17_2_6.png){: .align-center}  

</div>
</details>

<br><br>