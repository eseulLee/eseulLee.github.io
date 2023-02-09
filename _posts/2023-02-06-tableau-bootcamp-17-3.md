---
title: "[Tableau] 신병훈련소 17기 3일차"
excerpt: "#Tableau #신병훈련소 #데이터_시각화 #매개변수 #대시보드 #데이터_설명"

categories:
  - tableau
tags:
  - [tableau, data_visualization]

permalink: /tableau/bootcamp-17-3/

toc: true
toc_sticky: true

date: 2023-02-07
last_modified_at: 2023-02-07
---

##  ✏️ 3일차

> 📖 3일차 학습 안내  
> - **매개 변수 활용** : 내가 원하는 기준으로 측정값을 변경하며 커피 선택
> - **계산식 작성**과 **대시보드 상호 작용**
> - **데이터 설명(Explain data)** : 클릭 한 번으로 비즈니스 패턴 파악하기


### 💡 매개 변수

- **계산, 필터 및 참조선에서 상수 값을 동적으로 바꿀 수 있는 변수**
- 고급 분석에서 상호 작용까지 다양하게 사용
  - Top N 필터
  - 구간 차원 변경
  - What-If 분석
  - 참조선 값
  - 매개 변수를 이용한 집합 만들기
  - 이동 평균선
  - KPI 조정하기
  - 차트에서 필드 변경하기
  - 대시보드에서 차트 변경하기

<br>

#### 👀 매개 변수 활용 순서

``` 
 매개 변수 생성 👉 계산식 생성 👉 분석에 활용 
```

<br>

#### 1️⃣ 매개 변수 생성

- 매개 변수의 유형(실수, 정수, 문자열, 날짜 등)과 허용 가능한 값 설정 방법(전체, 목록, 범위) 선택
- 좌측 하단에 매개 변수 생성된 후 마우스 오른쪽 클릭하여 `매개 변수 표시` 선택
  - 우측 필터 표시 탭에 매개 변수 표시

![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_1.png){: .align-center}

<br>

#### 2️⃣ 매개 변수 활용

1. **KPI 조정** : 계산된 필드에서 **수치 입력 부분**을 [매개 변수명]으로 변경
    👉 매개 변수로 설정되는 '목표 매출 금액'에 따라 계산이 다르게 적용
2. **Top N** : 필터 > 상위 탭에서 **상위 '몇 개' 기준**을 선택하는 드롭다운에서 **매개 변수명** 선택    
    👉 매개 변수로 설정되는 'Top N'에 따라 상위 몇 개까지 그래프로 표시할지 결정
3. **측정값 변경** : 계산된 필드에서 CASE WHEN 구문을 활용하여 매개 변수명에 따라 불러올 측정값 설정  
    👉 <span style="color:orange">주의)</span> 측정값 별 집계 수준이 다른 경우   
   
   > **집계 수준이 모두 동일한 경우**에는 구분없이 행 수준에서 측정값을 계산 필드에 입력해도 괜찮지만,
   > **집계 수준이 서로 다른 경우**에는 계산 필드 내에서 측정값 별 집계 함수를 다르게 적용  
   > 👉 아래의 그림처럼 '집계'로 명시되어 따로 추가적인 집계없이 적용
          
![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_2.png){: .align-center}
 
<br>


### 💡 대시보드 동작

대시보드 > 동작 클릭시 아래와 같은 창이 뜨고, 필터, 하이라이트 등의 동작을 추가할 수 있음

![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_3.png){: .align-center}

대시보드에서 단일 뷰 선택시 옵션 중 하나인 '필터로 사용'이 해당 기능을 적용한 경우에 해당  
- 해당 옵션 적용 시 대시보드 > 동작 에 '필터' 동작이 생성
- 동작 편집(또는 추가)시 원본 시트, 동작 실행 조건, 대상 시트, 필터 등을 적용하여 동작 편집/생성

![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_4.png){: .align-center}

👉 2주차 때 좀 더 자세히 다룰 예정!


<br>

##  ✏️ 3일차 과제


### 1️⃣ 매개 변수를 사용하여 측정값 변경하기1 & 마크 색상 표현하기

```
- 하나의 시각화에서 여러 개의 측정값을 변경
- 선택한 카페인 함유량에 따라 카테고리 색상 표시
```

<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_7.png){: .align-center}  

</div>
</details>

<br>

1. "**측정값 선택**" 매개 변수 생성
      - 이름 : 측정값 선택
      - 데이터 유형 : 문자열
      - 허용 가능한 값 : 목록     
      - 값 목록 : 칼로리, 카페인, 당류 
2. "**선택한 측정값**" 계산된 필드 생성

   ![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_5.png){: .align-center}

3. "**카페인 함유량 선택**" 매개 변수 생성
      - 이름 : 카페인 함유량 선택
      - 데이터 유형 : 정수
      - 허용 가능한 값 : 범위
      - 값 범위 : 최소값 0, 최대값 200, 단계 크기 20

4. "**선택한 카페인**" 계산된 필드 생성  

   ![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_6.png){: .align-center}

5. **카테고리** - 열 선반, **선택한 측정값** - 행 선반 추가
   - **선택한 측정값**의 집계 형태 **평균**으로 변경
6. **선택한 카페인**을 마크 선반의 색상에 Drag & Drop
   - 카페인이 매개 변수보다 많이 들은 경우 노란색, 아닌 경우 회색으로 색상 편집
7. **측정값 선택**에 따라 제목이 변경되도록 **시트 제목에 파라미터를 삽입**
    - 제목 더블 클릭 후 원하는 위치에서 `삽입 > 매개 변수.측정값 선택`

<br>

### 2️⃣ 매개 변수를 사용하여 측정값 변경하기2

```
선택한 측정값에 따라서 두 측정값의 상관 관계를 살펴보는 동적 시각화 만들기
```

<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_10.png){: .align-center}  

</div>
</details>

<br>

1. X축 선택, Y축 선택 매개 변수 생성

   ![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_8.png){: .align-center}

2. 1의 각각의 매개 변수를 사용할 계산된 필드 X축, Y축 생성

   ![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_9.png){: .align-center}

3. 워크시트 작성
   - X축, Y축을 각각 열 선반, 행 선반에 추가 (둘 다 집계 형태 **평균**으로 변경)
   - 카테고리 > 메뉴명 수준까지 적용되도록 마크 선반의 **세부정보**에 **카테고리, 메뉴명** Drag & Drop
   - 분석 탭에서 평균 라인 > 테이블 추가
   - 메뉴 별 카페인 확인을 위해 마크 선반 **색상, 크기**에 **카페인** Drag & Drop


<br>

### 3️⃣ 대시보드 동작 적용하기

```
1번, 2번 과제를 이용해 아래와 같이 대시보드 만들고, 대시보드 동작을 이용해 해당 카테고리 별 제품 하이라이트
```

<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_12.png){: .align-center}  

</div>
</details>

<br>

1. 앞서 만든 워크시트 이용해 대시보드 생성
2. 대시보드 > 동작 > 동작 추가 > 하이라이트 선택
   - 원본 시트와 대상 시트 선택
   - 동작 실행 조건은 "**마우스 오버**"
   - 대상 하이라이트는 선택한 필드에서 "**카테고리**"만 선택
     - 2번 과제에서 '카테고리'를 시트에 추가한 이유!

![image](/assets/images/posts_img/tableau_bootcamp/day3/20230207_tableau_bootcamp_17_3_11.png){: .align-center}



<br><br>