---
title: "제주로드를 마치며 작성하는 회고록"
categories: Project
toc : true
toc_sticky: true
date: 2022-09-14
last_ modified_at : 2022-09-14
---

# 🍊 제주로드를 마치며..

`Dev.Playground` 라는 이름의 크루를 만들고 활동하면서 처음으로 크루원원들과 함께 참여한 프로젝트 ‘개발자들의 지극히 주관적인 제주도 여행 서포트 서비스, Jeju-Road’를 진행하면서 느꼈던 내용을 회고로 남긴다.

 - Front-End Team [Repository Link](https://github.com/develop-playground/jeju-road-front)
 - Back-End Team [Repository Link](https://github.com/develop-playground/jeju-road-back-end)
 - Android Team [Repository Link](https://github.com/develop-playground/jeju-road-android)

## 🤔 hongbeom

### 제주로드 Android 를 구현하며 느낀 점

시작할 당시에는 빠르게 일감을 정리하고 진행했다. 최대한 여러가지 패턴으로 앱을 구현해보았고, 페이징 처리 및 화면 회전 대응 등의 이슈에 대응하며 성장할만한 포인트가 있었다. 또한 단위 테스트, UI 테스트에 대한 스터디를 진행하며 지식을 쌓고 제주로드에 적용해내서 꽤 재미있었다. 

하지만 시기 상 중간 정도 진행했을 즈음, 새로운 feature가 더 이상 생기지 않아서 텐션이 떨어졌고 코드를 손댈 만한 부분도 없어졌다. 사실 제주로드 앱은 서버에서 내려주는 맛집 리스트를 표시하고, 상세 화면에 대해 표시하는 페이지 2개로만 이루어져 있어서 거의 기능이 없다고 할 수 있다. 사실 일주일 정도의 시간이면 완성할 난이도의 앱인데, 6개월 이상의 시간을 두고 구현하다보니, 루즈해진것 같다. 

백엔드와 API 문서를 공유하며 구현하는 부분은 괜찮은 것 같다. 하지만 최초 API 문서가 발행된 이후 변경점이 생겼을 때, 언제 어떻게 변경이 되었는지 인지하기가 쉽지 않고, 이슈를 체계적으로 관리하지 못했던 것 같다. 노션에 이슈나 feature를 작성하여 일감을 관리했어야 했는데, 꽤 많은 부분이 누락되었다고 느꼈다. 

디자인에 대한 가이드가 명확하게 없어서, 개발자의 수준으로 디자인 요소를 구현해내는 것이 매우 쉽지 않았다. (앱의 완성도가 매우 떨어졌다.) 

사실 다른 팀과의 활발한 소통을 통해 프로젝트를 구현한다기보단, 모바일 팀 내에서의 소통이 99%를 차지한 프로젝트였다고 느꼈다.

- 명확하게 due를 잡고 일감을 관리하면 좋을 것 같다.
- 코틀린 & 자바를 백엔드-모바일 팀은 사용하므로 서로 코드리뷰를 진행해봐도 좋을 것 같다.

## 🤓 junhyung

### 회의

제주로드를 처음 시작할 때는 모두 열의적으로 요구사항 및 의견을 내고 개선점을 도출하는 점이 좋았다. 

어느 정도 프로젝트의 feature가 완료된 후 부터 회의의 목적이 숙제를 검사한다는 느낌을 많이 받았다. 

이를 해결 하기 위해 “일감”와 같은 좋은 제도를 도입한 것은 좋았다. 하지만 그럼에도 주된 원인인 “루즈함"은 완벽하게 없어지지 않아 아쉬웠다. 

회의의 목적이 일감 전달이 아닌, 어느정도의 지식 공유 목적이 있었으면 좋겠다는 생각을 하였다. 우리 데브 크루의 목적은 성장이므로.

### 프로젝트 구현

처음 안드로이드 개발자와 협업을 진행하여 너무 좋았고 기대한 것처럼 여러 가지의 지식 공유, 문제 해결, 원활한 의사소통을 할 수 있어 좋았다.

구성 변경에 대한 대응, 에러 핸들링(Network, Global, Handling Exception), Test Code(Unit Test, UI Test) 세미나 및 구현, Paging, UiState 모델링 등과 같은 이슈를 홍범이와 같이 토론을 하면서 구현할 수 있어 나에겐 좋은 경험이였다. 또한 부족한 지식이나 배워할 지식 등을 세미나를 통해서 진행하여 개인적으로 성장할 수 있는 기회가 되었다. 

다만 페이지가 너무 한정적이고 기능에 비해서 일정이 길어지는 것에 대해서는 아쉬웠다. 다음 프로젝트를 구현할 때는 애자일 스크럼을 도입해서 일정을 짧게 잡고 사이클을 빠르게 돌렸으면 하는 바람이다.

## 😁 junsu

---

> “jeju road” 앱의 인프라 및 데이터 베이스 역할
> 

퍼블릭 환경에서 서비스 가능한 애플리케이션 환경 구현 성공

- 컨테이너 환경 구현: devpg(DB) / jeju-road-api(APP)
- 퍼블릭 도메인 주소: http://bulltakbulltak.duckdns.org:8080/api/restaurants

> 팀과의 협업
> 

인프라 및 데이터 베이스 구현은 프로젝트 중반 쯤 모두 완료 되었으며 이후 데이터 팀의 프로젝트 기여할 부분이 줄어들어 프로젝트 외 협업할 수 있는 세미나 진행 / 참여

- 진행: [Paging SQL](https://www.notion.so/Paging-SQL-cf763c4fbf9c4a999c2b07fbd6434317) [RDBMS NULL](https://www.notion.so/RDBMS-NULL-9146ba9442034604b65d549539ef81fd)
- 참여: [Git Flow](https://www.notion.so/Git-Flow-08384c01ff2040f9a2c94d116f5e71af) [Dragonfly DB 세미나](https://www.notion.so/Dragonfly-DB-7727496545844623b3c05be2db9a6171)

> 개인 총평
> 

ERD 모델을 구현하는데 총 3차에 걸쳐 모델 안을 구현하였지만 데이터가 발생하는 시점에 고려되지 않은 ERD 모델이 발견되어 여러번의 모델 변경이 발생 했습니다.

- 컬럼 성격을 제대로 파악하지 못해 “테이블 컬럼 수정”
- 팀원 별로 로컬 환경에서 테스트를 하다보니 테이블의 DDL이 변경 되는 부분을 놓침 “테이블 재정의”

ERD 모델 구현에서 놓쳤던 부분들을 파악하여 향후 프로젝트에서는 좀 더 효율적이고 유연하게 처리를 할 수 있을것으로 보입니다.

## 😏 cheolho

우리는 더 잘 할 수 있었다. 그런데 우리는 왜 더 잘하지 못했을까?

이번 회고록에서는 더 잘하지 못했던 이유를 팀 단위 차원과 개인적인 차원으로 구분하여 이야기해보려고 한다.

### 내가 어떻게 행동했기에, 이런 결과를 가져왔는가

최근 이직을 하게 되면서 크루활동에 대한 열정이 한풀 꺽인 것이 사실이다. 크루 프로젝트에 대한 목적을 너무 이직을 위한 포트폴리오로 두어서 이런 상황이 발생하지 않았을까 한다. 그렇다면 이제 나에게 있어 크루 프로젝트의 새로운 의미를 찾아야할 텐데, 그것을 어디서 찾아야할지는 앞으로의 숙제라고 생각한다.

현재로서 나의 가장 큰 관심사는 ‘수정하기 쉬운 코드'인데, 이러한 목적을 성취하기 위해서는 단순하지만 달성하기 어려운 조건들이 몇몇 있다. 예를 들어,

- 가독성이 좋아야한다
- 코드를 이루는 각 모듈 간에 결합도가 낮아야한다.
- 각 모듈에 대한 책임이 명확해야한다
- 등등…

이러한 조건들을 달성하기 위한 선지자들의 여러 지침들이 있고, 이러한 지침들을 실험적으로 적용해본 뒤 결과를 맞보는 것에 우선적으로 크루 프로젝트에 대한 나의 첫 번째 의미를 찾을 계획이다.

### 제도적인 측면에서, 어떤 것들이 부족했는가

지금까지 이행되어 왔던 크루의 제도의 목적은 ‘참여를 지속적으로 이끌어가는 것'이었다. 반은 성공했고, 반은 실패했다고 본다. 어쨋든 현재의 크루가 계속 이어져왔으니 반은 성공했고, 모든 참여 구성원들이 남아 있는 것은 아니니 반은 실패했다. 지속적인 참여를 유도하기 위해 책임에 대한 부담감을 최대한 줄이려고 하였으나, 여러가지 문제가 있었다. 

첫 번째로는 너무 루즈한 진행 속도로 인해 빠르게 달려가고 싶은 멤버들의 열정이 줄어들게 만들었다. 예전 대학원생 시절 교수님께서 수업을 진행하실 때 상위 25% 학생들을 바라보고 수업 준비하시는 모습을 봤었는데, 그 이유를 어느 정도 공감할 수 있을 것 같다. 앞으로의 제도들은 열정을 가지고 있는 멤버들을 바라보고 구비되어야 하지 않을까?

두 번째로는 명확한 책임할당 개념이 없었다. 크루 활동에 대한 부담감을 줄이려 개인에게 부여되는 책임을 최대한 줄이려고 하였는데, 이 부분이 모든 계획들을 흐지부지하게 만든 것 같다. 앞으로의 제도들은 명확한 책임할당을 기반으로 해야하지 않을까

## 😎 byeongsoon

### 협업에는 확실한 규칙과 의사소통이 필요하다

개개인이 공부를 진행하며 해왔던 프로젝트와는 다르게 제대로 된 협업이 이번 제주로드 프로젝트 였던 것 같다. Front-End, Back-End, Android, DB/Infra 4개의 팀으로 나누어 각자의 역할을 분배하고 서로 간의 업무를 연결시킬 인터페이스도 함께 맞춰가며 프로젝트를 시작했다.

초반에는 모두의 열정과 설렘으로 진행속도가 빠르게 진행되는 듯 했다. 하지만 각 팀의 열정이 평균적일 수 없었다. 한 팀의 열정에 비해 진행 속도가 더디니 그 팀은 열정이 식고, 다른 팀의 열정이 올라가면 다른 팀들의 사기가 이미 저하되어 있다고 판단되어 개발 속도는 점점 느리게, 또 안좋게 가는 악순환이 반복되고 있었다.

회사가 아닌 정말로 개발을 좋아하는 사람들끼리 어쩌면 개인의 시간을 쪼개서 진행한다는 것은 사실 쉬운일은 아니다. 단지 결과물과 그 과정에서 본인의 성장을 위해 투자하는 시간으로 강요할 수는 없다. 하지만 확실히 협업을 진행할 땐 모두의 확고한 목표와 방향성이 같아야만 그 열정을 서로에게 전달할 수 있고, 충분한 의사소통이 없이는 각 팀을 바라보는 시선이 ‘작업을 하는지?’,  ‘관심이 없는지?’ 알 수 없기 때문에 솔직하고 궁금한 내용은 명확하게 공유하여 의사소통을 진행해야 한다.

### 프로젝트 구현은 나를 성장하게 만든다

개발자를 꿈꾸며, 학부생 시절부터 대학원, 장교로 군생활 중에도 개발 공부를 뼈를 깎는 정도는 아니지만 꾸준히 관심을 가지고 공부했다. 혼자의 공부시간도 많았지만 대학교 연구실 소속일 땐 간단한 연구나 프로젝트에 참여해 신기술도 적용해보고 다양한 분야의 프로젝트도 진행했다. 백엔드 개발자를 준비하며 여러 회사의 지원자격 및 우대사항처럼 그 회사에서 사용하는 언어, 프레임워크, DevOps, 인프라 등 내가 기존에 알고있는 것보다는 훨씬 많고 다양한 기술이 존재한다.

이번 제주로드를 진행하면서 기존에 알고있던 지식에 더불어 최근 많이 유행하는 기술, 혹은 코드에 적용했을 때 더 효과적인 결과를 가져올 만한 것들을 적용하며 개인적인 성장을 많이 이루었던 것 같다. 대표적으로 기억에 남는 작업은 Github Actions를 활용한 CI/CD 구축으로 빌드와 배포 자동화를 한 것이다. 과정으로 프로젝트는 main 브랜치로 push 혹은 Pull Request가 Merge 될 때를 트리거로 동작해 빌드 후 DockerHub에 push가 된다. 제주로드를 배포 한 데이터 팀의 개인 서버에서는 Actions의 Runner를 통해 작성해 둔 스크립트가 실행되고 이를 통해 최신 버전의 프로젝트를 자동으로 배포할 수 있게 만들어 둔 것이다.

이 외에도 평소와는 다른 방식인 Mapper 사용, API 개발 후 발생한 트러블 슈팅, 테스트코드 작성 등 프로젝트는 성장의 발판이며 지난 실력을 확인할 수 있는 지표라고 생각한다.
