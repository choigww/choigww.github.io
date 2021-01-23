---
title: GloVe for Stock Price Prediction
date: 2021-01-23 11:12:35
categories:
- Machine Learning
- Finance
tags:
- GloVe
- NLP
- 자연어처리
- 주가예측
- 데이터 전처리
---

자연어처리를 활용해서 주가를 예측한다. 이야기가 들리기 시작했던 건 상당히 오래 전으로 기억합니다만, 최근 딥러닝 알고리즘의 발전에 힘입어 다시 떠오르고 있습니다. 오늘은 벡터 차이의 의미를 동시발생 확률 비율의 차이로 파악하는 GloVe 모델과 함께, 주가 예측 목적으로 자연어 텍스트를 전처리하는 방법 등에 대해 살펴봅니다.



## GloVe

### 벡터 차이의 의미 인코딩

동시발생 확률의 비율을 통해 의미 구성 요소를 인코딩한다.

|              $x=\text{solid}$               | $x=\text{solid}$ | $x=\text{gas}$ | $x=\text{water}$ | $x=\text{random}$ |
| :-----------------------------------------: | :--------------: | :------------: | :--------------: | :---------------: |
|              $P(x|\text{ice})$              |      large       |     small      |      large       |       small       |
|             $P(x|\text{steam})$             |      small       |     large      |      large       |       small       |
| $\frac{P(x|\text{ice})}{P(x|\text{steam})}$ |      large       |     small      |        ~1        |        ~1         |

| $x=\text{solid}$                            | $x=\text{solid}$    | $x=\text{gas}$      | $x=\text{water}$    | $x=\text{random}$   |
| ------------------------------------------- | ------------------- | ------------------- | ------------------- | ------------------- |
| $P(x|\text{ice})$                           | $\text{1.9 x 10}^4$ | $\text{6.6 x 10}^5$ | $\text{3.0 x 10}^3$ | $\text{1.7 x 10}^5$ |
| $P(x|\text{steam})$                         | $\text{2.2 x 10}^5$ | $\text{7.8 x 10}^4$ | $\text{2.2 x 10}^3$ | $\text{1.8 x 10}^5$ |
| $\frac{P(x|\text{ice})}{P(x|\text{steam})}$ | 8.9                 | $\text{8.9 x 10}^2$ | 1.36                | 0.96                |



### 단어 벡터 공간에서 선형 의미 구성 요소로 동시 발생 확률의 비율을 사용하는 방법

Log-bilinear 모형
$$
w_i\cdot w_j=log \ P(i \ | \ j)
$$

Log-bilinear 모형과 벡터의 차이

- 동시 발생 확률의 비율값을 활용
- 의미의 차이 = 비율의 차이

$$
w_x \cdot (w_a - w_b) = log \ \frac{P(x \ | \ a)}{P(x \ | \ b)}
$$



### What is GloVe?

- Global Vectors for Word Representation
  - 카운트 기반 + 예측 기반 방법론 모두 사용
- "GloVe: Global Vectors for Word Representation", Pennington et al., 2014
  - 카운트 기반의 LSA와 예측 기반의 Word2Vec, 2개 접근법의 단점 보완
  - 실제로는 Word2Vec과 유사한 성능을 보임 (상황별 적합한 모델 선택)



**카운트 기반 : LSA**

- 각 단어 빈도수를 카운트 한 행렬로 받아 차원 축소
- 특이값분해를 통해 의미 끌어내는 방법론
- 카운트 기반, 말뭉치의 전체적인 통계 정보 고려
  - 단어 의미 유추 작업에는 성능 떨어짐



**예측 기반 : Word2Vec**

* 실제값과 예측값에 대한 오차를 손실 함수를 통해 줄여가면서 학습
* 단어 간 유추 작업에는 LSA보다 뛰어난 성능
  * 중심단어 - 주변단어 간 일반화된 의미 추론 규칙을 학습
* 임베딩 벡터가 윈도우 크기 내에서만 주변 단어를 고려
* 말뭉치의 전체적인 통계 정보를 반영하지 못함



## NLP와 주가



### 전처리 과정 (Preprocess)

- 특성을 추출하기까지 작업의 양이 방대함
- 자연어처리는 특별히 전처리 과정이 힘든 과정
  - 감성분석 > 비꼬는 말의 최신 언어, 은어 등
  - 기계가 파악하기 어려움
- 사전처리의 정확도에 따라 예측력이 엄청나게 향상될 수 있음



### 특성추출 (Feature Extraction)

| 이름                                  | 설명                                                         |
| ------------------------------------- | ------------------------------------------------------------ |
| **트윗**                              | "@" 기호 > "PERSON"<br /> "#" 기호 > "TOPIC"                 |
| **정제**                              | 말뭉치의 노이즈 데이터 제거                                  |
| **정규화**                            | 표현 방법이 다양한 단어들을 하나의 단어로 통합               |
| **슬랭****                            | 정규화된 단어로 대체                                         |
| **불용어**                            | 더 이상 사용되지 않으므로 제거                               |
| **Negation**                          | 부정표현을 Negation이라는 토큰으로 대체                      |
| **품사 태거**<br /> (Parts of Speech) | - 명사, 동사, 접속사 등 문법적인 표시로 주석 첨부<br />- 문장의 의미 유추에 도움 |
| **Bag-of-Words**                      | - 단어들의 출현 빈도에 집중한 텍스트 데이터의 수치화 표현 방법<br / >- 단어의 unigram, bigram, n-gram 단계를 고려하여 감정 어휘를 사용해서 주관성 점수 제공 |
| **Feature Hashing** (FH)              | - 해시 태그가 지정된 단어는 작가가 직접 삽입한 감정과 레이블 >>> 매우 유용함 |



### 기계학습의 방법론

1. 전처리
2. ML / DL
   1. Support Vector Machine
   2. Naive Bayes
   3. Logistic Regresions
   4. Random Forest



### 뉴스 감성분석과 주가 예측

**감성분석 대상 데이터**

- 주가 데이터
  - 시가, 고가, 저가, 종가, 수정종가, 거래량
- 뉴스
  - 구글뉴스, 로이터, 야후뉴스
  - 2013.02 - 2016.04

**수집된 뉴스 텍스트의 긍정, 부정을 판단함**

- 주가에 미치는 영향 파악

**Feature = 긍정 2,360개 단어, 부정 7,383개 단어**

- 기계학습 방법론으로 테스트 (training data)
  - Random Forest > 약 88-92%
  - Support Vector Machine > 약 86%
  - Naive Bayse : 약 83%

* 테스트 데이터로 예측한 결과
  * **Support Vector Machine > 90%**
  * Random Forest > 80%
  * Naive Bayse > 75%

**전체 프로세스**

1. News collection
2. Text preprocessing
3. Poarity detection algorithm
4. Set polarity score to news
5. Document representation
6. Classifier learning (model buildingl)
7. System evaluation
8. Test the model with new data
9. Plot time series of past Adj_close price and scoring of news sentiment
10. Observe the relationship between news sentiment score and stock price



### 트위터(StockTweets) 메시지도 정보가 될 수 있다!

- 감성분석 실시
  - N-grams와 BN synsets를 조합한 감성분석의 예측력 = 약 72% (가장 높았음)



### 문장구조 분석과 주가 예측

감성분석 말고 뉴스 헤드라인의 문장 패턴을 구조 분석하면 어떨까?

- 어휘 접근법 > 약 40% 예측
- 어휘 접근법 + **문장 구조 분석** > 82-96% 예측

**> 문장 구조를 분석하는 것이 어휘만 분석하는 것보다 더 많은 정보량을 갖고 있다**



### BERT

구글에서 2018년 개발한 딥러닝 모델, Bidirectional Encoder Representations for Transforms

- 자연어처리 분야에서 가장 우수한 성능
- 트랜스포머(Transformer) 기반 모델
- 사전학습 후 특정 목적을 위해 Fine-Tuning하여 사용
- 양방향 모델이 문장 앞뒤 문맥을 동시에 고려

**> BERT 방법론과 거시경제 데이터를 함께 활용해 예측력 우수**

- 유가, 금, 환율 등 거시적인 데이터까지 학습 데이터에 포함
- 예측력 향상



### 자연어처리의 활용

> "자연어처리에 관한 많은 논문들이 연구, 발표되고 있고 투자에도 활용되고 있다"



### 뉴스 등 자연어의 NLP 분석이 주가 예측에 new factor가 될 수 있을까

- 설명력이 있다 = 새로운 (유효) 정보로서 작용하고 있다
- 기존 Pricing Theory에서 사용되지 않았던 **새로운 차원의 정보**를 다루는 영역
- 최근 빠르게 주목받으며 발전하고 있는 영역




---

K-mooc, [금융 AI](http://www.kmooc.kr/courses/course-v1:CAUk+CAU_AI03+2020_1/about), 중앙대학교 경영학부 유시용 교수님

*자료 출처: 강의자료 (12-2강)