---
title: 선형 모델의 Overfitting과 Regularization
date: 2021-01-24 22:02:16
categories:
- Machine Learning
- Data Preprocessing
tags:
- 선형 모델
- 데이터 전처리
- noise robust
- RANSAC

---

선형 모델은 Regression과 Classification 문제에 모두 활용되는 중요한 알고리즘입니다. 오늘은 선형 모델이 갖는 근본적인 문제점을 살펴본 뒤, 어떻게 문제점을 보완하고 견고한 모델을 만들 수 있는지 알아봅니다.

앞서 작성된 글:

- [Linear Regressor vs. Linear Classifier](https://choigww.github.io/machine%20learning/2021/01/19/Linear-Regressor-vs-Linear-Classifier/)
- [선형 모델을 위한 noise-robust 학습 방법론]



