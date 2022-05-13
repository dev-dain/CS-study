# 로드 밸런싱
작성자 : 김다인

---
### 로드 밸런싱
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a6/Elasticsearch_Cluster_August_2014.png/600px-Elasticsearch_Cluster_August_2014.png)    

로드 밸런싱(Load Balancing)은 컴퓨터 네트워크 기술로, **둘 혹은 셋 이상의 CPU, 저장장치 같은 컴퓨터 자원들에게 부하(Load)를 나누어 할당**하는 것을 의미한다. 이로써 가용성, 응답시간 최적화가 가능하다.  
로드 밸런싱은 보통 내부 네트워크를 이용한 병렬처리에 사용된다. 주로 로드 밸런서를 클라이언트-서버 사이에 두고 부하가 일어나지 않도록 여러 서버에 부하를 나누는 방식이다.    

### 로드 밸런싱의 방식
사용자 요청이 늘어나고 기존의 서버로 그것을 모두 감당하기 힘들 때, 2가지 방법을 생각할 수 있다.
* Scale-Up : 업그레이드. 기존에 갖고 있는 서버들의 하드웨어 성능을 높인다.
* Scale-Out : 확장. 여러 대의 서버를 더 증설해 서버들이 업무 분담을 하도록 한다.  

보통의 경우에는 Scale-Out 방식을 더 효과적이라고 할 수 있는데, 이유는 하드웨어 성능 향상에 드는 비용이 비싸며 서버가 여러 대 생기면 무중단 서비스를 제공하는 환경 구성에 좋기 때문이다.  

로드 밸런서는 부하를 나눌 서버를 선택하는데, 다음과 같은 것들이 있다.
* Round-Robin : CPU 스케줄링의 라운드-로빈 방식 활용
* Least Connections : 연결 개수가 가장 적은 서버 선택. 트래픽으로 세션이 길어지는 경우 권장됨.
* Source : 사용자 IP를 해싱해서 분배. 이 경우 특정 사용자는 항상 같은 서버로 연결

---
* [위키백과](https://ko.wikipedia.org/wiki/%EB%B6%80%ED%95%98%EB%B6%84%EC%82%B0)
* [gyoogle/tech-interview-for-developer](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Network/%EB%A1%9C%EB%93%9C%20%EB%B0%B8%EB%9F%B0%EC%8B%B1(Load%20Balancing).md)