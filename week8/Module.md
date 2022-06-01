# 모듈의 결합도/응집도
작성자: 장수현

## 모듈 (Module)
모듈은 모듈화를 통해 분리된 시스템의 각 기능들을 의미

모듈은 단독으로 컴파일, 재사용 가능

모듈은 독립성은 결합도와 응집도에 의해 측정

독립성을 높이려면 결합도는 약하게, 응집도는 강하게, 모듈의 크기는 작게 만들어야 함

<br>

## 결합도 (Coupling)
모듈 간의 상호 의존도, 두 모듈 사이의 연관 관계를 의미

결합도는 약할수록 좋으며, 강하면 시스템 구현 및 유지보수가 어려움

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsY1qg%2FbtqEZa4uYT4%2Fco74uR1XKyYKmms3kKPWk1%2Fimg.png">

<br>

1. 자료 결합도(Data Coupling)
- 모듈 간의 인터페이스가 자료 요소로만 구성되는 가장 바람직한 결합도  
- 한 모듈이 다른 모듈을 호출하면서 매개변수나 인수로 데이터를 넘겨주는 방식

2. 스템프 결합도(Stamp Coupling)  
- 모듈 간의 인터페이스로 배열이나 레코드 등의 자료 구조가 전달될 때의 결합도

3. 제어 결합도(Control Coupling)  
- 다른 모듈 내부의 흐름 제어를 위해 통신하거나 제어 요소(Function Code, Switch, Tag, Flag)를 전달할 때의 결합도

4. 외부 결합도(External Coupling)  
- 어떤 모듈에서 외부로 선언한 데이터(변수)를 다른 모듈에서 참조할 때의 결합도

5. 공통 결합도(Common Coupling)  
- 공유되는 공통 데이터 영역을 여러 모듈이 사용할 때의 결합도

6. 내용 결합도(Content Coupling)  
- 다른 모듈의 내부 기능이나 내부 자료를 직접 참조하거나 수정할 때의 결합도

<br>

## 응집도 (Cohension)
모듈 내부의 기능적인 집중도, 모듈 내부 요소들이 서로 관련되어 있는 정도를 의미

응집도는 높을수록 좋으며, 낮으면 유지보수가 어려움

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbSJfdn%2FbtqEXJfE25a%2FfFYbvYhID3bSVRF6QASkK1%2Fimg.png">

<br>

1. 기능적 응집도(Functional Cohesion)  
- 모듈 내부의 모든 기능 요소들이 단일 문제와 연관될 경우의 응집도

2. 순차적 응집도(Sequential Cohesion)  
- 모듈 내 하나의 활동으로부터 나온 출력 데이터를 그 다음 활동의 입력 데이터로 사용할 경우의 응집도

3. 교환적 응집도(Communication Cohesion)  
- 동일한 입력과 출력을 사용하여 서로 다른 기능을 수행하는 요소들이 모였을 경우의 응집도

4. 절차적 응집도(Procedural Cohesion)  
- 모듈 내부 구성 요소들이 특정 기능을 순차적으로 수행할 경우의 응집도

5. 시간적 응집도(Temporal Cohesion)  
- 특정 시간에 처리되는 기능을 모아 하나의 모듈로 작성할 경우의 응집도

6. 논리적 응집도(Logical Cohesion)  
- 유사한 성격을 갖거나 특정 형태로 분류되는 처리 요소들로 하나의 모듈이 형성되는 경우의 응집도

7. 우연적 응집도(Coincidental Cohesion)  
- 모듈 내부의 각 구성 요소들이 서로 관련없는 요소로만 구성된 경우의 응집도