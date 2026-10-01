# 데이터분석 5주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_5th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=ho0LZ6GWhtc&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=10
https://www.youtube.com/watch?v=deYY4xHsI0o&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=11
-->


## DataAnalysis_5th_TIL

### 5장 데이터 시각화하기
#### 01. 맷플롯립 기본 요소 알아보기
#### 02. 선 그래프와 막대 그래프 그리기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | ✅         |
| 5주차 | p.282~325 | ✅         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 맷플롯립 기본 요소 알아보기

Figure 객체  
- 시각화 함수를 사용하면 자동으로 피겨 객체가 생성  
- plt.figure() 함수로 명시적으로 피겨 객체를 만들어 활용하면 다양한 그래프 옵션을 조절 가능  

rcParams 객체  
- 맷플롯립 그래프의 기본값을 관리하는 객체   
- DPI(1인치를 몇개의 픽셀로 나타내는가) 기본값 변경 가능  
- 마커 모양 변경 가능   
 
subplots 객체  
(fig, axes) = plt.subplots(행, 열)   
- fig: 전체 그림 객체  
- axes: 각 서브 플롯을 나타내는 axes 객체의 배열  

*subplots와 subplot의 차이   
plt.subplot(행, 열, 사용할 서브플롯 위치 지정)    #사용할 위치 지정  
plt.subplots(행, 열)    # (fig, axes) 튜플 반환  

## 02. 선 그래프와 막대 그래프 그리기

pd.to_numeric(시리즈 혹은 배열, errors = 'coerce')  
df.value_counts(): 각 범주와 빈도 수 출력해서 리턴  
df.sort_values(): 값 순으로 정렬   
df.sort_index(): 인덱스 순으로 정렬  
plt.xticks(눈금 위치 배열, rotation = 45): x축에 눈금, 45도로 회전  
plt.annotate(문자열, (x좌표,y좌표)): 해당 좌표에 마커와 문자열 출력  

그래프 시각화 함수  
plt.plot(x축 데이터, y축 데이터): 선 그래프  
plt.bar(x축 데이터, y축 데이터): 막대 그래프   



# 2️⃣ 수행 인증

<!-- 교재에서 안내된 과정을 직접 실행해본 뒤, 진행 결과가 보이도록 4~6장의 스크린샷을 캡처하여 아래에 첨부해주세요.-->


<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/7ff66b25-e1d7-4792-90a6-928e416454e6" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/3450105c-5707-46f0-aa4b-cce62161db15" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/4aeec952-5c7f-4537-9227-c8373afd8a54" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/e535bc07-3b45-4d8d-92f7-40e550836cb7" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/99a8fb67-2799-4074-b07e-c353aec2d839" />


# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 데이터를 이용하여 matplotlib으로 선그래프를 그리는 코드를 작성해주세요.**
- x = [1, 2, 3, 4, 5]
- y = [2, 4, 6, 8, 10]
> 조건은 아래와 같습니다.
```
1️⃣ 제목은 "Linear Trend"로 설정해주세요.
2️⃣ x축 이름은 "X values"로 설정해주세요.
3️⃣ y축 이름은 "Y values"로 설정해주세요.
4️⃣ 마커(marker)를 포함하여 선그래프를 그려주세요.
```

```
import matplotlib.pyplot as plt

x = [1,2,3,4,5]
y = [2,4,6,8,10]
plt.plot(x, y)
plt.title("Linear Trend")
plt.xlabel("X values")
plt.ylabel("Y values")
for i in range(len(x)):
    plt.annotate(str(x[i]), (x[i], y[i]), textcoords = 'offset points', xytext = (1,1))
plt.show()
```



### 🎉 수고하셨습니다.
