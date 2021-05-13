# network-study
네트워크 공부
1. 네트워크 세상에 들어서며
   1. 네트워킹
      1. 서로 연결하는 것
2. 네트워크와 케이블, 그리고 친구들
   1. 이더넷(Ethernet)
      1. 네트워킹의 한 방식
      2. ``CSMA/CD`` 프로토콜을 사용하여 통신을 한다.
         1. Carrier Sense Multiple Access/Collision Detection 
         2. 두 PC가 한 PC로 동시에 통신을 시도했을 때, 충돌이 나는 것을 ``콜리전``이라고 하며, ``CSMA/CD``방식은 아무도 통신을 하고 있지 않알 때, 무조건 자기 데이터를 실어서 보낸 후 잘 갔는지 확인해보는 방식이다.
   2. 토큰링(TokenRing)
      1. 한 네트워크에 토큰이 하나인데, 그 토큰을 가진 PC만 통신을 할 수 있는 방식
   3. 맥 어드레스(MAC Address)
      1. 실제 통신은 IP주소를 다시 MAC(Media Access Control)으로 바꾸는 과정이며 이 과정을 ``ARP(Address Resolution Protocol)``라고 한다.
      2. 맥주소는 고유하다.
   4. 캐스트
      1. 유니캐스트
         1. 네트워크에서 가장 많이 사용되는 통신 방식
         2. 특정 목적지의 주소 하나만을 가지고 통신하는 방식
         3. 자신의 맥 어드레스가 아니라고 판단되면 랜카드가 해당 프레임을 버리기 때문에 그 목적지 주소가 아닌 다른 PC들의 CPU성능을 저하시키지 않는다.
      2. 브로드캐스트
         1. 라우터 밑에 달린 로컬 랜에 붙어있는 모든 장비들에게 통신을 보낸다.
         2. 받기 싫어도 무조건 받기 때문에 CPU성능이 저하된다.
      3. 멀티캐스트
         1. 특정 그룹의 다수에게 통신을 보낼 수 있다.
         2. 스위치나 라우터가 멀티캐스트 기능을 지원해야 가능(일반적으로 라우터는 브로드캐스트를 막아버림)
   5. OSI 7 Layer
      1. ``애-프-스-트-엔-들-피``
      2. 왜 쓸까?
         1. 데이터 흐름이 한 눈에 보인다.
         2. 문제를 해결하기 편리하다.
         3. 표준화를 위함
      3. 문제
         1. 데이터 케이블이나 허브 등은 무슨 계층?
            1. Physical Layer
         2. 스위치나 브리지
            1. Data Link Layer
         3. 라우터
            1. Network Layer
      4. 각 레이어별 설명
         1. Physical Layer
            1. 전기적, 기계적, 기능적인 특성을 이용해서 통신 케이블로 데이터를 전송
            2. 통신 단위는 ``비트``이며, 이것은 1과 0으로 나타나는, 즉 전기적으로 On, Off상태이다.
            3. 통신 케이블, 리피터, 허브 등
         2. Data Link Layer
            1. 피지컬 레이어를 통하여 송수신되는 정보의 오류와 흐름을 관리하여 정보 전달을 수행할 수 있도록 도와준다.
            2. 맥 어드레스를 갖고 통신할 수 있게 해준다.
            3. 통신 단위는 ``프레임``
            4. 브리지, 스위치 등
         3. Network Layer
            1. ``라우팅``의 역할
            2. 라우터
         4. Transport Layer
            1. 플로 컨트롤과 에러 복구 기능
               1. 에러 복구를 위해 패킷을 재전송하거나 프롤를 조절하여 데이터가 정상적으로 전달될 수 있도록 한다.
            2. TCP, UDP
         5. 데이터를 위의 단계를 거쳐 ``헤더``라는 정보가 추가되며 포장된다. ``헤더``는 전송을 위해 필요한 정보이며 네트워크 계층의 ``헤더``에는 IP 주소가 붙어 있다.
3. TCP/IP와의 만남
4. 네트워크 장비에 관한 이야기
   1. 랜카드(NIC: Network Interface Card)
   2. PC의 버스 방식
      1. 예전에는 ISA
      2. 현재는 PCI
   3. 장치관리자에서 네트워크 어댑터의 정보에서 리소스탭을 보면 ``IRQ``와 ``Base Memory``가 있다. ``IRQ``는 데이터가 들어왔을 때 CPU에 인터럽트 리퀘스트를 보내고 미리 정해놓은 ``Base Memory``로 이동해서 작업을 시작한다.