---
title: Your development and test sets
date: 2021-02-06 11:27:11
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
- Andrew Ng
---

앞서 살펴본 고양이 사진 탐지기로 돌아가 봅시다: 당신은 모바일 앱을 출시했고, 사용자들은 매우 다양한 사진들을 당신의 앱에 올리고 있습니다. 당신은 고양이 사진만 자동으로 찾아내고자 합니다.

# Your development and test sets

당신의 팀은 다양한 웹사이트로부터 고양이 사진들(positive example) 그리고 고양이가 아닌 사진들(negative examples)을 다운로드해서 커다란 데이터셋을 마련했습니다.

그들은 데이터셋의 70%를 트레이닝 셋, 30%를 테스트 셋으로 할당했습니다. 이 데이터를 사용하여 그들은 트레이닝 셋과 테스트 셋 양쪽에서 우수한 성능을 발휘하는 고양이를 찾아내는 분류 모델을 만들었습니다.

그러나 학습시킨 분류 모델을 모바일 앱에 배포하자, 모델 성능은 엄청나게 떨어져 버렸습니다.



![pikachu_surprise-600x374](https://i.loli.net/2021/02/06/uVIyoaS65dzqsKM.jpg)



무슨 일이 일어난 걸까요?

당신은 앱 사용자들이 올리는 이미지가 학습시킨 이미지와 다르게 생겼다는 사실을 발견했습니다. 사용자들은 핸드폰으로 촬영한 사진들을 주로 올렸는데, 이런 이미지들은 저해상도에 초점이 나가기도 하는 등 품질이 좋지 않았습니다.

당신의 모델이 학습한 이미지들은 깨끗한 웹사이트 이미지였으므로, 현실 세계에서 마주치게 될 실제 분포(actual distribution)에 대해서는 일반화(generalize)할 수 없었습니다. 실제 분포란, 바로 핸드폰으로 찍은 사진들을 말합니다.

오늘날 빅 데이터의 시대가 도래하기 전, 전체 데이터셋의 7할을 트레이닝 셋으로, 3할을 테스트 셋으로 나누는 것은 꽤 보편적인 규칙이었습니다. 이러한 관습은 잘 작동했지만, 웹사이트 이미지를 쓴 트레이닝 셋의 분포가 **당신이 궁극적으로 신경써야 할** 핸드폰 촬영 이미지들의 분포와 계속 달라지는 상황에서는 좋은 선택이 아니게 됩니다.

우리는 일반적으로 다음과 같이 정의합니다:

- **트레이닝 셋 (Training set)** - 당신이 알고리즘 학습에 사용하는 데이터 셋
- **디벨롭먼트 셋 (Development set)** - 파라미터 튜닝, 피쳐 셀렉션 및 학습 알고리즘과 관련한 의사결정을 내리는 데 사용하는 데이터 셋 (**hold-out cross validation set**)
- **테스트 셋 (Test set)** - 알고리즘이나 파라미터 선택 등이 아니라, 오직 알고리즘의 성능을 평가하기 위해 사용하는 데이터 셋



디벨롭먼트 셋과 테스트 셋을 정의하게 되면, 당신의 팀은 최선의 성능을 만들어내기 위해 학습 알고리즘 파라미터 등에 관한 다양한 가설을 시험할 수 있습니다. 디벨롭먼트 셋과 테스트 셋은 당신의 팀이 알고리즘이 얼마나 잘 작동하는지 신속하게 확인할 수 있도록 해 줍니다.

즉, **디벨롭먼트 셋과 테스트 셋의 목적은 머신러닝 시스템에 가장 중요한 변화를 만들어내는 방향으로 당신의 팀을 가이드하는 것**입니다.

따라서 당신은 다음 지침을 수행해야 합니다:

- **미래에 모델이 학습하게 될 데이터, 따라서 모델이 잘 작동하기를 원하는 데이터를 반영하는 디벨롭먼트 셋과 테스트 셋을 선택하세요.**



당신의 테스트 셋은 단순히 가용 데이터의 3할을 할당하는 것으로는 충분하지 않습니다. 특히 모델 학습에 사용한 데이터셋(웹사이트 이미지)이 미래에 학습하게 될 데이터셋(핸드폰 촬영 이미지)과 본질적으로 다른 특징을 가질 때에는 말이죠.

당신이 만약 모바일 앱을 출시하지 않았다면, 아직 사용자가 한 명도 없을 것이며 미래에 당신이 최적화해야 할 데이터가 무엇인지 정확하게 알 수 없을 겁니다. 그러나 여전히 이를 추정할 방법은 있습니다.

예를 들면, 당신의 친구에게 고양이 사진을 찍어서 보내달라고 부탁해보는 겁니다. 이렇게 함으로써 앱이 출시되었을 때, 당신은 실제 사용자 데이터를 사용한 디벨롭먼트 / 테스트 셋을 업데이트할 수 있게 됩니다.

만약 당신이 미래에 획득하게 될 데이터를 어떻게 해서도 추정할 수 없다면, 아마도 웹사이트 이미지부터 시작해볼 수 있을 겁니다. 그러나 당신은 깨끗한 웹사이트 이미지를 학습시킬 때 모델의 일반화 성능이 시원찮을 것임을 인지하고 있어야 합니다.

훌륭한 디벨롭먼트 셋과 테스트 셋을 구축하는 데 얼마나 많은 리소스를 투자해야 할까요? 이것은 당신의 판단에 달렸습니다. 그러나 당신의 트레이닝 셋 분포가 당신의 테스트 셋 분포와 동일할 것이라고 가정하지는 마세요.

모델 학습에 사용할 수 있는 아무 데이터를 쓰기보다는, 당신의 모델이 궁극적으로 목표해야 할 데이터를 반영하는 테스트 셋을 신중하게 선택하시기 바랍니다.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 이전 글

1. [Why Machine Learning Strategy](https://choigww.github.io/ml%20best%20practice/2021/02/02/Why-Machine-Learning-Strategy/)
2. [How to use this book to help your team](https://choigww.github.io/ml%20best%20practice/2021/02/03/How-to-use-this-book-to-help-your-team/)
3. [Prerequisites and Notation](https://choigww.github.io/ml%20best%20practice/2021/02/04/Prerequisites-and-Notation/)
4. [Scale drives machine learning progress](https://choigww.github.io/ml%20best%20practice/2021/02/05/Scale-drives-machine-learning-progress/)

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)