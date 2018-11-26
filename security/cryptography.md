# Cryptography

암호화 서비스는 전송 중인 데이터(보안 통신)와 유휴 데이터(보안 스토리지)를 보호하는 기반이 됩니다. 즉, 정보를 보호하기위한 수학적, 언어학적인 방법을 다루는 것이며, 컴퓨터과학, 수학, 언어학과 관련이 깊습니다. 암호학은 크게 두 가지 분류라 나누어 집니다. **1. 쌍방향 암호시스템과 2. 단방향 암호시스템** 이 그것이며, 쌍방향 암호시스템은 다시 **1.1 대칭 키 암호시스템과 1.2 공개 키 암호시스템  1.3스테가노그래피 등** 으로 나누어집니다.

정교한 수학을 사용하면 다음과 같은 이점이 있습니다.

- 외부 관찰자가 이해할 수 없도록 데이터 암호화 및 암호 해독

- 데이터가 원래 해싱, 서명 및 확인에 의해 전송되었기 때문에 수정되지 않았는지 확인합니다.

## Encryption and Decryption

암호화는 데이터를 다시 변환하는 방법을 알고 있는 사람을 제외하고 읽을 수 없는 형태로 변환하여 데이터를 보호하는 방법 중의 하나입니다.

암호화는 일반적으로 전송 중인 데이터와 유휴 상태의 데이터를 보호하는 데 사용됩니다. 신뢰할 수 없는 통신 채널을 통해 정보를 보내야 하는 경우 암호화를 사용하여 통신을 보호하는 것은 두 엔드포인트의 책임입니다. 마찬가지로 로컬 디스크에 정보를 저장할 때, 컴퓨터를 도난 당하더라도 제3자가 정보를 읽을 수 없도록 하기 위해 암호화를 사용할 수 있습니다.

암호라고 하는 암호화 기술은 여러 가지 방식으로 작동하고 다양한 용도로 사용할 수 있습니다.


## 1. 쌍방향 암호시스템

쌍방향 암호시스템이란 평문과 암호문 사이의 변환이 자유로운 암호체계입니다. 즉 특정 키를 통하여, Encryption과 Decryption이 가능하다는 것 입니다.

### 1.1 대칭키 암호시스템

대칭 키 암호 시스템은 암호를 해독하는 데에 사용하는 키와 암호를 만드는 데 사용하는 키가 같은 암호화 기법으로, 제작이 단순하지만 상대적으로 보안성이 낮으며, 또한 여러 사람이 사용할 경우 각자 메세지를 주고받기 위해서는 각자마다 다른 키가 필요한 점이 단점입니다.

대칭 암호화에서 단일 키(일반적으로 긴 랜덤 바이트 문자열)는 수학적으로 정보를 변환하는 데 사용되며 나중에 원래 정보를 검색하는 데 역방향으로 사용됩니다.

<img src = "https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Art/security_symmetric.jpg">

대칭 암호화는 보안 통신에 사용되는 경우가 많습니다. 그러나 두 엔드포인트는 동일한 비밀 키를 알아야 하므로 대칭 암호화만으로는 충분하지 않습니다.

카이사르 암호, 비즈네르 암호, 스키테일 등의 예가 있습니다.

### 1.2 공개 키 암호 시스템

공개 키 암호 시스템은 위의 대칭키 암호 시스템에서의 보안성과 기하급수적으로 늘어나는 키의 개수를 개선하기 위한 방법으로, **암호화에 사용되는 키와 복호화에 사용되는 키가 다릅니다.** 때문에 비대칭키 암호시스템이라고도 불립니다. 처리해야 하는 정보량이 많기 때문에 컴퓨터가 발명되고 난 뒤에 생겼습니다.

정보를 변환하기 위해 수학적으로 관련된 두 개의 키가 사용됩니다. 한 키로 암호화된 정보는 다른 키로만 해독할 수 있으며 그 반대의 경우도 마찬가지입니다. 일반적으로 이러한 키 중 하나(개인 키)는 기밀로 유지되며 다른 키(공용 키)는 광범위하게 사용할 수 있습니다. 타인이 메시지를 암호화할 때 사용하는 공개키(Public Key)와 암호문을 원래의 메시지로 복원할 때 쓰는 비밀키(Private key)로 구성돼 있어 두개의 키를 사용합니다.

두 키는 수학적으로 관련되어 있지만 다른 키에서 한 키를 추출하는 것은 계산적으로 불가능한 것으로 간주됩니다.


<img src="https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Art/security_asymmetric.jpg">

비대칭 암호화가 공유 통신 채널을 설정하는 데 사용되는 경우가 많습니다. 비대칭 암호화가 계산적으로 비싸기 때문에 두 엔드포인트는 비대칭 암호화를 사용하여 대칭 키를 교환한 다음 훨씬 더 빠른 대칭 암호화 알고리즘을 사용하여 실제 데이터를 암호화하고 암호를 해독합니다.

또한 신뢰도를 설정하는 데 비대칭 암호화를 사용할 수 있습니다. 개인 키로 정보를 암호화하면 다른 사용자가 공용 키로 해당 정보를 읽고 사용자가 해당 정보를 암호화했는지 확인할 수 있습니다.

### 1.3 Steganography

전달하려는 정보를 이미지, 오디오 등의 파일에 인간이 감지할 수 없도록 숨겨져 상대방에게 전달하는 기술의 총칭입니다. 기존의 암호화 방법은 메시지를 암호화하여 정보를 보호하는 반면에 스테가노그래피는 비밀정보를 매체에 은닉하여 그 정보의 존재 자체를 감추는 보안 기술입니다.

<img src="https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Art/security_steganography.jpg">

## 2. 단방향 암호시스템

단방향 암호시스템이란 평문에서 암호문으로 만드는 것은 자유지만 그 반대는 아닌 암호체계입니다. 대부분이 해쉬 암호화 체계로 이루어져 있습니다.