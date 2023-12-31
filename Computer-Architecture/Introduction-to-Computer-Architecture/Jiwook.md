# 목차 
[1. 컴퓨터의 기본 구조](#컴퓨터의-기본-구조) <br>
[2. 정보의 표현과 저장](#정보의-표현과-저장) <br>
[3. 시스템의 구성](#시스템의-구성) <br>
[3-1. CPU와 기억장치의 접속](#cpu와-기억장치의-접속) <br>
[3-2. CPU와 I/O 장치의 접속](#cpu와-io-장치의-접속) <br>
[4. 컴퓨터 구조의 발전 과정](#컴퓨터-구조의-발전-과정) <br>

## 컴퓨터의 기본 구조
<img src="https://github.com/hdaisywd/CS-Study/assets/102342953/592a735f-e0f0-4774-9c73-488178994722">

- 중앙처리장치(CPU) <br>
  컴퓨터 시스템 전체를 제어하는 장치로써 입력장치에서 입력받은 데이터를 처리한 후 출력장치와 기억장치로 보내는 일련의 과정을 수행한다. 즉, 컴퓨터의 두뇌라고 할 수 있다. <br>
  - 산술논리연산장치(ALU) <br>
  CPU의 해심 요소로써 산술연산과 논리연산을 수행한다. <br>
  - 제어장치(CU) <br>
  CPU 내부에서 일어나는 모든 작업을 통제하고 관리한다. <br>
  제어장치는 적절한 순서로 명령어를 인출하고 그 명령어를 해석한 결과에 따라 컴퓨터 시스템의 필요한 부분으로 제어신호를 전달한다.
  
- 기억장치(MU)
  - 주 기억장치(내부 기억장치) <br>
    컴퓨터 시스템에서 수행되는 프로그램과 수행에 필요한 데이터를 기억한다. <br>
    CPU에 접근하는 속도가 비교적 빠르며 많은 양의 데이터를 기억할 수 있다. <br>
    현재 주 기억 장치로는 **RAM**을 사용한다.(휘발성) <br>
  - 보조기억장치(외부 기억장치) <br>
    반영구적으로 데이터를 저장하고 보존할 수 있다. <br>
    그러나 보조기억장치에 저장된 데이터는 CPU와 직접 정보를 교환할 수 없기 때문에 주 기억장치로 옮겨진 후 처리된다. <br>
    보조기억장치에는 하드 디스크, SSD, USB 메모리, DVD, CD-ROM 등이 있다. <br>

<img src="https://github.com/z-wook/z-wook/assets/101041221/e87d5255-8516-4024-92c0-99ba55f8d515">
<br>

- 입력 장치 <br>
  컴퓨터에서 처리할 데이터와 정보를 외부에서 입력할 수 있게 해준다. <br>
  입력장치에는 키보드, 마우스 등이 있다. <br>

- 출력장치 <br>
  컴퓨터 내부에서 처리된 결과를 사용자가 보거나 들을 수 있도록 출력매체를 이용해서 내보낸다. <br>
  출력장치에는 모니터, 프린터, 스피커 등이 있다. <br>


## 정보의 표현과 저장 
- 컴퓨터에서 정보의 표현 
  컴퓨터 내부에서는 데이터를 주로 2진수로 표현한다. <br>
  10진수와 8진수 혹은 16진수를 사용하기도 하지만, 일반적으로 데이터 1비트를 0, 1 두 개의 숫자로 표현하는 2진법을 사용하는 것이 기본이다. <br>
  (8 bit = 1 byte) 

- 컴파일러(Compiler)란? <br>
프로그래밍 언어로 작성된 소스 코드를 기계어나 중간 코드로 변환해 주는 소프트웨어 도구이다. <br>
컴퓨터는 0, 1로 이루어진 기계어만 이해할 수 있기 때문에 우리가 C, Java, Swift와 같은 언어로 작성하는 소스 코드는 컴퓨터가 이해할 수 없다. <br>
따라서 우리가 작성한 소스 코드를 컴퓨터가 이해할 수 있게 0, 1로 이루어진 기계어로 번역하는 컴파일 과정이 필요하다. 즉, 컴퓨터가 이해할 수 있는 언어로 번역해 주는 도구를 컴파일러라고 한다. <br>

## 시스템의 구성 
버스란? <br>
컴퓨터에서 두 개 혹은 그 이상의 장치를 연결하는 공유 전송매체다. <br>

시스템 버스의 분류 <br>
시스템 버스에는 전송되는 데이터가 의미하는 내용에 따라 주소버스, 데이터 버스, 제어 버스로 분류된다. <br>

- 주소 버스 <br>
주소 버스는 데이터를 읽거나 쓸 기억장소의 주소를 전송하는 통로다. 즉, CPU가 발생하는 주소 정보를 외부로 전송하는 신호 선들의 집합이다. <br>
이 버스는 선들의 수(주소 버스 폭)에 의해 CPU와 접속될 수 있는 최대 기억장치 용량이 결정된다. <br>

- 데이터 버스 <br>
데이터 버스는 모듈 사이로 데이터를 전송하는 통로다. 즉, CPU가 기억장치와 입출력장치와의 사이에 데이터를 전송하기 위한 신호 선의 집합이다. <br>

- 제어 버스 <br>
제어 버스는 제어 신호들을 전송하는 통로 즉, CPU가 컴퓨터 시스템 내의 각종 장치 요소들의 동작을 제어하기 위한 신호 선의 집합이라고 할 수 있다. <br>


<img src="https://github.com/z-wook/z-wook/assets/101041221/60f05c30-2216-4492-957c-876b46b01273">
<br><br>

## CPU와 기억장치의 접속
시스템 버스의 방향성
1. 주소 버스는 주소를 표현하는 신호가 CPU로부터 기억장치 혹은 입출력장치로 전송되고 반대로의 전송은 없기 때문에 단방향성 버스다.
2. 데이터 버스는 읽기 동작과 쓰기 동작을 모두 수행해야 하기 때문에 양방향성을 갖는다.
3. 제어 버스 또한 데이터를 요구하는 제어신호와 올바른 전송을 확인해 주는 제어신호를 사용하므로 양방향성을 갖는다.

## CPU와 I/O 장치의 접속
- CPU와 주변장치의 데이터 전송 <br>
CPU는 기억장치뿐만 아니라 외부 장치들과도 데이터를 송수신한다. 그러나 입출력 장치는 버스와 직접적으로 연결되어 데이터를 송신하거나 수신하지 않는다. 입출력 장치는 처리하는 속도 차이가 커서, 처리 속도가 느린 입출력장치가 빠르게 전송되어온 데이터를 제대로 처리하지 못하기 때문이다.

- CPU의 기능과 동작 <br>
CPU가 모든 명령어에 대하여 공통적으로 수행하는 기능은 명령어 인출과 명령어 해독이다. 명령어 인출 기능은 주 기억장치에 저장되어 있는 명령어를 읽어오는 기능이다. 명령어 해독 기능은 읽은 명령어에 대하여 수행해야 할 동작을 결정하기 위하여 인출된 명령어를 해독하는 과정이다.

- 명령어의 기능 <br>
  1. 데이터의 인출 기능
  명령어 실행을 위하여 데이터가 필요한 경우, 기억장치 또는 입출력장치에서 그 데이터를 읽어오는 과정이다. <br>
  사용하는 데이터를 불러오는 과정이라 할 수 있다.
  2. 데이터 처리 기능
  읽어온 데이터에 대한 산술적 또는 논리적 연산을 수행한다.
  3. 데이터 쓰기 기능
  데이터 처리 과정에서의 수행 결과를 저장하는 기능이다.
  
- CPU의 동작 <br>
CPU는 4단계의 기본 동작으로 구성된다.
  1. 처리해야 할 데이터는 주기억장치 RAM에서 인출되고 외부 시스템 버스를 통해서 레지스터 1번으로 전달된다.
  2. 제어장치는 새롭게 저장된 레지스터 1번 데이터와 이전부터 저장되고 있던 레지스터 2번의 데이터를 덧셈하라는 제어 신호를 ALU로 전달한다.
  3. ALU에서는 제어신호에 의해서 덧셈을 수행하고 그 결과를 누산기에 저장한다.
  4. 덧셈의 계산 결과는 외부 시스템 버스를 통해서 다시 주 기억장치로 전달된다.

## 전체 시스템의 구성
1. **중앙처리장치 (CPU):** 컴퓨터 시스템을 제어하고 데이터를 처리하는 핵심 장치입니다. CPU는 산술논리연산장치(ALU)와 제어장치(CU)로 구성되며, 명령어를 실행하여 데이터를 처리하고 시스템을 제어합니다.

2. **기억장치 (MU):** 주 기억장치(내부 기억장치)와 보조기억장치(외부 기억장치)로 구분됩니다. 주 기억장치는 프로그램과 데이터를 저장하며, 주로 RAM을 사용합니다. 보조기억장치는 데이터를 영구적으로 저장하며 하드 디스크, SSD, USB 메모리 등이 포함됩니다.

3. **입력 장치:** 외부에서 컴퓨터로 데이터나 정보를 입력할 수 있게 해주는 장치로 키보드, 마우스 등이 있습니다.

4. **출력 장치:** 컴퓨터에서 처리한 결과를 사용자에게 보여주거나 들려주는 역할을 하는 장치로 모니터, 프린터, 스피커 등이 있습니다.

5. **정보의 표현과 저장:** 컴퓨터는 데이터를 2진수로 표현하며, 컴파일러를 사용하여 프로그래밍 언어로 작성된 소스 코드를 기계어로 변환합니다.

6. **시스템의 구성:** 시스템 버스는 주소 버스, 데이터 버스, 제어 버스로 분류되며, 각각 주소, 데이터, 제어 정보를 전송하는 역할을 합니다.

7. **CPU와 기억장치의 접속:** 시스템 버스를 통해 CPU와 주 기억장치가 데이터와 명령어를 주고받습니다.

8. **CPU와 I/O 장치의 접속:** 입출력 장치는 처리 속도 차이로 인해 직접 CPU와 연결되지 않고 시스템 버스를 통해 데이터를 주고받습니다.

9. **CPU의 기능과 동작:** CPU는 명령어 인출과 명령어 해독을 수행하여 데이터를 처리하고 제어합니다.

10. **CPU의 동작:** CPU는 명령어를 인출하여 레지스터에 저장하고, ALU와 제어장치를 통해 연산하며, 결과를 기억장치에 저장하는 단계로 동작합니다.

## 컴퓨터 구조의 발전 과정 
1. 기계식 컴퓨터
초기 컴퓨터는 기계식 부품을 사용하여 계산을 수행함. 대표적으로 제한된 용도로 사용되던 장치로, 물리적 기어와 레버를 활용하여 계산을 수행

2. 전구 및 진공관 컴퓨터
진공관이나 전구 등의 전자 부품이 도입되면서 컴퓨터의 성능과 신뢰성이 향상 <br>
하지만 컴퓨터는 크기가 크고 발열이 심한 단점이 있었다.

3. 트랜지스터 시대
트랜지스터의 발명으로 작고 저전력의 전자 부품이 가능해졌다. 이로 인해 컴퓨터의 크기와 전력 소비가 줄어들면서 효율적인 계산이 가능해졌다.

4. 집적 회로 (IC) 및 마이크로프로세서
집적 회로(IC)의 등장으로 많은 전자 부품이 하나의 칩에 통합되었습니다. 이에 따라 컴퓨터의 크기가 더욱 작아지고, 마이크로프로세서의 등장으로 컴퓨터의 성능과 효율성이 크게 향상되었습니다.

5. 개인용 컴퓨터와 그래픽 사용자 인터페이스
IBM PC의 등장과 함께 개인용 컴퓨터가 보급되기 시작 <br>
이 시기에는 그래픽 사용자 인터페이스(GUI)가 개발되어 사용자가 더 직관적으로 컴퓨터와 상호작용할 수 있게 되었다.

6. 인터넷과 네트워크
인터넷의 보급으로 컴퓨터는 세계적으로 연결되는 환경이 구축

7. 모바일 및 클라우드 컴퓨팅 
휴대폰과 태블릿 컴퓨터 등 모바일 장치의 보급으로 컴퓨팅은 더욱 이동성과 개인화로 향함. <br>
또한 클라우드 컴퓨팅 기술의 발전으로 데이터와 서비스를 온라인에서 제공하는 환경이 구축되었습니다.