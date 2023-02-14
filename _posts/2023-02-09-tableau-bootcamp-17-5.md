---
title: "[Tableau] 태블로 신병훈련소 17기 5일차"
excerpt: "#Tableau #신병훈련소 #데이터_시각화 #배경이미지_맵 #플로우맵 #버퍼함수"

categories:
  - tableau
tags:
  - [tableau, data_visualization]

permalink: /tableau/bootcamp-17-5/

toc: true
toc_sticky: true

date: 2023-02-09
last_modified_at: 2023-02-09
---

##  ✏️ 5일차

> 📖 5일차 학습 안내  
> - **배경 이미지**를 이용한 **Custom Map** 사용
> - **플로우 맵(흐름)**
> - **버퍼(Buffer) 함수**를 이용한 맵 활용


### 💡 매핑하기(Mapping)

- 태블로에는 국가, 지역, 시도, 시군구의 명칭에 따른 위·경도값을 가지고 있음 👉 위도(생성됨), 경도(생성됨) 필드 
    - 해당 위·경도 필드를 이용해서 맵을 표현
- 맵에 위치가 표현되는 원리? 
  - **약속된 좌표 체계**를 따르기 떄문
  - 위·경도 값을 약속된 값으로 보고, 실제 그 값을 표현하기 위해 맵이라는 하나의 **이미지**가 있는 것과 같음
- 꼭 지도가 아니어도 배경 이미지에서의 좌표에 따른 위치 표시 가능
  - 치아 위치 별 충치 스케일 맵  
  ![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_2.png){: .align-center}

<br>

#### 1️⃣ 기호 맵

- 기본 마크는 원형으로 되어있지만, 다른 모양의 마크 사용 가능
- 마크 선반에서 **모양**으로 변경 후, 원하는 모양으로 설정
- 마크 선반의 **색상**에 필드 추가하여 지역별 색상 차이 확인 가능

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_3.png){: .align-center}


<br>

#### 2️⃣ 채워진 맵

- 마크 선반의 **색상**에 측정값 필드 Drag & Drop
- 합계 수량에 따른 지역별 차이를 맵에 채워진 색으로 확인 가능
- 크기 등 변경 불가

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_4.png){: .align-center}

<br>

#### 3️⃣ 히트 맵(밀도 맵)

- 마크 선반의 **밀도**에 측정값 필드 Drag & Drop
- 시각적 군집에 대한 추세를 표시하려는 경우 사용
- 데이터 요소 수가 많거나 적은 위치 쉽게 식별 가능
- 맵의 마크 간에 겹치는 부분이 많은 다수의 데이터 요소가 포함된 데이터 집합 작업 시 가장 효과적
> 예) 택시 승차가 가장 많은 맨해튼 지역 찾기

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_5.png){: .align-center}

<br>

#### 4️⃣ 흐름 맵(경로 맵)

- 경로를 연결하고 시간별 추이 확인
- 태풍의 경로와 같이 특정 기간 동안의 변화 양상을 보여 주려는 경우 가장 적합
- [태블로 참고 문서: Tableau에서 특정 기간 동안의 경로를 보여 주는 맵 만들기](https://help.tableau.com/current/pro/desktop/ko-kr/maps_howto_flow.htm)

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_6.png){: .align-center}

<br>

#### 5️⃣ 스파이더 맵(원점-목적지 맵)

- 원점 위치와 하나 이상의 목적지 위치가 상호 작용하는 방식 표시
- 사용 예시: 지하철역 사이의 경로를 연결하여 매핑, 원점에서 하나 이상의 목적지까지 이동하는 공유 자전거 대여 상황 추적
- [태블로 참고 문서: Tableau에서 기점과 종점 간의 경로를 표시하는 맵 만들기](https://help.tableau.com/current/pro/desktop/ko-kr/maps_howto_flow.htm)

> <span style="color:orange">예제)</span> 프랑스 파리의 지하철역 통행량

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_7.png){: .align-center}

<br>


### 💡 공간 함수(공간 계산식)

#### 1️⃣ BUFFER, MAKEPOINT 함수

> 카페 별로 영업권이 얼마나 겹치는지 표현해보기

- `맵 > 배경 맵` 으로 배경 맵 이미지 변경 가능 (해당 예시에서는 **거리** 사용) 
- **공간 계산식** 생성 (계산된 필드 만들기/ field name: Buffer)

    ```
  BUFFER( MAKEPOINT( [Latitude], [Longitude] ), 100, 'm')
  ```
  - **BUFFER 함수**: 점을 중심으로 지정된 거리의 버퍼 반환
      - 형식: BUFFER(기하 도형(MAKEPOINT(latitude, longitude)), 숫자(거리), 단위('m', 'km', etc.))
  - **MAKEPOINT 함수**: 위도 및 경도 열의 데이터를 공간 개체로 변환
- 마크 형태 **맵**으로 설정 후 공간 계산식을 통해 생성한 필드를 세부 정보에 Drag & Drop
  - 각 카페 별로 100m (필드 생성시 설정한 거리값) 이내 거리 만큼의 영역 확인
  - 영역의 겹침 정도를 통해 영업권이 얼마나 겹쳐 있는지 확인 가능

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_1.png){: .align-center}
    
<br>

#### 2️⃣ MAKELINE 함수

> Finished Flight Path(비행 경로)

- 기점 도시와 종점 도시의 위·경도 좌표를 이용해 이동경로(라인) 확인하는 필드 생성
    ```
  MAKELINE(MAKEPOINT([Lat],[Lng]),MAKEPOINT([Dest Lat],[Dest Lng]))
  ```
    - **MAKELINE 함수**: 두 점 사이에 선 표시 생성, 기점-종점 맵 만드는 데 유용
      - 형식: MAKELINE(OriginPoint, DestinationPoint)
      - 'Spatial Point'의 경우, MAKEPOINT 함수를 이용해 지리적 좌표 데이터를 공간 개체로 변환

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_8.png){: .align-center}


##  ✏️ 5일차 과제

### 1️⃣ 배경 이미지를 이용한 Custom Map 사용하기

```
수도권 지하철 노선도 위에 일 별 평균 승/하차 승객수 표현
```

<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_9.png){: .align-center}  


</div>
</details>

<br>

1. 배경 이미지로 사용할 지하철 노선도 load
   1. 맵 > 배경 이미지 > 해당 데이터 원본 선택 > `이미지 추가`
   2. 이미지 Load
   3. X필드, Y필드 값 선택(각각 데이터의 X, Y좌표 값에 해당)
      - 이미지 사이즈에 맞춰 수치 기입
      - 이미지 크기가 2040*1654 라면? 
        - 가로(x) 오른쪽: 2040, 세로(y) 위쪽: 1654
   4. 필요에 따라 투명도 설정

2. 파라미터 변경에 따라 승/하차 승객수를 나눠 조회할 수 있도록 매개변수 생성
   - 데이터 유형: 문자열
   - 허용 가능한 값: 목록
     - 평균 승차승객수
     - 평균 하차승객수

3. 2에서 생성된 매개변수를 활용하기 위한 **계산된 필드(승하차승객수)** 생성

   ```
    CASE [승/하차]
    WHEN '평균 승차승객수' THEN [승차총승객수]
    WHEN '평균 하차승객수' THEN [하차총승객수]
    END
   ```
   
4. 열 선반에 X, 행 선반에 Y 추가
   - 추가시 집계 형태가 **합계**로 되어있는데, 각각의 필드는 **이미지 상의 역의 좌표**를 나타내는 값
   - X, Y값은 날짜에 따라 중복되어 나타나고 있기 떄문에 합계로 집계를 하게되면 고유값이 나올 수 없음
   - 따라서, 집계 형태를 **평균**으로 변경해야 해당 역의 원래 X, Y값을 가져올 수 있음
   
5. '역명' 필드를 마크 선반의 **세부정보**에 Drag & Drop 👉 역마다 마크가 퍼짐
6. 3에서 만든 '**승하차승객수**' 필드를 마크 선반의 **색상, 크기**에 각각 Drag & Drop
   - 마크 **원**으로 변경
   - 색상, 크기 각각 편집
   - 집계 형태를 **평균**으로 세팅

<br>

### 2️⃣ 공간 테이블 계산을 이용한 맵 활용

> - 시애틀 사람들은 주로 어느 나라로 여행을 많이 갈까요?
> - 비행기를 타면 모니터에서 나오는 근사한 이동경로는 어떻게 시각화 할 수 있을까요?  

```
시애틀에서 출발한 항공편의 취항지별 승객수 표현
```

<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_12.png){: .align-center}  

</div>
</details>

<br>

1. 계산된 필드 **Arrival, Departure** 생성
   - **MAKEPOINT 함수** 이용하여 위·경도 좌표로 출발지(Departure), 도착지(Arrival) 위치 점으로 나타내기

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_10.png){: .align-center}

2. **MAKELINE 함수**로 1에서 만든 'Arrival', 'Departure'를 경로로 잇는 필드 '**Flight Path**' 생성

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_11.png){: .align-center}

3. 2에서 만든 'Flight Path' 필드를 더블 클릭하여 시트에 표현(시트 중앙으로 Drag & Drop 해도 됨)
4. 각 Flight Path별 평균 Passenger 수를 색상으로 표현
   - 'Passenger' 필드를 마크 선반의 **색상**에 Drag & Drop
   
   > - 태블로가 Passenger 수를 전체 평균으로 집계하고 있음!
   > - 취항지별로 나눠야 하기 때문에 **세부정보**로 'Arriving Airport'를 끌어와야 집계 기준이 전체가 아닌 취항지(도착지)별로 바뀌게 됨 
5. 'Arriving Country'를 필터로 추가

<br>

### 3️⃣ Buffer 함수를 이용한 맵 활용

> - 새로운 매장을 내려면 어느 곳을 공략해야 할까요? 
> - 내가 선택한 반경 안에 동종 업계가 얼마나 포진해 있는지 볼 수 있을까요?

```
주유소 위치와 각 위치 별로 선택한 반경 Buffer 함수 이용하여 나타내기
```

<details>
<summary>최종결과 🌈</summary>
<div markdown="1">       

![image](/assets/images/posts_img/tableau_bootcamp/day5/20230209_tableau_bootcamp_17_5_13.png){: .align-center}  

</div>
</details>

<br>

1. 행 선반에 'Latitude', 열 선반에 'Longtitude' 추가
   - Latitude와 Longitude는 주유소 별 위/경도 값
2. **세부 정보**에 “**고유id**"를 추가한 후, “**모든 멤버 추가**" 선택
   - 고유 id: 각 주유소 별 Unique ID
3. “**시도**"에서 마우스 오른쪽 버튼을 클릭하여 "**필터 표시**" 선택 후, “시도" 필터 옵션에서 "**단일 값(드롭다운)**" 선택 
4. “**시군구**"에서 마우스 오른쪽 버튼을 클릭하여 "**필터 표시**" 선택 후, “시군구"필터 옵션에서 "**단일 값(목록)**" 선택 
    - 시군구 필터에 해당 시도 내에 있는 시군구만 나타내기 위해 '**관련된 값만**' 선택 
5. 거리 선택을 위한 매개 변수 및 계산식 만들기
    1) **매개 변수**
        - 이름 : 거리 선택
        - 데이터 유형 : 정수
        - 현재 값 : 150 
        - 허용 가능한 값 : 범위
        - 최소값 : 50 , 최대값 : 500 , 단계 크기 : 50
 
    2) 매개 변수를 이용한 계산식
        - 이름 : 반경 계산
       ```
        BUFFER(MAKEPOINT([Latitude], [Longitude]), [거리 선택], 'm')
       ```

6. "거리 선택" 매개 변수 표시
7. 마크 유형을 "**맵**"으로 변경 후 "**반경 계산**" 필드를 마크 선반의 **세부 정보**에 Drag & Drop
8. "**상표**" 필드 마크 선반의 **색상**에 Drag & Drop (상표별 색상 차이)
9. 거리 뷰를 보기 위한 맵 옵션 변경
      1) 맵 > 배경 맵 > `거리` 선택
      2) 맵 > `백 그라운드 레이어` 선택 > 투명도 30%로 조정

<br>

### 🔥 추가 자료

아래 웹사이트를 통해 이미지에 대한 X, Y좌표나 경로, 영역에 대한 데이터를 만드실 수 있습니다.   
<http://drawingtool.powertoolsfortableau.com/>

<br><br>