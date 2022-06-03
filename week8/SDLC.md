
# Software Development Life Cycle (SDLC)
작성자: 김다인

---

### 소프트웨어 생명 주기
소프트웨어 생명 주기(SDLC)란 소프트웨어 공학에서 정보 시스템을 계획, 개발, 테스트, 배포하는 과정을 뜻한다. 하드웨어부터 소프트웨어까지 넓은 범위에 적용할 수 있다. 보통 요구사항 분석 → 설계(디자인) → 개발 → 테스트 → 운영 및 유지보수 단계로 구성되어 있다.  
SDLC는 여러 단계들로 명확하게 나뉜다. SDLC의 목적 역시 고품질의 시스템, 프로그램을 만들어 고객 요구를 만족시키는 것이다. 고객 요구 만족을 위한 소프트웨어 개발 방법론의 일환으로 폭포수 모델, 나선형 모델, V, 애자일, 프로토타입, 반복 점증적 등의 모델 등이 만들어졌다.  
<br>
<img  src="https://miro.medium.com/max/1400/1*GU-YWDqM-ZljYHGs1iDNPg.jpeg">

### SDLC 모델
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Waterfall_model.svg/525px-Waterfall_model.svg.png">
<br>

* (1) 폭포수 모델
	* 순차적 소프트웨어 개발 프로세스로, 개발 흐름이 폭포수처럼 아래로 향하는 것처럼 보이는 특징
	* 요구사항 분석에서 설계, 구현, 테스트, 통합을 거쳐 유지보수 단계에 이르름
	* 간결하면서도 구조화된 접근 방법을 제공해 쉽게 이해할 수 있고 설명 가능한 모델
	* 시간이 많이 걸리며, 진행 중인 단계가 완료될 때까지 새로운 단계를 시작할 수 없어 단기 프로젝트에서 사용이 어려움  

<br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/V-model.JPG/525px-V-model.JPG">

* (2) V 모델
	* 폭포수 모델의 확장 형태 중 하나로, 기존 폭포수 모델과 달리 코딩 단계에서 V 자로 꺾여서 진행되며 테스트 계획 및 테스트가 초기 단계부터 시작된다는 특징
	* 개발 생명주기의 각 단계와 그에 상응하는 테스트 단계 간 관계를 보여줌
	* 간단하고 이해하기 쉬움
	* 이미 진행 중인 프로젝트에 적합하지 않으며, 나중에 요구 사항을 변경하는 것에 많은 비용이 따름
	* Verification (검증) 단계
		* 요구사항 분석
		* 시스템 설계
		* 아키텍처 설계
		* 모듈 설계
	* Validation (유효화) 단계
		* 단위 테스트
		* 통합 테스트
		* 시스템 테스트
		* 인수 테스트

<br>
<img src="https://itwiki.kr/images/b/b9/%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9D%B4%ED%95%91_%EB%AA%A8%EB%8D%B8_%EC%A0%88%EC%B0%A8%EB%8F%84.png">

* (3) 프로토타입 모델
	* 사용자 요구사항을 충분히 분석할 목적으로 시스템의 중요 일부를 우선적으로 구현한 다음 다시 요구사항을 반영하는 과정을 반복
	* 사용자 중심, 의사소통 강화, 점진적 상세화
	* 계획 수립, 요구 분석과 정의, 프로토타입 개발과 개선, 프로토타입 평가, 상세 개발, 설치 및 운영
	* 결함이 일찍 발견되기 때문에 개발 비용과 시간을 줄일 수 있음
	* 고객이 모든 단계에 참여하는 것이 오히려 단점이 될 수 있음

<br>
<img src="https://mblogthumb-phinf.pstatic.net/20140218_259/seilius_1392697072484Bg2UG_PNG/SpiralModel.png?type=w2">

* (4) 나선형 모델
	* 시스템 개발 시 위험을 최소화하기 위해 점진적으로 완벽한 시스템으로 개발하는 모델
	* 위험 최소화, 점진적 개발
	* 목표 설정, 위험 분석, 구현 및 테스트, 고객 평가 및 다음 단계 수립 과정이 반복됨
	* 위험 관리를 한다는 것이 장점이며 고객 요구사항을 상세히 적용 가능
	* 프로젝트 기간이 오래 걸리며 반복 단계가 길어질수록 프로젝트 관리가 어려움

<br>
<img src="https://mblogthumb-phinf.pstatic.net/20140217_82/seilius_13926222294156F843_GIF/IncrementalModel_01.gif?type=w2"> 
증분형 모델
<br>
<img src="https://mblogthumb-phinf.pstatic.net/20140217_28/seilius_1392622369483EQJYQ_JPEG/%C1%F8%C8%AD%C7%FC%B8%F0%B5%A8.jpg?type=w2">
진화형 모델

* (5) 반복적 모델
	* 요구사항, 제품 일부만을 개발/반복해 최종 사용자 요구 사항에 부합하는 시스템을 완성하는 모델
	* 반복적으로 사용자가 원하는 완제품을 점차적으로 만들어가는 특징
	* 증분형
		* 시스템을 기능별로 여러 서브시스템으로 분리
		* 서브시스템 구현 후 배포, 다음 서브 시스템을 구현하는 방식
	* 진화형
		* 하나의 프로토타입을 만들고 지속적으로 추가 기능을 붙이는 방식
		* 눈덩이를 만들어 굴려가며 큰 눈덩이로 만들어가는 방식

[(6) 애자일](https://github.com/dev-dain/CS-study/blob/main/week8/Agile.md)


---
* [위키백과](https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EA%B0%9C%EB%B0%9C_%EC%88%98%EB%AA%85_%EC%A3%BC%EA%B8%B0)
* [위키백과](https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EA%B0%9C%EB%B0%9C_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4?tableofcontents=1)
* [SDLC (소프트웨어 개발 생명주기) 단계, 방법론, 프로세스 및 모델](https://ko.myservername.com/sdlc-phases)
* [프로토타이핑 모델 - IT 위키](https://itwiki.kr/w/%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9D%B4%ED%95%91_%EB%AA%A8%EB%8D%B8)
* [소프트웨어 공학 - 나선형 모델(Spiral Model)](https://m.blog.naver.com/seilius/130185846022)
* [소프트웨어 공학 - 반복 점증적 모델(Iterative & Incremental Model)](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=seilius&logNo=130185785755)