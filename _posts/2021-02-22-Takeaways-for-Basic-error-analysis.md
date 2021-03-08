---
title: Takeaways for Basic error analysis
date: 2021-02-22 21:39:03
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
---

기초적인 에러 분석(error analysis)에 대하여, 우리는 아래와 같은 6개의 교훈 또는 지침을 얻을 수 있습니다.

# Takeaways: Basic error analysis

- 새로운 프로젝트를 시작할 때, 특히 당신이 해당 기술분야 또는 도메인에 대한 전문가가 아니라면, 최적의 방향성을 결정하는 것은 어렵습니다.
- 따라서 처음부터 완벽한 시스템을 설계하고 구축하려 하지 마세요. 대신, 간단한 시스템을 가능한 빠르게 구축해서 학습시켜 보세요. 그 다음에 에러 분석을 실시하여 좋은 방향성을 찾아내고, 그 지점으로부터 알고리즘을 반복적으로(iteratively) 개선시켜 나가세요.
- 알고리즘이 오분류한 ~100개의 디벨롭먼트 셋 샘플에 대하여 하나하나 수동으로 에러 분석을 수행하고, 에러 카테고리 별 갯수를 세어 보세요. 이렇게 얻은 정보를 사용하여, 어떤 종류의 에러를 먼저 개선해야 할 지 작업 우선순위를 정하세요.
- 디벨롭먼트 셋을 아이볼 셋과 블랙박스 셋으로 나누는 것을 고려해 보세요. 아이볼 셋은 당신이 하나하나 에러 분석을 수행할 데이터이고, 블랙박스 셋은 에러 분석을 수행하지 않을 데이터입니다. 아이볼 셋에서의 모델 성능이 블랙박스 셋에서의 모델 성능보다 훨씬 좋게 나온다면, 아이볼 셋에 대하여 오버피팅이 일어난 것이므로 아이볼 셋에 더 많은 데이터를 보충해 주어야 합니다.
- 아이볼 셋은 당신이 분석하게 될 오분류 샘플을 충분하게 만들어낼 수 있을 만큼 데이터 사이즈가 커야 합니다. 블랙박스 셋은 1000개에서 10000개 가량의 사이즈면 대부분 충분합니다.
- 디벨롭먼트 셋이 아이볼과 블랙박스로 나눌 만큼 크지 않다면, 디벨롭먼트 셋 전체를 아이볼 셋으로 사용해서 수동 에러 분석, 모델 셀렉션 그리고 하이퍼파라미터 튜닝에 사용하세요.





---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)