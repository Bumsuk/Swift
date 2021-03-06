# About Concurrent programming

~~잘못 설계된다면..~~

<img src="./assets/multiprocessing.gif">

## Table of Contents
- Processor, CPU, Core의 차이

- Concurrency(병행성)와 Parallelism(병렬성)의 차이

- Process와 Thread의 차이

- 멀티 프로세싱, 멀티 태스킹, 멀티 쓰레딩의 차이

## Processor, CPU, Core의 차이

### Processor
프로세서는 컴퓨터 운영을 위해 기본적인 명령어들을 처리하고 반응하기 위한 논리회로입니다. 종종 시스템 내에서의 CPU를 말하기 위해 사용되기는 하지만, 일반적으로 컴퓨터 시스템 내에는 여러개의 프로세서들이 혼합되어져 있습니다.

ex) CPU, GPU, VPU, TPU ...

### CPU

컴퓨터에서 구성 단위 중 기억, 연산, 제어의 3대 기능을 종합하는 장치인 Central Processing Unit(중앙 처리 장치)의 줄임말입니다. 컴퓨터의 대뇌라고 할 정도로 가장 중요한 부분으로, 프로그램의 명령어를 해석하여 데이터를 연산/처리를 하는 부분, 혹은 그 기능을 내장한 칩을 말합다.  컴퓨터가 동작하는 데 필요한 모든 계산을 처리합니다. 컴퓨터를 뇌에 비유하자면 단기기억 담당은 RAM, 장기기억은 하드디스크, CPU는 사고를 담당하는 대뇌피질 정도로 볼 수 있습니다. GHz단위의 한번의 정보 처리량을 통해 CPU 사양을 알 수 있습니다.

### Core

CPU내에서 연산을 담당하는 핵심요소입니다. 많을 수록 일반적으로 처리속도가 빨라집니다. (듀얼코어, 쿼드코어, 헥사코어, 옥타코어...)

## Concurrency(병행성)와 Parallelism(병렬성)의 차이

<img src="https://cdn-images-1.medium.com/max/1600/1*_4B2PKsJn9pUz3jbTnBnYw.png">

**Concurrency는 프로그램의 성질이고 parallel execution은 기계의 성질입니다.**  
Concurrenty is a property of the program and prallel execution is a property of the machine.



### Concurrency
어떤 **프로그램이나 알고리즘이 순서에 상관없이 동시에 수행**될 수 있다면 concurrent하다고 말합니다.  예를 들어, 1부터 100까지 숫자를 더하는 과정을 생각해보면 숫자 100개를 여러 부분 집합으로 나눈 뒤 동시에 부분합을 구합니다. 그리고 이 부분합을 다시 더하면 원래 얻고자 하는 값을 얻을 수 있습니다. 이 때 이 알고리즘은 concurrent하다라고 말합니다.

Concurrent한 프로그램은 싱글코어 머신에서도 분명히 돌아갑니다. 뮤텍스, 데드락은 싱글코어에서도 얼마든지 그 의미를 갖습니다. 멀티스레드 프로그램이 비록 물리적인 제약으로 싱글코어에서 시분할 형태로 돌아가지만 겉으로는 concurrent하게 작동한다고 속일 수 있습니다. 반대로 아무리 멀티스레드로 작성된 프로그램이라 하더라도 멀티코어가 아니라면 병렬로 작동한다고 말하지 못합니다.


### Parallelism

위에서 1부터 100까지 더하는 알고리즘이 정말 물리적으로 병렬로 돌아갈지 아닐지는 이 알고리즘이 어떤 하드웨어 위에서 돌아갈지 알아야만 확답할 수 있습니다. 방금 이야기한 알고리즘이 멀티 프로세서 머신에서 돌아가야 병렬 실행된다라고 말할 수 있습니다. Parallel execution은 따라서 프로그램의 성질보다는 하드웨어의 성질입니다.

OpenMP, MPI, CUDA 같은 프로그래밍 방법론은 병행 프로그래밍 보다는 병렬 프로그래밍이 옳은 표현합니다. 언급한 세 방법론 모두 물리적으로 제공되는 다양한 **병렬 하드웨어**를 활용하기 때문입니다.


## Process와 Thread의 차이

### Process
컴퓨터에서 **프로세서에 의해 연속적으로 실행되고 있는 컴퓨터 프로그램, 즉 운영체제로부터 자원을 할당받는 작업의 단위**입니다. 종종 스케줄링의 대상이 되는 작업(task)이라는 용어와 거의 같은 의미로 쓰입니다. 프로그램은 실행이 되기 전의 명령어와 데이터의 묶음인데, 이러한 정적인 요소인 프로그램이 실행 중에 있을때 그것들을 우리는 프로세스라고 말합니다.

다시 말해서, 하드디스크에 저장되어 있는 명령어와 데이터의 묶음 자체는 프로그램이며, 프로세스는 그러한 프로그램을 구동하여(실행하여), 프로그램 자체와 프로그램의 상태가 메모리 상에서 실행되는 작업단위를 말합니다.

일반적으로 CPU는 한번에 하나의 프로세스만 관리할 수 있습니다.

### Thread

스레드(thread)는 어떠한 프로그램 내에서, 특히 **프로세스 내에서 실행되는 흐름의 단위**를 말합니다. 일반적으로 한 프로그램은 하나의 스레드를 가지고 있지만, 프로그램 환경에 따라 둘 이상의 스레드를 동시에 실행할 수 있습니다.

실행 중인 프로그램을 프로세스라고 했는데, 스레드는 그러한 프로세스 내부에서 실행되는 흐름의 단위 입니다. 즉 프로세스의 내부에 있는 개체를 말합니다. 하나의 프로세스에는 최소 하나이상의 스레드가 존재합니다. 하나의 스레드가 있을 때는 단일 스레드라고 말하며 두개 이상의 스레드가 존재하면 멀티스레드, 다중스레드라고 말합니다.

### 차이

프로세스는 자신을 실행할 프로세서를 할당받으며 필요한 메모리공간과 데이터등을 할당받습니다.

그리고 스레드란 이러한 프로세스 안에서 실행되는 흐름의 단위로써, 프로세스 안에서의 주소나 데이터를 스레드 간에 공유하면서 실행됩니다.

스레드가 존재함으로써 데이터와 같은 자원을 메모리에 할당하는 동작이 줄어들어서 자원을 효율적으로 관리하고 운영할 수 있습니다. 또한 프로세스간의 전환 속도보다 스레드간의 전환 속도가 빠르게 됩니다.

하지만 스레드를 사용하면 동일한 데이터를 전역 변수로 이용하므로 다양한 문제가 발생될 수 있다는 단점이 있습니다.


## 멀티 프로세싱, 멀티 태스킹, 멀티 쓰레딩의 차이

### 멀티 프로세싱
<img src="https://t1.daumcdn.net/cfile/tistory/2776454A56BDA67F29" width=400>

멀티 프로세싱은 한마디로 말해서 **'두개 이상, 다수의 프로세서 (CPU) 가 협력적으로 작업을 동시에 처리하는 것'** 입니다.

각각의 프로세서가 하나의 작업만을 처리하는 것이 아니라 다수의 작업을 처리하며, 하나의 작업은 하나의 프로세서에 의해 처리되는 것이 아니라 다수의 프로세서에 의해 처리됩니다.

멀티 프로세싱을 하는 장점으로는 여러가지가 있습니다.

먼저 프로세서를 여러 개 사용하여 여러 개의 작업을 동시에 수행함으로써 작업 속도를 높일 수 있습니다.

또한, 만약 하나의 프로세서가 하나의 작업만을 처리한다면 특정 프로세서가 고장이 났을 때 해당 작업은 정지됩니다. 하지만 멀티 프로세싱을 사용한다면 작업은 정지되지 않습니다. 단지 속도가 느려지는 정도의 손해만 발생하는 등 신뢰성이 증가합니다.

**즉, 여러 프로세서를 사용하여 여러 작업(프로세스)을 동시에 수행하는 것 입니다.**

### 멀티 태스킹

<img src = "https://t1.daumcdn.net/cfile/tistory/2530B93856BDDFD107" width = 400>

다수의 Task(프로세스보다 보다 확장된 개념)를 운영체제의 스케줄링에 의해 번갈아 가면서 수행하는 것 입니다. 프로세서가 각각의 Task를 조금씩 자주 번갈아가면서 처리하기 때문에 사용자는 마치 동시에 여러 Task가 수행되는 것처럼 보게 됩니다. 우리가 컴퓨터로 워드를 작성하면 멜론 PC로 노래를 듣는 것 역시 멀티태스킹 입니다.

**즉, 하나의 프로세서 상에서 여러 작업(프로세스)을 번갈아가며 (분할) 동시에 가깝게 보이도록 수행하는 것 입니다.**

### 멀티 쓰레딩

하나의 프로세스 내에는 여러 개의 스레드가 존재하게 됩니다. 또한 이런 다수의 스레드는 하나의 데이터 자원을 공유 합니다. 때문에 메모리에 대한 효율성을 가질 수 있습니다.

멀티 프로세싱과의 차이점을 말하면,
멀티 스레딩은 **하나의 프로그램 안에서 병렬 처리의 이점을 보는 것**이며
멀티 프로세싱은 여러 개의 프로그램들을 병렬로 처리할 수 있는 것입니다.

멀티 스레딩의 장점으로는 **자원을 공유하여 메모리에 대한 효율성을 가져올 수 있는 것과 이로 인해 경제성 또한 증가하는 것** 등이 있습니다. 더불어 프로세스 생성과 소멸에 비해 스레드 생성 소멸이 훨씬 적은 자원을 필요로 합니다. 또한 멀티 프로세스는 서로 간의 자원이 공유되지 못하기 때문에 자원 전달을 위해서는 IPC를 구현해야 하며, 멀티 스레딩에 비해 운영체제에 부담을 줄 수 있습니다.

그러나 멀티 스레딩은 동시에 복수 개의 코드가 같은 주소 공간에서 실행됨으로써 서로 간섭하고 영향을 주는 경우가 빈번하여 주소 공간 분리의 이점이 없고, 스레드간의 실행 순서를 전혀 예측 할 수 없어 디버깅이 어렵습니다. 또한 **공유자원(메모리지역의 전역변수)을 보호하기가 어렵습니다.** (Critical Section 문제)

#### Deadlock
멀티 스레드 중 스레드간에 대기 상태가 종료 되지 않아 무한정 대기만 하는 비정상적인 상태입니다.

### 정리

이를 총 정리하자면 다음과 같습니다.
> Multi-processing : run in parallel on several processors
Multi-tasking : run several processes in parallel
Multi-threading : run several threads in parallel and manged by the process

<img src="https://t1.daumcdn.net/cfile/tistory/2576BC335977D4910E" width = 600>


### Reference:
  - http://12bme.tistory.com/184
  - http://donghoson.tistory.com/14?category=799810
  - http://eaco.tistory.com/1
