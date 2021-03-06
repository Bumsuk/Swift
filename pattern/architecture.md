# Swift 아키텍쳐 패턴

아키텍쳐 패턴이란 주어진 상황에서의 소프트웨어 아키텍쳐에서 일반적으로 발생하는 문제점들에 대한 일반화되고 재사용 가능한 정형화된 해결 패턴을 말합니다. 이러한 패턴을 적용하면 코드의 가독성, 유지보수, 협업 등이 쉬워지며, 비슷한 상황을 마주하였을 때, 더욱 빠르고 유연하게 대처할 수 있습니다.

일반적으로 여러 아키텍쳐 패턴들의 공통적인 특징이자 장점은 화면에 보여주는 로직(View)과 실제 데이터가 처리 되는 로직(Model)을 분리한다는 것 입니다.

종류로는 웹 개발시 많이 쓰이는 MVC부터 시작해서 파생되어 나온 MVP, MVVM, Viper 등등 많은 패턴들이 있습니다.

## 아키텍쳐를 선택하는 것을 소흘히 하게 되면

- 하나의 class에서 목적이 다른 수많은 일을 하게 됨
- 그런 대형 class에서 버그가 있을 시 디버깅하는 것이 어려워짐
- 그러면, 중요한 세부사항을 놓치기 마련

## 나쁜 아키텍쳐의 예시

- 데이터가 UIViewController에서 직접적으로 저장됨
- UIView는 거의 아무것도 하지 않음
- Model은 단지 dumb data structure 역할
- Unit Test가 아무것도 커버하지 못함

## 그러면, 좋은 아키텍쳐란

- Distribution : 엄격한 role에 의해 각 entities 사이에 잘 균형된 책임(단일 책임 원칙)
- Testability : 테스트 가능한 코드
- Ease of use : 낮은 유지보수 비용 (적은 코드 = 적은 버그)

## MV(X) Series

MVC
MVP
MVVM
VIPER
