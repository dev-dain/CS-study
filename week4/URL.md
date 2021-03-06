# URL에 https://www.naver.com 을 쳤을 때 일어나는 일
작성자: 장수현

## in 브라우저

url 에 입력된 값을 브라우저 내부에서 HTTP Request 메시지로 만든다. 만들어진 메시지를 웹 서버로 전송한다. 이 때 만들어진 메시지 전송은 브라우저가 직접하는 것이 아니라 OS에 의뢰하여 메시지를 전달한다. 단, OS에 송신을 의뢰할 때는 도메인명이 아니라 ip 주소로 메시지를 받을 상대를 지정해야 하는데, 이 과정에서 DNS 서버를 조회해야 한다.

<br>

## in 프로토콜 스택, LAN 어댑터
프로토콜 스택이 브라우저로부터 메시지를 받아 패킷 속에 저장한다. 그리고 수신처 주소 등의 제어정보를 덧붙인다. 그 다음 패킷을 LAN 어댑터에 넘긴다. LAN 어댑터는 다음 Hop의 MAC 주소를 붙인 프레임을 전기신호로 변환시킨다. 그리고 신호를 LAN 케이블에 송출시킨다.

<br>

## in 허브, 스위치, 라우터
LAN 어댑터가 송신한 프레임은 스위칭 허브를 경유하여 인터넷 접속용 라우터에 도착한다. 라우터는 패킷을 프로바이더(통신사)에게 전달하고 인터넷으로 들어가게 된다.

<br>

## in 액세스 회선, 프로바이더
패킷은 인터넷의 입구에 있는 액세스 회선에 의해 POP(통신사용 라우터)까지 운반된다. POP 를 거쳐 인터넷의 핵심부로 들어가게 된다. 수 많은 고속 라우터들 사이로 패킷이 목적지를 향해 흘러가게 된다.

<br>

## in 방화벽, 캐시서버
패킷은 인터넷 핵심부를 통과하여 웹 서버측의 LAN 에 도착한다.
방화벽이 도착한 패킷을 검사하고 캐시서버가 패킷이 웹 서버까지 가야하는지 가지 않아도 되는지를 판단한다.

<br>

## in 웹 서버
패킷이 물리적인 웹 서버에 도착하면 웹 서버의 프로토콜 스택은 패킷을 추출하여 메시지를 복원하고 웹 서버 애플리케이션에 넘긴다. 메시지를 받은 웹 서버 애플리케이션은 요청 메시지에 따른 데이터를 응답 메시지에 넣어 클라이언트로 회송한다. 왔던 방식대로 응답 메시지가 클라이언트에게 전달된다.

<br>

참고 - [웹 통신의 큰 흐름](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Network#%EC%9B%B9-%ED%86%B5%EC%8B%A0%EC%9D%98-%ED%81%B0-%ED%9D%90%EB%A6%84)