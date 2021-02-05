---
title: Why Machine Learning Strategy
date: 2021-02-02 20:27:45
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
- Andrew Ng
- deeplearning.ai
- 머신러닝 실무 지침
---

머신러닝은 웹 검색, 이메일 스팸 차단, 음성 인식, 제품 추천 등 수없이 많은 어플리케이션의 기초입니다. 나는 당신 또는 당신의 팀이 머신러닝 어플리케이션 업무를 담당하고 있으며, 빠르게 발전하기를 원한다고 가정하겠습니다. 이 책은 당신이 머신러닝 어플리케이션 분야에서 빠르게 성장하도록 도와줄 것입니다.

# Why Machine Learning Strategy

## Example: Building a cat picture startup

당신이 고양이 애호가들을 위해 끝없는 고양이 사진 스트림을 제공하는 스타트업을 만든다고 해 봅시다.

![image-20210202230619592](https://i.loli.net/2021/02/02/f1WwYOi9k6dhJlc.png)



당신은 무작위 사진들로부터 고양이를 찾아내는 컴퓨터 비전 시스템을 구축하기 위해 뉴럴 네트워크를 사용하고자 합니다.

그러나 안타깝게도, 당신이 쓰는 학습 알고리즘의 정확도가 영 시원치 않습니다. 당신은 어떻게 해서든 고양이 사진 탐색기를 개선해야만 한다. 무엇을 해야 할까요?

당신의 팀은 다음과 같은 아이디어를 내놓았습니다:

- **데이터를 더 모으자**: 고양이 사진을 더 수집한다.
- **더 다양성을 가진 트레이닝 셋**을 수집한다. 예를 들어,
  - 이상한 곳에 위치한 고양이 사진
  - 이상한 색상을 가진 고양이 사진
  - 다양한 카메라 설정을 적용한 고양이 사진
- **알고리즘을 더 길게 학습**한다
  - gradient descent iteration을 더 돌려본다
- **더 큰 뉴럴 네트워크**를 시도한다
  - 레이어, 히든 유닛, 파라미터를 늘린다
- **더 작은 뉴럴 네트워크**를 시도한다
- **정규화**를 추가해 본다
  - 예: L2 regularization
- **뉴럴 네트워크 구조**를 변경한다
  - 활성화 함수, 히든 유닛 갯수, 기타 등등
- ...


위와 같은 가능한 선택지들을 당신이 잘 선택했다면, 당신은 업계 1위 고양이 사진 플랫폼을 구축하여 회사를 성공으로 이끌게 되겠죠. 선택이 잘못되었다면 수 개월을 날릴 겁니다. *어떻게* 하면 좋을까요?

이 책은 바로 그 *어떻게* 를 알려줄 겁니다. 대부분의 머신러닝 문제들은 무엇이 시도해 볼 가치가 있고, 무엇이 없는가를 알려주는 단서를 남깁니다. 그런 단서들을 읽는 법을 배움으로써 당신은 수 개월, 수 년의 개발시간을 단축할 수 있습니다.



---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)