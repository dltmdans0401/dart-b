# SQL_ADVANCED 3주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=1YmWy-7-OhQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=10
https://www.youtube.com/watch?v=tuQFkzjqEGw&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=11
https://www.youtube.com/watch?v=IOCsreDYqFE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=12
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_3rd_TIL

### 4장 SQL 고급 문법
#### 01. MySQL의 데이터 형식
#### 02. 두 테이블을 묶는 조인
#### 03. SQL 프로그래밍 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. MySQL의 데이터 형식

<!-- MySQL의 데이터 형식에 관해 배우게 된 점을 적어주세요. -->
<!-- 과제 설명 예시처럼 직접 실습 후 사진 한 장 이상을 첨부해주세요. -->  
정수형  
TINYINT: 1바이트  
SMALLINT: 2바이트  
INT: 4바이트  
BIGINT: 8바이트  

UNSIGNED: 정수형의 데이터 형태를 0부터 시작하도록 변환  
CREATE TABLE 테이블명 (  
열이름 정수형 UNSIGNED 열특성 키특성, ...);  

문자형  
CHAR(): 고정된 바이트 수의 문자열. 빠른 속도.  
VARCHAR(): 가변적인 바이트 수의 문자열. 느린 속도.   

대량의 데이터 형식  
TEXT: 대용량의 텍스트  
LONGTEXT: 훨씬 대용량의 텍스트  
BLOB: 대용량의 이진 데이터  
LONGBLOG: 훨씬 대용량의 이진 데이터  

실수형  
FLOAT: 4바이트  
DOUBLE: 8바이트  

날짜형  
DATE: YYYY-MM-DD   
TIME: HH:MM:SS  
DATETIME: YYYY-MM-DD HH:MM:SS  

@변수: 세션변수. 쿼리문 전체에서 사용 가능  

DECLARE 변수: 지역변수. 프로시저 내부에서 사용 가능  
DECLARE로 선언해야 사용가능  
DECLARE 변수명 자료형;   

SET: 변수 선언 혹은 지정한 열의 값 입력  
SET 변수명 = 값;  
UPDATE 테이블명 SET 열이름 = 값 WHERE 조건문  

CONVERT: 데이터 형 변환  
CONVERT(값, 변경할_자료형)  

CONCAT: 입력값들을 문자열로 변환 후 연결  
CONCAT(입력값, 입력값, 입력값...)   

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/7f180803-4235-4b25-88d1-d610aec81bb4" />


> **확인문제: 다음 보기에서 데이터 형식의 변환에 사용되는 함수를 2개 고르세요.**

보기는 아래와 같습니다.
```
CONVERT() / DATA() / CAST() / MOVE() / TYPE() / SUM() / AVG() / CURRENT_DATE()
```

```
CONVERT(), CAST()
```


## 2. 두 테이블을 묶는 조인

<!-- 두 테이블을 묶는 조인에 관해 배우게 된 점을 적어주세요. -->
<!-- 과제 설명 예시처럼 직접 실습 후 인증 사진 4장 이상을 첨부해주세요. -->  

내부 조인: 조인될 조건에서 양쪽 모두 일치하면 조인  
SELECT 열이름 '별칭', ...   
FROM 테이블명 테이블별칭  
JOIN 테이블명 테이블별칭  
ON 조인조건  
.....  

외부 조인: 기준이 되는 테이블의 열은 모두 출력하고, 그에 맞춰 조인  
SELECT 열이름 '별칭'...  
FROM 기준테이블명 기준테이블별칭  
LEFT JOIN 테이블명 테이블별칭  
ON 조인조건  
....  


FULL OUTER JOIN: LEFT JOIN과 RIGHT JOIN이 합쳐진 것  

상호조인: ON 조건 없이 모든 데이터를 조인  
SELECT 열이름 FROM 테이블명 CROSS JOIN 테이블명...;  

자체조인: 하나의 테이블에 대해서 조인.   
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/191618f7-02be-4374-bfd5-1e384d5a0763" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/522034b7-595d-4b22-b57c-8e1c0b2f90d7" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/a78871b1-a42c-4611-a722-b5bdffca046b" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/c0f933e6-1f30-45c9-b2e2-feb423e065b0" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/ddae4367-50f8-49ae-a4ea-7a6ca73f4f0f" />





> **확인문제: 다음 SQL은 회원으로 가입만 하고, 한 번도 구매한 적이 없는 회원의 목록을 조회하는 쿼리입니다. 빈칸에 들어갈 가장 적절한 구문을 고르세요..**

```sql
SELECT DISTINCT M.mem_id, B.prod_name, M.mem_name, M.addr
  FROM member M
    LEFT OUTER JOIN buy B
    ON M.mem_id = B.mem_id
  __________
  ORDER BY M.mem_id;
```
보기는 아래와 같습니다.
```
1. JOIN B.prod_name IS NULL
2. LIMIT B.prod_name IS NULL
3. HAVING B.prod_name IS NULL
4. WHERE B.prod_name IS NULL
```
```
4. WHERE B.prod_name IS NULL
member 테이블을 기준으로 외부 조인을 취했을 때 모든 buy의 mem_id에 값이 존재하지 않더라도, 즉 물품을 사지 않았더라도 모든 member 테이블의 mem_id는 조회된다. 이때 buy테이블에 mem_id가 존재하지 않을 경우 B.prod_name은 NULL값으로 처리된다. 따라서 NULL값만 조회하는 조건문이 들어가야 한다. 따라서 정답은 4. 
```

## 3. SQL 프로그래밍 

<!-- IF문, CASE문, WHILE문에 관해 배우게 된 점을 적어주세요. -->  
DELIMITER: SQL문의 종료문자인 ;를 다른 문자로 변환  
DELIMITER $$ ~~~~~ DELIMITER ;  

스토어드 프로시저: 프로그래밍 기능을 가진 쿼리문  
DELIMITER $$ -- 종료문자 변환  
CREATE PROCEDURE 프로시저명 BEGIN  
~~~~~~~~~~~~~~~~~~~~ -- 프로시저 내부에서는 ; 사용  END $$ -- 프로시저 종료
DELIMITER ; -- 종료문자를 다시 ;로 변환  
CALL 프로시저명  


IF문  
IF 조건문 THEN 수행문;  
ELSE 수행문;   
END IF;  


CASE문  
CASE   
WHEN 조건문 THEN 수행문;   
...  
ELSE 수행문;  
END CASE;  


WHILE문  
WHILE 조건문 DO 수행문;  
END WHILE;  

동적 SQL  
-쿼리문을 문자열에 PREPARE  
-EXECUTE로 문자열 속 쿼리문 실행  
-DEALLOACATE 로 지정된 쿼리문 해제  
*동적 SQL에서는 변수를 사용할 수 없어서 USING 예약어 사용  

PREPARE 문장 FROM '쿼리문 문자열';  
EXECUTE 문장 USING 변수;  
DEALLOCATE PREPARE 문장;    

> **확인문제: 다음은 CASE 문의 형식입니다. 빈칸에 들어갈 가장 적절한 명령어를 보기에서 고르세요..**

```sql
CASE
    (1) 조건 THEN
        SQL문장들1
    ELSE
        SQL문장들4
END (2);
```

보기는 아래와 같습니다.
```
WHEN / THEN / CURRENT / DATE / TIME / IF / END IF / CASE
```

```
여기에 답을 적어주세요!
(1) WHEN
(2) CASE
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week3_db;

-- 2. 사용할 데이터베이스 선택
USE week3_db;

-- 3. 기존 테이블 삭제 (초기화용)
DROP TABLE IF EXISTS orders;
DROP TABLE IF EXISTS customers;

-- 4. 테이블 생성 (조인 실습용)
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(20),
    signup_date_str VARCHAR(8) 
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,           
    order_date_str VARCHAR(8), 
    amount_str VARCHAR(10)     
);

-- 5. 데이터 삽입
INSERT INTO customers VALUES
(1, '신영', '20241528'),
(2, '경모', '20220261'),
(3, '세원', '20203401'),
(4, '진우', '20221024'),
(5, '성환', '20225100'),
(6, '혜준', '20244946'),
(7, '채은', '20250412'),
(8, '다나', '20212774'); -- 주문 없는 고객(외부 조인용)

INSERT INTO orders VALUES
(101, 1, '20240220', '12000'),
(102, 1, '20240303', '30000'),
(103, 2, '20240111', '15000'),
(104, 3, '20221201', '9000'),
(105, 5, '20231111', '20000'),
(106, 7, '20220707', '5000'),
(107, 99, '20240210', '7000'); -- 고객 테이블에 없는 customer_id (외부 조인용)
```

## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.

1. **데이터 형식 변환**
   - orders 테이블의 `order_date_str`을 DATE 형식으로 변환하여 조회하시오.
   (힌트: STR_TO_DATE 사용)

2. **데이터 형식 변환**
   - orders 테이블의 `amount_str`을 숫자형으로 변환하여 조회하시오.

3. **내부 조인 (INNER JOIN)**
   - customers와 orders를 customer_id 기준으로 내부 조인하여
     고객 이름(name)과 주문 번호(order_id)를 함께 조회하시오.

4. **외부 조인 (LEFT JOIN)**
   - customers를 기준으로 LEFT JOIN을 수행하여,
     주문이 없는 고객도 함께 조회하시오.

5. **스토어드 프로시저 (IF문 사용)**
   - 입력받은 금액이 10000 이상이면 '고액 주문',
     그렇지 않으면 '일반 주문'을 출력하는
     프로시저를 생성하시오.
   - 생성 후 CALL로 실행 결과를 확인하시오.


<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/82928973-0416-40c5-ae5a-fc01362c964c" />



### 🎉 수고하셨습니다.







