# MVC

### **작성자 강수지** <br><br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbYq3QZ%2FbtrDcrGoB9L%2Fy4gBpdYbAtPqjkl0ZURbAk%2Fimg.png">

## MVC
MVC 는 소프트웨어 설계와 관련된 디자인 패턴으로 Model + View + Controller 의 약자를 의미한다

Laravel PHP, Django, Express JS, Angular JS 등 여러 웹 프레임워크에서 MVC 패턴을 사용한다


MVC 패턴은 사용자에게 보여지는 UI와 Business Logic 이 분리되어 있어 서로 영향을 주지 않으며

코드의 가독성을 높일 수 있다

---

## Model
**데이터와 데이터를 처리하는 부분**이다

데이터베이스를 다루며 컨트롤러에게 데이터를 전달한다

모델이 뷰와 직접적으로 소통하는 일은 없다

---

## View
**화면을 구성해주는 부분**이다

유저가 보는 화면을 담당하며 데이터를 받고 보여지는 역할을 수행한다

모델이나 데이터베이스와는 소통하지 않고 컨트롤러와 소통한다

컨트롤러에게 액션이나 데이터를 전달하고 전달받기만 한다

---

## Controller
**사용자의 입력을 받아 처리하는 부분**이다

뷰에서 엑션과 이벤트에 대한 인풋값을 받는다

모델에게 전달해주기 전 데이터를 가공할 수 있다

뷰에게 보델에게 받은 데이터를 가공할 수 있다
