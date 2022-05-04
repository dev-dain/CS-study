# Restful API

### **작성자 강수지** <br><br>

## REST ( Representational State Transfer ) 

REST 란 " 대표젹인 상태 전달 " 이다

즉 웹에 존재하는 모든 자원에 대한 고유한 URI 를 부여해 활용하는 것으로 자원을 정의하고 자원에 대한 주소를 지정하는 방법론으로 이해하면 된다
 
**RESTful API 는 REST 의 특징을 지키면서 API 를 제공한다는 것을 의미한다**
 

REST에서 모든 데이터와 처리방식은 URL 를 통해 정의되며 직관적이고 이해가 쉽다

URL를 통해 자원을 명시하고 HTTP Method( POST, GET, PUT, DELETE ) 를 통해

자원에 대한 CRUD 동작을 적용하는데 여기서 CRUD 동작은 아래와 같다

- Create : 생성 ( POST )
- Read : 조회 ( GET )
- Update : 수정 ( PUT )
- Delete : 삭제 ( DELETE )
- Head : header 정보 조회 ( HEAD )
 

웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하여 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다

---

## REST 구성요소

### 1) 자원 ( Resource ) : URI

모든 자원에 고유한 ID 가 존재하고 Server에 존재한다

자원을 구별하는 ID 는 '/group/group_id' 와 같은 HTTP URI이다

Client 는 URI 를 이용하여 자원을 지정하고 해당 자원의 상태에 대한 조작을 Server에 요청한다
 

### 2) 행위 ( Verb ) : HTTP Method

HTTP Method 는 GET, POST, PUT, DELETE 와 같은 메서드를 제공한다

### 3) 표현 ( Representation of Resource )

Client 가 자원의 상태에 대한 조작을 요청하면 Server 에서 응답 ( Representation ) 을 보낸다

REST 에서 하나의 자원은 JSON, XML, TEXT, RSS 등 여러 형태로 나타낼 수 있고

JSON 이나 XML 로 데이터를 주고 받는 것이 일반적이다

---

## REST 의 특징
### 1) Uniform ( 유니폼 인터페이스 )

HTTP 표준에만 따른다면 안드로이드/IOS 플랫폼이든 특정 언어나 기술에 종속되지 않고

모든 플랫폼에 사용이 가능하며 URI 로 지정한 리소스에 대한 조작이 가능한 아키텍처 스타일을 의미한다

### 2) Stateless ( 무상태성 )

세션 정보나 쿠기정보를 별도로 저장하거나 관리하지 않기 때문에

API 서버는 들어오는 요청만을 단순 처리하고 구현은 단순해진다

 
### 3) Cacheable ( 캐시 가능 )

기존 웹표준을 그래도 사용하기 때문에 HTTP 가 가진 캐싱 기능이 적용이 가능하다


### 4) Self-descriptiveness ( 자체 표현 구조 )

Method (동사) + URI (명사) 로 이루어져 어떤 메서드에 무슨 행위를 하는지 알 수 있고

메세지 포맷 역시 JSON 을 이용하여 직관적으로 이해가 가능한 구조이다


### 5) Client-Server 구조

REST 서버는 API 제공, 클라이언트는 사용자인증이나 세션, 로그인 정보 등을 직접 관리하는 구조로

각 역할이 확실히 구분되어 클라이언트와 서버의 의존성이 줄어들게 된다

### 6) 계층형 구조

REST 서버는 다중 계층으로 구성될 수 있으며 보안, 로드 밸런싱, 암호화 계층을 추가해

구조상의 유연성을 둘 수 있고 프록시나 게이트웨이 같은 네트워크 기반의 중간매체를 사용할 수 있다

---

## RESTful API 디자인 가이드

REST API 설계 시 가장 중요한 항목인 아래 두가지를 잊지말자 !

**URI 는 정보의 자원을 표현해야한다**
**자원에 대한 행위는 HTTP Method 로 표현한다**

1-1. REST API 중심규칙
1) URI 는 정보의 자원을 표현해야한다 ( 리소스명은 동사보다 명사를 사용 )

아래 방식은 REST 를 제대로 적용하지 않은 URI 이다 !

URI 는 자원을 표현하는데 중점을 두어야하므로 delete 와 같은 행위에 대한 표현이 들어가면 안된다

```
GET /members/delete/1
```

2) 자원에 대한 행위는 HTTP Method 로 표현한다

위 잘못된 URI 를 HTTP Method 를 통해 수정해보면 아래와 같다 
```
DELETE /members/1
```
회원 정보를 가져올때는 GET, 회원 추가시 행위는 POST를 사용하여 표현한다

회원 정보를 가져오는 URI
```
GET members/show/1 (X)
GET members/1      (O)
```
회원을 추가하는 URI
```
GET /members/insert/2 (X)
POST /memebers/2      (O)
```

1-2. URI 설계시 주의할 점
1) 구분자(/) 는 계층 관계를 나타내는데 사용되고 마지막 문자로 슬래시를 포함하지 않는다 <br>
REST API 는 분명한 URI 를 만들어 통신해야 하기 때문에 마지막 경로에는 슬래시를 사용하지 않는다
```
http://restapi.example.com/houses/apartments/ (X)
http://restapi.example.com/houses/apartments  (0)
```
2) 하이픈(-)은 URI 가독성을 높이는데 사용한다

불가피하게 긴 URI 경로를 사용하게 된다면 하이픈을 통해 가독성을 높일 수 있다 <br> 반면 밑줄(_) 은 가독성에 방해가 되기 때문에 사용하지 않는다

3) URI 경로에는 소문자가 적합하다

대문자의 사용은 피해야하는데 대소문자에 따라 다른 리소스로 인식할 수 있다 <br> RFC3986(URI 문법 형식)은 URI 스키마와 호스트를 제외하고는 대소문자를 구별하도록 규정하기 때문이다 <br> RFC 3986 is the URI (Unified Resource Identifier) Syntax document

4) 파일 확장자는 URI 에 포함시키지 않는다
```
http://restapi.example.com/members/soccer/345/photo.jpg (X)
```
REST API 에서는 메세지 바디 내용의 포맷을 나타내기 위한 파일 확장자를 포함시키지 않는다 <br> 대신 Accept header 를 사용하면 된다 !
```
GET / members/soccer/345/photo HTTP/1.1 Host: restapi.example.com Accept: image/jpg
```

1-3. 리소스간의 간의 관계를 표현하는 방법
REST 리소스 간에는 연관관계가 있을 수 있고 이런 경우 다음과 같은 표현방법을 사용한다

/리소스명/리소스 ID/관계가 있는 다른 리소스명
```
GET : /users/{userid}/devices (일반적으로 소유 ‘has’의 관계를 표현할 때)
```

만약 관계명이 복잡하다면 서브 리소스에 명시적으로 표현하는 방법이 있다<br> 사용자가 '좋아하는' 디바이스 목록을 표현해야한다고 가정하면 아래와 같은 형태로 표현할 수 있다
```
GET : /users/{userid}/likes/devices (관계명이 애매하거나 구체적 표현이 필요할 때)
```

1-4. 자원을 표현하는 Collections 과 Document
Doument 는 단순히 문서로 이해해도 되고 한 객체라고 이해해도 된다

Collections 는 문서들의 집합, 객체들의 집합으로 이해하면 된다

둘 다 모두 리소스라고 표현할 수 있으며 URI 에 표현된다
```
http:// restapi.example.com/sports/soccer
```
위 URI 를 보면 sports 라는 컬랙션과 soccer 라는 도큐먼트로 표현되어 있다
```
http:// restapi.example.com/sports/soccer/players/13
```
위 URI 에서 중요한 것은 sports 와 players 컬랙션을 복수로 사용하고 있다는 점이다

좀 더 직관적인 REST API 를 위해서는 컬랙션과 도큐먼트를 사용할 때 단수복수를 지켜주어야한다