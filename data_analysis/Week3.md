# 데이터분석 3주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=CE3_InvbmLY&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=6
https://www.youtube.com/watch?v=hhbzUEQWdTg&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=7
-->


## DataAnalysis_3rd_TIL

### 3장 데이터 정제하기
#### 01. 불필요한 데이터 삭제하기
#### 02. 잘못된 데이터 수정하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | 🍽️         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 불필요한 데이터 삭제하기

3-1: 불필요한 데이터 삭제하기

#행 조건, 열 조건에 일치하는 데이터프레임을 리턴  
df = df.loc[(행 대상), (열 대상)]   
____________________________________________________________  
'''  
삭제  
axis = 1이면 열을 삭제, 기본값은 행을 삭제  
'''  
df = df.drop(삭제대상, axis = 1)  
____________________________________________________________  
'''  
널 값을 삭제  
axis매개변수에 1을 지정하면 열을 삭제  
how = 'all'이면 모든값이 nan일때, how = 'any'일때는 하나만 nan이어도 열을 삭제.  
'''  
df = df.dropna(axis = 1, how = 'all')  
____________________________________________________________  
'''  
열이름에 대해 중복된 행에 True 부여  
keep = False 일때 중복된 모든 행에 True, keep = 'last' 일때 중복된 마지막 제외 나머지 행에 True, 기본값은 중복된 첫행 제외 나머지 행에 True 부여.    
조건문처럼 ~dup_rows로도 사용가능  
'''  
dup_rows = df.duplicated(subset = ['열이름들'], keep = False)  
____________________________________________________________  
'''  
그루핑  
dropna = False 일때 NaN 행을 삭제하지 않음. 기본값은 삭제  
'''  
df = df.groupby(by = ['열이름들'], dropna = False)  

## 02. 잘못된 데이터 수정하기

df.isna()   #NaN에다가 1 부여  
df.isna().sum()    #각 열의 NaN 값 조회  
df.isna().sum().sum()    #데이터프레임의 모든 열의 NaN값 합  
___________________________________________________________  
#데이터 타입 수정  
df = df.astype({열이름: 자료형 형태의 딕서너리로 전달})  
____________________________________________________________  
#결측치 채우기   
df = df.fillna({열이름: 값 형태의 딕셔너리로 전달})  
____________________________________________________________  
#값 바꾸기  
df = df.replace({원래값: 새로운값 형태의 딕셔너리로 전달})  
df = df.replace({열이름: {원래값: 새로운값, ...} 형태의 딕셔너리})  
____________________________________________________________  
'''  
정규 표현식  

r: 정규 표현식 시작  
(): 1개의 그룹  
\1: 1번째 그룹  
\d: 숫자 1글자  
\D: 숫자가 아닌 다른 모든 문자에 대응  
\s: 공백 1글자   
.: 한 글자   
{n}: n회 반복  
*: 0회 이상 반복  
regex = True: 정규 표현식으로 해석하겠다.   
'''  
df = df.replace({'저자': {r'(.*)\s\(지은이\)(.*)\s\(옮긴이\)':   
r'\1\2'}}, regex = True)  
____________________________________________________________  
'''  
해당 문자열을 포함하고 있는 데이터 조회  
na = True일때 결측값은 True로, na = False일때 결측값은 False로, 기본값은 결측값은 nan으로 처리  
'''  

df = df['열이름'].str.contains('\D', na = True)  


# 2️⃣ 수행 인증

<!-- 교재에서 안내된 과정을 직접 실행해본 뒤, 진행 결과가 보이도록 4~6장의 스크린샷을 캡처하여 아래에 첨부해주세요.-->
<!-- 이번 주차에는 API를 발급받는 과정도 포함하여 첨부해주세요.-->

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/0c2669d8-fec2-4f9e-9537-0ca9ac8145fc" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/98f4a61f-1040-4c70-bb3f-4ce6ac509ad7" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/2d871ffa-8cb0-4a18-8417-dc876acc6ff8" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/6f37de5c-661a-469c-bf03-675b96c2e9f5" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/b7cc3962-bce4-468a-9ffe-216689e2331e" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/5ba5aa85-210d-4321-9004-369102b3eed0" />



# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 두 데이터프레임 df1, df2를 합쳐서 데이터프레임 df3를 만들려고 합니다.**  
> 적절한 판다스 명령을 선택해주세요.

<table>
<tr>

<td>

### df1

| index | col1 | col2 |
|-------|------|------|
| 0     | x    | 5    |
| 1     | y    | 6    |
| 2     | z    | 7    |

</td>

<td>

### df2

| index | col3 | col4 |
|-------|------|------|
| 0     | x    | 50   |
| 1     | y    | 60   |
| 2     | w    | 70   |

</td>

<td align="center" valign="middle">

<h2> ➜ </h2>

</td>

<td>

### df3 (결과)

| index | col1 | col2 | col3 | col4 |
|-------|------|------|------|------|
| 0     | x    | 5.0  | x    | 50.0 |
| 1     | y    | 6.0  | y    | 60.0 |
| 2     | z    | 7.0  | NaN  | NaN  |
| 3     | NaN  | NaN  | w    | 70.0 |

</td>

</tr>
</table>

```
1️⃣ pd.merge(df1, df2)
2️⃣ pd.merge(df1, df2, how='left')
3️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='outer')
4️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='inner')
```

```
3번  
양 쪽의 기준 열은 df1의 기준 열은 col1, df2의 기준 열은 col3이고 df3에는 공통된 값 외에도  
각각의 테이블에 고유하게 존재하는 w, z가 모두 포함되어서 how = 'outer' 옵션이 필요. 
```



### 🎉 수고하셨습니다.
