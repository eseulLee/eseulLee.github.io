---
title: "[Tableau] 신병훈련소 17기 1일차"
excerpt: "#Tableau #신병훈련소 #데이터_시각화 #막대차트 #트리맵"

categories:
  - tableau
tags:
  - [tableau, data_visualization]

permalink: /tableau/bootcamp-17-1/

toc: true
toc_sticky: true

date: 2023-02-03
last_modified_at: 2023-02-03
---

##  ✏️ 1일차

> 📖 1일차 학습 안내  
> 태블로 제품 개요, 데이터 연결하기, 대시보드 만들기


### 💡 차원? 측정값?

태블로의 필드는 정성적인 값과 정량적인 값에 따라 **차원**과 **측정값**으로 구분  

- **차원**: 정성적 데이터(제품명, 날짜, 지리명 등), 분석 기준이 되는 값, 불연속형 데이터로 측정값을 쪼개어 보는 하나의 관점
- **측정값**: 정량적 수치, 연속형 데이터로 <u>집계</u>가 되는 데이터. 차원을 기준으로 집계되어 표현
  - 집계: 합계, 평균, 중앙값, 카운트, 카운트 (고유), 최소값, 최대값, 백분위수, 표준편차, 분산 등 을 의미

<br>

### 💡 막대 차트(Bar Chart)

- 수치 데이터 값들 간의 작은 양적 차이를 비교하는 데 유용
- 특정 참조선(ex. 평균값, 중간값) 등을 표현해 해당 막대가 그 참조선 값에 도달했는지 도달하지 못했는지 비교 가능
- 바인바(Bar in Bar) 차트 등을 통해 목표값에 도달했는지 아닌지 등도 살펴볼 수 있음
- <span style="color:orange">주의)</span> 막대 차트를 사용할 때는 **비슷한 값들의 비교를 명확하게 하기 위해서 데이터를 정렬하는 것을 권장**

<br>

### 💡 트리맵(Tree Map)

- 계층 구조의 데이터를 표시하는데 적합한 시각화
- 전체 대비 부분의 비율이 얼마나 되는지 비교하는데 많이 사용
- 사각형의 크기와 색상에 따라 데이터의 패턴을 확인할 수 있을 뿐만 아니라 많은 데이터를 한 번에 볼 수 있음

<br>

### 💡 산점도(Scatter Plot)

- 2개의 연속형 데이터에 대한 상관관계를 분석하는 데 가장 많이 사용되는 시각화
- 두 개의 축으로 데이터가 얼마나 퍼져 있는지 분포 확인
- 상수 라인/ 평균 라인/ 사분위수 및 중앙값/ 추세선 등과 같은 참조 라인을 추가하여 값의 분포 비교

<br>

## ✏️ 1일차 과제

"스타벅스 메뉴 데이터"와 "매장 정보 데이터"를 이용해 시각적 분석을 하고 대시보드를 만들기  
> 👀 다이어트 중에 스타벅스 메뉴 선택을 하려면? 아메리카노가 최선일까?

### 1️⃣ 카테고리 별 평균 칼로리 & 평균 카페인

1. 왜 집계를 평균으로 해야할까?
   - 데이터 구성을 보았을 때, 하나의 카테고리 안에 여러 개의 메뉴가 있음
   - 카테고리를 기준으로 합계로 집계해주면 카테고리 내의 메뉴들의 칼로리와 카페인 값이 모두 더해져 카테고리 별 메뉴들의 총 합계 칼로리, 총 합계 카페인 값이 보여지게 됨

2. 명확한 비교를 위해 **평균 칼로리 기준**으로 정렬

3. 칼로리가 낮으면서 카페인이 적은 카테고리는 무엇일까?  
   - 브루드 커피의 경우, 가장 평균 칼로리가 낮지만 평균 카페인이 가장 높은 것으로 확인
   - 스타벅스피지오, 스타벅스주스(병음료), 티바나가 상대적으로 칼로리가 낮으면서 카페인이 적은 카테고리로 보여짐 

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_1.png){: .align-center}  

</div>
</details>

<br>

### 2️⃣ 메뉴명 별 칼로리 & 카페인

🧐 왜 집계를 평균이 아닌 합계를 사용했을까?  

- 데이터의 가장 낮은 행 수준이 '메뉴명'으로 유일하게 구분되고 중복되지 않는 값
- 즉, 하나의 메뉴명에는 하나의 칼로리, 하나의 카페인 값이 있기 때문에 합계/평균 상관없이 결과 동일

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_2.png){: .align-center}  

</div>
</details>

<br>

### 3️⃣ 카테고리와 메뉴명을 한 번에 살펴보기

카테고리에 마우스 오버시 해당 카테고리에 해당되는 메뉴 트리맵 도구설명으로 띄우기

- 도구 설명 편집 창 내에 다른 시트 추가 가능
  - 도구 설명 편집 > 삽입 클릭 > 시트 > 시트 선택
  - 너비(maxwidth)와 높이(height) 조정 가능

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_3.png){: .align-center}  

</div>
</details>

<br>

### 4️⃣ 당분 함유량과 칼로리 상관관계

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_4.jpg){: .align-center}

1. 메뉴명 수준으로 당류와 칼로리 살펴보기 위해 메뉴명을 마크 선반의 **세부 정보**에 가져다 놓기
   - **시각화의 집계 기준이 전체에서 메뉴명 수준으로 변경**
2. 마크의 형태를 "**원**"으로 변경
3. **카페인**으로 마크의 색상, 크기 표현
   - 겹쳐지는 제품들을 볼 수 있도록 색상의 불투명도 조정 및 테두리 추가
4. 추세 확인을 위해 추세선(선형) 추가

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_5.png){: .align-center}  

- 당류(g)가 높을수록 칼로리(Kcal)가 높음
- 비슷한 당류가 들어가도 칼로리가 메뉴에 따라 달라짐

</div>
</details>

<br>

### 5️⃣ 시군구 별 매장 분포 현황

어느 시군구에 스타벅스 매장이 가장 많은지 확인

- 시도, 시군구 필드로 매장 존재하는 시군구 지도로 표현
- 마크의 크기와 색상을 스타벅스 매장 수로 나타내기
  - 스타벅스 매장 수는 **매장코드**를 **카운트**해서 크기와 색상에 표현

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_6.png){: .align-center}  


</div>
</details>

<br>

### 6️⃣ 대시보드 만들기

1~3번 과제에서 만든 ‘카테고리 별 평균 칼로리와 평균 카페인’, ‘당분 함유량과 칼로리 상관관계’ 시트를 이용해 대시보드 만들기

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_7.png){: .align-center}  

</div>
</details>

<br>

### 🔥 추가 도전 과제

**경도/위도 데이터를 이용**해서 서울시의 실제 매장 위치 표현해보기

<details>
<summary>최종결과</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/20230203_tableau_bootcamp_17_1_8.png){: .align-center}  

</div>
</details>

<br><br>