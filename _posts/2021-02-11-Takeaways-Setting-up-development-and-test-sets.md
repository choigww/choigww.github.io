---
title: Takeaways: Setting up development and test sets
date: 2021-02-11 20:03:13
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
---

디벨롭먼트 셋과 테스트 셋에 관한 9가지 교훈들.

# Takeaways: Setting up development and test sets

- 미래에 당신의 모델이 학습해야 할 데이터를 반영하고 있는 분포로부터 디벨롭먼트 셋과 테스트 셋을 선택하세요.
- 가능한 동일한 분포로부터 디벨롭먼트 셋과 테스트 셋을 선택하세요.
- 당신의 팀이 최적화해야 할 단일 평가 지표를 선택하세요. 만약 목표가 여러 개라면 오차 지표들의 평균값과 같이 단일 수식으로 통합하거나 최적화 지표를 정의하세요.
- 머신러닝은 개선을 위해 반복을 거듭하는 프로세스입니다: 당신은 만족스러운 아이디어를 찾기 전까지 수십 가지의 아이디어들을 시도해야 할 수 있습니다.
- 디벨롭먼트/테스트 셋과 단일 평가 지표를 선택함으로써 당신은 알고리즘을 신속하게 평가하고, 따라서 더 빠르게 프로세스를 반복할 수 있게 됩니다.
- 신규 어플리케이션을 만들고자 할 때에는 가능한 빠르게, 말하자면 일주일 안으로 디벨롭먼트/테스트 셋과 단일 평가 지표를 정립하도록 노력하세요. 기성 어플리케이션(mature application)이라면 더 오래 걸려도 괜찮을 겁니다.
- 당신이 많은 데이터를 가지고 있다면, 트레인 셋과 테스트 셋을 70 대 30으로 구분하는 오래된 관습은 적용할 필요가 없습니다. 디벨롭먼트 셋과 테스트 셋은 전체 데이터의 30%보다 훨씬 작아도 됩니다.
- 당신의 디벨롭먼트 셋은 알고리즘 정확도의 변화를 의미있는 수준까지 포착할 만큼 커야 하지만, 그 이상으로 훨씬 많을 필요는 없습니다. 당신의 테스트 셋은 머신러닝 시스템의 최종 성능에 대한 신뢰성 있는 추정치를 제공할 만큼 커야 합니다.
- 기존의 디벨롭먼트 셋과 평가 지표가 개선을 위한 방향을 더 이상 가리키지 못한다면, 빠르게 교체하세요.
  - (i) 디벨롭먼트 셋에 오버피팅이 일어났다면, 디벨롭먼트 셋에 더 많은 데이터를 보강하세요.
  - (ii) 당신이 목적하는 실제 분포가 디벨롭먼트/테스트 셋 분포와 다르다면, 새로운 디벨롭먼트/테스트 셋 데이터를 마련하세요.
  - (iii) 당신의 평가 지표가 "당신에게 가장 중요한 것"을 더 이상 측정하지 못한다면, 평가 지표를 교체하세요.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)