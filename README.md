# Dacon_제주도 도로 교통량 예측 AI 경진대회
데이콘에서 주관하는 제주도 도로 교통향 예측 AI 경진대회의 데이터를 활용하여 분석하였습니다.

### 경진대회 소개

![슬라이드2](https://user-images.githubusercontent.com/50400392/211268231-dd9bf5d8-1f22-406f-9b49-e9753f25c67c.PNG)

### 데이터 분석 프로세스
 
제주도 도로 교통량 데이터 분석 프로세스는 다음과 같습니다.

1) EDA
2) 데이터 전처리
3) Feature Engineering
4) 모델링 및 앙상블

### Data Description

![슬라이드3](https://user-images.githubusercontent.com/50400392/211268855-453ce124-c048-4c27-92cf-684ca7c8ebc2.PNG)

우측의 외부 데이터는 분석에 있어서 추가적으로 수집한 데이터를 의미합니다.  
공공 데이터들과 위치 정보 API를 활용하여 외부 데이터를 수집하여 활용하였습니다.  

### EDA

![슬라이드4](https://user-images.githubusercontent.com/50400392/211269486-2a37079f-98b2-440c-bd44-d6e1da4ed67e.PNG)

EDA를 통해 분석에 필요없는 변수를 찾거나 데이터가 소실된 기간 및 결측치 존재 여부를 파악할 수 있었습니다.  

### 데이터 전처리

![슬라이드5](https://user-images.githubusercontent.com/50400392/211269755-42272022-51c1-465d-90ad-5d4649cabcf0.PNG)

EDA를 통해 도로명의 결측치가 '-'로 표기되어 있는 것을 관찰할 수 있었습니다.  
도로명 결측치를 처리하기 위해 위치 정보 API를 활용하였으며 위도와 경도를 이용하여 도로명을 추출하여 전처리하였습니다.  

### Feature Engineering

내부 / 외부 데이터들을 활용하여 여러 개의 파생변수를 생성하였고 2개의 파생변수에 대해 소개하고자 합니다.  

#### 가설1. 평일과 휴일에 따라 교통 혼잡도가 다를 것이다.

![슬라이드6](https://user-images.githubusercontent.com/50400392/211270685-7391e572-c5a0-474b-8e49-eb445995bcf8.PNG)

#### 가설2. 날씨에 따라 교통 혼잡도가 다를 것이다.

![슬라이드7](https://user-images.githubusercontent.com/50400392/211270675-c6c8fe0c-21fb-4462-901d-f5bab441a271.PNG)

### Feature Selection

Feature Engineering를 통해 최종적으로 모델링에 사용한 변수들을 아래와 같습니다.  
위에서 소개하지는 않았지만 EDA 과정에서 도로의 길이나 제주공항 주변 도로, 권역 별 도로에 따라 차이를 보였기 때문에 추가적으로 파생 변수를 생성하였습니다.  
또한, 가설 설정을 통해 관광객 수, 날씨 변수를 추가하였습니다.  

![슬라이드8](https://user-images.githubusercontent.com/50400392/211270679-2497039b-2f96-4f10-9477-30d2df774644.PNG)

### 모델링 및 앙상블

모델링 및 앙상블에서는 2가지 방법을 사용하였고 더 높은 성능을 보인 auto ML을 사용하였습니다.  
기존에 시도한 방법과 auto ML 방법에 대해 설명합니다.  

#### 1. 기존에 시도한 방법

- 숫자형 데이터들을 Data Scaling 및 카테고리형 데이터들의 인코딩을 진행
- 모델 선정 ('LightGBM', 'Xgboost', 'CatBoost')
- Optuna를 이용한 하이퍼 파라미터 조정
- Stacking 앙상블을 활용하여 앙상블 모델 생성

#### 2. Auto ML

![슬라이드9](https://user-images.githubusercontent.com/50400392/211270683-0ecd9e9c-4e6a-43f9-b529-a03dce313a9f.PNG)

### 마치며

#### 제한 사항

- 약 500만개의 데이터 볼륨을 가지고 있기 때문에 소유하고 있는 장비를 통해 모델링을 진행하기에는 제한 사항이 많아서 아쉬움이 남습니다.  
- 하드웨어 장비를 추가하거나 클라우드 환경을 활용하기에는 비용적 측면에서 제한되어 데이터를 축약하고자 하였으나 날짜, 시간, 도로별 평균 데이터를 생성하여 진행할 경우, 소실되는 데이터로 인해 높은 성능의 모델을 생성하지 못했습니다.  

#### 배운 점

- 이전에는 데이터를 스크래핑하거나 내부 데이터만 활용하여 데이터 분석을 진행하였으나, 이번 프로젝트에서는 적극적으로 공공 데이터 및 open API를 활용하는 방법을 알 수 있었습니다.  
- auto ML을 알게 되어 모델링을 생성하기 위해 필요한 작업들을 줄임과 동시에 높은 성능의 모델링을 할 수 있는 방법에 대해 배울 수 있었습니다.  
