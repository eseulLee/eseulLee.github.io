---
title: "[Tableau] 태블로 신병훈련소 17기 8일차"
excerpt: "#Tableau #신병훈련소 #데이터_시각화 #집합분석"

categories:
  - tableau
tags:
  - [tableau, data_visualization]

permalink: /tableau/bootcamp-17-8/

toc: true
toc_sticky: true

date: 2023-02-15
last_modified_at: 2023-02-15
---

##  ✏️ 8일차

> 📖 8일차 학습 안내
> - 집합의 개념을 알아보고, 분석에 적용해보기
> - **집합/매개변수  값 변경**, **Viz in tooltip** 등의 상호작용을 활용하여 보다 인터랙티브한 대시보드 만들기



### 💡 태블로의 집합(Set)

- 일부 조건을 기반으로 데이터의 하위 집합을 정의하는 **사용자 지정 필드**
  - **사용자 지정 필드**이기 때문에 간단하게 필터에만 쓸 수 있는게 아니라 행/열 선반, 마크 카드에 올리면서 다양한 시각적 결과를 만들어내는 데에 활용 가능
  - 조건을 기반으로 하나의 영역을 **IN/OUT** 으로 분리
  - **필터**는 **IN에 속하는 멤버만 유지**하는 경우이기 때문에 **집합의 하위 개념**으로 볼 수 있음

<br>

#### 👀 집합 생성 방법 

1. 동적 집합: 조건이나 상황에 따라 바뀔 수 있는 형태
  1. 필드 기준: 필드 자체를 조건으로 사용

       ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_4.png){: .align-center}

  2. 조건 > `수식 기준` 일 때: 수식에는 집합 생성 대상 차원을 포함하거나 집계 형태여야 하며, 결과는 참/거짓(BOOLEAN) 형태여야 함(IN/OUT)
  
       ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_1.png){: .align-center}

  3. 집합 간 연산
     - 2015년도, 2016년도 구매고객을 각각의 집합으로 만든 후 두 집합을 하나로 합친 "**2015&2016 구매고객**' 집합 생성
     
       ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_2.png){: .align-center}
     
     - 위에서 만든 **2015&2016 구매고객** 집합으로 하나의 IN/OUT 필터를 만들 수 있음
     
       ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_3.png){: .align-center}
       - 2015, 2016년도 모두 구매를 한 고객은 다른 연도에 구매했을 확률이 더 높기 때문에 전체 매출 트렌드가 상대적으로 높은 것으로 확인
     
2. 정적 집합: 데이터 직접 선택

<br>

#### 👀 집합 활용

- **계산식에 집합 사용**
  - 집합은 참/거짓의 BOOLEAN 이므로 집합을 **행 수준**에서 사용하게 되면 `[집합 이름] = TRUE` 라고 쓰지 않아도 이름 자체에 내재되어 있음
  - 아래의 두 계산식은 동일한 결과

    ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_5.png){: .align-center}

<br>

#### 👀 [집합 활용 예시] 비대칭 드릴다운 I

- 선택적으로 제품 대분류, 제품 중분류 드릴다운
  - 제품 대분류, 중분류 각각 드릴다운을 원하는 카테고리를 선택한 집합 생성
  - 각각 계산된 필드를 만들어 생성된 집합에 해당되는 경우에만 표현되도록 생성
    
    ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_6.png){: .align-center}
  
- 한계점: 비대칭적으로 드릴다운이 되지만, **다른 카테고리를 보고 싶을 때** 동적으로 변환이 되지 않고 **일일이 집합을 편집**해줘야 하는 문제 발생
  - 이를 해결할 기능이 <u>**집합 작업**</u>

<br>

### 💡 집합 작업(Set Actions)

- 작동 원리
  - 2018.3 버전에 추가된 기능
  - 선택된 마크를 기반으로 집합의 멤버 조정 가능
  - 기존의 Action은 하나의 작업으로만 연동 가능하나, 집합 작업은 구성 내용에 따라 **제한 없이** 결과 도출 가능
- 집합 작업은 집합에 영향을 주게 되는데, 그 Scope은 워크시트 수준과 대시보드 수준
  - Scope의 선택 기준은 작동이 일어날 위치가 어디인지에 따라 결정  

#### 👀 예시 1

  - 시트의 항목 중 일부 선택 후 집합 만들기("**집합 작업 연습")
  - 워크시트 > `동작` 선택 후 **동작 실행 조건, 대상 집합, 동작 실행 결과 및 선택 해제 시 결과 등** 설정
  
    ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_7.png){: .align-center}
  
    - 집합 선택 해제 후에도 색상이 유지되게 하고 싶기 때문에 해제 시 결과를 '**집합 값 유지**'로 선택함 
  - 워크시트에서 다른 항목들을 선택 후 앞서 만든 '집합 작업 연습' 집합의 멤버를 확인해보면 새로 선택된 항목들로 구성되어 있음 확인    
  - 최종 결과
  
    ![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_8.gif){: .align-center}

<br>

#### 👀 [예시 2] 부분 VS 전체

> 지역 선택에 따른 전체 대비 매출 비율 동적 확인

1. 대시보드의 '지역별 판매현황'시트의 지역 중 하나 선택 > `집합 만들기`
   - 국가는 모두 **대한민국으로 동일**하므로 삭제 후 **시도**만 멤버로 선택된 상태인 집합 '**시도 (집합)**' 생성
2. '전체 대비 매출 비율' > `시트로 이동`
   - 1에서 만든 '시도 (집합)'을 마크 선반의 **색상**에 Drag & Drop
   - IN/OUT에 따라 전체 대비 매출 비율을 확인할 수 있음
3. 지역별로 동적으로 변환되게 하기 위해 **집합 작업** 진행
   - 보고 있는 뷰의 수준이 '대시보드'이기 때문에 집합 작업을 **대시보드에서 진행**
   - 동작 추가 > 집합 값 변경
     - 원본 시트: 지역별 판매 현황
     - 동작 실행 조건: 선택
     - 대상 집합: 해당 대시보드 > 시도 (집합)
     - 선택 해제시 결과: 집합에서 모든 값 제거
4. 최종 결과

![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_9.gif){: .align-center}

<br>

#### 👀 [예시 3] 선택 VS 기타

> 선택된 항목은 개별 그래프, 나머지 항목들은 묶어서 하나의 그래프로 표현

1. 선택된 항목들의 집합("제품 중분류(집합)"), 해당 집합 사용한 계산된 필드("선택VS기타") 생성
    ```
    IF [제품 중분류(집합)]
    THEN [제품 중분류] ELSE '기타'
    END
    ```
2. 1에서 만든 **선택VS기타** 필드를 마크 선반의 **색상**에 Drag & Drop
3. 원 대시보드에서 항목 선택에 따라 그래프가 바뀌도록 **대시보드 수준**에서 집합 작업 설정 
4. 최종 결과

![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_10.gif){: .align-center}

<br>

#### 👀 장바구니 분석

> 선택된 제품을 구매한 고객 이력과 고객별 선택 제품 이력 확인

1. 선택 제품 집합("제품 중분류(집합)_장바구니"),  선택 고객 집합("고객명(집합)_장바구니") 각각 생성
2. [장바구니] 시트 작업
   1. 고객 중에서 선택한 제품 중분류를 구매한 고객을 집합으로 생성
   2. 조건 > `수식 기준` 에 아래 수식 입력
      ```
      MAX([제품 중분류(집합)_장바구니])
      ```
      - 집계를 무조건 해줘야 하기 때문에 MAX() 함수 사용
      - 해당 고객이 제품 중분류에 해당하는 제품 중 하나라도 구입하면 무조건 TRUE
   3. 마크 선반의 색상에 위에서 만든 집합을 끌어오게 되면 선택된 제품 중분류를 선택한 고객이 다른 제품 중분류를 산 비중을 색상으로 구분할 수 있음    

3. [아이템 구매 고객] 시트 작업
    - 선택된 제품 중분류를 구매한 고객만 조회가 되도록 필터링
4. [선택 구매 고객 이력] 시트 작업
   - 선택된 고객이 **한번이라도** 등장한 제품 중분류 조회
   - 제품 중분류 > 집합 만들기 > `조건` > `수식 기준`
     ```
     MAX([고객명(집합)_장바구니])
     ```
     - 해당 고객이 한번이라도 등장한 경우(한번이라도 구매한 제품 중분류가 IN으로 필터링) TRUE
5. 동적으로 연결되게 하기 위해 집합 작업 설정
   - 대시보드 > `동작` > 동작 추가
     1. **장바구니** 시트에서 선택 시 **제품 중분류(집합)**을 대상 집합으로 설정
     2. **아이템 구매 고객**시트에서 선택 시 **고객명(집합)**을 대상 집합으로 설정
6. 최종 결과

![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_11.gif){: .align-center}

<br>

#### 👀 비대칭 드릴다운 II

> 위에서 했던 예시(비대칭 드릴다운 I)의 한계점 극복
 
- 기존에 만들었던 '제품 대분류(집합)', '제품 중분류(집합)' 에 대해 집합 동작(Set Action) 생성
  - 워크시트 > 동작 > 동작 추가 > `집합 값 변경` 
  - 해당 집합을 각각 **대상 집합**으로 설정
  - 동작 실행 조건: 선택
  - 선택 해제 시 결과: 집합에서 모든 값 제거
- 최종 결과

![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_12.gif){: .align-center}


<br>

### 💡 집합 작업(Set Actions) 참고 사이트

<https://www.artofthevizable.com/>


<br>

##  ✏️ 8일차 과제

### 1️⃣ 집합 동작

```
선택한 지역의 전체 대비 매출 현황과 제품 중분류별 매출을 동적으로 확인하는 대시보드 만들기  
- 사용 Data: 주문+반품 추출
```


<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_과제_1.png){: .align-center}  


</div>
</details>

<br>

1. 값을 선택할 필드의 집합 생성
   1. '시도' 필드 > **마우스 우클릭 > 만들기 > 집합** ("시도 선택 집합")
   2. [전체 대비 매출 현황], [제품 중분류 별 매출] 시트 작업
      - 마크의 '색상'에 1에서 만든 **시도 선택 집합** 추가
2. 선택에 따라 집합 값이 변하도록 집합 동작 생성
   - 대시보드에서 진행
   1. 대시보드 > 동작 > 동작 추가 > 집합 값 변경
   2. 추가 동작 설정
      1. 원본 시트 : “지역별 매출 현황”
      2. 작업(동작) 실행 조건 : “선택” 
          - 선택 → 마우스 클릭했을 때
          - 마우스 오버 → 마우스를 차트에 올렸을 때, 
          - 메뉴 → 마우스로 클릭한 후 도구설명에서 메뉴 버튼을 클릭했을 때
      3. 대상 집합 : 데이터 소스 - “주문+반품 추출” / Set(집합) - “시도 선택 집합”
      4. 선택 내용을 지울 경우의 결과 : “집합 값 제거”
         - 집합 값 유지 → 지도에서 서울을 선택했다가, 선택된 값을 취소했을 때 여전히 서울 값 유지
         - 집합에 모든 값 추가 →  서울을 선택했다가, 선택된 값을 취소했을 때 시도 모든 값을 집합에 추가
         - 집합에 모든 값 제거 → 서울을 선택했다가, 선택된 값을 취소했을 때 시도 모든 값을 집합에서 제거
3. "제품 중분류 별 매출" 막대그래프 모양 바꾸기(파란색을 시작점으로)
   - 색상 마크에 추가된 '시도 선택 집합'을 **마우스 우클릭 > 정렬**
   - 정렬 기준을 **수동**으로 변경 후, OUT을 위로 올리기

<br>

### 2️⃣ 매개변수 변경을 이용한 드릴 다운 


```
특정 대분류 막대 선택 시 해당 대분류의 중분류 수준으로 매출과 매출 구성 비율 확인하기
- 사용 Data: 주문+반품 추출
```

<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day8/20230215_tableau_bootcamp_17_8_13.gif){: .align-center}  

</div>
</details>

<br>

1. 제품 대분류를 행 선반에, 매출을 열 선반에 추가
2. 매개변수 생성 ("제품 대분류 매개 변수")
   1. 제품 대분류 > 마우스 우클릭 > **매개변수**
   2. 값 목록에 자동 추가된 제품 대분류 값에 "**전체**" 값 추가
   3. 2에서 추가한 전체 값을 맨 위로 드래그하여 순서 변경 
3. 매개변수 적용할 계산식 생성 ("제품대분류_드릴다운")
   - 제품 대분류와 제품 대분류 매개 변수 값이 같으면, 제품 중분류를 가져오고 아닐 때는 제품 대분류를 가져오도록 
4. 3에서 만든 "제품중분류_드릴다운" 필드를 마크 선반의 색상에 추가

   > 🤔 매개변수 값을 변경할 때마다 제품 대분류의 색상이 자꾸 바뀐다면?
   
    👉 “대분류 매개 변수”에서 “전체”를 선택하고, 마크 “색상”에서 각각 제품 대분류 별 색상 지정
5. 레이블에 정보 추가
    1. **"제품 중분류_드릴다운", "매출"** 필드를 **레이블**에 Drag & Drop
    2. "**제품 중분류 레이블**" 생성
   
       ```
       IF [제품 대분류] = [제품대분류 매개변수]
       THEN [매출]
       END
       ```
       
    3. 생성된 "제품 중분류 레이블"을 **레이블**에 추가 후, **퀵 테이블 계산**을 이용해 **구성 비율** 나타내기
       - 범위: 테이블(옆으로)
6. 시각화를 눌렀을 때도 매개변수 값이 변경되도록 설정
   - 워크시트 > 동작 > 동작 추가 > `매개 변수 변경`
     - 동작 실행 조건: **마우스 오버**
     - 대상 매개 변수: **제품 대분류 매개 변수**
     - 값 필드에서 매개 변수에 적용할 필드 선택: **제품 대분류**
       - 시각화에 있는 제품 대분류 값을 선택할 때마다 매개변수 값 변동


<br><br>