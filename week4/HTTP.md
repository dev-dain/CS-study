# HTTP
작성자 : 김다인

---
### HTTP (HyperText Transfer Protocol)
웹을 구성하는 요소로 HTML, URI와 URL, 웹브라우저와 웹서버, HTTP가 있다. 이 중 HTTP는 말그대로 하이퍼텍스트 전송 규약이다. 서버-클라이언트 간 요청-응답 통신을 위한 통신 규칙(프로토콜)을 뜻한다. 수신자(브라우저) 측에 의해 요청이 초기화되는 프로토콜이다.  
HTTP 통신으로 서버에서 HTML 문서 같은 리소스들을 가져올 수 있다. TCP 위의 응용(Application) 계층 프로토콜로, 클라이언트와 서버가 서로 통신하는 기준을 마련한다.  
주로 HTML 문서를 주고받는 데 사용되며, 80번 포트를 사용한다.  

### HTTP 프로토콜
* HTTP는 기본적으로 connectionless, stateless이다.
* connectionless란, 서버가 클라이언트로부터 요청을 받고 그에 맞는 응답을 주고 나면 서버에서 연결을 끊어 버리는 것을 말한다. HTTP 1.1 Connection: Keep-Alive 옵션 이전에는 connectionless가 기본이었으나 keep-alive 옵션을 주면 연결을 유지한다.
* stateless란, 서버와 클라이언트 간 연결이 끊어지면 통신이 종료되고 상태 정보를 버린다는 의미이다. 
* 이 같은 특징 때문에 지속적으로 사용자 정보가 필요한 경우에도 정보를 기억할 수 없어서 쿠키와 세션이 등장하게 됐다.

### HTTP 메소드 (요청)
* GET
	* RFC 7231. 특정 리소스의 표시를 요청. GET을 사용하는 요청은 오직 데이터 수신만 함.
	* 요청에 Body가 없음. 
	* **READ**에 해당. 
	* 다음은 /images/logo.gif를 요청.
	* **GET /images/logo.gif HTTP/1.1**
* POST
	* RFC 7231. 서버나 특정 리소스에 엔티티를 제출할 때 사용됨.  POST 요청으로 서버의 상태 변화나 사이드 이펙트가 유발됨. 
	* [*멱등성*](https://developer.mozilla.org/ko/docs/Glossary/Idempotent)을 가지지 않음. 동일한 요청을 1번 보낼 때와 연속해서 여러 번 보낼 때의 효과가 다름.
	* **Create**에 해당하지만, Update, Delete도 수행 가능.
	* 다음은 foo.com의 루트에 { say: 'Hi', to: 'Mom' }을 전송.
```
POST / HTTP/1.1
Host: foo.com
Content-Type: application/x-www-form-urlencoded

Content-Length: 13

say=Hi&to=Mom
```
* PUT
	* RFC 7231. 요청 페이로드를 사용해 새로운 리소스를 생성하거나 대상 리소스를 나타내는 데이터를 완전히 교체. Create, Update에 해당하지만 전체 자원을 수정하는 데 사용.
	* 다음은 example.com에 /new.html이라는 이름의 자원을 등록함.
```
PUT /new.html HTTP/1.1
Host: example.com
Content-type: text/html
Content-length: 16

<p>New File</p>
```
* PATCH
	* RFC 5789. 리소스의 일부를 수정하는 데 사용됨.  
	* 멱등성을 갖지 않음.
	* **Update**에 해당. 
	* 다음은 www.example.com의 /file.txt 일부 수정을 요청.
```
PATCH /file.txt HTTP/1.1
Host: www.example.com
Content-Type: application/example
If-Match: "e0023aa4e"
Content-Length: 100

[description of changes]
```
* DELETE
	* RFC 7231. 특정 리소스를 삭제함.
	* 요청에 Body가 없음. 
	* **Delete**에 해당.
	* 다음은 file.html을 삭제하는 요청
	* **DELETE /file.html HTTP/1.1** 

### HTTP 요청/응답 헤더
이 부분은 [WeareSoft](https://github.com/WeareSoft/tech-interview/blob/master/contents/network.md#http-%EC%9A%94%EC%B2%AD-%EC%9D%91%EB%8B%B5-%ED%97%A4%EB%8D%94) 문서를 많이 참고했으며, 그 중 일부만 정리함.   

1. 일반 항목 (General Header)
	* 요청/응답 메시지 모두에서 사용 가능한 헤더 항목
	* **Date** (HTTP 메시지 생성 일시) 
	* **Connection** (클라이언트-서버 간 연결 옵션. close/Keep-Alive)
2. 엔티티 항목 (Entity Header)
	* 요청/응답 메시지 모두에서 사용 가능한 Entity 설명 헤더
	* **Content-Type** (해당 개체에 포함되는 미디어 타입. ex) text/html)
	* **Content-Language** (해당 개체와 가장 잘 어울리는 자연어)
	* **Content-Encoding** (해당 개체 데이터 압축 방식. gzip, defalte 등 용량이 큰 개체의 경우 압축함)
	* **Content-Length** (전달되는 개체의 바이트 길이 혹은 크기)
	* **Last-Modified** (리소스를 마지막으로 갱신한 일시)
3. 요청 헤더 (Request Header)
	* HTTP 요청 메시지에만 나타남
	* **Host** (요청하는 호스트에 대한 호스트명/포트번호)
	* **User-Agent** (클라이언트 소프트웨어(브라우저, OS) 명칭과 버전)
	* **If-Modified-Since** (마지막으로 언제 받은 파일인지 서버에 알려줌. 서버는 이 시간을 확인해서 최신 파일이 있다면 보내 주고, 서버의 파일과 동일 버전이라고 판단하면 보내지 않음)
![image](https://mdn.mozillademos.org/files/13821/HTTP_Request_Headers2.png)
4. 응답 헤더 (Response Header)
	* 특정 유형의 HTTP 요청이나 헤더를 수신했을 때 응답
	* **Server** (서버 소프트웨어 정보)
	* **Expires** (리소스가 지정된 일시까지 캐시로서 유효함을 나타냄)
	* **Allow** (해당 엔티티에 대해 서버에서 지원 가능한 HTTP 메소드 리스트를 나타냄)
![image](https://mdn.mozillademos.org/files/13823/HTTP_Response_Headers2.png)

### HTTP 응답 코드
응답은 5개 그룹으로 나뉘며, 이 문서에는 자주 쓰이는 코드 일부만 수록. 전체 코드를 확인하려면 문서 하단의 출처를 확인하세요.  
* 100 (정보성)
	* 100 Continue : 지금까지 상태가 괜찮음을 알림
	* 101 Switching Protocol : 클라이언트가 보낸 Upgrade 요청 헤더에 대한 응답. 서버에서 프로토콜을 변경할 것임을 알림
* 2XX (성공)
	* 200 OK : 요청이 성공
	* 201 Created : POST/PUT 요청 후 새로운 리소스가 생성됨을 알림
	* 204 No Content : 요청은 잘 받았으나 요청에 대해 보내줄 수 있는 콘텐츠가 없음을 의미
	* 207 Multi-Status (여러 리소스가 여러 상태 코드인 상황이 적절한 경우, 해당되는 정보 전달)
* 3XX (리다이렉트)
	* 301 Moved Permanently (요청한 리소스의 URI가 변경됨)
	* 302 Found (요청한 리소스의 URI가 일시적으로 변경됨)
	* 303 See Other (클라이언트가 요청한 리소스를 다른 URI에서 GET으로 얻어야 함)
	* 304 Not Modified (캐시 목적. 클라이언트에게 응답이 수정되지 않았음을 알림)
* 4XX (클라이언트 에러)
	* 400 Bad Request (잘못된 문법으로 서버가 요청을 이해할 수 없음)
	* 401 Unauthorized (클라이언트가 응답을 받기 위해서는 인증이 필요함)
	* 403 Forbidden (클라이언트가 콘텐츠에 접근할 권리가 없음. 401과 다른 점은, 서버가 클라이언트가 누구인지 알고 있음)
	* 404 Not Found (서버가 요청한 리소스를 찾을 수 없음)
	* 405 Method Not Allowed (요청한 메소드를 서버에서 알고는 있지만 제거됐기 때문에 사용할 수 없음)
	* 408 Request Timeout (요청을 한 지 오래된 연결에 일부 서버가 전송하는 응답코드)
	* [418 I'm a teapot](https://developer.mozilla.org/ko/docs/Web/HTTP/Status/418) (1998년 만우절 농담이던 HyperText Coffee Pot Control Protocol의 레퍼런스. 그냥 개그입니다)
* 5XX (서버 에러)
	* 500 Internal Server Error (서버가 처리 방법을 모르는 상황)
	* 501 Not Implemented (요청 방법을 서버에서 지원하지 않음)
	* 502 Bad Gateway (서버가 요청을 처리하는 데 필요한 응답을 얻기 위해 게이트웨이로 작업하는 동안 잘못된 응답 수신)
	* 503 Service Unavailable (서버가 요청을 처리할 준비가 되지 않음)
	* 504 Gateway Timeout (서버가 게이트웨이 역할을 하고 있으며, 제시간에 응답을 받을 수 없음)

---
* [MDN Web docs : HTTP 요청 메소드](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods)
* [위키백과 HTTP](https://ko.wikipedia.org/wiki/HTTP)
* [MDN Web docs : HTTP 메시지](https://developer.mozilla.org/ko/docs/Web/HTTP/Messages)
* [MDN Web docs : HTTP 상태 코드](https://developer.mozilla.org/ko/docs/Web/HTTP/Status)