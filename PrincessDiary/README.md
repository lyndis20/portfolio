# 일기 텍스트 분석 AI 서비스

## 프로젝트 개요

AI스쿨 부트캠프 파이널 프로젝트 5인팀

주제: **블로그 일기 분석 서비스 (해시태그 추출 & 감정 분석 & 토픽 모델링)**

기간: 2022.12.26 ~ 2023.01.05 (2주)

사용한 언어 및 기술 스택

python, pandas, matplotlib, seaborn, tensorflow, github, Selenium, BeautifulSoup

## 담당 역할

**기술적 기여도**

- 데이터 전처리(라벨링)
- KR-wordRank 키워드 추출
- 감성 분석 (KcElectra 모델 활용)
- 모델링 결과 시각화

**비기술적 기여도**

- 블로그 운영 경험을 통해 도메인 지식 적용
- PPT 제작
- 대시보드 시연 및 영상 편집

## 프로젝트 소개

[**최종 주제]**

**일기 분석을 통한 요약 태그 자동 생성, 토픽 분류 & 감정 변화 트래킹**

→ 일기 내용을 **요약한 태그**를 통해 쉽게 특정 일기를 빠르게 찾고, **비슷한 주제끼리** 모아서 볼 수 있다.

→ 또한 일기 내용안에 포함된 **감정을 자동으로 파악해서 시각화**해서 보여준다.

**[프로젝트의 진행 배경]**

일기 작성에는 **“자기 객관화”, “안정적인 감정 유지”, “자아 효능감 상승”**

**1️⃣ 일기 요약 태그 추출** , **2️⃣ 감성 분석 및 감정 분류** , **3️⃣ 토픽 모델링** 등 일기 작성 및 검색을 도와줄 수 있는 서비스를 구현하고자 하였다.

**[사용한 데이터]**

실제로 개인의 일기를 다량으로 수집하기 어렵기 때문에 대안으로 **네이버 블로그 주간일기 데이터**를 활용했다.

- 네이버 블로그 `#주간일기챌린지`  `#블챌`  `#일상`  `#일기`  태그된 게시물 크롤링 (selenium 활용)

## 프로젝트 프로세스
<img width="1438" alt="p1" src="https://github.com/lyndis20/portfolio/assets/114198737/d8fdc9a0-83fc-4f68-8aaf-7564415fe838">

![p2](https://github.com/lyndis20/portfolio/assets/114198737/251c89e6-92d4-49c0-8840-5743cb16e7a8)

### [프로젝트 수행과정]

1. 네이버 블로그 데이터 수집 `#주간일기챌린지`
2. 자연어 데이터 EDA 및 전처리 (문장 전처리, gensim 유의어 분석, 워드클라우드, 라벨링)
3. 모델 제작 
    - 태그 추출기 (KeyBert) `평가산식 RDASS`
    - 토픽 모델링 (LDA, berTOPIC)
    - 감성 분석 (KcELECTRA)
4. 태그 추출 모델 평가 및 데이터 전처리를 통한 성능 개선
5. Streamlit을 활용한 웹 대시보드 구축


### **[분석 결과]**

사전 설문조사를 통해 일기 사용 행태와 원하는 일기 앱 서비스를 조사하였다.
<img width="1290" alt="image" src="https://github.com/lyndis20/portfolio/assets/114198737/070583e6-f93a-4b79-b06e-3c88161cacf4">

**해시태그 Before**

기존 블로그 게시물에 원래 포함된 해시태그를 살펴보면, 내용과 관련없이 홍보와 이벤트 참여를 위한 일반적인 내용의 해시태그가 대부분인 것을 확인할 수 있다. (ex. 서이추 환영, 주간일기, 일상 등)
![w1](https://github.com/lyndis20/portfolio/assets/114198737/ca055ca7-9cf0-4e93-bc65-60c5c609ce8a)
기존 블로그 해시태그 워드 클라우드

**해시태그 After (내용 요약 반영)**

KeyBert를 활용한 키워드 추출 모델을 통해 생성한 해시태그는 **본문의 내용을 더욱 잘 요약해서 반영해주고 있음**을 확인할 수 있다. 아래와 같은 해시태그를 통해 비슷한 주제의 일기를  모아서 확인할 수 있다.
![w2](https://github.com/lyndis20/portfolio/assets/114198737/11f08575-e700-44a2-94c2-af888dbe34f8)
팀에서 생성한 내용 요약이 반영된 해시태그 워드 클라우드

## 프로젝트 결과물
[YOUTUBE 시연 동영상 확인하기]
https://www.youtube.com/watch?v=wHMYT7pdk0g

[결과물 서비스화면]
스트림릿을 활용한 웹페이지
[ 일기 작성 및 제출 ]
[ 일기로부터 태그와 주제 추출 ]
[ 일기로부터 감정분석한 결과 ]
[필요 시 수정 후 일기 저장 ]
[ 태그 선택을 통해 과거의 일기 빠르게 탐색 가능 ]


## 프로젝트 회고

**[문제 상황 및 회고]**

- 현실세계의 문제를 해결하려고 할 때, **정답 설정의 문제와 평가 산식의 문제**를 동시에 느꼈다.
    - 요약 모델에 많이 사용하는 ROUGE가 아닌 비교적 최신 등장한 RDASS 평가산식을 적용해 평가하면서 참고자료가 많지 않아 직접 코드를 만들어 사용했다.
    - “평가 점수가 무조건 높은게 좋다.”가 아니라 몇 점이 어느정도 의미하는지 계속 파악하면서 우리 도메인에 맞게 성능을 올리기 위해 방법을 찾는 것이 중요하다는 것을 배웠다.
- **일기 관련 설문조사**를 활용하여 이용자 친화적으로 만들 수 있어 의미있었다.
- 블로그 글을 하나하나 뜯어보면서 작성자의 특성, 글의 특성을 이해하고, 해시태그의 특성을 발견하여 정답 데이터를 직접 라벨링 해본 것이 의미있었다.
- 팀원들에게 기술적인 것뿐만 아니라 분석 결과 해석, 정리, 적극적인 소통, 끝까지 완성도를 높이는 노력 등 소프트 스킬까지 정말 많은 것을 배우고, 단시간에 성장할 수 있었다.

**[개선할 점]**

- 여러 개의 모델을 쓰기 보단 하나의 모델 내부에 기능을 연결시켜 구현해보기
- 블로그 글을 좀 더 다양한 시점에서 수집하고, 글 내에서 전환점 (날짜, 기호 등)을 파악해서 전처리해보기
- 신조어, 유행어 등을 별도로 사전 만들어서 태그에 반영하기

## 참고자료
- KcELECTRA    
    [GitHub - searle-j/KOTE: Korean Online That-gul Emotions Dataset](https://github.com/searle-j/kote)
- KeyBERT
    [점프 투 파이썬](https://wikidocs.net/159467)
- LDA
    [점프 투 파이썬](https://wikidocs.net/30708)
- RDASS
    [텍스트 요약 모델 성능 평가를 위한 새로운 척도, RDASS를 소개합니다.](https://kakaoenterprise.github.io/deepdive/210729)
    [[논문리뷰] Reference and Document Aware Semantic Evaluation Methods for Korean Language Summarization (1/2)](https://velog.io/@ckstn0777/%EB%85%BC%EB%AC%B8%EB%A6%AC%EB%B7%B0-Reference-and-Document-Aware-Semantic-Evaluation-Methods-for-Korean-Language-Summarization)
- KR-WordRank: https://github.com/lovit/KR-WordRank
