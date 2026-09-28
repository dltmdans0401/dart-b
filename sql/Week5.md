# SQL_ADVANCED 5주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_5th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=KZmW6VaY5BU&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=16
https://www.youtube.com/watch?v=vWTDuoSG-YQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=17
https://www.youtube.com/watch?v=aiMSluMNzI8&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=18
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_5th_TIL

### 6장 인덱스
#### 01. 인덱스 개념을 파악하자
#### 02. 인덱스의 내부 작동
#### 03. 인덱스의 실제 사용  


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | ✅         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 인덱스 개념을 파악하자 

<!-- 인덱스에 관해 배우게 된 점을 적어주세요. -->
클러스터형 인덱스  
-기본 키에 자동으로 생성  
-테이블 당 한 개만 생성 가능  
-클러스터 인덱스가 생성된 열을 기준으로 테이블 자동 정렬  

보조 인덱스  
-고유 키에 자동으로 생성  
-테이블에 여러개 생성 가능  

*  
고유 인덱스: 인덱스의 값이 중복되지 않는다는 의미  
단순 인덱스: 인덱스의 값이 중복되어도 된다는 의미  

> **확인문제: 다음은 인덱스 종류와 관련된 설명입니다. 가장 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 클러스터형 인덱스는 영어사전과 비슷한 개념입니다.
2️⃣ 보조 인덱스는 일반 책의 찾아보기와 비슷한 개념입니다.
3️⃣ 클러스터형 인덱스는 기본 키를 설정하면 자동 생성됩니다.
4️⃣ 보조 인덱스는 NOT NULL을 설정하면 자동 생성됩니다.
```

```
여기에 답과 그 이유를 적어주세요!
4️⃣ 보조 인덱스는 NOT NULL을 설정하면 자동 생성됩니다.
보조 인덱스는 NOT NULL이 아닌 해당 열을 UNIQUE 키로 지정했을 때 자동으로 생성된다. 
```


## 2. 인덱스의 내부 작동 

<!-- 인덱스의 내부 작동에 관해 배우게 된 점을 적어주세요. -->  
균형트리: 나무를 거꾸로 표현한 자료 구조  
루트(뿌리) 노드: 가장 상단의 뿌리  
중간(줄기) 노드: 중간  
리프(잎) 노드: 하단  

* 데이터 변경 작업(INSERT, UPDATE, DELETE) 수행 시 인덱스가 존재하면 페이지의 자리가 없을 경우 페이지 분할이 발생해서 성능이 오히려 안좋아진다.  

클러스터형 인덱스 구조: 영어사전  
보조 인덱스 구조: 책 뒷페이지의 찾아보기  

> **확인문제: 다음 설명에서 빈칸에 공통으로 들어갈 용어를 쓰시오.**

```
인덱스를 구성하게 되면 데이터의 변경 작업(INSERT, UPDATE, DELETE)시에 성능이 나빠지는 단점이 있습니다.  
특히 INSERT 작업이 일어날 때 더 느리게 입력될 수 있는데요, 이유는 (           ) 이라는 작업이 발생하기 때문입니다.  
(            ) 작업이 일어나면 MySQL이 느려지고 너무 자주 일어나면 성능에 큰 영향을 줍니다.
```

```
여기에 답을 적어주세요!
데이터 분할
```


## 3. 인덱스의 실제 사용 

<!-- '인덱스 생성과 제거 실습(310p~)' 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/5c12d139-3dbe-4dea-b745-c3ddbcc96bfc" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/6838e437-db25-42ac-a0ef-82b46638c26d" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/eeff9770-6ae5-455a-9428-55f250a1a734" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/2d8a8b0a-5d19-4884-bb11-5c412fc2405d" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/c8b69674-ca59-4e33-8418-0466510cb4a6" />



인덱스 생성  
CREATE [UNIQUE] INDEX 인덱스명   
ON 테이블명 (열이름) [ASC 혹은 DESC];  

인덱스 적용  
ANALYZE TABLE 테이블명;  

인덱스 정보 출력  
SHOW INDEX FROM 테이블명;  

인덱스 제거  
DROP INDEX 인덱스명 ON 테이블명  
*기본키, 고유키로 생성된 인덱스는 ALTER TABLE ~ DROP으로   
기본키, 고유키를 해제하여 인덱스 삭제 가능  

---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week5_db;
USE week5_db;

DROP TABLE IF EXISTS employees;

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(20),
    department VARCHAR(30),
    salary INT,
    hire_date DATE
);

INSERT INTO employees VALUES
(1, '신영', 'Marketing', 3500, '2026-03-01'),
(2, '경모', 'HR', 3200, '2026-06-15'),
(3, '세원', 'IT', 4000, '2024-09-10'),
(4, '진우', 'HR', 5000, '2024-01-20'),
(5, '성환', 'Actuary', 3800, '2025-04-01'),
(6, '혜준', 'Judge', 4500, '2025-12-01'),
(7, '채은', 'HR', 3700, '2026-08-18'),
(8, '다나', 'Actuary', 3700, '2025-08-18');
```

## 2. 실습 문제

다음 문제를 수행하고 실행 결과를 캡처하여 제출하세요.

1. department 컬럼에 보조 인덱스를 생성하시오.
    - 인덱스 생성 후, `SHOW INDEX FROM employees;` 실행 결과가 보이도록 캡처합니다.
    - (idx_department 인덱스가 존재하는지 확인되어야 합니다.)
2. employees 테이블의 인덱스를 확인하시오.  
3. department가 'Sales'인 직원을 조회하시오.
   - 'Sales' 조회 시, 반드시 `EXPLAIN`을 함께 실행한 화면을 캡처합니다.
   - (key 컬럼에 idx_department가 표시되어야 합니다.)
4. 생성한 인덱스를 삭제하시오.
   - 인덱스 삭제 후, 다시 `SHOW INDEX FROM employees;`를 실행하여 idx_department가 사라진 것을 확인한 화면을 캡처합니다.

## 3. 제출방법

인덱스 생성 결과, EXPLAIN 실행 결과, 인덱스 삭제 결과가 모두 보이도록 캡처하여 제출하세요.

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/5e1b7a07-a6b2-4464-adf6-ce0761c17943" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/9b562634-7505-4b86-a87d-1cca824e742c" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/1458c01d-241d-4e00-95c7-c08c1e883af6" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/01c86ca6-1893-4ce4-9d09-713f8b27e997" />



### 🎉 수고하셨습니다.







