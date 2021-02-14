---
title: Your dev and test sets should come from the same distribution
date: 2021-02-08 19:02:53
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
---

당신은 시장이 큰 순서대로 미국, 중국, 인도 그리고 기타 4개 지역을 선정하고, 지역별로 고양이 앱 이미지 데이터를 분류했습니다. 미국과 인도 사진은 디벨롭먼트 셋, 중국과 기타 지역 사진은 테스트 셋이라고 가정해 봅시다. 사실 4개의 지역별 세그멘트 중 임의의 2개 셋을 디벨롭먼트 셋으로, 나머지를 테스트 셋으로 지정할 수도 있을 겁니다.

# Your dev and test sets should come from the same distribution

디벨롭먼트 셋과 테스트 셋을 정의하고 나면, 당신의 팀원들은 디벨롭먼트 셋에 대한 모델 성능을 개선하는 데 집중할 겁니다. 따라서, 디벨롭먼트 셋은 반드시 당신이 최우선적으로 개선하고자 하는 태스크를 반영하고 있어야 합니다. 미국과 인도뿐 아니라 중국과 기타 지역 세그먼트 데이터도 대표할 수 있어야만 하죠.

디벨롭먼트 셋과 테스트 셋의 분포가 서로 다른 문제가 발생할 수 있습니다. 이는 즉, 당신의 팀이 디벨롭먼트 셋에 대하여 열심히 모델을 개선했지만 테스트 셋 성능이 형편없을 수도 있음을 의미합니다. 모든 노력들이 허사가 되는, 좌절스럽기 짝이 없는 일입니다. 이러한 일이 당신과 당신의 팀에 일어나지 않도록 하세요.

예를 들어, 당신의 팀이 디벨롭먼트 셋에서는 성능이 좋지만 테스트 셋에서는 그렇지 않은 머신러닝 시스템을 구축했다고 가정해 봅시다. 만약 당신의 디벨롭먼트 셋과 테스트 셋이 동일 분포에서 비롯되었다면, 당신은 무엇이 잘못되었는지 매우 명확한 진단을 내릴 수 있을 겁니다. 디벨롭먼트 셋에 대하여 오버피팅이 발생한 것이죠. 디벨롭먼트 셋에 더 많은 데이터를 추가하면 해결할 수 있을 겁니다.

그러나 디벨롭먼트 셋과 테스트 셋이 서로 다른 분포로부터 비롯됐다면, 문제점은 명확하지 않을 수 있습니다. 몇 가지가 잘못되었을 수 있습니다:

1. **디벨롭먼트 셋에 대하여 오버핏**이 발생했음
2. 테스트 셋의 분포가 디벨롭먼트 셋 분포보다 ***샘플링하기 어려운 경우**** 
   1. 알고리즘이 기대한 만큼의 성능을 내지만, 의미있는 수준의 개선이 불가능함
3. 테스트 셋이 특별히 샘플링하기 어렵지는 않으나 **디벨롭먼트 셋과 그냥 다른 경우**
   1. 디벨롭먼트 셋에서의 성능이 테스트 셋에서 보장되지 않음
   2. 디벨롭먼트 셋 성능 개선을 위한 노력들이 물거품이 됨



머신러닝 어플리케이션을 구축하는 것은 어려운 일입니다. 디벨롭먼트 셋과 테스트 셋이 서로 다른 분포를 가지고 있다면, 이는 디벨롭먼트 셋 분포에 대한 개선이 테스트 셋에 대한 개선으로 이어지지 않을 수도 있다는 불확실성 문제를 낳습니다. 어떤 아이디어가 효과적이고 효과적이지 않은지 구별하기가 어려워지고, 무엇에 집중해야 할 지 우선순위를 판단하기 어려워집니다.

만약 당신이 서드파티 벤치마크 문제를 작업하고 있다면, 서드파티 개발자가 서로 다른 분포로부터 비롯된 디벨롭먼트 셋과 테스트 셋을 정의했을 가능성이 있습니다. 디벨롭먼트 셋과 테스트 셋이 서로 다른 분포를 가졌다면, 그 벤치마크에 대한 성능은 기술보다는 순전히 운에 달린 문제일 겁니다.

알고리즘을 하나의 분포로 학습시켜서 다른 분포에 대해서도 일반화할 수 있도록 개발하는 것은 중요한 연구 주제입니다. 그러나 당신의 목표가 연구 성과가 아니라 특정한 문제를 잘 해결하는 머신러닝 어플리케이션이라면, 동일한 하나의 분포로부터 추출한 디벨롭먼트 셋과 테스트 셋을 선택하고자 노력할 것을 추천합니다. 이는 당신의 팀을 더 효율적으로 만들어줄 겁니다.





## '샘플링하기 어려운 분포(hard distribution to sample from)'의 의미

source [https://math.stackexchange.com/](https://math.stackexchange.com/questions/3252899/what-does-it-mean-that-a-distribution-is-hard-to-sample-from)

Good question. Very foundational to learning the true value of efficient sampling techniques.

It boils down to the simple fact that to "sample from a distribution" you need to know the CDF of the distribution. More precisely you need the Inverse CDF i.e. a function that will give you the a sample if you feed it a probability. Although all CDFs are monotonically increasing and hence theoretically invertible analytically (practically) it not that easy. 

So two issues prevent you from directly getting values from the CDF. One is getting the CDF itself and the second is inverting it. The problem gets more complex in higher dimensions. So efficient sampling techniques are used to approximate the functions instead.

Hope this helps.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)