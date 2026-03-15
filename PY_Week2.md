# Python 2주차 정규 과제 

📌Python 정규과제는 매주 정해진 분량의 『*파이썬 라이브러리를 활용한 데이터 분석*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **Python_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 참고 자료를 통해 보완하는 것이 좋습니다.

**교재 실습 예제 파일은 07_Python_Template 레포지토리의 notebooks 폴더에 업로드되어 있습니다.**

**👀(수행 인증샷은 필수입니다.)** 

## Python_2nd_TIL

### 3장 내장 자료구조, 함수, 파일
#### 1. 자료구조와 순차 자료형
#### 2. 함수
#### 3. 파일과 운영체제
#### 4. 마치며


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.25~82    | ✅         |
| 2주차 | p.83~129   | ✅         |
| 3주차 | p.131~179  | 🍽️         |
| 4주차 | p.181~246 | 🍽️         |
| 5주차 | p.247~309 | 🍽️         |
| 6주차 | p.310~379 | 🍽️         |
| 7주차 | p.381~465 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 자료구조와 순차 자료형

### 개념정리

3.1 자료구조와 순차 자료형
- 파이썬의 내장 자료구조(특히 순차 자료형)를 잘 다루면 코드가 짧아짐, 읽기 쉬어짐, 실수 줄어듦

3.1.1 튜플 (tuple)

- 핵심 성질
  - 한 번 만들면 길이/원소(슬롯) 변경 불가(불변, immutable)인 순차 자료형.
  - 값들을 쉼표로 나열하면 되고, 괄호는 보통 쓰지만 생략 가능.

- 생성/변환
  - `(4, 5, 6)` 또는 `4, 5, 6`
  - `tuple([4, 0, 2])`, `tuple("string")` 처럼 이터러블을 튜플로 변환가능.

- 접근/중첩
  - 인덱싱은 `0`부터 시작: `tup[0]`
  - 중첩 튜플: `nested = (4,5,6), (7,8)` → `nested[0]`, `nested[1]`

- 불변인데 안에 리스트 바뀜
  - 튜플은 슬롯 자체를 바꾸는 건 불가능하지만,
  - 슬롯 안에 있는 객체가 가변 객체(list 등)면 그 객체의 내용은 바뀔 수 있음.
    - 예: `tup = ('foo', [1,2], True)`에서 `tup[1].append(3)` 가능

- 연산
  - 이어붙이기: `+`
  - 반복: `*`
  - 단, 반복/이어붙이기에서 객체가 복사되는 게 아니라 참조가 복제될 수 있음(가변 객체일 때 특히 주의).

- 튜플 언패킹(값 분리)
  - `a, b, c = (4, 5, 6)`
  - 중첩도 가능: `a, b, (c, d) = (4, 5, (6, 7))`
  - 변수 swap: `a, b = b, a`
  - 나머지 받기: `a, b, *rest = values`
  - 필요 없는 값 무시 관습: `a, b, *_ = values`

- 주요 메서드
  - `count(x)`: 튜플(리스트도 가능)에서 `x`의 개수

3.1.2 리스트

- 핵심 성질
  - 크기/내용 변경 가능(가변, mutable)한 순차 자료형.
  - 생성: `[]` 또는 `list(iterable)`

- 원소 추가/삭제
  - 끝에 추가: `append(x)`
  - 특정 위치 삽입: `insert(i, x)`  
    - 단, 뒤 원소들을 밀어야 해서 비용이 큼 (append보다 무거움)
  - 꺼내며 삭제: `pop(i)` → 값 반환 + 삭제
  - 값으로 삭제: `remove(x)` → 처음 만나는 x 하나만 삭제

- 포함 검사
  - `"x" in a_list`, `"x" not in a_list`
  - 리스트의 포함 검사는 내부적으로 순회하므로 딕셔너리/집합보다 느림(해시 기반 아님).

- 리스트 이어붙이기
  - `+`는 새 리스트 생성 + 복사 비용 발생
  - `extend(iterable)`는 기존 리스트에 붙여서 보통 더 효율적

-  정렬
  - `sort()`는 제자리 정렬(in-place)
  - `sort(key=함수)`로 정렬 기준 지정 가능 (예: `key=len`)

- 슬라이싱
  - `seq[start:stop]`에서 start 포함, stop 미포함
  - 생략 가능: `seq[:5]`, `seq[3:]`
  - 음수 인덱스: 뒤에서부터 `seq[-4:]`
  - step: `seq[::2]`
  - 역순: `seq[::-1]`
  - 슬라이스 대입 가능: `seq[3:5] = [6, 3]`

3.1.3 딕셔너리 (dict)

- 핵심 성질
  - 키-값(key-value) 저장 구조(해시 맵).
  - 생성: `{}` 또는 `{"a": 1, "b": 2}`

- 기본 사용
  - 값 넣기/수정: `d[key] = value`
  - 값 읽기: `d[key]`
  - 키 존재 확인: `key in d`

-  삭제
  - `del d[key]`
  - `d.pop(key)`는 값 반환 + 삭제

- 조회/반복
  - `keys()`, `values()`, `items()`  
    - `items()`는 `(key, value)` 튜플들의 이터러블
  - 파이썬(현대 버전)에서는 삽입 순서가 유지되는 것이 일반적이라, 키/값도 그 순서를 따름.

- 병합/갱신
  - `update(other_dict)`  
    - 같은 키가 있으면 기존 값이 덮어씌워짐

- 순차 자료형에서 dict 만들기
  - `zip(key_list, value_list)`로 짝지어 만든 뒤 `dict()`로 변환 가능
    - 예: `mapping = dict(zip(keys, values))`

- 기본값 처리
  - `d.get(key, default)`로 키가 없을 때 기본값 반환 가능
  - `setdefault(key, default)`는
    - 키가 없으면 기본값을 넣고 그 값을 반환 → “그룹핑” 패턴에 자주 씀
  - `collections.defaultdict(list)` 같은 형태는 더 깔끔한 기본값 딕셔너리 구성 방법

- 유효한 키(중요)
  - 키는 해시 가능(hashable) 해야 함: 보통 `int/float/str/tuple(안도 불변)` 등
  - 리스트는 가변이라 키 불가: `TypeError: unhashable type: 'list'`
  - 리스트를 키로 쓰고 싶으면 `tuple(list)`로 변환

3.1.4 집합 (set)

- 핵심 성질
  - 중복 없는 원소를 담는 정렬되지 않은 자료형.
  - 생성: `set([...])` 또는 `{...}`

- 대표 연산
  - 합집합: `a.union(b)` 또는 `a | b`
  - 교집합: `a.intersection(b)` 또는 `a & b`
  - 차집합: `a - b`
  - 대칭차집합: `a ^ b`
  - 제자리 대입 버전도 존재: `|=`, `&=`, `-=`, `^=`

- 원소 제약
  - 집합 원소도 해시 가능해야 함 → 리스트 같은 건 직접 못 넣고, 필요하면 튜플로 변환

- 포함 관계/동등 비교
  - 부분집합: `issubset`, 상위집합: `issuperset`
  - 같은 원소면 순서와 무관하게 동일: `{1,2,3} == {3,2,1}`

3.1.5 내장 순차 자료형 함수

- `enumerate(collection)`  
  - `(index, value)`를 함께 제공 → 인덱스 추적할 때 깔끔
- `sorted(iterable, key=..., reverse=...)`  
  - 정렬된 새 리스트 반환
- `zip(a, b, ...)`  
  - 여러 순차 자료형을 묶어 튜플로 반환  
  - 가장 짧은 길이에 맞춰 종료
- `reversed(seq)`  
  - 역순 이터레이터 반환(필요할 때 `list()`로 펼침)

3.1.6 리스트/집합/딕셔너리 표기법(컴프리헨션)

- 리스트 컴프리헨션
  - 형식: `[expr for value in collection if condition]`
  - 반복문 + 필터 + 변환을 한 줄로 압축

- 집합 컴프리헨션
  - 형식: `{expr for value in collection if condition}`
  - 중복 제거가 자동으로 발생

- 딕셔너리 컴프리헨션
  - 형식: `{key_expr: value_expr for value in collection if condition}`

- 중첩 리스트 컴프리헨션(중요 포인트)
  - `for`의 순서는 바깥 → 안쪽으로 나열됨
  - 예: `flattened = [x for tup in some_tuples for x in tup]`  
    - “튜플들을 돌면서, 각 튜플 안의 x들을 뽑아서” → 1차원으로 평탄화
  - 반면 `[[x for x in tup] for tup in some_tuples]`는  
    - 각 튜플을 “리스트로 바꾼 리스트” → 리스트의 리스트(2차원)가 됨  
    - 결과 형태가 완전히 다르니 헷갈리면 큰일 남

### 실습 인증

<img width="840" height="553" alt="스크린샷 2026-03-12 164533" src="https://github.com/user-attachments/assets/cf3f4e19-560a-4271-b4e1-49c4f0ca73ab" />
<img width="633" height="508" alt="image" src="https://github.com/user-attachments/assets/ae65dd92-f3dc-44c3-9048-743b253ecc5b" />
<img width="915" height="506" alt="image" src="https://github.com/user-attachments/assets/d74f63cf-f02d-4a7b-87a4-b85e54c94b5f" />
<img width="534" height="296" alt="image" src="https://github.com/user-attachments/assets/38b63420-e442-4f68-b8d7-920159204bd5" />
<img width="942" height="793" alt="image" src="https://github.com/user-attachments/assets/1dce6c82-923b-4f69-bfb9-6fc40540bb42" />
<img width="752" height="206" alt="image" src="https://github.com/user-attachments/assets/11899ebf-0e1f-497e-bfd0-27cd4fd2a9d3" />
<img width="754" height="114" alt="image" src="https://github.com/user-attachments/assets/e5bf9be0-026d-4580-9a7a-63f43dd8f32d" />


## 2. 함수

### 개념정리

3.2 함수

- 함수 정의와 반환
  - 함수는 `def` 예약어로 정의한다.
  - 함수는 필요하면 `return`으로 값을 반환한다.
  - `return`을 만나면 함수 실행이 즉시 종료되고, 뒤의 값이 호출한 곳으로 전달된다.
  - `return`이 없으면 자동으로 `None`이 반환된다.

3.2.2 여러 값 반환하기

- 여러 값 반환
  - 파이썬 함수는 한 번에 여러 값을 반환
  - 실제로는 튜플(tuple) 하나를 반환하는 방식

3.2.3 함수도 객체다

- 문자열 정제
  - 문자열 리스트를 공백 제거, 구두점 제거, 대소문자 정리로 정제

- 함수 목록을 이용한 처리
  - 여러 함수 리스트를 넣고 순서대로 적용 가능
  - 재사용성과 확장성이 높음

- map 함수
  - 순차 자료형의 각 원소에 함수를 적용할 때 사용
  - 함수 자체를 인수로 전달

3.2.4 익명(람다) 함수

- 람다 함수
  - 이름 없는 한 줄짜리 함수
  - 짧고 간단한 연산을 바로 전달할 때 유용
  - 정렬 기준으로 사용 (ex: 'key' 인수)
    - 문자열에 사용된 서로 다른 문자 수 기준 정렬

3.2.5 제너레이터

- 이터레이터와 순회
  - ex. 딕셔너리 : 반복문에서 키 하나씩 반환
  - 이터레이터 프로토콜 기반
    
- 제너레이터
  - 순회 가능한 객체를 만드는 간단한 방법
  - 'yield' 사용해 값 하나씩 반환 <-> 'return'
  - 필요할 때마다 실행 이어짐

- 제너레이터 특징
  - 함수를 호출했다고 바로 실행되지 않음
  - 값을 요청할 때 실행
  - 한 번에 전체 데이터를 만들지 않음 -> 메모리 절약

  3.2.5-1 제너레이터 표현식

  - 제너레이터를 간단하게 만드는 방법
  - 리스트 컴프리헨션과 비슷. 대괄호 `[]` 대신 괄호 `()` 사용
    
  - 장점
    - 코드가 간결함
    - 큰 데이터를 다룰 때 리스트보다 메모리 효율이 좋음
    - 경우에 따라 속도 면에서도 이점

  3.2.5-2 itertools 모듈

  - 개념
    - 반복 가능한 데이터를 처리하는 데 유용한 표준 라이브러리
    - 여러 종류의 제너레이터 기반 도구 제공
      
  - group by 예시
  ```python
  import itertools

  def first_letter(x):
      return x[0]

  names = ["Alan", "Adam", "Wes", "Will", "Albert", "Steven"]

  for letter, group in itertools.groupby(names, first_letter):
      print(letter, list(group))
  ```

  - 주요함수
    - chain(*iterables) : 여러 이터레이터를 하나로 이어 붙임
    - combinations(iterable, k) : 순서를 고려하지 않는 길이 `k` 조합 생성
    - permutations(iterable, k) : 순서를 고려하는 길이 `k`의 순열 생성
    - groupby(iterable[, keyfunc]) : 같은 키를 가진 데이터끼리 그룹화
    - product(*iterables, repeat=1) : 데카르트 곱 계산

3.2.6 오류와 예외 처리
  
  - try / except : 예외가 발생할 수 있는 코드를 `try`에 넣고, 문제가 생기면 `except`에서 처리
  - 특정 예외만 처리 : except
  - finally : 예외 발생 여부와 상관없이 반드시 실행할 코드 (ex. 파일 닫기 같은 정리 작업)
    
  - IPython에서의 예외 처리
    - IPython은 예외가 발생했을 때 일반 파이썬보다 더 자세한 스택 트레이스
    - `%xmode`로 출력 수준을 조절
    - `%debug`, `%pdb`로 대화형 디버깅

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 4-5장 캡쳐하여 제출해주세요. -->

<img width="368" height="162" alt="Image" src="https://github.com/user-attachments/assets/6ce1eb3c-5183-4cf0-9b71-4dd9feaebef8" />
<img width="370" height="277" alt="Image" src="https://github.com/user-attachments/assets/04a34492-2f7c-4a5d-ae8e-8144687efd97" />
<img width="498" height="316" alt="Image" src="https://github.com/user-attachments/assets/ebd6fe0a-f026-4256-8922-b3a9aeac43df" />
<img width="648" height="364" alt="Image" src="https://github.com/user-attachments/assets/16e0a6d2-cc1a-4ddc-9918-98c2a1843e10" />

## 3. 파일과 운영체제

### 개념정리

3.3 파일과 운영체제

- 'open()' : 파일 읽고 쓰기
- 'rstrip' : 줄 끝 개행 문자 제거
- 'with' : 블록 끝날 때 자동으로 닫힘
  
- 파일 모드
  - `r` : 읽기 전용
  - `w` : 쓰기 전용, 기존 파일이 있으면 덮어씀
  - `x` : 새 파일 생성, 이미 있으면 실패
  - `a` : 기존 파일 끝에 추가
  - `r+` : 읽기/쓰기
  - `b` : 이진 모드
  - `t` : 텍스트 모드(기본값)

- 읽기 관련 메서드
  - `read(size)` : 지정한 크기만큼 읽기
  - `tell()` : 현재 파일 위치 확인
  - `seek(pos)` : 특정 위치로 이동

- 쓰기 관련 메서드
  - `write(string)` : 문자열 쓰기
  - `writelines(strings)` : 여러 문자열 쓰기
 
- 자주 쓰는 파일 메서드와 속성
  - `read([size])`
  - `readable()`
  - `readlines([size])`
  - `write(string)`
  - `writable()`
  - `writelines(strings)`
  - `close()`
  - `flush()`
  - `seek(pos)`
  - `seekable()`
  - `tell()`
  - `closed`
  - `encoding`

3.3.1 바이트와 유니코드

  - 텍스트 모드와 이진 모드
    - 파이썬 파일은 기본적으로 텍스트 모드로 열린다.
    - 텍스트 모드는 문자열(`str`)을 다루고,
    - 이진 모드는 바이트(`bytes`)를 다룬다.

  - 'decode()' : 이진 모드에서 읽은 바이트 문자열로 변경

  - 인코딩 지정
    - 플랫폼마다 기본 인코딩이 다를 수 있다.
    - 따라서 일관된 동작을 원하면 `encoding="utf-8"`처럼 명시하는 것이 좋다.

### 실습 인증

<!-- 예제 실습을 진행한 후, 실행 화면을 4-5장 캡쳐하여 제출해주세요. -->

<img width="456" height="135" alt="Image" src="https://github.com/user-attachments/assets/2c8256a9-566c-44a2-bd11-a4a65b9c654d" />
<img width="625" height="109" alt="Image" src="https://github.com/user-attachments/assets/7d5e979a-3628-4dc6-b163-7867dfee1d09" />
<img width="448" height="207" alt="Image" src="https://github.com/user-attachments/assets/2a747598-430f-4abf-84b5-4fa7d97427e4" />
<img width="650" height="117" alt="Image" src="https://github.com/user-attachments/assets/6f1c1de5-231e-41fd-ba9c-764f55be5855" />



# 2️⃣ 실습 과제

각 문제에 대한 실행 결과가 확인되도록 코드를 작성하고 실행한 뒤, **모든 문제의 실행 화면을 캡처하여 제출하시기 바랍니다.**

**1. 다음 형식으로 학생 정보를 저장하세요.**
```python
students = [
    {"name": "규서", "score": 85},
    {"name": "예운", "score": 72},
    {"name": "민서", "score": 90}
]
```

**2. 문제**
```
1. 전체 평균 점수를 구하는 함수 작성 및 결과 출력
  - students 리스트를 입력받아 평균 점수를 반환하는 get_average 함수를 작성하세요.
  - 함수를 호출하여 계산된 평균 점수를 print()를 이용해 화면에 출력하세요.

2. 80점 이상 우수 학생 추출 및 리스트 출력
  - 리스트 표기법을 사용하여 점수가 80점 이상인 학생의 이름만 담긴 새로운 리스트를 만드세요.
  - 생성된 우수 학생 명단 리스트를 print()를 이용해 화면에 출력하세요.
```

```
1. 전체 평균 점수 계산
```
<img width="858" height="202" alt="Image" src="https://github.com/user-attachments/assets/cf4cc107-a1c0-439d-9263-2d7b1719baaa" />

```
2. 80점 이상 우수 학생 추출
```
<img width="960" height="135" alt="Image" src="https://github.com/user-attachments/assets/06faed0b-39d5-4c8c-b194-96275d2d9d0e" />

### 🎉 수고하셨습니다.







