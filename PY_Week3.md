# Python 3주차 정규 과제 

📌Python 정규과제는 매주 정해진 분량의 『*파이썬 라이브러리를 활용한 데이터 분석*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **Python_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 참고 자료를 통해 보완하는 것이 좋습니다.

**교재 실습 예제 파일은 07_Python_Template 레포지토리의 notebooks 폴더에 업로드되어 있습니다.**

**👀(수행 인증샷은 필수입니다.)** 

## Python_3rd_TIL

### 4장 넘파이 기본: 배열과 벡터 연산
#### 1. 다차원 배열 객체 ndarray
#### 2. 난수 생성
#### 3. 유니버설 함수: 배열의 각 원소를 빠르게 처리하는 함수
#### 4. 배열을 이용한 배열 기반 프로그래밍
#### 5. 배열 데이터의 파일 입출력
#### 6. 선형대수
#### 7. 계단 오르내리기 예제
#### 8. 마치며 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.25~82    | ✅         |
| 2주차 | p.83~129   | ✅         |
| 3주차 | p.131~179  | ✅         |
| 4주차 | p.181~246 | 🍽️         |
| 5주차 | p.247~309 | 🍽️         |
| 6주차 | p.310~379 | 🍽️         |
| 7주차 | p.381~465 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 다차원 배열 객체 ndarray

### 개념정리

- 핵심 개념
  - ndarray는 넘파이의 핵심 자료구조로, 같은 자료형의 값을 담는 N차원 배열이다.
  - 배열 전체에 대해 원소 단위 연산을 한 번에 수행할 수 있다.
  - 파이썬 리스트보다 빠르고 메모리 효율적이며, 대규모 수치 데이터를 다루기에 적합하다.

- 주요 속성
  - shape: 배열의 각 차원 크기
  - dtype: 배열 원소의 자료형
  - ndim: 배열의 차원 수

- 배열끼리의 연산은 같은 위치의 원소끼리 수행된다.
- 스칼라와의 연산은 배열 전체 원소에 적용된다.
- 넘파이는 보통 import numpy as np로 불러온다.

4.1.1 ndarray 생성하기

- 생성 방법
  - np.array(...): 리스트, 튜플, 다른 배열 등을 넘파이 배열로 변환
  - 중첩 리스트 → 다차원 배열 생성

- 생성 함수
  - np.array(data): 일반적인 배열 생성
  - np.asarray(data): 이미 ndarray면 복사 없이 변환
  - np.arange(n): range와 비슷하지만 ndarray 반환
  - np.zeros(shape): 0으로 채운 배열
  - np.ones(shape): 1로 채운 배열
  - np.empty(shape): 초기화되지 않은 배열
  - np.full(shape, value): 지정한 값으로 채운 배열
  - np.eye(n), np.identity(n): 단위행렬 생성
  - *_like: 기존 배열과 같은 모양/자료형으로 새 배열 생성 (zeros_like, ones_like, empty_like, full_like)

- np.empty()는 값이 초기화되지 않으므로 쓰레기값이 들어 있을 수 있다.

4.1.2 ndarray의 자료형

- 핵심 개념
  - dtype은 배열 원소가 메모리에 어떻게 저장되고 해석되는지를 나타낸다.
  - 넘파이는 생성 시 자료형을 자동 추론하지만, dtype=으로 직접 지정할 수 있다.

- 자료형
  - 정수형: int8, int16, int32, int64
  - 부호 없는 정수형: uint8, uint16, uint32, uint64
  - 실수형: float16, float32, float64
  - 복소수형: complex64, complex128
  - 불리언형: bool
  - 문자열형: string_, unicode_
  - 객체형: object

- 형 변환
  - astype(...): 배열 자료형을 다른 형으로 변환
  - 정수 → 실수 변환 가능
  - 실수 → 정수 변환 시 소수점 이하는 버려짐
  - 문자열 배열도 숫자 형식이면 숫자로 변환 가능

- astype()는 같은 dtype으로 변환해도 항상 새 배열을 복사해서 생성한다.
- 문자열 dtype은 고정 길이이므로 값이 잘릴 수 있다.

4.1.3 넘파이 배열의 산술 연산

- 핵심 개념
  - 배열은 for문 없이 전체 데이터를 한 번에 처리하는 벡터화(vectorization) 연산이 가능하다.
  - 같은 크기의 배열끼리 연산하면 원소별 연산이 수행된다.

- 가능한 연산
  - 덧셈: arr + arr
  - 뺄셈: arr - arr
  - 곱셈: arr * arr
  - 나눗셈: 1 / arr
  - 거듭제곱: arr ** 2
  - 비교: arr2 > arr → 불리언 배열 반환

- 크기가 다른 배열끼리도 연산할 수 있는데, 이를 브로드캐스팅이라고 한다.

4.1.4 색인과 슬라이싱 기초

- 1차원 배열
  - arr[i]: 특정 위치 원소 선택
  - arr[a:b]: 슬라이싱
  - 슬라이스에 값 대입 가능: arr[5:8] = 12

- 중요한 특징
  - 넘파이 슬라이스는 복사본이 아니라 뷰(view) 이다.
  - 슬라이스를 수정하면 원본 배열도 같이 바뀐다.
  - 복사본이 필요하면 copy()를 사용해야 한다.

- 다차원 배열 색인
  - arr2d[0][2] 또는 arr2d[0, 2]
  - 마지막 색인을 생략하면 한 차원 낮은 배열 반환
  - 예: 3차원 배열 arr3d[0] → 2차원 배열 반환

- 다차원 슬라이싱
  - arr2d[:2]: 앞의 두 행 선택
  - arr2d[:2, 1:]: 앞의 두 행, 두 번째 열 이후 선택
  - 정수 색인 + 슬라이스를 섞으면 차원이 줄어든다.

- 슬라이싱 결과는 대체로 뷰
- 값 대입 시 선택 영역 전체에 적용 가능

4.1.5 불리언 값으로 선택하기

- 핵심 개념
  - 조건식을 배열에 적용하면 같은 길이의 불리언 배열이 만들어진다.
  - 이 불리언 배열을 인덱스로 사용해 조건에 맞는 값만 선택할 수 있다.

- 예시 개념
  - names == "Bob" → 이름이 Bob인 위치만 True
  - data[names == "Bob"] → 해당 행만 선택

- 논리 연산
  - !=: 같지 않음
  - ~: 조건 반전
  - &: AND
  - |: OR

- 파이썬의 and, or는 배열 조건식에 사용하지 않는다. 대신 &, | 사용.
- 불리언 인덱싱 결과는 복사본이다.
- 조건에 맞는 위치에 값 대입도 가능하다.
  - 예: 음수만 0으로 바꾸기

4.1.6 팬시 색인

- 핵심 개념
  - 팬시 색인은 정수 배열이나 리스트를 사용해 원하는 순서대로 원소를 선택

- 예시 개념
  - arr[[4, 3, 0, 6]]: 특정 행을 지정한 순서로 선택
  - 음수 인덱스도 가능

- 다차원 팬시 색인
  - 행/열 인덱스를 동시에 넘기면 각 위치 쌍에 해당하는 원소를 선택한다.
  - 결과는 보통 1차원 배열이 된다.

- 핵심 차이
  - 팬시 색인은 슬라이싱과 달리 항상 복사본을 반환한다.
  - 팬시 색인을 이용한 대입은 원본에 반영된다.

4.1.7 배열 전치와 축 바꾸기

- 전치(transpose)
  - 행과 열을 뒤바꾸는 연산
  - arr.T 또는 arr.transpose() 사용
  - 데이터 복사 없이 뷰를 반환한다.

- 행렬 곱
  - np.dot(arr.T, arr)
  - arr.T @ arr

- 축 바꾸기
  - swapaxes(axis1, axis2)
  - 지정한 두 축을 서로 교환
  - 뷰를 반환.

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="701" height="219" alt="image" src="https://github.com/user-attachments/assets/8304816a-638c-4502-8155-cc19db424e9f" />
<img width="372" height="150" alt="image" src="https://github.com/user-attachments/assets/f3722619-122f-4dd5-902e-f6f385149656" />
<img width="620" height="374" alt="image" src="https://github.com/user-attachments/assets/1fcafc29-1c24-40c4-8026-fb1ed58546c0" />

## 2. 난수 생성

### 개념정리

- 핵심 개념
  - numpy.random은 다양한 확률분포에서 난수를 빠르게 생성한다.
  - 파이썬 내장 random보다 대량 생성에서 훨씬 빠르다.

- 권장 방식
  - np.random.default_rng(seed=12345)로 난수 생성기 객체 생성
  - 생성기 객체(rng)를 통해 난수 생성

- 자주 쓰는 메서드
  - integers(): 정수 난수
  - standard_normal(): 표준정규분포
  - normal(): 일반 정규분포
  - uniform(): 균등분포
  - binomial(), beta(), gamma(), chisquare() 등
  - shuffle(), permutation()

- 난수는 진짜 난수가 아니라 유사난수다.
- seed를 고정하면 같은 결과를 재현할 수 있다.

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="771" height="189" alt="image" src="https://github.com/user-attachments/assets/a4fac308-958b-4eae-9322-7c9599561a71" />
<img width="875" height="162" alt="image" src="https://github.com/user-attachments/assets/574b3a44-92ea-400a-95ec-d3c22b1adfb9" />
<img width="603" height="138" alt="image" src="https://github.com/user-attachments/assets/514a317f-f8f5-44bb-97eb-78e144fae56b" />

## 3. 유니버설 함수: 배열의 각 원소를 빠르게 처리하는 함수

### 개념정리

- 핵심 개념
  - ufunc는 배열의 각 원소에 대해 빠르게 연산하는 벡터화 함수다.

- 단항 ufunc : 하나의 입력 배열을 받는 함수
  - np.sqrt(arr)
  - np.exp(arr)
  - np.abs(arr)
  - np.log(arr)
  - np.sign(arr)
  - np.ceil(arr), np.floor(arr), np.rint(arr)

- 이항 ufunc : 두 배열(또는 배열과 스칼라)을 입력받는 함수
  - np.add(x, y)
  - np.subtract(x, y)
  - np.multiply(x, y)
  - np.divide(x, y)
  - np.maximum(x, y)
  - np.minimum(x, y)

- 여러 결과 반환 : np.modf(arr) → 소수 부분과 정수 부분을 따로 반환

- out 인수
  - 연산 결과를 새 배열 대신 기존 배열에 저장 가능
  - 메모리 사용을 줄일 수 있다.

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->
<img width="871" height="207" alt="image" src="https://github.com/user-attachments/assets/1f25d23f-5dc0-4698-9793-81f45b7be382" />
<img width="894" height="362" alt="image" src="https://github.com/user-attachments/assets/768a5867-9522-4eb2-9926-4aac614ab236" />


## 4. 배열을 이용한 배열 기반 프로그래밍

### 개념정리

- 핵심 개념
  - 넘파이는 반복문 없이 배열 연산만으로 복잡한 계산을 처리한다.
  - 이런 방식을 배열 기반 프로그래밍, 벡터화라고 한다.

- 예시: 격자 좌표 계산
  - np.meshgrid()로 1차원 좌표 배열을 2차원 그리드로 확장
  - z = np.sqrt(xs ** 2 + ys ** 2)처럼 전체 격자에 함수 적용 가능

- 장점
  - 코드가 간결하다.
  - 순수 파이썬 반복문보다 매우 빠르다.

4.4.1 배열 연산으로 조건부 표현하기

- 핵심 개념
  - np.where(condition, x, y)는 조건에 따라 값을 선택하는 벡터화된 삼항 연산이다.

- 역할
  - 조건이 True이면 x
  - False이면 y

- 활용
  - 두 배열 중 조건에 따라 선택
  - 배열과 스칼라를 섞어서도 사용 가능
  - 데이터 분석에서 값 치환에 매우 자주 사용된다.
  - 예 : 양수는 2, 음수는 -2로 바꾸기 / 양수만 2로 바꾸고 음수는 그대로 두기

4.4.2 수학 메서드와 통계 메서드

- 대표 메서드
  - sum(): 합
  - mean(): 평균
  - std(): 표준편차
  - var(): 분산
  - min(), max(): 최솟값, 최댓값
  - argmin(), argmax(): 최솟값/최댓값 위치

- 축(axis) 지정
  - axis=0: 행 방향으로 집계 → 열별 결과
  - axis=1: 열 방향으로 집계 → 행별 결과

- 누적 연산
  - cumsum(): 누적합
  - cumprod(): 누적곱

- 축을 지정하면 차원이 하나 줄어든 결과가 반환된다.

4.4.3 불리언 배열을 위한 메서드

- 핵심 개념
  - 불리언 배열에서 True는 1, False는 0처럼 동작한다.

- 주요 메서드
  - sum() → True 개수 계산
  - any() → 하나라도 True가 있으면 True
  - all() → 모두 True여야 True

- 활용
  - 조건을 만족하는 데이터 개수 세기
  - 특정 조건이 하나라도 존재하는지 확인
  - 모든 값이 조건을 만족하는지 검사

4.4.4 정렬

- 핵심 개념
  - 배열은 sort() 또는 np.sort()로 정렬할 수 있다.

- 차이
  - arr.sort() → 원본 배열 자체를 정렬
  - np.sort(arr) → 정렬된 복사본 반환

- 다차원 정렬
  - axis=0: 각 열 정렬
  - axis=1: 각 행 정렬

4.4.5 집합 관련 함수

- 핵심 개념
  - 넘파이는 1차원 배열용 집합 연산 함수를 제공한다.

- 주요 함수
  - np.unique(x): 중복 제거 + 정렬
  - np.intersect1d(x, y): 교집합
  - np.union1d(x, y): 합집합
  - np.in1d(x, y): 포함 여부를 불리언 배열로 반환
  - np.setdiff1d(x, y): 차집합
  - np.setxor1d(x, y): 대칭차집합

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->
<img width="876" height="301" alt="image" src="https://github.com/user-attachments/assets/a44046ce-929e-42cf-a084-d9781dd34777" />
<img width="909" height="593" alt="image" src="https://github.com/user-attachments/assets/10f9b7ed-a8e4-4ddb-9a05-302a0a956dac" />

## 5. 배열 데이터의 파일 입출력

### 개념정리

- 핵심 개념
  - 넘파이는 배열을 디스크에 효율적으로 저장하고 불러올 수 있다.

- 주요 함수
  - np.save("file.npy", arr): 단일 배열 저장
  - np.load("file.npy"): 배열 불러오기
  - np.savez("file.npz", a=arr1, b=arr2): 여러 배열 저장
  - np.savez_compressed(...): 압축 저장

- 파일 형식
  - .npy: 단일 배열 바이너리 파일
  - .npz: 여러 배열을 담는 압축 아카이브 형식

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="599" height="166" alt="image" src="https://github.com/user-attachments/assets/33088a5b-143d-4b01-ba6d-222ba1da5f36" />
<img width="862" height="481" alt="image" src="https://github.com/user-attachments/assets/fa6b9d75-58c1-47c3-9788-72d642148137" />

## 6. 선형대수

### 개념정리

- 핵심 개념
  - 넘파이는 행렬 연산과 선형대수 기능을 제공한다.
  - *는 원소별 곱이고, 행렬 곱은 dot() 또는 @ 를 사용한다.

- 대표 연산
  - np.dot(x, y) 또는 x @ y: 행렬 곱
  - inv(): 역행렬
  - det(): 행렬식
  - eig(): 고유값/고유벡터
  - qr(): QR 분해
  - svd(): 특잇값 분해
  - solve(A, b): 연립방정식 풀이
  - lstsq(A, b): 최소제곱해
  - diag(), trace(), pinv() 등

- 2차원 배열과 1차원 배열의 행렬 곱 결과는 1차원 배열이 될 수 있다.

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->
<img width="775" height="402" alt="image" src="https://github.com/user-attachments/assets/db2ce470-fe45-457f-adf1-84cbbd6554e4" />
<img width="756" height="393" alt="image" src="https://github.com/user-attachments/assets/8e78e449-094d-4454-b5a3-d11a06b55b25" />

## 7. 계단 오르내리기 예제

### 개념정리

- 핵심 개념
  - 무작위로 +1 또는 -1을 반복해서 더해 가는 과정을 시뮬레이션하는 예제다.
  - 넘파이의 배열 연산과 누적합(cumsum)이 얼마나 강력한지 보여준다.

- 단일 시뮬레이션
  - 난수를 생성해 +1/-1로 변환
  - cumsum()으로 현재 위치 기록
  - min(), max()로 최대 이동 범위 계산
  - 특정 거리 도달 시점은 argmax() 등으로 계산 가능

- 다중 시뮬레이션
  - 2차원 배열을 만들어 한 번에 여러 번 시뮬레이션
  - walks = steps.cumsum(axis=1)
  - 각 시뮬레이션별 통계를 한꺼번에 계산 가능

- 관련 메서드
  - any(axis=1): 각 시뮬레이션이 조건을 만족하는지 검사
  - argmax(axis=1): 조건을 처음 만족한 위치 찾기
  - mean(): 평균 도달 시간 계산

- 벡터화는 매우 빠르지만, 시뮬레이션 수가 많으면 메모리 사용량이 커질 수 있다.

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 2-3장 캡쳐하여 제출해주세요. -->

<img width="921" height="269" alt="image" src="https://github.com/user-attachments/assets/e0ec6435-65d0-4afd-a672-78a92782c166" />
<img width="868" height="529" alt="image" src="https://github.com/user-attachments/assets/f1fdc5af-a21c-4cd1-94c9-d7515923e7a4" />

# 2️⃣ 실습 과제

각 문제에 대한 실행 결과가 확인되도록 코드를 작성하고 실행한 뒤, **모든 문제의 실행 화면을 캡처하여 제출하시기 바랍니다.**

**1. 아래 코드를 실행하여 5일간 3개 품목의 판매량 데이터를 생성합니다.**
```python
import numpy as np

# 5일간 3개 품목의 판매량
# 행: 월, 화, 수, 목, 금 / 열: 사과, 배, 포도
sales = np.array([
    [45, 30, 75],  # 월요일
    [50, 60, 15],  # 화요일
    [85, 20, 40],  # 수요일
    [30, 90, 55],  # 목요일
    [70, 45, 80]   # 금요일
])
```

**2. 문제**
```
1. 품목별 총 판매량 계산 및 출력
  - 문제 설명: 각 품목이 5일 동안 총 몇 개 팔렸는지 계산
  - sum() 메서드의 axis 옵션을 활용하여 품목별 합계를 구하세요.
  - print()를 이용해 품목별 총 판매량 리스트를 출력하세요.

2. 특정 기간 및 품목 추출
  - 문제 설명: 수요일부터 금요일까지(3~5행), 첫 번째와 두 번째 품목(사과, 배)의 판매량만 따로 보기 
  - 배열 슬라이싱을 사용하여 해당 데이터를 추출하세요.
  - print()를 이용해 추출된 3x2 배열을 출력하세요.

3. 목표 미달 판매량 조정
  - 문제 설명: 하루 판매량이 40개 미만인 경우, 값을 0으로 표시하고, 40개 이상인 경우는 기존 값을 유지
  - np.where() 함수를 사용하여 40 미만은 0, 40 이상은 원래 값을 가지는 새로운 배열을 만드세요.
  - print()를 이용해 수정된 배열을 출력하세요.
```
**정답**
<img width="710" height="626" alt="image" src="https://github.com/user-attachments/assets/ba106eb7-8214-439e-96cf-3dada50cf09e" />





### 🎉 수고하셨습니다.







