# Python 7주차 정규 과제 

📌Python 정규과제는 매주 정해진 분량의 『*파이썬 라이브러리를 활용한 데이터 분석*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **Python_7th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 참고 자료를 통해 보완하는 것이 좋습니다.

**교재 실습 예제 파일은 07_Python_Template 레포지토리의 notebooks 폴더에 업로드되어 있습니다.**

**👀(수행 인증샷은 필수입니다.)** 

## Python_7th_TIL

### 9장 그래프와 시각화 
#### 1. 맷플롯립 API 간략하게 살펴보기
#### 2. 판다스에서 시본으로 그래프 그리기 
#### 3. 다른 파이썬 시각화 도구
#### 4. 마치며
### 10장 데이터 집계와 그룹 연산
#### 1. 그룹 연산에 대한 고찰
#### 2. 데이터 집계
#### 3. apply 메서드: 일반적인 분리-적용-병합
#### 4. 그룹 변환과 래핑되지 않은 groupby
#### 5. 피벗 테이블과 교차표
#### 6. 마치며 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.25~82    | ✅         |
| 2주차 | p.83~129   | ✅         |
| 3주차 | p.131~179  | ✅         |
| 4주차 | p.181~246 | ✅         |
| 5주차 | p.247~309 | ✅         |
| 6주차 | p.310~379 | ✅         |
| 7주차 | p.381~465 | ✅         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 맷플롯립 API 간략하게 살펴보기

### 개념정리

- matplotlib은 파이썬 기본 시각화 라이브러리
- `matplotlib.pyplot as plt` 형태로 import
- 가장 기본은 `plt.plot()`
- 그래프는:
    - Figure(전체 캔버스)
    - Axes/Subplot(실제 그래프 영역)로 구성됨
- matplotlib은 저수준 라이브러리라 세부 설정 자유도가 높음

#### 9.1.1 피겨와 서브플롯
- `figure()` : 빈 캔버스 생성
- `add_subplot()` : 그래프 영역 추가
- `subplots()` : 여러 subplot 한 번에 생성
- 여러 그래프를 동시에 비교할 때 사용
- `sharex`, `sharey`
    - 여러 그래프 축 공유
    - 비교 분석할 때 중요
- `subplots_adjust()`: subplot 사이 간격 조절
- subplot이 많아지면 레이블 겹칠 수 있음 → 직접 조절 필요

### 9.1.2 색, 마커, 선 스타일
- 그래프 가독성 향상 목적
- 주요 옵션:
    - `color`
    - `linestyle`
    - `marker`
- 선 스타일:
    - 실선
    - 점선
    - dotted
- marker: 데이터 위치 강조
- `drawstyle`: 계단형 그래프 가능
- `label + legend()`: 범례 생성 핵심

#### 9.1.3 눈금, 레이블, 범례
- 그래프를 “읽을 수 있게” 만드는 파트
- `set_title()`: 제목
- `set_xlabel()`, `set_ylabel()`: 축 이름
- `set_xticks()`: 눈금 위치 지정
- `set_xticklabels()`: 눈금 이름 지정
- `rotation`: 글자 회전
- 범례:
    - `label`
    - `legend()`
- matplotlib은 자동으로 안 예쁘게 해줌 → 직접 조절 필요

#### 9.1.4 주석과 그림 추가하기
- 그래프에 설명 추가
- `text()`: 단순 텍스트
- `annotate()`: 화살표 + 설명
- 특정 이벤트 강조 가능
    - 금융위기
    - 급등락 시점 등
- patch 객체:
    - Rectangle
    - Circle
    - Polygon
- 그래프 위에 도형 추가 가능

#### 9.1.5 그래프를 파일로 저장하기
- `savefig()`: 그래프 파일 저장
- 지원 포맷:
    - png
    - pdf
    - svg 등
- `dpi`: 해상도 설정
- 출판/보고서용 그래프 제작 시 중요

#### 9.1.6 맷플롯립 설정
- `plt.rc()`: 전역 스타일 설정
- 설정 가능:
    - figure 크기
    - 글꼴
    - 색상
    - grid 스타일
- `rcParams`: 현재 설정 저장된 딕셔너리
- 전체 프로젝트 스타일 통일 가능

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="905" height="630" alt="image" src="https://github.com/user-attachments/assets/5867ece5-75b4-47cc-8316-8fd5e5224500" />
<img width="937" height="686" alt="image" src="https://github.com/user-attachments/assets/7842c9c5-2f93-46fb-b2cd-3c84fbf82a6e" />
<img width="888" height="737" alt="image" src="https://github.com/user-attachments/assets/3a7be4e3-fb10-40d9-81e8-319fe5c7fd8b" />

## 2. 판다스에서 시본으로 그래프 그리기 

### 개념정리

- pandas와 seaborn은 matplotlib 기반
- pandas: 빠르고 간단한 시각화
- seaborn:
    - 통계 시각화 강화
    - prettier 기본 스타일 제공

#### 9.2.1 선 그래프
- `Series.plot()`
- `DataFrame.plot()`
- 기본 그래프는 line plot
- pandas index가 자동 x축 사용
- 여러 열이면 자동 범례 생성
- 시계열 데이터 표현에 자주 사용

#### 9.2.2 막대그래프
- `plot.bar()`: 세로 막대
- `plot.barh()`: 가로 막대
- 범주별 비교에 사용
- `stacked=True`: 누적 막대그래프
- `value_counts().plot.bar()`: 빈도 시각화 자주 사용
- seaborn `barplot()`: 평균 + 신뢰구간 자동 계산

#### 9.2.3 히스토그램과 밀도 그래프
- 데이터 분포 확인 목적
- `hist()`: 구간별 빈도
- `density()`: 부드러운 확률분포 곡선
- KDE(kernel density estimate): 밀도 추정
- seaborn `histplot()`: 히스토그램 + KDE 쉽게 생성

#### 9.2.4 산포도
- 두 변수 관계 확인
- `regplot()`: 산포도 + 회귀선
- 상관관계 파악 가능
- `pairplot()`: 변수들 전체 관계 시각화
- EDA(탐색적 데이터 분석)에서 핵심 도구

#### 9.2.5 패싯 그리드와 범주형 데이터
- 여러 조건별 그래프 비교
- `catplot()`: 범주형 시각화 통합 함수
- `hue`: 색으로 그룹 구분
- `row`, `col`: subplot 분리
- boxplot:
    - 중앙값
    - 사분위수
    - 이상치 확인
- 다차원 범주 비교에 매우 유용

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="895" height="697" alt="image" src="https://github.com/user-attachments/assets/aa26f957-0133-46dd-833e-74fe4b6bad3a" />
<img width="902" height="583" alt="image" src="https://github.com/user-attachments/assets/475d9d54-2f4d-4c6e-8da5-138df45363f1" />

## 3. 다른 파이썬 시각화 도구

### 개념정리

- matplotlib 외 도구 소개
    - `Altair`
    - `Bokeh`
    - `Plotly`
- 웹 기반 interactive visualization 가능
- 하지만 pandas와 호환성 때문에 matplotlib 여전히 중요

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="886" height="495" alt="image" src="https://github.com/user-attachments/assets/04c1da52-f1e6-4837-a944-cb835d65d83d" />
<img width="887" height="763" alt="image" src="https://github.com/user-attachments/assets/5f454696-e7b3-4001-84c8-5362e1d7feed" />

## 4. 그룹 연산에 대한 고찰

### 개념정리

- split-apply-combine 개념 소개
- groupby 기본 구조:
    ```python
    df.groupby("key")
    ```
- 그룹 기준:
    - 열 이름
    - 배열
    - 함수
    - 딕셔너리 가능
- 결과는 GroupBy 객체

#### 10.1.1 그룹 간 순회하기
- 그룹별 데이터 직접 접근
    ```python
    for name, group in grouped:
    ```
- 각 그룹 이름과 데이터 반환
- 디버깅/확인할 때 유용

#### 10.1.2 열이나 열의 일부만 선택하기
- 특정 열만 집계 가능
- 메모리 절약
- 성능 향상:
    ```python
    grouped["data"]
    ```

#### 10.1.3 딕셔너리와 Series에서 그룹화하기
- mapping 기반 그룹화
- 열들을 그룹으로 묶기 가능
- axis="columns" 사용 가능

#### 10.1.4 함수로 그룹화하기
- 함수 반환값 기준 그룹화
- 예:
    - 문자열 길이별 그룹화
    ```python
    groupby(len)
    ```

#### 10.1.5 색인 단계로 그룹화하기
- MultiIndex 대상
- 특정 level 기준 그룹화
    ```python
    groupby(level=...)
    ```

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="755" height="567" alt="image" src="https://github.com/user-attachments/assets/67c32fa9-b42e-4c25-878b-11fc8c54332d" />
<img width="807" height="442" alt="image" src="https://github.com/user-attachments/assets/8318ca3a-073b-4957-9e1a-bddc93762644" />

## 5. 데이터 집계

### 개념정리

- 그룹별 통계 계산
- 주요 함수:
    - mean
    - sum
    - std
    - var
    - min/max
    - median
    - count
    - size

#### 10.2.1 열에 여러 가지 함수 적용하기
- `agg()` 핵심
- 여러 함수 동시 적용 가능
    ```python
    agg(["mean", "std"])
    ```
- 열마다 다른 함수 적용 가능
- 사용자 정의 함수 가능

#### 10.2.2 색인되지 않은 형태로 집계된 데이터 반환하기
```python
as_index=False
```
- SQL 결과 형태처럼 반환
- reset_index() 대체 가능

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<!-- 이 부분을 지우고 실행 화면을 제출해주세요. -->
<img width="796" height="317" alt="image" src="https://github.com/user-attachments/assets/eb17333b-be90-4cb9-9aac-c497c85918e9" />
<img width="811" height="237" alt="image" src="https://github.com/user-attachments/assets/46cb611c-4c14-4cbf-8958-b37dc97959ec" />

## 6. apply 메서드: 일반적인 분리-적용-병합 

### 개념정리

- 가장 자유로운 groupby 함수
- 그룹별 custom 로직 적용
    ```python
    groupby().apply()
    ```
- 반환:
    - DataFrame
    - Series
    - scalar

#### 10.3.1 그룹 키 생략하기
```python
group_keys=False
```
- 계층 색인 제거

#### 10.3.2 사분위수 분석과 버킷 분석
- `cut()`: 구간 분할
- `qcut()`: 동일 개수 분위수 분할
- 그룹 기반 통계 분석 가능

#### 10.3.3 그룹별 값으로 결측치 채우기
- 그룹 평균 기반 fillna
- 그룹별 다른 값 사용 가능
- 데이터 정제에서 중요

#### 10.3.4 랜덤 표본과 순열
- `sample()`
- 그룹별 랜덤 샘플링
- 몬테카를로/실험 데이터에 활용

#### 10.3.5 그룹 가중평균과 상관관계
- weighted average 계산
    ```python
    np.average(weights=...)
    ```
- corr/corrwith 사용
- 금융 데이터 분석 예시 등장

#### 10.3.6 그룹별 선형 회귀
- statsmodels 활용
- 그룹별 회귀모델 가능
- OLS 회귀 수행

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->
<img width="835" height="522" alt="image" src="https://github.com/user-attachments/assets/d719464c-9754-47f5-8f0a-8d264845b050" />
<img width="777" height="352" alt="image" src="https://github.com/user-attachments/assets/6bc72d69-6fad-4160-9e13-49d092cde0b3" />

## 7. 그룹 변환과 래핑되지 않은 groupby

### 개념정리

- transform: 원본과 같은 크기 유지
- 그룹 평균/표준화 등에 사용
    ```python
    transform("mean")
    ```
- normalize
- rank 계산 가능

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="571" height="697" alt="image" src="https://github.com/user-attachments/assets/7004f61c-b780-4068-94e7-c04ce457a9b2" />
<img width="922" height="461" alt="image" src="https://github.com/user-attachments/assets/9d534faf-1e1b-4c7a-a943-a03a9c62c203" />

## 8. 피벗 테이블과 교차표 

### 개념정리

- pivot_table
- 엑셀 피벗테이블 느낌
    ```python
    pivot_table()
    ```
- 행/열 기준 그룹화
- 집계 함수 적용
- margins=True: 총합/부분합

#### 10.5.1 교차표
```python
pd.crosstab()
```
- 범주 빈도 계산
- 설문조사 데이터 분석 자주 사용

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="806" height="497" alt="image" src="https://github.com/user-attachments/assets/25bd97ee-7ed2-4afc-83dc-f03f463e9239" />
<img width="862" height="448" alt="image" src="https://github.com/user-attachments/assets/6a7d4217-d12a-4631-b5dc-159f0eab03dc" />

---

이번 주차는 마지막 주차로, 별도의 실습 과제가 없습니다.

부족한 커리큘럼이었음에도 불구하고 한 학기 동안 과제를 성실하게 수행해주셔서 감사합니다.

파이썬 과제 제작을 마무리하는 시점에 이 글을 작성하고 있는데, 저 또한 파이썬에 능통하거나 익숙하지 않았지만, 과제를 제작하기 위해 책을 찾아보고, 템플릿을 제작하고 검수하면서 많은 배움이 있었던 것 같습니다. 

여러분들께서도 모든 과제를 마친 지금 시점에 파이썬이 아직 낯설게 느껴질 수도 있을 것 같습니다.

하지만 자주 접하고, 직접 코드를 작성해보고, 데이터를 어떻게 다루면 좋을지 고민해보는 시간을 가지다 보면 점점 익숙해질 것이라 생각합니다.

정말 고생 많으셨고, 여러분들께서 앞으로 파이썬을 활용하는 데에 있어 이 과제가 한 줌이라도 보탬이 된다면 정말 감사하겠습니다.

여러분의 앞날을 응원합니다!! 😄



### 🎉 수고하셨습니다.







