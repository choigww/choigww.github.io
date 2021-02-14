---
title: Having a dev set and metric speeds up iterations 
date: 2021-02-10 19:05:53
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
- single-number evaluation metric
---

새로운 문제에 어떻게 접근하면 좋을지를 미리 알기는 어렵습니다. 경험 많은 머신러닝 연구원조차 만족스러운 방법을 찾기 전까지 수십 개의 아이디어를 시도해야 할 겁니다. 머신러닝 시스템을 구축할 때, 나는 다음과 같은 일들을 수행합니다:

1.  시스템 구축에 대한 어떤 **아이디어**로 시작한다
2. **코드**로 아이디어를 구현한다
3. 아이디어가 얼마나 잘 작동했는가 알아보기 위하여 **실험**을 수행한다 (대개 나의 첫번째 아이디어는 실패한다)
4. 실험 결과로부터 더 많은 아이디어를 생성하고 위 과정을 **반복**한다

# Having a dev set and metric speeds up iterations

이것은 반복적인 프로세스입니다. 루프를 빠르게 돌릴수록 당신은 더 빠르게 발전할 수 있습니다. 이는 디벨롭먼트 셋과 테스트 셋 그리고 지표가 중요한 이유이기도 합니다: 아이디어를 실험할 때마다, 디벨롭먼트 셋에 대한 아이디어의 성능을 평가함으로써 당신은 올바른 방향으로 나아가고 있는지 알 수 있기 때문입니다.

반대로, 당신이 특정한 디벨롭먼트 셋이나 평가 지표를 갖고 있지 않다고 가정해 봅시다. 그래서 매번 당신의 팀이 새로운 고양이 분류기를 개발할 때마다, 당신은 분류기를 앱과 통합시키고 결과를 확인하기 위해 수 시간을 기다려야만 합니다. 끔찍한 일이죠!

당신의 팀이 분류기 정확도를 95.0%에서 95.1%로 개선했다면, 앱 테스트 만으로는 0.1% 개선을 탐지하기 어려울 겁니다. 그러나 머신러닝은 바로 0.1%의 개선들을 수십개씩 축적시키면서 발전해 나가는 것이며, 따라서 0.1%의 개선을 빠르게 확인하는 것은 중요합니다.

디벨롭먼트 셋과 평가 지표를 갖춤으로써 당신은 어떤 아이디어가 작은 (혹은 커다란) 개선을 만들어 내는지 빠르게 확인할 수 있습니다. 따라서 당신은 계속 가다듬어야 할 아이디어가 무엇이고, 버려야 할 아이디어는 무엇인지 결정할 수 있습니다.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)