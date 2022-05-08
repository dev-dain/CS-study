# Web Socket 과 Socket.io 차이

### **작성자 강수지** <br><br>


## Web Socket
```
Web Socket 은 웹 페이지의 한계에서 벗어나 실시간으로 상호작용하는 웹 서비스를 만드는 표준 기술이다 
```
HTTP 프로토콜은 클라이언트에서 서버로 단방향 통신을 위해 만들어진 방법이고

실시간으로 웹을 구현하기 위해서는 양방향 통신이 가능해야한다

Web Socket 이전에 Polling, Streaming 방식의 Ajax 코드를 이용하여 이를 구현했다

 

하지만 이 방법은 각 브라우저마다 구현 방법이 달라 개발이 어렵다는 단점이 있어

이를 위해 HTML5 표준의 일부로 Web Socket 이 만들어지게 되었다


일반 TCP Socket 과 차이는 일반 HTTP Request 를 통해 handshaking 과정을 거쳐 최초의 접속이 이루어진다는 점이다
 

Web Socket 의 특징은 아래와 같다

- 소켓을 이용하여 자유롭게 데이터를 주고 받을 수 있다
- 기존의 요청-응답 관계 방식보다 더 쉽게 데이터를 교환할 수 있다
- 다른 HTTP Request 와 마찬가지로 80 포트를 통해 웹 서버에 연결한다
- http:// 대신 ws:// 로 시작하여 Streaming 과 유사한 방식으로 푸쉬를 지원한다
- 클라이언트인 브라우저 중에서는 Chrome, Safari, Firefox, Opera에서 WebSocket을 사용할 수 있으며 각종 모바일 브라우저에서도 WebSocket을 사용할 수 있다


장점은

- HTTP Request를 그대로 사용하기 때문에 기존의 80, 443포트로 접속을 하므로 추가로 방화벽을 열지 않고도 양방향 통신이 가능하다
- HTTP 규격인 CORS 적용이나 인증 등 과정을 기존과 동일하게 사용할 수 있다

**하지만 Web Socket 은 미래의 기술로 아직 인터넷 기업에서 상용되진 않는다**

---

## Socket.io
```
Socket.io 는 브라우저의 종류에 상관없이 다양한 방식의 웹 기술을 실시간으로 구현할 수 있도록 한 기술이다
```

다양한 방식의 실시간 웹 기술을 손쉽게 사용할 수 있는 모듈이라 이해하면 된다

개발자가 Socket.io 를 개발하고 클라이언트로 푸쉬 메세지를 보내기만 하면 Web Socket 을 지원하지 않는 브라우저의 경우 

브라우저 모델과 버전에 따라 Ajax Long Polling, MulitPart Streaming, Iframe 를 이용한 푸쉬, JSONP Polling, Flash Socket 등 다양한 방법으로 

내부적 푸쉬 메세지를 보내준다

**정리하면 WebSocket을 지원하지 않는 어느 브라우져라도 푸쉬 메시지를 일관된 모듈로 보낼 수 있다는 것이다**
 
Socket.io는 현재 바로 사용할 수 있는 기술이다

---

**Web Socket 과 socket.io 의 가장 큰 차이는 Socket.io 는 어느 브라우저와 상관없이 일관적으로 통신한다는 점이다**