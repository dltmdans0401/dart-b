# SQL_ADVANCED 4주차 정규 과제

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=DMNpkj_bZIs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=13
https://www.youtube.com/watch?v=BUHj-behLyc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=14
https://www.youtube.com/watch?v=JrXWxku7ZIM&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=15
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_4th_TIL

### 5장 테이블과 뷰
#### 01. 테이블 만들기
#### 02. 제약조건으로 테이블을 견고하게
#### 03. SQL 가상의 테이블: 뷰 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 테이블 만들기 

<!-- 테이블 만들기에 관해 배우게 된 점을 적어주세요. -->
테이블 생성: 기본키 - 외래키 설정  
CREATE TABLE 테이블명 (  
열이름 자료형 열특성 키특성,  
........................................... ,   
PRIMARY KEY (열이름),   
FOREIGN KEY (열이름) REFERENCES 기준테이블명(열이름)  
ON UPDATE CASCADE ON DELETE CASCADE  
);  

## 2. 제약조건으로 테이블을 견고하게 

<!-- 제약조건에 관해 배우게 된 점을 적어주세요. -->  
ON UPDATE CASCADE: 기준 테이블 열 변경 시 참조 테이블 변경  
ON DELETE CASCADE: 기준 테이블 열 삭제시 참조 테이블 열 삭제  

CHECK: 테이블에 조건을 만족해야 입력되도록 제약  
열이름 자료형 [NOT NULL] CHECK 조건문 ...  

DEFAULT: 데이터 기본값 정의  
열이름 자료형 [NOT NULL] DEFAULT 디폴트값...  

ALTER: 뷰 혹은 테이블 구조를 변환  
ALTER TABLE 테이블명 ADD CONSTRAINT PRIMARY KEY (열이름);  
ALTER TABLE 테이블명 ADD CONSTRAINT FOREIGN KEY (열  
이름) REFERENCES 기준테이블명(열이름)   
ON UPDATE CASCADE ON DELETE CASCADE;  
ALTER TABLE 테이블명 ADD CONSTRAINT UNIQUE (열이름);  
ALTER TABLE 테이블명 ADD CONSTRAINT CHECK 조건문;  
ALTER TABLE 테이블명 ALTER COLUMN 열이름 SET DEFAULT 디폴트값;  
ALTER TABLE 테이블명 DROP PRIMARY KEY;  
ALTER TABLE 테이블명 DROP FOREIGN KEY 제약조건이름;  
제약조건  
1: 기본 키   
2: 외래 키  
3: 고유 키  
4: 체크   
5: 기본값 정의  
6: 널 값 허용  

*기본키와 외래키의 관계  
기본키에서 외래키가 참조하고 있을 경우, 그 기본키는 삭제가 불가능  
==> 따라서 외래키가 존재하는 테이블의 데이터를 모두 삭제  
==> 그 후 기준 테이블에서의 데이터도 삭제 가능!  

> **확인문제: 다음 보기 중에서 각 문항이 설명하는 것을 고르세요.**

보기는 아래와 같습니다.
```
CHECK / DEFAULT / PRIMAY KEY / UNIQUE / NOT NULL / FOREIGN KEY
```

```
여기에 답과 그 이유를 적어주세요!
1. 입력되는 데이터가 조건에 맞는지 검사하는 기능: CHECK. CHECK (조건문) 형식으로 조건에 맞지 않는 데이터가 입력하지 않도록 제약조건을 걸 수 있다. 
2. 값을 입력하지 않으면 자동으로 들어갈 값: DEFAULT. DEFAULT 디폴트값 형식으로 입력되지 않았을 경우 디폴트값으로 처리되도록 제약조건을 걸 수 있다.  
3. 빈 값을 입력하는 것을 허용하지 않음:  NOT NULL. 해당 제약조건으로 NULL이 입력되지 않도록 제약조건을 걸 수 있다.  
```


## 3. 가상의 테이블: 뷰 

<!-- 뷰에 관해 배우게 된 점을 적어주세요. -->  
뷰(VIEW): 기존 테이블에서 정의된 SELECT 쿼리 결과를 보여준다.  
=> 따라서 기존 테이블이 변경되면 뷰도 변경된다.   

뷰 생성  
CREATE VIEW 뷰이름 AS  
SELECT ~~~~~  

뷰 조회: 공백이 있을 때는 열이름을 백틱(`)으로 묶어야 출력가능  
SELECT `열이름` FROM 뷰이름 ~~~~  

뷰 수정  
ALTER VIEW 뷰이름 AS   
SELECT ~~~~~  

뷰 삭제  
DROP VIEW IF EXIST 뷰이름;  

뷰 혹은 테이블의 생성 소스코드 확인  
SHOW CREATE VIEW 뷰이름;  
SHOW CREATE TABLE 테이블명;  

> **확인문제: 다음은 뷰의 특징입니다. 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
2️⃣ 뷰는 복잡한 SQL을 단순하게 만드는 효과가 있습니다.
3️⃣ 뷰는 보안에 도움이 됩니다.
4️⃣ 일부 사용자가 테이블에는 접근하지 못하게 하고, 뷰에만 접근하도록 설정할 수 있습니다.
```

```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
CREATE VIEW 뷰이름 AS
SELECT ~~~
형식으로 일부 열만 선택할 수 있다. 
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week4_db;
USE week4_db;
```

## 2. 실습문제

1. 다음 조건을 만족하는 `users` 테이블을 생성하시오.
```
- user_id는 INT이며 **기본키(Primary Key)**로 설정합니다.
- name은 VARCHAR(20)이며 NULL을 허용하지 않습니다.
- email은 VARCHAR(50)이며 중복을 허용하지 않습니다.
- signup_date는 DATE 타입으로 설정합니다.
- grade는 INT이며 기본값(Default)을 1로 설정합니다.
```

2. 다음 조건을 만족하는 `orders` 테이블을 생성하시오.
```
- order_id는 INT이며 기본키(Primary Key)로 설정합니다.
- user_id는 INT이며 NULL을 허용하지 않습니다.
- amount는 INT이며 0보다 커야 합니다.
- order_date는 DATE 타입으로 설정합니다.
```

3. 다음 조건을 만족하여 데이터를 삽입하시오.
```
- users 테이블에 3명 이상의 데이터를 직접 INSERT 하시오. (단, user 중 본인이 포함돼야 함)
- orders 테이블에 3건 이상의 데이터를 직접 INSERT 하시오.
```

4. users와 orders 테이블을 활용하여 다음 컬럼을 보여주는 뷰 user_order_view를 생성하시오.
```
- user_id
- name
- amount
```

5. 생성한 user_order_view를 조회하시오.

## 3. 제출 방법

1. 각 문제의 실행 결과가 보이도록 화면을 캡처합니다.
2. 테이블 생성 결과, 데이터 삽입 결과, 뷰 생성 및 조회 결과가 모두 보이도록 제출합니다.

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/4aceefaf-38a7-491e-84de-177544d5cd05" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/3939de52-b2ea-4755-915e-e42e931e6d2c" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/05134194-3f95-42af-a9ca-9808a6f4a07f" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/50c8b9cc-de9e-4634-a62a-b8ef1ff97c8a" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/6f0bcafe-09c1-4fdc-9fc2-3a2aa92581f8" />






### 🎉 수고하셨습니다.







