# 데이터분석 2주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=s_-VvTLb3gs&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=4
https://www.youtube.com/watch?v=Il6L8OtNFpc&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=5
-->


## DataAnalysis_2nd_TIL

### 2장 데이터 수집하기
#### 01. API 사용하기
#### 02. 웹 스크래핑 사용하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | 🍽️         |
| 4주차 | p.222~279 | 🍽️         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. API 사용하기

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
API: 웹페이지를 요청하면 이를 전송하는 형식

*API를 실현하기 위한 통신 규약 중 하나인 HTTP - 웹 기반 API  
-웹 브라우저가 웹 페이지를 웹 서버에게 요청, 웹 서버는 웹 페이지를 웹 브라우저에게 제공.  
-HTTP 프로토콜은 텍스트 기반으로 동작하기 JSON, XML을 전송받으면 기본적으로 문자열 형식

HTTP, 즉 웹 기반 API로 제공 받는 데이터 형식의 파일  
-CSV  
-JSON  
-XML  
____________________________________________________________  
JSON: 딕셔너리와 리스트를 중첩해 놓은 데이터 형식  
EX)  
d = '''  
[{'name': '혼자 공부하는 데이터 분석', 'author': '박해선', 'year': 2022}, {'name': '혼자 공부하는 머신러닝 + 딥러닝', 'author': '박해선', 'year': 2020}]   
'''  
import json  
import pandas as pd  
json.dumps(): JSON 텍스트로 리턴  
json.loads(): JSON 텍스트를 파이썬 객체, 즉 딕셔너리로 리턴  
pd.read_json(): JSON 텍스트를 데이터프레임으로 리턴  
pd.DataFrame(): JSON 파이썬 객체를 데이터프레임으로 리턴  
____________________________________________________________  
XML: 부모, 자식 엘리먼트들이 시작태그와 종료태그를 기준으로 계층구조를 이루면서 정보를 표현하는 데이터 형식   
EX)  
'''  
<books>  
    <book>   
        <name> 혼자 공부하는 데이터 분석 </name>  
        <author> 박해선 </author>   
        <year>2022</year>   
    </book>  
    < book>  
        <name>혼자 공부하는 머신러닝 + 딥러닝 </name>   
        <author> 박해선 </author>   
        <year>2020</year>   
    </book>  
</books>  
'''  

import xml.etree.ElementTree as et  
import pandas as pd  
d = et.fromstring(): XML 텍스트를 파이썬 객체, 즉 클래스로 리턴  
d.tag: 부모 엘리먼트  
d.findtext(): 매개변수에 입력된 열에 해당하는 자식 엘리먼트 리턴  
d.findall(): 자식 엘리먼트 여러개 리턴  
pd.read_xml(): XML 텍스트를 데이터프레임으로 리턴  
____________________________________________________________  
파일 가져오는 법  
단순히 CSV, JSON, XML 다운로드 받기   
VS  
파이썬에서 requests 패키지로 API 호출해서 CSV, JSON, XML받기  

*파이썬으로 API 호출하기   
import requests  
import pandas as pd   
url = '~~~~~'            #API 호출 URL을 매뉴얼에서 찾아보기  
r = requests.get(url)           #Response 클래스 객체로 파일 리턴  
data = r.json()      #JSON텍스트를 파이썬객체, 즉 딕셔너리로 리턴  
df = pd.DataFrame(data)       #JSON 파이썬 객체를 DF로 리턴  
df.to_json()          #데이터프레임을 JSON 텍스트로 리턴  

## 02.웹 스크래핑 사용하기

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
웹 스크래핑(웹 크롤링): 프로그램을 통해 웹사이트에서 웹사이트로 페이지를 옮겨 가면서 데이터를 추출하는 작업 

1: 패키지 불러오기  
import requests   
from bs4 import BeautifulSoup  
2: 페이지 HTML 호출하기( isbn에 대한 사이트 HTML 텍스트 리턴)  
r = requests.get(url.format(isbn))  
3: HTML 파싱  
soup = BeautifulSoup(r.text, 'html.parser')  
4: 개발자 도구에서 이동할 웹페이지 링크를 찾기. 첫번째 매개변수는 찾을 태그, attrs 매개변수는 태그 속성을 딕셔너리로 지정  
prd_info = soup.find('a', attrs = {'class': 'gd_name'})   
5: 이동할 페이지 HTML 호출하기  
r = requests.get(url + prd_info['href'])  
반복  

*apply 매서드    
page_count = top10_books.apply(get_page_cnt2, axis = 1)    
#top10_books의 값이 모두 get_page_cnt2 함수에 적용됨  

*merge 매서드  
top10_with_page_count = pd.merge(top10_books, page_count, left_index = True,right_index=True)  
#데이터 프레임 합치기  
# 2️⃣ 수행 인증

<!-- 교재에서 안내된 과정을 직접 실행해본 뒤, 진행 결과가 보이도록 4~6장의 스크린샷을 캡처하여 아래에 첨부해주세요.-->

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/4d7b0b3f-cb2c-4a31-8ffc-563c1260fe87" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/bb42858c-dd9e-4bfc-bdf2-65243821ec3b" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/8a6290b7-9c14-4d68-8cc3-55780b1904c4" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/56010466-739a-4474-be52-2887a5375594" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/04a216d0-8352-4fdb-808b-f71167fd596f" />
<br>
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/ea10e2cb-929b-4bb7-901f-f86d8a5770ce" />


# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 중 BeautifulSoup 외에 웹 스크래핑에 사용할 수 있는 파이썬 패키지로 가장 적절한 것은 무엇인가요?**

```
1️⃣ NumPy  
2️⃣ Scrapy  
3️⃣ Matplotlib  
4️⃣ Scikit-learn  
```

```
Scrapy
코랩에서는 사용할 수 없지만 웹 스크래핑이 가능한 또 하나의 패키지이다. 
```



### 🎉 수고하셨습니다.
