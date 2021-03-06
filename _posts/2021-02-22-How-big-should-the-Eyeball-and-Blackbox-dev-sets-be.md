---
title: How big should the Eyeball and Blackbox dev sets be?
date: 2021-02-22 20:03:47
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
---

아이볼 디벨롭먼트 셋은 학습 알고리즘의 주요 에러 카테고리들이 무엇인지 보여줄 수 있을 만큼 커야 합니다. 당신이 작업 중인 태스크가 고양이 구분하기처럼 사람도 잘 할 수 있는 일이라면, 다음과 같은 지침을 참고할 수 있습니다:

# How big should the Eyeball and Blackbox dev sets be?

- 분류기가 샘플 10개를 오분류하는 아이볼 디벨롭먼트 셋은 크기가 아주 작다고 생각할 수 있습니다. 고작 10개의 에러만으로는 다양한 에러 카테고리들의 영향력을 정확하게 추정하기 어렵습니다. 그러나 당신이 가진 데이터가 매우 적은 상황이라면, 없는 것보다는 나으므로 그대로 프로젝트 우선순위 판단의 근거로 사용해야 할 것입니다.
- 분류기가 아이볼 디벨롭먼트 셋에 대하여 샘플 ~20개를 오분류한다면, 에러가 주로 어디에서 발생하는지를 대충 알 수 있다고 생각할 수 있습니다.
- 분류기가 샘플 ~50개를 오분류하는 아이볼 디벨롭먼트 셋이라면, 주요 에러 원인들에 대해 적당히 좋은 수준으로 이해할 수 있습니다.
- 분류기가 샘플 ~100개를 오분류하는 아이볼 디벨롭먼트 셋이라면, 주요 에러 원인들에 대해 상당히 좋은 수준으로 이해할 수 있습니다. 저는 100개보다 더 많은 에러들, 가령 500개 정도까지도 하나하나 분석하는 사람들도 보았습니다. 데이터만 충분하다면, 에러 분석을 수행할 데이터 크기를 늘리는 것은 전혀 나쁠 것이 없습니다.



당신의 분류기가 5%의 에러율을 보인다고 가정해 봅시다. 아이볼 디벨롭먼트 셋에 대하여 ~100개의 오분류 샘플을 얻기 위해, 아이볼 디벨롭먼트 셋은 대략 2000개의 샘플을 갖고 있어야 합니다. 분류기의 에러율이 낮을수록, 충분히 많은 에러 분석 셋을 얻기 위해서 아이볼 디벨롭먼트 셋도 많이 확보해야 합니다.

만약 작업하고 있는 태스크가 사람에게도 어려운 일이라면, 아이볼 디벨롭먼트 셋을 검사하는 작업은 그다지 효과적이지 않을 수 있습니다. 왜냐하면 알고리즘이 어째서 데이터 샘플을 올바르게 분류하지 못했는지 확인하기가 더 어렵기 때문입니다. 이러한 경우, 당신은 아이볼 디벨롭먼트 셋을 구분하는 작업을 건너뛸 수 있습니다. 이 주제와 관련해서는 이후 챕터에서 다시 살펴볼 것입니다. 

![black-box-Optimization](https://i.loli.net/2021/02/19/rwOAb2fSuHKMsED.png)



블랙박스 디벨롭먼트 셋은 어떨까요? 이전 챕터에서 우리는 블랙박스 디벨롭먼트 셋 사이즈로 1000개에서 10000개 가량이 적당하다고 살펴본 바 있습니다. 더 자세히 말하자면, 블랙박스 디벨롭먼트 셋은 1000-10000개의 사이즈를 가질 때 하이퍼파라미터 튜닝 및 모델 셀렉션을 하기에 일반적으로 충분합니다. 물론 이보다 더 데이터가 많아도 나쁠 것은 없습니다. 사이즈가 100개인 블랙박스 디벨롭먼트 셋도 작기는 하지만 그럼에도 유용하게 사용할 수 있습니다.

디벨롭먼트 셋의 사이즈가 작다면, 당신은 각각의 목적을 달성할 만큼 충분한 아이볼 셋과 블랙박스 셋을 확보하기 어려울 수 있습니다. 이 경우, 당신은 디벨롭먼트 셋 전체를 아이볼 디벨롭먼트 셋으로 사용할 수도 있습니다. 디벨롭먼트 셋 데이터 전부에 대해 하나하나 에러 분석을 수행하는 것이죠.

머신러닝 태스크가 사람이 잘 해결할 수 있는 문제이고, 따라서 에러 분석이 유의미하다면 아이볼 셋이 블랙박스 셋보다 더 중요하다고 생각할 수 있습니다. 블랙박스 디벨롭먼트 셋이 없더라도, 아이볼 디벨롭먼트 셋만 있으면 당신은 에러 분석, 모델 셀렉션 그리고 하이퍼파라미터 튜닝을 수행할 수 있습니다. 그러나 블랙박스 디벨롭먼트 셋이 없으므로, 디벨롭먼트 셋에 대해 학습모델이 오버피팅될 리스크가 더 커진다는 것이 단점입니다.

가용 데이터가 매우 넉넉한 상황이라면, 아이볼 디벨롭먼트 셋 사이즈는 당신이 하나하나 진행해야 하는 에러 분석에 얼마나 시간을 할애할 수 있는가에 따라 결정될 것입니다. 개인적인 경험을 말씀드리자면, 1000개 이상의 에러 샘플을 하나하나 검사하는 사람은 거의 본 적이 없습니다.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)