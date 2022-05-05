# CORS

### **작성자 강수지** <br><br>

## CORS
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdQQcBo%2FbtrBm8gFBgy%2Fvlf89KRoNMKUMmN3w6QqB0%2Fimg.png"> <br>

CORS 란 교차 출처 리소스 공유 ( Cross-Origin Resource Sharing ) 의 약자로
추가 HTTP 헤더를 사용하여 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제 라고 MDN 에 정의되어 있다


쉽게 말하자면 ! **브라우저에서 다른 출처의 리소스를 공유할 수 있도록 하는 체제** 로 이해하면된다


여기서 origin 이란 protocol, host, port 의 구성으로 브라우저 개발자도구의 콘솔창에 아래 명령어를 실행하면 확인할 수 있다
```
location.origin
```
동일출처 ( same origin ) 란 protocol, host, port 가 모두 같은 경우를 말한다

실제 웹페이지에서는 다른 출처의 리소스를 자주 사용하게 되는데
SOP( same origin policy )로 인해 CORS Policy 오류가 발생하기도 한다

SOP( same origin policy ) 란 같은 출처의 리소스를 공유할 수 있다는 규칙이다
 
**SOP 가 존재하는 이유**는 다른 출처의 애플리케이션이 서로 통신하는 것에 대해 아무런 제약이 존재하지 않을때
악의를 가진 사용자가 소스코드를 보고 CSRF ( cross-site request forgery ) 나 XSS( cross-site scripting) 등의
**보안 취약점을 노린 공격을 통해 정보를 탈취할 수 있게 되기 때문에 이를 방지하기 위해 존재한다**

CORS 는 다른 출처의 리소스가 필요한 경우 SOP 를 우회하기 위한 여러 방법 중 가장 권장되는 방법이다

---

## CORS 해결 방법

CORS 정책 위반으로 에러가 발생하는 경우 서버에서 응답헤더에 특정 헤더를 포함하는 방식으로 해결할 수 있다
 
**Access-Control-Allow-Origin**
```
이 방법은 서버측 응답에서 접근 권한을 주는 헤더를 추가하여 해결하는 방법이다
```
 
**Access-Control-Allow-Method**
```
이 방법은 특정 HTTP Method만 리소스에 접근이 가능하도록 허용하는 방법이다
```

**Access-Control-Expose-Headers**
```
이 방법은 자바스크립트에서 헤더에 접근할 수 있도록 허용하는 방법이다
``` 

**Access-Control-Allow-Credentials**
```
이 방법은 서버측 응답에서 Access-Control-Allow-Credentials 헤더에 true 값을 포함하고 있는 방법이다
```

---

### CORS 관련 예상질문
CORS 에 관한 정의와 Origin 의 구성 등에 대해 질문할 수 있을 것 같고

또한 SOP 가 존재하는 이유 , CORS 에러 해결방법 등도 공부하면 좋을 것 같아요 !

*( 동작 방식까지는 구체적으로 물어보지 않는 것 같아요 .. 아마도 ^^ )*