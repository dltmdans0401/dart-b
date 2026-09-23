# 데이터분석 4주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=HNlRYQnLkek&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=8
https://www.youtube.com/watch?v=Cbk_tQtuhbM&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=9
-->


## DataAnalysis_4th_TIL

### 4장 데이터 요약하기
#### 01. 통계로 요약하기
#### 02. 분포 요약하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | ✅         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 통계로 요약하기

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
기술 통계: 정량적인 수치 (통계량)으로 데이터 요약하거나 시각화  
통계량: 평균, 표준편차 등 표본의 수치적 요약   
==> 이러한 데이터 분석 방법이 탐색적 데이터 분석 (EDA)  

np.array(df['열이름']): df의 열의 값을 넘파이 시리즈 배열로 만든다.  

df.describe(): 수치형 열에 대한 요약통계   
df.describe(percentiles = [0.3~~]): 해당 분위수의 값도 조회가능  
df.describe(include = 'object'): 문자형의 통계 조회  

*df['열이름']과 df[['열이름']]의 차이!!!!!!!!!  
df['열이름']: 시리즈 객체   
df[['열이름']]: 데이터프레임 객체  

#시리즈 객체로 함수를 실행할 수도 있다. 또한 열이름을 입력하지 않거나 [['열이름']] 형식으로 입력해  서 데이터프레임 객체로 함수를 실행하면 각 열의 함숫값을 데이터프레임형식으로 리턴한다.   
#수치형 변수들에 대한 함수를 사용할 때 수치형으로 출력이 불가능한 함수가 있음에도   df.mean(numeric_only = True) 매개변수를 지정하지 않으면 오류가 난다.   
df['열이름'].mean(): 평균  
df['열이름'].median(): 중앙값  
df['열이름'].mode(): 최빈값  
df['열이름'].var(): 표본분산  
df['열이름'].std(): 표준편차  
df['열이름'].min(): 최솟값  
df['열이름'].max(): 최댓값  
df['열이름'].quantile([x, y...]): 각 분위수에 해당하는 값 시리즈 객체  
df = df['열이름'].drop_duplicates()    #해당 열의 중복 제거  

*해당 값의 백분위 구하기   
#불리안 배열: True 혹은 False의 불리언 자료가 배열된 시리즈 객체. loc 함수의 매개변수로도 사용해서 해당 행과 열을 가져올 수 있다  
df_flag = df['열이름'] < 10    # 불리언 배열 생성  
df_flag.mean()    #True는 1이니까 평균내면 백분위 확인 가능  

*브로드캐스팅  
df['열이름1']/df['열이름2']: 각 대응 원소에 대해 계산한 시리즈 객체  

*넘파이의 기술통계 함수  
'''  
판다스와 넘파이 기술통계 함수의 차이!!!!  
판다스: 시리즈혹은데이터프레임.함수()  
넘파이: np.함수(시리즈혹은데이터프레임)  
'''  
np.mean():    평균  
np.average():    평균 (가중치를 매개변수로 부여할수도 있다.)  
np.median(): 중앙값  
np.min(): 최솟값  
np.max(): 최댓값  
np.quantile(): 분위수  
np.var(): 분산. 다만 판다스는 n-1으로나누는데, 즉 표본분산을 구하는데 넘파이는 n으로 나눈다.   
np.std(): 표준편차. 마찬가지로 판다스는 표본분산의 표준편차, 즉 n-로 나누고 제곱근 구하는데 넘파이  는 n으로 나누고 제곱근 구한다.   

## 02. 분포 요약하기

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
import numpy as np  
import matplotlib.pyplot as plt  
import seaborn as sns  
plt.figure(figsize = (x축인치, y축인치))  

plt.scatter([x축배열], [y축배열]): 산점도  
plt.scatter([x축배열], [y축배열], alpha = 0.1)  
#alpha = 0.1: 투명도 조절   

plt.hist([데이터배열], bins = 5): 히스토그램  
#bins = 5: 5개의 구간으로 나누기  
np.histogram_bin_edges([데이터배열], bins = 5): 히스토그램의 구간경계를 배열로 출력  
plt.yscale('log'): 한구간의 빈도수가 너무커서 다른구간이 안보일때 log스케일로 y구간 변환  
plt.xscale('log'): 마찬가지로 x축 log스케일 변환  
plt.xlim(하한, 상한): x축 시각화 범위 제한  
plt.ylim(하한, 상한): y축 시각화 범위 제한  

plt.boxplot(df[['x축변수', 'y축변수']] 혹은 열이 2개인 데이터프레임):  
첫번째열은 x축, 두번째열은 y축으로 해서 박스플롯그리기  
plt.boxplot(df[['x축변수', 'y축변수']], vert = False)    #수평 그리기  

맷플롯립 기타 시각화 함수 종류  
plt.plot(x, y): 선그래프: 변화와 추세를 보여줄 때  
plt.bar(x, y): 막대그래프: 범주별 빈도나 크기를 보여줄 때  
plt.barh(x, y): 수평막대그래프  
plt.pie(데이터): 원형그래프: 전체에서 차지하는 비율을 보여줄 때   


맷플롯립 기타 꾸미기 및 보조 함수  
plt.title('제목'): 그래프의 제목 표기  
plt.xlabel(): x축의 이름 표기  
plt.ylabel(): y축의 이름 표기  
plt.legend(): 범례(어떤 범주의 그래프인지 알려주는 표) 표기  
plt.grid(True): 배경에 격자 표기  
plt.subplot(행, 열, 인덱스): 총 몇행, 총 몇열의 서브플롯인지, 그리고 인덱스 옵션을 통해 현재 작업  할 부분을 설정  

plt.show()  

# 2️⃣ 수행 인증

<!-- 교재에서 안내된 과정을 직접 실행해본 뒤, 진행 결과가 보이도록 3장 이상의 스크린샷을 캡처하여 아래에 첨부해주세요.-->
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/27d3064c-f4e7-40f4-bcc3-66b0c4856a6e" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/d46214ca-d443-40bb-af07-ff423b6b3139" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/775c1588-8d48-4d88-aff6-dfc140631876" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/77d06d7c-80f2-4658-815e-b4cee7fc2649" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/0d2d9bde-7164-4ee6-be48-7f41dbec24da" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/012124fa-f22d-470a-a08d-580be1bec02b" />




# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 이번 주차에는 확인문제 대신 실습 과제를 진행합니다. 캐글에서 원하는 데이터셋을 선택하여 기술통계를 계산하고, 다양한 시각화를 수행해보세요.
작업은 코랩에서 진행한 뒤, 코랩 링크를 아래에 첨부해주세요.**

```
여기에 코랩 링크를 첨부해주세요!
(제출 전, 코랩의 공유 설정을 ‘링크가 있는 모든 사용자가 보기 가능’으로 변경했는지 반드시 확인해주세요.)
https://colab.research.google.com/drive/16n01Nr5FJA-gHysM1yndIxMpxL6Jnb23#scrollTo=2sJUc8T1Pqqm
```



### 🎉 수고하셨습니다.
