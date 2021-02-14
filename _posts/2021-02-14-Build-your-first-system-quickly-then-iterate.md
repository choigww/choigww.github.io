---
title: Build your first system quickly, then iterate
date: 2021-02-14 15:30:03
categories:
- ML Best Practice
tags:
- Machine Learning Yearning
---

당신은 새로운 스팸 메일 차단 시스템을 만들고자 합니다. 팀원들은 다음과 같은 아이디어를 내놓았습니다:

# Build your first system quickly, then iterate

- 학습에 사용할 스팸 메일 데이터를 가능한 많이 수집하자. 예를 들면, 일종의 "허니팟"을 이용해 스팸 메일을 유도해 보자. 잘 알려진 스팸 메일 전송자들에게 가짜 이메일 주소들을 제공하면 자동적으로 스팸 메시지들을 수집할 수 있다.
- 이메일의 문자열 내용을 이해하기 위한 피쳐들을 개발하자.
- 메시지가 거쳐 온 인터넷 서버들을 보여주는 envelope(SMTP 클라이언트-서버 통신)와 header(이메일 메타데이터) 정보를 이해하기 위한 피쳐들을 개발하자.
- 기타 등등.



스팸 차단 문제로 야근까지 했지만, 당신은 여전히 어떤 방향이 좋을지 고르지 못하고 있습니다. 당신이 스팸 차단 어플리케이션 분야의 전문가가 아니라면 더욱 고르기 어려울 겁니다.

그러니 시작부터 완벽한 시스템을 설계하고 구축하려고 해서는 안 됩니다. 대신, 기본 시스템을 구축하고 빠르게 학습시키세요. 며칠 걸리지 않을 겁니다. 기본 시스템이 당신이 만들 수 있는 "최상의" 시스템에 한참 못 미치더라도, 기본 시스템이 어떻게 동작하는지 빠르게 살펴볼 수 있는 것은 매우 가치있는 일입니다. 시간을 투자할 가치가 있는 가장 유망한 방향성을 알려주는 단서들을 빠르게 발견할 수 있으니까요.

다음 몇 개의 챕터를 통해 이러한 단서들을 어떻게 읽는 지 알려드리고자 합니다.





*위 조언은 연구논문이 아니라 인공지능 어플리케이션을 구축하고자 하는 독자들을 위한 것입니다. 연구 부문의 주제에 대해서는 나중 챕터에서 살펴보겠습니다.*

---

[deeplearning.ai](https://www.deeplearning.ai)를 이끄는 Andrew Ng의 책, [MACHINE LEARNING YEARNING](https://d2wvfoqc9gyqzf.cloudfront.net/content/uploads/2018/09/Ng-MLY01-13.pdf?utm_campaign=MLY%20Ebook%20Email&utm_medium=email&_hsmi=78646066&_hsenc=p2ANqtz-8EN6pTX4f_zSAT80ls6z_VnjtNqRW5_6H7bwAgac2tcKhJ0ZXMwNquIMXhBZzXz2nL9v2cwqsEnEeEOlFfen_ZyuVQtw&utm_content=78646066&utm_source=hs_automation)은 머신러닝 프로젝트 수행에 있어 반드시 알아야 할 개념과 노하우를 담고 있습니다. 총 58편으로 이루어진 이 책을 1편씩 번역하여 게재합니다.

### Machine Learning Yearning 전체 목록 보기

- [전체 글 리스트](https://choigww.github.io/tag/#/Machine%20Learning%20Yearning)