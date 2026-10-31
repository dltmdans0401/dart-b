# SQL_ADVANCED 6주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_6th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=cw1wGN0ZdFA&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=19
https://www.youtube.com/watch?v=bMQ_dAoaMzA&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=20
https://www.youtube.com/watch?v=bggWVsBmKag&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=21
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_6th_TIL

### 7장 스토어드 프로시저
#### 01. 스토어드 프로시저 사용 방법
#### 02. 스토어드 함수와 커서
#### 03. 자동 실행되는 트리거 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | ✅         |
| 6주차 | p.330~369 | ✅         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 스토어드 프로시저 사용 방법 

<!-- 스토어드 프로시저에 관해 배우게 된 점을 적어주세요. -->

스토어드 프로시저: 프로그래밍 기능이 저장된 데이터베이스 개체  
DELIMITER $$ -- SQL 종료문자를 $$로 변경  
CREATE PROCEDURE 프로시저명   
BEGIN  
~~ 프로시저 내부에서는 종료문자가 ;  
END $$ -- 프로시저 종료  
DELIMITER ; -- SQL 종료문자를 ;로 변경  

프로시저 호출  
CALL  프로시저명();  

프로시저 삭제  
DROP PROCEDURE 프로시저명;  

declare, in, out으로 선언하는 그냥 변수: 지역변수  
@변수: 사용자가 정의하는 변수 (세션변수)  
@@변수: 전역변수  


입력 매개변수, 출력 매개변수가 존재하는 스토어드 프로시저 생성  
DELIMITER $$  
CREATE PROCEDURE 프로시저명(  
IN 입력매개변수명 자료형,  
OUT 출력매개변수명 자료형)  
BEGIN   
~~  
END $$  
DELIMITER ;  
CALL 프로시저명(입력값, @출력받을변수명)  

<!-- 이번 챕터에서는 확인문제를 실습 인증으로 대체하여 진행합니다. 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/f49f77b1-e021-4256-b2c2-cd595ce5f5f3" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/e3a30318-4f68-4df8-916d-5301b8fadcce" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/65e28a17-57fc-4795-bf3f-29ccb34db7eb" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/2f82dbc9-4866-4924-ac9b-1db938eba3e6" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/261050a2-d7e9-4f4d-8228-c5e7d408a930" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/befe9d57-5948-463c-9b08-daaa8ccedb01" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/9a72b639-1719-42a4-9ea0-7ce76b4b6241" />



## 2. 스토어드 함수와 커서 

<!-- 스토어드 함수와 커서에 관해 배우게 된 점을 적어주세요. -->

스토어드 함수: MYSQL에서 사용자가 직접 만들어 사용하는 함수  
*스토어드 함수를 SELECT의 열로서 출력할 수도 있다!  

DELIMITER $$  
CREATE FUNCTION 함수명(변수명 자료형, 변수명 자료형...)   
RETURNS 반환자료형   
BEGIN  
~~    
RETURN 반환값  
END $$  
DELIMITER ;  
SELECT 함수명(입력값...);  

SELECT문으로 변수 입력하기  
SELECT 입력값 INTO 변수명 FROM  테이블명;  

커서: 테이블에서 한 행씩 처리하기 위한 방식  
한 행에 대해서 읽고 (fetch) 동작을 수행하고 그렇게 모든 테이블의 행을 읽으면 종료하는 구조 

<!-- 이번 챕터에서는 확인문제를 실습 인증으로 대체하여 진행합니다. 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/48f9bafd-5a69-4c8d-b9b8-3babda43facf" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/16f455cf-1edb-42fd-b5d0-28139bde39c8" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/8a02e92a-0646-4075-8ccc-b64a827877cb" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/38ea2f1c-30be-4ff2-b1ba-172fce1b2fa6" />



## 3. 자동 실행되는 트리거 

<!-- 트리거에 관해 배우게 된 점을 적어주세요. -->  

트리거: INSERT, UPDATE, DELETE, 즉 DML이 발생할 떄 실행되는 코드  

delimiter $$
create trigger 트리거명 after insert -- 혹은 update 혹은 delete  
on 테이블명 for each row begin  
~~  
end $$
delimiter ;

<!-- 이번 챕터에서는 확인문제를 실습 인증으로 대체하여 진행합니다. 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/00abf615-8198-4b22-a901-839754f00b12" />
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/2d95962e-8591-4673-a0af-4da2d949496e" />



---


### 🎉 수고하셨습니다.







