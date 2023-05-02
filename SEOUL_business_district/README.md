# 서울시 상권 분석 대시보드 제작 프로젝트

## 프로젝트 개요

AI스쿨 부트캠프 미드프로젝트 (EDA, 대시보드 제작) 6인 팀
주제: 예비창업자, 소상공인을 위한 서울시 상권분석 서비스 제작
기간: 2022.10.19 - 2022.10.24 (6일)
기술: Python, Pandas, Matplotlib, Seaborn, Folium, Streamlit, Tableau
![image](https://user-images.githubusercontent.com/114198737/235697869-d1cfc305-4d41-427d-b891-72e0516f9ffb.png)
깃허브 링크: https://github.com/lyndis20/ai7_Mid-Project

## 담당 역할

- 데이터 전처리 및 EDA (11개 데이터셋 중 점포 수, 행정동별 좌표, 지도 시각화 데이터)
- Folium을 활용한 지도 시각화
- 대시보드 화면 기획 (Figma)
- 프로젝트 발표

## 프로젝트 소개

**[프로젝트의 진행 배경]**

개인이 창업을 하려고 할 때, 가장 큰 문제점 중 하나는 **정보 수집의 어려움**이다. 창업을 하기 위해선 업종, 입지, 인구, 주변 상권, 매출 등 고려해야할 점이 많은데, 개인 스스로 이를 조사하는 데엔 많은 시간과 비용이 수반되기 때문이다. 따라서 관련 정보를 **대시보드 형태**로 개인 창업자에 제공할 수 있는 서비스를 제작하고자 하였다. 

**[프로젝트의 목표]**

**예비 창업자를 위한 서울시 상권 분석 보고서를 제공하는 웹서비스 만들기**
- 지도 형태로 한 눈에 지역별, 업종 별로 상권 정보를 비교할 수 있다.
- 타 서비스와 달리, 뉴스 검색을 통해 최신 동향을 함께 얻을 수 있도록 구성했다.

**[활용 데이터]**

1. 공공 데이터

서울시 골목 상권 분석 데이터(http://data.seoul.go.kr/dataList/3/literacyView.do)의 서울 상권 관련 각종 지표를 제공하는 18개 데이터셋 중 
업종 분류, 점포 수, 추정 매출, 인구 통계, 생활 인구 데이터를 활용했다.

2. 네이버 뉴스 크롤링 데이터

## 프로젝트 프로세스

![image](https://user-images.githubusercontent.com/114198737/235698094-bccf086c-74b3-49e2-adf4-893a78f477c8.png)

---


## 📊 분석리포트 페이지
![image](https://user-images.githubusercontent.com/114198737/235698834-84080724-6a67-497e-b403-7e589992a3bd.gif)
대시보드 캡쳐 gif 이미지

> Sidebar
- 분석 리포트, 관련 뉴스 검색 : 상단에 두 개의 페이지를 제공하여 이동할 수 있다.
- 창업자를 위한 분석 보고서 :
- page 가이드 : 각 페이지에 대한 간단한 이용방법을 제공한다
- 검색 : 사용자가 분석하고자 하는 ”시군구 / 행정동 / 업종”을 직접 선택할 수 있다.

---

> Folium 시각화
- 사이드바에서 선택한 시군구의 행정동으로 시점을 이동하여 지도를 보여준다.
- 원형 마커 크기를 통해 선택한 구 내에 업종별 점포 수 분포를 나타낸다.
- 원을 클릭하면 해당 행정동 내에 선택한 업종의 점포 수가 몇 개인지 알 수 있다.

---

> 상세 분석 리포트
- 지도 하단에 상세 분석 리포트를 제공한다. (매출 분석, 생활인구 분석, 거주인구 분석)
- 사용자가 선택한 업종의 매출에 대해 연령대 및 성별 등으로 나누어 시각화 자료를 제공한다.
- 사용자가 검색했던 지역의 생활인구 / 거주인구를 연령대 및 성별 등으로 나누어 시각화 자료를 제공한다.

> 뉴스 검색 페이지
- 궁금한 키워드의 뉴스를 검색하여 모아서 확인해볼 수 있다.

---


## 프로젝트 회고


**[문제인식]**
1. 데이터셋 합칠때(merge) 중복 제거를 하지 않아 데이터가 무한 증식했던 문제가 발생했다.
2. Folium 시각화를 위한 rawdata 전처리 과정에서  1️⃣ 원본 데이터의 특정 지역의 좌표 데이터 누락으로 수작업으로 데이터 입력 2️⃣ ”행정동명”을 기준으로 합쳐서 중복 발생 3️⃣ 원본데이터 좌표값 오류로 데이터셋 변경 등 계속해서 수정 사항이 발생했다.
3. Folium을 처음 다뤄보았기 때문에, 원하는 기능을 어떻게 구현해야할지 검색하고, 적용하는 과정이 어려웠다.
4. 첫번째 팀 프로젝트 경험으로, 파일 관리의 어려움을 느꼈다 

**[극복과정]**
1. 하나의 검색 결과에 한정되기 보다는 더 많은 참고자료를 찾아보았다. 처음부터 사용하려고 하는 데이터셋이 정확한 정보인지 잘 파악하고 선택하는 것도 중요하다는 것을 배웠다.
2. Folium 시각화를 할 때, 무작정 다른 코드를 따라하기보다, 각 파라미터 값이 무슨 결과를 만들어내는지 하나씩 이해하고 적용해보았다.
3. 팀원간 파일 저장명에 규칙을 부여했다. 날짜와 수정 번호를 추가해서 어떤 것이 최신 파일인지 확인하기 용이하도록 했다. 그리고 개인 깃허브 리포지터리를 만들어서 빠르게 파일 내용을 확인하고 공유할 수 있도록 했다.

**[해결과제]**

- Folium Map Circle marker 크기 조절, 태블로 대시보드로 구현해보기 (완료)

### **태블로로 구현한 지도 시각화 (2023.04)**

- 동일한 지도 시각화를 Python Folium과 태블로 대시보드로 구현해보면서 차이점을 느낄 수 있었다.
- 줌인 줌아웃을 하면서 Clustering하여 보여주는 기능은 Folium이 우수하다.
- 비주얼적으로 편집할때 크기나 색상을 미세하게 조정하기에는 태블로가 우수하다.
![image](https://user-images.githubusercontent.com/114198737/235699374-5d298997-e2a5-4f43-afe2-79aa63693e7e.png)


## 프로젝트 참고자료
   
**[데이터분석]**
- 2015 서울 유동인구조사 보고서(NIA 한국정보화진흥원, 서울특별시)
- ‘창업, 상권분석 방법 알면 쉽다!’ [http://www.fcmedia.co.kr/news/articleView.html?idxno=20901](http://www.fcmedia.co.kr/news/articleView.html?idxno=20901)
- 우리마을가게 상권분석 서비스 [https://golmok.seoul.go.kr/main.do](https://golmok.seoul.go.kr/main.do)
    
**[폴리움]**    
1. Streamlit Folium: [https://github.com/randyzwitch/streamlit-folium](https://github.com/randyzwitch/streamlit-folium)
2. Choropleth Map (지도 경계표시)
    - [https://dailyheumsi.tistory.com/m/144?category=854906](https://dailyheumsi.tistory.com/m/144?category=854906)
    - [https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=da0097&logNo=222327643758&categoryNo=28&proxyReferer=](https://m.blog.naver.com/da0097/222327643758)
3. 마커클러스터링: [https://blog.naver.com/PostView.naver?blogId=life4happy&logNo=222161099861&categoryNo=34&parentCategoryNo=0](https://blog.naver.com/PostView.naver?blogId=life4happy&logNo=222161099861&categoryNo=34&parentCategoryNo=0)
    
**[스트림릿]**
- Streamlit Components - Community Tracker : [https://discuss.streamlit.io/t/streamlit-components-community-tracker/4634](https://discuss.streamlit.io/t/streamlit-components-community-tracker/4634)
    
### 데이터셋 출처
- 시군구 geojson파일 : [https://github.com/southkorea/southkorea-maps/](https://github.com/southkorea/southkorea-maps/)
- 행정동 좌표 데이터 : [https://github.com/cubensys/Korea_District](https://github.com/cubensys/Korea_District)
- 상권분석 데이터 : [http://data.seoul.go.kr/dataList/3/literacyView.do](http://data.seoul.go.kr/dataList/3/literacyView.do)
