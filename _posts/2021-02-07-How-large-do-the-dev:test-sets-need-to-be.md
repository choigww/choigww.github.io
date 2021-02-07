---
title: How large do the dev/test sets need to be?
date: 2021-02-07 08:02:53
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
- Dev Set
- Development Set
---

디벨롭먼트 셋은 얼마나 커야 할까요? **사용하고자 하는 알고리즘들 간의 차이를 포착할 수 있을 만큼 커야 합니다**.

# How large do the dev/test sets need to be?

예를 들어, 분류기 A가 90.0%의 accuracy를 갖고 분류기 B가 90.1% accuracy를 갖는다면, 100개짜리 디벨롭먼트 셋으로는 0.1%의 차이를 감지할 수 없을 겁니다.

제가 지금까지 봐 온 다른 머신러닝 문제들과 비교해 보면, 경험적으로 100개짜리 디벨롭먼트 셋은 작습니다. 디벨롭먼트 셋의 크기는 일반적으로 1,000개에서 10,000개가 적당합니다. 1만개 가량을 사용한다면 0.1%의 차이를 높은 확률로 포착할 수 있을 겁니다.

긴 시간 발전해 성숙기에 접어든 중요한 분야들, 예를 들어 광고, 웹 검색, 제품 추천 등에 대해서, 고작 0.01%의 개선조차도 커다란 동기부여가 됩니다. 기업의 수익과 직결되기 때문이죠. 이런 경우, 디벨롭먼트 셋은 매우 작은 개선을 포착하기 위하여 1만개보다 훨씬 더 크기가 커야 할 겁니다.

테스트 셋의 크기는 얼마나 크면 좋을까요? **당신의 모델이 가진 전반적인 성능에 대하여 높은 신뢰성을 제공할 만큼 커야 합니다**. 오랜 시간, 테스트 셋은 가용 데이터 셋의 3할을 할당하는 것이 대중적인 휴리스틱으로 받아들여졌습니다. 이러한 방식은 그다지 많지 않은, 말하자면 데이터 사이즈가 100개에서 1만개 수준일 때 효과적입니다.

그러나 억 단위의 데이터 사이즈를 가지고 머신러닝 문제를 다루는 빅데이터의 시대에, **디벨롭먼트 셋과 테스트 셋에 할당하는 데이터 비율은 점차 작아지는 추세**입니다. 비율은 작아질지언정 절대 크기로 비교하면 여전히 과거보다 훨씬 많은 수준이지만요.

당신의 알고리즘 성능을 평가하는 데 필요한 것보다 많은 데이터를 디벨롭먼트 셋과 테스트 셋에 초과 할당할 필요는 없습니다.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 이전 글

1. [Why Machine Learning Strategy](https://choigww.github.io/ml%20best%20practice/2021/02/02/Why-Machine-Learning-Strategy/)
2. [How to use this book to help your team](https://choigww.github.io/ml%20best%20practice/2021/02/03/How-to-use-this-book-to-help-your-team/)
3. [Prerequisites and Notation](https://choigww.github.io/ml%20best%20practice/2021/02/04/Prerequisites-and-Notation/)
4. [Scale drives machine learning progress](https://choigww.github.io/ml%20best%20practice/2021/02/05/Scale-drives-machine-learning-progress/)
5. [Your development and test sets](https://choigww.github.io/ml%20best%20practice/2021/02/06/Your-development-and-test-sets/)

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)