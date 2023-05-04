# 브라질 이커머스(Olist) 평점 상승을 위한 데이터 분석

## 프로젝트 개요

기관: 멋쟁이사자처럼 AI스쿨 부트캠프 프로젝트 (6인 팀)

기간: 2023.01.06 ~ 2023.01.12 

사용한 기술: Python, Pandas, Seaborn, Tableau, Google spreadsheet

발표자료: [구글 슬라이드 링크](https://docs.google.com/presentation/d/1sIeQglB-lzw73C9Sa2GKZRmz3cX5GMZO/edit?usp=sharing&ouid=102129209336474301034&rtpof=true&sd=true)

## 담당 역할

데이터 전처리(20%) → 가설 설정 및 검증(20%) → 태블로 시각화 (100%)

## 사용한 데이터 소개

Brazilian E-Commerce Public Dataset by Olist
브라질 소재의 Olist라는 이커머스 기업의 고객, 판매자, 주문, 결제, 제품, 평점 테이블을 포함하고 있다.
출처: [https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

## 주제 소개

### 문제 상황

Olist 기업의 **CS 담당자**는 어떻게 하면 **고객 만족도**를 개선할 수 있는지 데이터 분석을 의뢰했다.
**Olist의 데이터 분석 조직**이라고 가정하고, 데이터 분석 및 해결 방안을 제시하는 것이 목표이다.

## 데이터 분석

### 분석 배경

Olist의 경우 고객이 각 주문에 대해 **1~5점까지 평점**을 매기고, 그에 대한 **텍스트리뷰**를 작성할 수 있다.
![image](https://user-images.githubusercontent.com/114198737/235694665-384574b1-42de-4d8e-83fc-2d855b07157e.png)

- 전체 평점의 평균은 4.03점으로, 4점 이상을 긍정적인 고객 집단, 1~3점을 부정적인 고객 집단으로 구분하여 분석했다.
- 평점 1점을 남긴 고객(14,546 건) 중 77.7%의 고객(11,314 건)이 텍스트 리뷰를 작성했다.

![image](https://user-images.githubusercontent.com/114198737/235694730-9dcc9572-781a-4a2a-a558-57c635aa4dce.png)
긍정 리뷰 고객과 부정리뷰 고객의 텍스트 리뷰 단어 조합 시각화

부정적인 평점(1, 2, 3 점)을 준 고객과 긍정적인 평점(4, 5점)을 준 고객의 텍스트리뷰에서 자주 등장하는 단어 조합을 분석한 결과, 부정적인 리뷰의 내용은 not receive, not delivered, not arrived 등 배송을 받지 못한 의미가 대부분으로, 긍정 적인 리뷰의 before deadline, arrive early, within deadline과는 상반된 것을 확인할 수 있다.

#### > 즉, 배송과 평점 사이에 연관성이 있을 것이라고 가정하고 관련된 가설을 분석했다.


### 분석 결과

1. **배송 기간이 길수록 평점이 낮다**
![image](https://user-images.githubusercontent.com/114198737/235694891-65749e62-acaf-48fa-b734-5a19c26b44b0.png)
- 배송시간과 평점이 반비례하는 분포를 확인할 수 있다.
    
2. **배송 상태에 따라 평점이 달라진다**

![image](https://user-images.githubusercontent.com/114198737/235694971-08243c16-4eed-4e6c-8deb-6c178299ba68.png)
- 배송 완료를 제외한 주문 상태에서는 평점 1점의 빈도가 매우 높다.
- 다만 전체 주문의 98%가 배송완료 상태이다

→ 배송이 완료되지 않은 경우에도 olist는 중간 설문조사 메일을 통해 평점을 수집한다. 

→ 이미 평점을 매긴 이후에 배송 완료로 상태가 변경되었을 가능성이 높다.

3. **예상 배송일과 실제 배송일 사이의 오차가 커서 만족도가 낮을 것이다.**
![image](https://user-images.githubusercontent.com/114198737/235695105-c5f17105-2c87-41ba-8b78-4566093a878b.png)
- 예상 배송일과 실제 배송완료일이 늦은 경우, 부정적인 평점을 남긴 비율은 65.3%로 비교적 높다.
- 다만 예상 배송일 내에 배송된 경우가 93%로 훨씬 비율이 높아, 배송 예측 개선의 시급성은 낮다고 판단하였다.

4. **지역에 따라 배송 기간과 만족도가 차이가 날 것이다.**
![image](https://user-images.githubusercontent.com/114198737/235695230-355d4645-3835-413b-8ef6-8793b7c72c4c.png)
- 브라질의 지역을 5개 지방(북부(North), 북동(North-east), 중서(Mid-west), 남동(Southeast), 남부(South))으로 구분하여 배송 기간과 평점을 분석했다.
- 배송 기간은 남동, 남부, 중서, 북동, 북부 지역순으로 길어지며, 부정적인 평점을 준 비율도 비례하여 증가하는 양상을 보인다.

### 해결 방안

1. 물류 전문 업체와 파트너쉽 구축
2. 북부 지역 판매자 수 확보
3. 배송 CS 전담 부서 개설
---

1. 물류 전문업체와의 파트너쉽 구축
브라질의 넓은 면적을 고려하면 자체물류센터를 확보하기에는 천문학적인 비용과 많은 시간을 투자해야할 것이므로, 따라서 자체물류센터를 확보하기 보다는 물류 전문 업체와 협업하여 파트너쉽을 구축한다.

2. 북부 지역(North, Northeast)의 판매자 모집
![image](https://user-images.githubusercontent.com/114198737/235695778-be68c3cf-aac4-4f6d-b9f4-ae8b3e989ce9.png)
배송 시간 단축을 위해 소비자와 판매자 간 물리적인 거리를 줄이는 것이 목적이다. 판매자와 구매자수가 거의 동수에 가까운 남부와 달리 북부, 북동부 지역은 **판매자 수 1인 대비 구매자 수가 각각 64명, 19명**으로 매우 높은 편이다. **동일 지역 내 거래 건의 경우 평균 배송기간이 짧으므로(9.9일)** 북부 지역 판매자 수가 증가할 경우 해당 지역 구매자에게 더 짧은 배송 기간을 제공할 수 있을 것이다. 북부 지역 판매 계약 수수료 감면 이벤트 등을 시행하여, 북부 판매자 유입을 늘려야 한다.

3. 배송 관련 문의 전담 부서 개설

부정적인 평점을 올리기 위해서는 배송 관련 CS를 해결하는 것이 최우선으로 판단된다. 여러 개의 물건을 주문한 경우, 분리 배송이 되어 일부 제품을 늦게 받거나 설문 조사 시점에서 아직 받지 못했다는 리뷰가 많았다. 배송관련 문의를 집중 담당하는 부서 개설하여 개별 제품 배송 추적 및 안내에 집중한다.


## 프로젝트 회고

**[문제인식 및 극복과정]**

1. 불균형 데이터로 인해 예측한 가설과 다른 결과가 나와 결론을 도출하는데 어려움이 있었다.

**Funnel 분석 결과**
![image](https://user-images.githubusercontent.com/114198737/235695871-2cfe5eb9-ab06-455d-8eb2-69784611ca36.png)

→ 리텐션 분석 결과 2번째 구매율이 3%로 극단적인 결과가 나타났다.

→ 원인을 파악한 결과, 데이터셋 자체에 VIP 데이터가 개인정보 이슈로 삭제되어 있었다는 점을 알게 되었다. 

→ 따라서 재구매율에 관한 문제는 배제하고 평점과 배송 중심으로 데이터 분석을 진행하게 되었다.

2. 제품의 카테고리가 중복되고 의미가 불분명한 것이 많다.

→ 73개의 카테고리를 국내 이커머스 쿠팡의 카테고리를 참고하여 15개 카테고리로 재분류하였다.
![image](https://user-images.githubusercontent.com/114198737/235695983-03dabd15-d832-4163-b8f8-1091f6ba3780.png)


3. 도시 컬럼의 데이터가 중복되어 있어 지역 시각화를 하는데 적합하지 않다. (city의 고유값 개수 `4119`개)

→ 도시명 대신 `도시 코드`와 브라질 특성 자료를 토대로`5`개 지역으로 구분하여 분석했다.
![image](https://user-images.githubusercontent.com/114198737/235696061-118995f0-21ef-4b97-9521-6bea490c0cc0.png)


**[개선할 점]**

- 팀원 간 가설을 나누어서 검증하고, 주제 설정으로 인해 시간이 부족하다 보니, 그래프 간 색상이나 형식을 통일하지 못하여 보고서의 완성도에 아쉬움이 남는다. → `전체 시각화의 톤 맞추기`
- 정확한 데이터 명세서가 존재하지 않고, 영문으로 되어있다보니, 각 컬럼명 또는 고유 값에 대해 의미가 불분명한 경우가 발생했다. → `실제 비즈니스 데이터를 분석한다면, 자사의 서비스 전반에 대해 이해도가 높아야 하며, 사용하는 용어간 통일과 정의가 필요하다는 것을 느꼈다.`
- `회귀분석 등 통계 기법을 통해 해결 방안에 대한 실질적인 이득이나 효과를 계산해보기`

---

- 참고자료
    1. [E-Commerce Sentiment Analysis: EDA + Viz + NLP ✍ | Kaggle](https://www.kaggle.com/code/thiagopanini/e-commerce-sentiment-analysis-eda-viz-nlp/notebook)
    2. [Geospatial Analysis of Brazilian E-Commerce | Kaggle](https://www.kaggle.com/code/andresionek/geospatial-analysis-of-brazilian-e-commerce)
    3. [Olist Store - Brazilian e-commerce public dataset | Tableau Public](https://public.tableau.com/app/profile/marien.abeli/viz/Olist_16207865690910/Story1)
    4. [해외시장보고서-관세,규제,마케팅 등 수출에 필요한 모든 무역정보를 통합해서 제공하는 국가무역정보포털 (tradenavi.or.kr)](http://www.tradenavi.or.kr/CmsWeb/viewPage.req?idx=PG0000001352&reportId=RP00000000014456&viewType=detail&query=%EC%86%8C%EB%B9%84%EC%9E%90%20%EA%B5%AC%EC%84%B1%EC%9D%84%20%ED%86%B5%ED%95%B4%20%EB%B3%B8%20%EB%B8%8C%EB%9D%BC%EC%A7%88%20%EC%86%8C%EB%B9%84%EC%8B%9C%EC%9E%A5)
    5. 소비자 구성을 통해 본 브라질 소비시장, 한국무역협회 (2018)
    6. [브라질의 인구 - 위키백과, 우리 모두의 백과사전 (wikipedia.org)](https://ko.wikipedia.org/wiki/%EB%B8%8C%EB%9D%BC%EC%A7%88%EC%9D%98_%EC%9D%B8%EA%B5%AC)
