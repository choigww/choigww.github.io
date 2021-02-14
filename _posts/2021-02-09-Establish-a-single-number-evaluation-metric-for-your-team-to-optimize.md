---
title: Establish a single-number evaluation metric for your team to optimize
date: 2021-02-09 18:31:53
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
- single-number evaluation metric
---

분류 정확도는 **단일 평가 지표**(single-number evaluation metric)에 해당합니다: 당신은 디벨롭먼트 셋 또는 테스트 셋에 분류기를 돌려본 다음, 분류기가 올바르게 분류한 데이터 비율에 대한 단일 평가 지표를 확인하게 됩니다. 분류기 A가 97%의 정확도, 분류기 B가 90%의 정확도를 나타낸다면, 우리는 평가 지표에 따라 분류기 A가 더 우수하다고 판단합니다.

# Establish a single-number evaluation metric for your team to opimize

반대로, Precision과 Recall은 **단일 평가 지표**에 해당하지 않습니다: 분류기를 평가하는 숫자를 2개 내놓기 때문인데요. 복수의 숫자를 갖는 평가 지표들은 알고리즘 비교를 어렵게 만듭니다. 예를 들어, 당신의 두 알고리즘의 성능이 아래와 같다고 해 봅시다:



**Classifier A**

- Precision 95%
- Recall 90%

**Classifier B**

- Precision 98%
- Recall 85%



두 개 중에서 어느 한 분류기가 명백하게 우월하지 않다면, 분류기를 선택하기가 난감해 집니다.

**Classifier A**

- Precision 95%
- Recall 90%
- F1 Score 92.4%



개발 도중, 당신의 팀은 알고리즘 아키텍쳐, 모델 파라미터, 피쳐 셀렉션 등에 대한 다양한 아이디어들을 시도하게 될 겁니다. 분류 정확도와 같은 **단일 평가 지표**를 설정함으로써, 당신은 지표를 기반으로 모델을 성능순으로 정렬해 가장 좋은 것을 빠르게 결정할 수 있게 됩니다.

만약 Precision과 Recall 지표를 어떻게든 원한다면, 두 지표를 단일 지표로 결합하는 다양한 표준 방법 중 하나를 사용하시길 바랍니다. 예를 들어 Precision과 Recall의 평균값을 사용할 수 있을 겁니다. 아니면 두 지표의 평균을 활용한 값이면서, 단순평균보다 더 성능을 잘 표현하는 F1 score를 사용할 수도 있습니다.



**Classifier A**

- Precision 95%
- Recall 90%
- **F1 score 92.4%**

**Classifier B**

- Precision 98%
- Recall 85%
- **F1 score 91.0%**



단일 평가 지표를 설정하면 당신은 수많은 분류기들 중 하나를 빠르게 선택할 수 있게 됩니다. 분류기 성능 순위를 명확히 매길 수 있다면 발전적인 방향이 어디인지도 알 수 있습니다.

마지막으로 예를 하나 더 들겠습니다. 당신이 4개의 핵심 시장인 미국, 중국, 인도, 기타 국가에서 당신의 고양이 분류기의 정확도를 각각 추적한다고 해 봅시다. 4개의 지역이므로 4개의 지표가 나올 겁니다. 이 4개의 지표에 대해 단순평균 또는 가중평균을 취하면, 당신은 하나의 지표를 얻게 될 것입니다. 단순평균 또는 가중평균은 복수의 지표를 하나로 합치는 가장 흔한 방법들 중 하나입니다.



*F1 score에 대하여 더 알고 싶다면: https://en.wikipedia.org/wiki/F1_score*

- F1 score = "harmonic mean" between Precision and Recall, calculated as $\frac{2}{(\frac{1}{Precision})+(\frac{1}{Recall})}$

---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)