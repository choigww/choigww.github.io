---
title: Bias and Variance: The two big sources of error
date: 2021-03-12 19:05:38
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
---

트레이닝, 디벨롭먼트, 테스트 셋 모두 같은 분포에서 나온다고 가정해 봅시다. 당신은 모델 성능을 위해 최대한 많은 트레이닝 셋을 얻고자 합니다. **물론 데이터는 다다익선이지만, 항상 기대만큼 도움이 되는 것은 아닙니다**. 때로 시간낭비가 될 수도 있죠. 데이터를 더 구하는 일이 시간낭비인지 아닌지, 어떻게 판단할 수 있을까요?

# Bias and Variance: The two big sources of error

머신러닝 오류를 만드는 가장 큰 두 요인은 편향(bias)과 분산(variance) 입니다. 편향과 분산을 이해함으로써, 데이터 보강을 포함한 다양한 성능 개선 방법들을 언제 시도해야 할 지 판단할 수 있습니다.

당신이 5% 에러율을 갖는 고양이 사진 분류기를 만들고 싶어한다고 해 봅시다. 지금 당신의 트레이닝 셋은 15%의 에러율을, 디벨롭먼트 셋은 16%의 에러율을 보이고 있습니다. 이 경우, 트레이닝 데이터를 더 추가하는 것은 그다지 도움이 되지 않을 겁니다.

실제로, 위와 같은 상황에서 트레이닝 데이터를 더 추가해주는 것은 오히려 알고리즘이 트레이닝 셋을 학습하는 것을 더 어렵게 만들게 됩니다. 우리는 이후 챕터에서 왜 그렇게 되는지 살펴볼 겁니다.

만약 트레이닝 셋에 대한 에러율이 15%인 상황에서 당신의 목표는 5% 에러율이라면, 트레이닝 셋에 대한 에러율을 줄이는 것이 최우선 과제일 겁니다. 당신의 디벨롭먼트/ 테스트 셋 성능은 일반적으로 트레이닝 셋 성능보다 낮기 때문입니다. 알고리즘이 본 적이 있는 데이터(트레이닝 셋)에 대해 85% 정확도가 나오는데, 본 적 없는 데이터(테스트 셋)에 대해 95% 정확도가 나오기란 대단히 어렵습니다.

위에서 말한 대로, 알고리즘이 디벨롭먼트 셋에 대해 16% 에러율을 갖는다고 가정해 봅시다. 우리는 16% 에러율을 두 개의 구성 요소로 쪼개볼 수 있습니다:

1. 트레이닝 셋에 대한 알고리즘의 에러율 = **알고리즘의 편향(bias)**
2. 알고리즘의 디벨롭먼트/ 테스트 셋 성능이 트레이닝 셋 성능에 비하여 얼마나 나쁜가 = **알고리즘의 분산(variance)**



학습 알고리즘을 일부 변경하는 것은 알고리즘 편향 문제를 개선하여, 트레이닝 셋에 대한 성능을 향상시킬 수 있습니다. 또 다른 방법으로 학습 알고리즘을 변경한다면, 알고리즘 분산 문제를 개선하여 모델 일반화(generalization) 성능을 향상시킬 수 있습니다.

가장 큰 개선을 이끌어내려면 무엇을 바꾸어야 할까요? **모델의 편향과 분산 중 무엇이 문제에 더 관여하고 있는지 이해하는 것은 매우 유용**한 지침이 됩니다. 모델 편향과 모델 분산에 대해 직관을 쌓으면, 알고리즘 성능 향상으로 이어지는 선택지를 판단할 수 있겠죠.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)