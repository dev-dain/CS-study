# synchronous and asynchronous

### **작성자 강수지** <br><br>

## 동기

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbsfayV%2FbtrEUhA1xn9%2FrvCDq2tFfqPCG6dK6sK2JK%2Fimg.png">

동기는 ajax 에서 많이 사용된다

해당 데이터를 모두 가져와 다음 테스크에서 함께 사용하는 경우가 많기 때문이다

동기는 하나의 물길이라 생각하면 이해가 쉽다

순차적으로 처리하는 경우 비동기에 비해 결과값 처리가 느리지만 디버깅이 쉽다는 특징이 있다

---

## 비동기

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FccL0BL%2FbtrEQSwqIDn%2FDVuO5AqGfOZOhbbLcH27zk%2Fimg.png">

비동기는 다양한 작업이 동시에 일어난다

메인화면이 노출되는데 실시간 채팅창이 로딩되어 보여지고 .. 등 동시에 여러 작업이 일어난다

한 테스크에서 에러가 나더라도 다른 테스크에 영향을 끼치지 않고 개별적으로 진행된다
 

비동기는 여러가지 로직이 동시에 처리되고 매우 빠르게 결과가 도출된다

다른 테스크의 결과값을 받아 쓸때 이를 조절해야한다

---

## 동기와 비동기 차이

동기는 순차적이고 직렬적으로 테스크를 수행하고

비동기는 병렬적으로 테스크를 수행한다

 

서버에서 데이터를 가져와 화면에 표시하는 작업을 수행한다고 가정하면

동기는 서버에 데이터를 요청하고 데이터가 응답될때까지 이후 테스크들은 블로킹(blocking) 된다

비동기는 서버에 데이터를 요청한 이후 서버로부터 데이터가 응답될때까지 대기하지 않고(non-blocking)

즉시 다음 테스크를 계속하여 수행한다는 차이가 있다 !