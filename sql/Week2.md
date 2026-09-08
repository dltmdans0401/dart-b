# SQL_ADVANCED 2주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=_JURyg_KzHE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=7
https://www.youtube.com/watch?v=6qkPy7RfLqQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=8
https://www.youtube.com/watch?v=WWAFAm9op2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=9
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_2nd_TIL

### 3장 SQL 기본 문법
#### 01. 기본 중에 기본 SELECT ~ FROM ~ WHERE
#### 02. 좀 더 깊게 알아보는 SELECT문
#### 03. 데이터 변경을 위한 SQL문


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 기본 중에 기본 SELECT ~ FROM ~ WHERE

<!-- 기본적인 SQL 문법에 관해 배우게 된 점을 적어주세요. -->  
DROP DATABASE IF EXISTS market_db;          -- market_db 존재한다면 삭제  
CREATE DATABASE market_db;                  -- market_db 생성  
USE market_db;                              -- market_db 데이터베이스에서 명령어 수행  
CREATE TABLE member ( 열이름 자료형 제약조건, ...)    -- member 테이블 생성  
INSERT INTO member VALUES (...)             -- member 테이블에 데이터 입력  

SELECT 열이름  
FROM 테이블명  
WHERE 조건식  
GROUP BY 열이름  
HAVING 집계함수_조건식  
ORDER BY 열이름 [ASC|DESC}  
LIMIT 숫자{,숫자}  


<!-- 과제 페이지를 참조하여 인증 사진 2장을 아래의 부분을 지우고 제출해주세요. -->

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/97301478-a7b3-4d5d-9c32-f15d09fbb870" />  
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/7b0ec4aa-95e3-47c6-9474-8b6119ab1d7c" />



> **확인문제: 주소의 지역이 서울, 경기인 회원을 추출하는 SQL 문입니다. 빈칸에 들어갈 수 있는 것을 모두 고르세요.**

```sql
SELECT *
FROM table
WHERE ________;
```

보기는 아래와 같습니다.
```
1. addr IN('서울', '경기')
2. addr BETWEEN '서울' AND '경기'
3. addr = '서울' OR addr = '경기'
4. addr = '서울' AND addr = '경기'
```

```
1, 3
3: addr = '서울' or addr = '경기'  -- addr 컬럼이 서울이거나 경기일 경우 조회되는 조건
1: addr IN('서울', '경기')    -- addr 컬럼이 IN() 내부의 서울, 경기 중 하나일 경우 조회되는 조건. 
```


## 2. 좀 더 깊게 알아보는 SELECT문

<!-- ORDER BY절과 GROUP BY절 그리고 HAVING절에 관해 배우게 된 점을 적어주세요. -->

```
여기에 배우게 된 점을 적어주세요!
ORDER BY절: 열 이름을 기준으로 오름차순 정렬. desc로 지정할 경우 내림차순.
GROUP BY절: 지정한 열로 그룹핑. 여러 컬럼을 사용할 수도 있다. 
HAVING절: WHERE 조건절과 달리 집계함수에 대한 조건절 사용 가능
```

> **확인문제: 다음 표는 주요 집계함수를 정리한 것입니다. 각 설명에 해당하는 올바른 함수명을 기호에 맞게 작성하세요.**

| 함수명 | 설명 |
|--------|------|
| SUM() | 합계를 구합니다. |
| (ㄱ) | 평균을 구합니다. |
| (ㄴ) | 최소값을 구합니다. |
| MAX() | 최대값을 구합니다. |
| (ㄷ) | 행의 개수를 셉니다. |
| (ㄹ) | 행의 개수를 셉니다 (중복은 1개만 인정). |

```
여기에 답을 적어주세요!
(ㄱ) AVG()
(ㄴ) MIN()
(ㄷ) COUNT()
(ㄹ) COUNT(DISTINCT)
```


## 3. 데이터 변경을 위한 SQL문

<!-- INSERT문, UPDATE문, DELETE문에 관해 배우게 된 점을 적어주세요. -->

```
여기에 배우게 된 점을 적어주세요!
INSERT문: INSERT INTO 테이블명 (컬럼명...) VALUES (데이터...)    -- 컬럼명 생략시 NULL 입력
UPDATE문: UPDATE 테이블명 SET 열이름 = 변경값 WHERE 조건문        -- WHERE문 생략시 모든값 변경 
DELETE문: DELETE FROM 테이블명 WHERE 조건문                     -- WHERE문 생략시 모든값 삭제
```


# 2️⃣ 실습과제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.(market_db를 그대로 사용합니다.)

1. 모든 그룹 멤버의 정보를 조회하시오.
2. 멤버의 수가 6명 이상인 그룹 정보를 조회하시오.
3. 현재 구매 테이블에 존재하는 서로 다른 상품(prod_name)이 어떤 것이 있는지 조회하시오.
4. 총 구매 금액이 1000미만인 prod_name 중 상위 2개만 조회하시오.

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/bd3732d8-1c8c-46bc-8c23-8f5c4c9e0db6" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/894e8086-d96a-4f82-9e4a-3ee4cf3e6c45" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/14abd748-2949-432c-acd7-e7ef4c1d1790" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/36855733-8f87-4c79-9aef-1808612a1869" />




### 🎉 수고하셨습니다.







