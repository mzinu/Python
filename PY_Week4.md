# Python 4주차 정규 과제 

📌Python 정규과제는 매주 정해진 분량의 『*파이썬 라이브러리를 활용한 데이터 분석*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **Python_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 참고 자료를 통해 보완하는 것이 좋습니다.

**교재 실습 예제 파일은 07_Python_Template 레포지토리의 notebooks 폴더에 업로드되어 있습니다.**

**👀(수행 인증샷은 필수입니다.)** 

## Python_4th_TIL

### 5장 판다스 시작하기 
#### 1. 판다스 자료구조 소개
#### 2. 핵심 기능
#### 3. 기술 통계 계산과 요약
#### 4. 마치며 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.25~82    | ✅         |
| 2주차 | p.83~129   | ✅         |
| 3주차 | p.131~179  | ✅         |
| 4주차 | p.181~246 | ✅         |
| 5주차 | p.247~309 | 🍽️         |
| 6주차 | p.310~379 | 🍽️         |
| 7주차 | p.381~465 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 판다스 자료구조 소개

### 개념정리

**5.1.1 Series**

- 개념
  - 1차원 배열 형태의 자료구조
  - 값과 함께 색인(index) 을 가진다
  - 넘파이 배열과 비슷하지만, 레이블 기반 접근이 가능하다

- 생성
  - 리스트로 생성 가능
  - index=를 지정해서 원하는 라벨을 붙일 수 있음
  - 딕셔너리로도 생성 가능

- 핵심 특징
  - values 대신 array, index 속성으로 데이터와 색인 확인 가능
  - 정수 인덱스뿐 아니라 문자열 라벨로 선택 가능
  - 조건 필터링, 산술 연산, 넘파이 함수 적용 가능
  - 연산을 해도 색인과 값의 연결이 유지됨

- 딕셔너리와의 관계
  - Series는 정렬된 딕셔너리 비슷하게 이해 가능
  - 딕셔너리 → Series 변환 가능
  - to_dict()로 다시 딕셔너리로 변환 가능

- 누락값(결측치)
  - 존재하지 않는 라벨에 대응하는 값은 NaN
  - isna(), notna()로 결측치 확인 가능

- 자동 정렬
  - Series끼리 연산하면 색인 기준으로 자동 정렬
  - 겹치지 않는 색인은 NaN

- 이름 지정
  - name: Series 자체 이름
  - index.name: 색인 이름

**5.1.2 DataFrame**

- 개념
  - 2차원 표 형태 자료구조
  - 행과 열에 각각 색인이 있음
  - 여러 개의 Series가 모여 있는 구조로 볼 수 있음

- 생성
  - 가장 흔한 방법:
    - 딕셔너리 안에 리스트
    - 넘파이 2차원 배열
    - 중첩 딕셔너리
    - Series의 딕셔너리

- 핵심 특징
  - 열 이름은 딕셔너리 키 기준
  - 행 색인은 자동 생성되거나 직접 지정 가능
  - head(), tail()로 앞/뒤 일부 확인 가능
  - columns=로 열 순서 지정 가능
  - 존재하지 않는 열을 지정하면 NaN으로 채워짐

- 열/행 접근
  - 열:
    - df["col"]
    - df.col (단, 이름이 파이썬 변수 규칙에 맞을 때만)
  - 행:
    - loc[] : 라벨 기반
    - iloc[] : 위치 기반

- 값 대입과 열 추가/삭제
  - 열 전체에 스칼라, 배열, Series 대입 가능
  - 없는 열에 대입하면 새 열 생성
  - del df["col"]로 열 삭제 가능

- 중첩 딕셔너리로 생성
  - 바깥 키 → 열
  - 안쪽 키 → 행 인덱스

- 전치
  - T 사용
  - 행과 열을 뒤집음

- 배열 변환
  - to_numpy()로 넘파이 배열 변환 가능
  - 열 자료형이 다르면 dtype=object가 될 수 있음

**5.1.3 색인 객체(Index)**

- 개념
  - 색인은 단순 번호가 아니라 축 레이블을 저장하는 객체
  - Series와 DataFrame의 행/열 이름을 관리함

- 특징
  - 불변(immutable) 객체
  - 여러 객체가 안전하게 같은 색인을 공유할 수 있음
  - 중복값 허용 가능
  - 집합 연산 비슷한 기능 지원

- 주요 속성/메서드
  - append()
  - difference()
  - intersection()
  - union()
  - isin()
  - delete()
  - drop()
  - insert()
  - is_monotonic
  - is_unique
  - unique()


### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="868" height="400" alt="image" src="https://github.com/user-attachments/assets/fdf44776-2ca5-4d0f-8b96-df2af7696fae" />
<img width="870" height="601" alt="image" src="https://github.com/user-attachments/assets/f37a09e4-b220-4611-a3bc-1530eead34b3" />
<img width="869" height="650" alt="image" src="https://github.com/user-attachments/assets/edac85b2-a8fe-40f4-aa82-7558e1520a2b" />
<img width="865" height="564" alt="image" src="https://github.com/user-attachments/assets/ce2a8790-f7be-4d12-b660-889add46ad1f" />

## 2. 핵심 기능

### 개념정리

**5.2.1 재색인(reindex)**

- 개념
  - 새로운 색인에 맞춰 데이터를 다시 정렬하는 기능
  - 없는 색인은 NaN으로 채움

- 활용
  - Series 재배열
  - DataFrame의 행/열 재배열
  - 빠진 값 채우기 가능

- 주요 옵션
  - index=
  - columns=
  - axis=
  - method="ffill" : 앞의 값으로 채움
  - fill_value= : 비어 있는 곳을 특정 값으로 채움

**5.2.2 하나의 행이나 열 삭제하기**

- 방법
  - drop() 사용

- 예시 개념
  - 행 삭제: drop(index=...)
  - 열 삭제: drop(columns=...)
  - 또는 axis="columns" 사용 가능

- 특징
  - 원본을 직접 바꾸지 않고 삭제된 새 객체 반환
  - (inplace=True를 쓰지 않는 한)

**5.2.3 색인하기, 선택하기, 거르기**

- Series 선택
  - obj["a"] : 라벨
  - obj[1] : 위치 또는 라벨로 해석될 수 있어 주의
  - obj.loc[...] : 라벨 기준
  - obj.iloc[...] : 정수 위치 기준

- DataFrame 선택
  - df["col"] : 열 선택
  - df[["c1", "c2"]] : 여러 열
  - df[:2] : 행 슬라이싱
  - df[df["col"] > x] : 조건 필터링

- loc / iloc
  - loc : 레이블 기반
  - iloc : 정수 위치 기반
  - 예:
    - df.loc["Colorado"]
    - df.iloc[2]
    - df.loc[행, 열]
    - df.iloc[행위치, 열위치]

- 주의점 1: 정수 인덱스 함정
  - 판다스에서 []는 정수에 대해 헷갈릴 수 있음
  - 항상 loc, iloc 사용이 안전

- 주의점 2: 연쇄 색인(chained indexing)
  - 예:
  ```python
  df[df['col'] > 0]['other'] = 1
  ```  
  -> 이런 식은 경고가 뜰 수 있고 원본 반영이 안 될 수 있음
  - 올바른 방법
  ```python
  df.loc[df['col'] > 0, 'other'] = 1
  ```

**5.2.4 산술 연산과 데이터 정렬**

- 특징
  - 판다스는 연산 시 색인 기준 자동 정렬
  - 일치하지 않는 라벨은 NaN

- Series 연산
  - 같은 색인끼리 계산
  - 없는 색인은 결과가 NaN

- DataFrame 연산
  - 행, 열 모두 자동 정렬
  - 공통이 없는 부분은 NaN

- 결측치 채워서 연산
  - add, sub, div, mul 등 사용 가능
  - fill_value=로 누락값 대체 가능
  - 예:
  ```python
  df1.add(df2, fill_value=0)
  ```

- 역연산 메서드
  - radd, rsub, rdiv 등

- DataFrame과 Series 연산
  - 기본적으로 Series의 인덱스를 DataFrame의 열에 맞춤
  - 필요하면 axis="index"로 행 기준 연산 가능

**5.2.5 함수 적용과 매핑**

- 넘파이 함수 적용
  - np.abs(df)처럼 가능

- apply()
  - 행 또는 열 단위로 함수 적용
  - 기본은 열 방향
  - axis="columns"면 행 방향

- 반환값
  - 스칼라 반환 가능
  - Series 반환도 가능

- map() / applymap()
  - Series.map() : Series 각 원소에 함수 적용
  - DataFrame.applymap() : DataFrame의 모든 원소에 함수 적용

**5.2.6 정렬과 순위**

- 정렬
  - sort_index() : 인덱스 기준 정렬
  - sort_values() : 값 기준 정렬

- DataFrame 정렬
  - 하나 또는 여러 열 기준 정렬 가능

- 결측치 정렬
  - 기본적으로 NaN은 뒤로 감
  - na_position="first" 가능

- 순위(rank)
  - 값의 크기 순서대로 순위 부여
  - 같은 값은 기본적으로 평균 순위
  - method="first" : 등장 순서대로
  - ascending=False : 내림차순 순위

**5.2.7 중복 색인**

- 특징
  - 판다스는 중복 색인 허용
  - 하지만 동작이 달라질 수 있음

- 예
  - 유일한 색인 선택 → 스칼라 반환 가능
  - 중복 색인 선택 → 여러 값을 담은 Series/DataFrame 반환

- 확인
  - index.is_unique

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="871" height="551" alt="image" src="https://github.com/user-attachments/assets/4f35505f-d2b6-4734-a118-c396fc1b5eab" />
<img width="859" height="302" alt="image" src="https://github.com/user-attachments/assets/55ef7193-f3de-4422-986b-5e5f2cec6b99" />

## 3. 기술 통계 계산과 요약

### 개념정리

**기본 축소 통계**

- 주요 메서드
  - sum()
  - mean()
  - min()
  - max()
  - count()
  - std()
  - var()
  - median()

- 특징
  - 기본적으로 NaN은 제외하고 계산
  - skipna=False로 제외하지 않도록 설정 가능

- 축 기준
  - 기본은 열 기준
  - axis="columns"면 행 기준

**누산 / 요약 통계**

- 누산 메서드
  - cumsum()
  - cummin()
  - cummax()
  - cumprod()

- 위치 반환
  - idxmax(), idxmin()
  - 최댓값/최솟값의 색인 라벨 반환

- 전체 요약
  - describe()
    - 수치형: 개수, 평균, 표준편차, 최소/최대, 사분위수
    - 비수치형: 개수, 고유값 수, 최빈값, 빈도수

**5.3.1 상관관계와 공분산**

- 메서드
  - corr() : 상관계수
  - cov() : 공분산
  - corrwith() : 다른 Series/DataFrame과의 상관관계

- 특징
  - 정렬된 색인을 기준으로 계산
  - 시계열, 금융 데이터 분석에서 자주 사용

**5.3.2 유일값, 값 세기, 멤버십**

- 고유값
  - unique() : 중복 제거한 값 반환

- 빈도수
  - value_counts() : 각 값의 출현 횟수 계산

- 포함 여부
  - isin() : 특정 값이 포함되는지 불리언으로 반환

- 색인 매칭
  - get_indexer() : 값이 어느 위치에 있는지 정수 인덱스로 반환

- DataFrame 전체 적용
  - apply(pd.value_counts)로 열별 빈도표 생성 가능

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="882" height="629" alt="image" src="https://github.com/user-attachments/assets/3128a21a-cfaa-4f4d-8a03-e41183f3224b" />
<img width="884" height="450" alt="image" src="https://github.com/user-attachments/assets/f87d1168-cd3c-463c-8738-9243b63336a5" />

# 2️⃣ 실습 과제

각 문제에 대한 실행 결과가 확인되도록 코드를 작성하고 실행한 뒤, **모든 문제의 실행 화면을 캡처하여 제출하시기 바랍니다.**

**1. 아래 코드를 실행하여 도서 매출 데이터를 생성합니다.**
```python
import pandas as pd
import numpy as np

# 도서 데이터 생성
data = {
    "book_name": ["Python 기초", "Pandas 실무", "데이터 분석", "머신러닝 입문", "딥러닝 가이드"],
    "price": [25000, 32000, 28000, 45000, 38000],
    "sales_count": [15, 8, 20, 5, 12],
    "stock": [10, 5, 0, 15, 7]
}
df = pd.DataFrame(data)
```

**2. 문제**
```
1. 데이터 확인 및 기초 통계 출력
  - 문제 설명: 요약 정보 확인 
  - describe() 메서드를 사용하여 수치형 데이터(가격, 판매량 등)의 기술 통계 정보를 출력하세요.
  - print()를 이용해 기술 통계 결과를 화면에 출력하세요.

2. 특정 조건의 데이터 필터링 (불리언 색인)
  - 문제 설명: 현재 재고가 하나도 없는(0인) 도서 찾기 
  - stock 열의 값이 0인 행만 추출하여 새로운 변수에 저장하세요.
  - print()를 이용해 재고가 0인 도서의 정보를 출력하세요.

3. 새로운 열 추가 (파생 변수 생성)
  - 문제 설명: 각 도서별 총 매출액(total_revenue) 계산
  - price와 sales_count를 곱하여 total_revenue라는 새로운 열을 추가하세요.
  - print()를 이용해 새로운 열이 추가된 DataFrame의 상단 5행(head)을 출력하세요.
```
**데이터 생성**
> <img width="866" height="291" alt="image" src="https://github.com/user-attachments/assets/d16b9007-6b16-4fe6-afe7-ea59f6449d62" />

**1**
> <img width="602" height="438" alt="image" src="https://github.com/user-attachments/assets/22845e1b-d671-47fa-be5f-5518258ffa02" />

**2**
> <img width="547" height="93" alt="image" src="https://github.com/user-attachments/assets/fb2fdf2b-7618-4390-be1b-391ecedb4e9c" />

**3**
> <img width="803" height="278" alt="image" src="https://github.com/user-attachments/assets/87966d84-5756-4175-b958-079dfb7995b9" />

### 🎉 수고하셨습니다.







