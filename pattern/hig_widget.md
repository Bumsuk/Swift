# Widget

애플이 권장하는 가이드는 다음과 같습니다.

- **한눈에 훑어볼 수 있게**

사람들은 간단한 업데이트를 받고 아주 단순한 작업을 수행하는데에 위젯을 사용함
그러므로 적절한 양의 정보와 인터랙션을 제공하는 것이 필수적
가능하면 한 번의 탭으로 완료 할 수 있는 작업을 제공할 것
이동(pan) 및 스크롤 제스처는 지원안함

- **컨텐츠 표시는 신속하게**

사람들은 위젯을 볼때 아주 적은 시간을 들이며, 컨텐츠 로딩을 기다리지 않음
그러므로 정보를 캐시해서 새 정보 로딩중에도 항상 최근 정보가 표시되게 할 것

- **충분한 여백과 패딩**

컨텐츠를 위젯 영역 끝까지 채우지 말고 적어도 몇 픽셀은 여백을 줄 것
위젯 상단의 앱 아이콘의 센터에 컨텐츠 좌측 정렬 라인을 맞추면 적당함
그리드 형태의 레이아웃이라면 아이템을 한 행에 4개 정도로 제한

- **다양한 해상도 대응**

축소형은 대략 2.5행의 높이
확장형은 화면 높이보다 길어지지 않게
퀵액션 위젯은 축소형만 표시됨
축소형에서는 단독으로도 의미있는 필수 정보를 표시할 것

- **배경 커스터마이징은 피할 것**

블러 처리된 밝은 기본 배경은 일관성과 가독성을 위한 것
사진 배경을 절대 사용하지 말것. 잠금 화면 및 홈 화면 배경과 충돌할 수 있음
텍스트는 검정 혹은 어두운 회색의 시스템 폰트 사용

- **시스템 폰트는 가독성을 위해**

어두운 컬러는 기본 배경 컬러에 잘 맞음
앱을 실행시켜서 추가적인 작업을 할 수 있게 하라
위젯은 앱과 독립적으로 동작해야 함
공간만 차지하는 "앱으로 열기"같은 버튼을 넣지 말것. 그대신 컨텐츠 자체를 탭하게.
절대 다른 앱을 실행시키지 말것

- **올바른 이름 선택**

위젯 컨텐츠 상단에 아이콘과 제목 표시됨
위젯이 하나라면 보통은 앱 이름과 일치시킴
위젯이 여러개라면 대표 위젯에 앱 이름과 동일한 이름, 나머지는 명확하고 간결하게
이름 앞에 앱 이름을 붙여주는 것도 좋음. 그 앱에서 제공하는 위젯이라는걸 알림

- **로그인이 필요한 경우 알림**

로그인 기반의 컨텐츠라면, "로그인하면 해당 컨텐츠를 볼 수 있다"라고 알릴 것
퀵 액션용 위젯 선택
위젯이 여러개인 경우 하나를 선택해서 표시
