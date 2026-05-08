# Python 6주차 정규 과제 

📌Python 정규과제는 매주 정해진 분량의 『*파이썬 라이브러리를 활용한 데이터 분석*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **Python_6th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 참고 자료를 통해 보완하는 것이 좋습니다.

**교재 실습 예제 파일은 07_Python_Template 레포지토리의 notebooks 폴더에 업로드되어 있습니다.**

**👀(수행 인증샷은 필수입니다.)** 

## Python_6th_TIL

### 7장 데이터 정제 및 준비 
#### 3. 확장 데이터 유형
#### 4. 문자열 다루기 
#### 5. 범주형 데이터
#### 6. 마치며
### 8장 데이터 준비하기: 조인, 병합, 변형
#### 1. 계층적 색인
#### 2. 데이터 합치기 
#### 3. 재구성과 피벗
#### 4. 마치며 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.25~82    | ✅         |
| 2주차 | p.83~129   | ✅         |
| 3주차 | p.131~179  | ✅         |
| 4주차 | p.181~246 | ✅         |
| 5주차 | p.247~309 | ✅         |
| 6주차 | p.310~379 | ✅         |
| 7주차 | p.381~465 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 확장 데이터 유형

### 개념정리

- 넘파이 한계
  - 정수/불리언 + 결측치 → 자동으로 float64 변환됨
  - 문자열 처리 비효율 (메모리/속도)
  - 일부 타입은 파이썬 객체 사용 → 느림
- 해결: 판다스 확장 dtype
  - 결측치(NA) 지원
  - 원래 타입 유지 가능
- 핵심 타입
  - <Int64> → 결측 가능한 정수
  - <boolean> → 결측 가능한 bool
  - <string> → 문자열 전용 타입
  - <Float64> → 결측 가능한 float
  - <category> → 범주형
- 특징
  - 결측값은 np.nan이 아니라 pd.NA
  - dtype 명시 안 하면 기존 방식 유지됨
- 사용
  ```python
  df["A"].astype("Int64")
  df["B"].astype("string")
  ```

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<!-- 이 부분을 지우고 실행 화면을 제출해주세요. -->


## 2. 문자열 다루기 

### 개념정리

#### 7.4.1 파이썬 문자열 메서드

- 기본 처리
  - <split()> → 나누기
  - <strip()> → 공백 제거
  - <join()> → 합치기
  - <replace()> → 치환
- 검색
  - <"a"in text> → 포함 여부
  - <find()> → 위치 (없으면 -1)
  - <index()> → 위치 (없으면 에러)
- 기타
  - <count()> → 개수
  - <lower()/upper()> → 대소문자 변환

#### 7.4.2 정규 표현식(regex)

- re 모듈 사용
- 주요 기능
  - split() → 패턴 기준 분리
  - findall() → 전부 찾기
  - search() → 첫 번째 찾기
  - match() → 시작부터 검사
  - sub() → 치환
- 패턴 예시
  - \s+ → 공백
  - 이메일 패턴 → 구조 파싱 가능
- 그룹화
  ```python
  (user)@(domain).(suffix)
  ```  
  -> <group()>로 분리

#### 7.4.3 판다스 문자열 함수

- <Series.str> 사용
- 장점
  - 결측치 자동 처리 (에러 안 남)
  - 벡터화 → 빠름
- 주요 메서드
  - <str.contains()> → 포함 여부
  - <str.findall()> → 패턴 찾기
  - <str.extract()> → 그룹 추출 (DataFrame)
  - <str.replace()> → 치환
  - <str.slice()> → 자르기
- 예
  ```python
  data.str.contains("gmail")
  ```  

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<!-- 이 부분을 지우고 실행 화면을 제출해주세요. -->


## 3. 범주형 데이터

### 개념정리

#### 7.5.1 개념

- 반복되는 값 많을 때 사용
- 문자열 대신 정수 코드로 저장
- 구조
  - categories → 실제 값
  - codes → 정수 인덱스

#### 7.5.2 Categorical 타입

- 생성
  ```python
  df["col"].astype("category")
  ```
- 내부 구조
  - .cat.categories
  - .cat.codes
- 특징
  - 메모리 절약
  - 연산 빠름

#### 7.5.3 연산
- <groupby>, <value_counts> 빠름
- <qcut()> → 구간 나누기 → 범주형 반환
- 예
  ```python
  df["col"].astype("category")
  ```

#### 7.5.4 메서드
- <set_categories()> → 범주 변경
- <rename_categories()> → 이름 변경
- <remove_unused_categories()> → 안 쓰는 값 제거
- <as_ordered()> → 순서 부여

#### 성능 핵심
- 문자열 → category 변환 시
  - 메모리 ↓ 속도 ↑

#### 더미 변수
- 머신러닝용 변환
  ```python
  pd.get_dummies(data)
  ```

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<!-- 이 부분을 지우고 실행 화면을 제출해주세요. -->


## 4. 계층적 색인 

### 개념정리

- 개념
  - 하나의 축에 여러 단계 index
  - 고차원 데이터를 2차원으로 표현
- 기본 사용
  - 부분 선택 가능
    ```python
    data["b"]
    data.loc[:, 2]
    ```  
- 구조 변환
  - <unstack()> → 행 → 열
  - <stack()> → 열 → 행
- 정렬 & 재배치
  - <swaplevel()> → 순서 바꾸기
  - <sort_index(level=...)> → 특정 레벨 정렬
- 색인 다루기
  - <set_index()> → 열 → index
  - <reset_index()> → index → 열

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<!-- 이 부분을 지우고 실행 화면을 제출해주세요. -->


## 5. 데이터 합치기 

### 개념정리

#### 8.2.1 merge

- SQL Join 느낌
- 기본
  ```python
  pd.merge(df1, df2, on="key")
  ```
- 옵션
  - <inner> → 교집합
  - <left> → 왼쪽 기준
  - <right> → 오른쪽 기준
  - <outer> → 합집합
- 특징
  - 다대다 → 곱집합 발생

#### 8.2.2 색인 기반 병합
- 옵션
  ```python
  left_index=True
  right_index=True
  ```

#### 8.2.3 join

- 색인 기준 병합 (간단버전 merge)
  ```python
  df1.join(df2)
  ```
- 기본: left join

#### 8.2.4 concat

- 단순 이어붙이기
- 방향
  - <axis=0> → 아래
  - <axis=1> → 옆
- 옵션
  - <keys> → 계층 index 생성
  - <ignore_index=True>

#### 8.2.5 combine_first
- 결측치
  ```python
  a.combine_first(b)
  ```
- “a가 비면 b로 채움”

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<!-- 이 부분을 지우고 실행 화면을 제출해주세요. -->


## 6. 재구성과 피벗 

### 개념정리

#### 8.3.1 stack / unstack

- <stack()> → wide → long
- <unstack()> → long → wide

#### 8.3.2 pivot

- 긴 데이터 → 넓게 
```python
df.pivot(index, columns, values)
```

#### 8.3.3 melt
- 넓은 데이터 → 길게
```python
pd.melt(df)
```
- 결과 컬럼
  - <variable>
  - <value>

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<!-- 이 부분을 지우고 실행 화면을 제출해주세요. -->



# 2️⃣ 실습 과제

각 문제에 대한 실행 결과가 확인되도록 코드를 작성하고 실행한 뒤, **모든 문제의 실행 화면을 캡처하여 제출하시기 바랍니다.**

**1. 아래 코드를 실행하여 분석에 필요한 기초 데이터를 생성합니다.**
```python
import pandas as pd
import numpy as np

# 1. 고객 기본 정보
customers = pd.DataFrame({
    "customer_id": [101, 102, 103, 101, 104, 105],
    "name": ["Kim", "Lee", "Park", "Kim", "Choi", "Jung"],
    "age": [23, 35, 45, 23, 18, 55],
    "email": ["kim@gmail.com", "lee@naver.com", "park@gmail.com", "kim@gmail.com", "choi@naver.com", "jung@gmail.com"]
})

# 2. 구매 이력 정보
purchases = pd.DataFrame({
    "customer_id": [101, 102, 103, 106],
    "product": ["iPhone", "iPad", "MacBook", "Watch"],
    "amount": [1500, 800, 2500, 500]
})
```

**2. 문제**
```
1. 중복 고객 제거 및 연령대 그룹화
  - 문제 설명: 고객의 연령대 나누기 
  - drop_duplicates()를 사용하여 customer_id 기준 중복을 제거하세요.
  - pd.cut()을 사용하여 나이(age)를 10대(10-19), 20대(20-29), 30대 이상(30-100)으로 나누고 age_group 열을 만드세요.
  - print()를 이용해 정제된 고객 데이터프레임을 출력하세요.

2. 이메일 도메인 추출
  - 문제 설명: 고객들의 이메일 도메인(gmail, naver 등) 정보만 추출 
  - str.split()과 str.get()을 사용하여 이메일 주소에서 @ 뒷부분의 도메인만 추출하여 domain 열을 만드세요.
  - print()를 이용해 도메인이 추가된 결과를 출력하세요.

3. 고객 정보와 구매 이력 병합
  - 문제 설명: 고객 정보와 구매 이력을 하나로 합치기 
  - pd.merge()를 사용하여 customers와 purchases를 customer_id 기준으로 합치세요.
  - 이때 구매 이력이 없는 고객 정보도 모두 유지되도록 외부 조인(Outer Join) 방식을 사용하세요.
  - print()를 이용해 병합된 최종 데이터프레임을 출력하세요.
```

<!-- 이 부분을 지우고 인증 사진을 제출해주세요.-->



### 🎉 수고하셨습니다.







