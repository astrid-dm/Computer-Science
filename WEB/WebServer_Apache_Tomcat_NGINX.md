## 아파치 (Apache)
아파치는 여러가지 프로젝트를 통해 오픈소스를 만들어내는 소프트웨어 단체 이름이다.\
따라서 아파치 서버란 이 단체에서 만든 http 웹서버를 의미하며, 아차피 서버는 http 요청을 처리할 수 있다.\
클라이언트가 `GET`, `POST`, `DELETE`같은 메서드를 요청하면 그에 대한 결과값을 반환한다.\
이때 결과값은 정적 데이터다. (ex : html, css, js, jpeg...)


## 톰캣 (Tomcat)
톰캣은 WAS(Web Application Server)다. 얼핏 생각하면 아차피 서버와 같다고 생각할 수 있지만, 둘의 목적은 다르다.\
아파치 웹서버(WS)는 **정적 데이터**를 처리하는 서버이고, WAS는 **동적 데이터**를 처리하는 서버다.\
즉, WAS는 DB와 연결되어 데이터를 주고 받는 것이다. 웹 사이드 주소를 보다보면 html이 아닌 http://~/abcde.jsp라는 주소를 볼 때가 있는데, **웹 애플리케이션 서버는 이 JSP(Java Server Page)를 처리하는 프로그램**이다. 즉, Java로 만들어진 프로그램을 웹 서버에서 돌려서 결과값을 클라이언트에게 돌려준다.

#### ❗️ 관계 정리 : 클라이언트 - 웹서버 - WAS(웹 어플리케이션 서버) - DB

## 엔진엑스 (NGINX)
엔진엑스는 아파치와 같은 웹 서버다. 그러나 아파치의 단점을 보완하기 위해 만든 프로그램이다.\
아파치는 C10K Problem, 즉, 하나의 웹 서버에 10,000개의 클라이언트 접속을 커버하기 위해 가벼움과 높은 성능을 추구하여 만들어졌다. 아파치와의 차이점은 아파치는 멀티 쓰레드 / 멀티 프로세스 기반 구조이며, 각 요청당 쓰레드 하나가 처리한다.\
한명의 클라이언트 당 하나의 쓰레드가 할당되므로 사용자가 많아지면 시스템 자원 낭비가 심해진다는 단점이 있다.\
반면 NGINX는 비동기 기반 구조라 더 적은 리소스를 활용해서 요청을 처리할 수 있다.\
이 비동기 구조를 `Event-Driven`이라 부르며, 한 개 혹은 고정된 프로세스만 생성해서 사용한다.\
이때 비동기 방식으로 요청들을 Concurrency하게 처리할 수 있다.\
아파치와 마찬가지로 WS(웹 서버)이기 떄문에, 동적 데이터는 처리하지 않는다. (다른 WAS의 도움 필요)

## Apache vs NGINX
![분석표](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FJnnYB%2Fbtrv8Eyfi4P%2FDsxzDFx61BgKe4moaFmIn1%2Fimg.png)

#
##### 출처 1 : [장철원님의 아파치(Apache), 톰캣(Tomcat), 엔진엑스(Nginx) 차이](https://losskatsu.github.io/it-infra/webserver/#웹서버-아파치apache-톰캣tomcat-엔진엑스nginx-차이)
##### 출처 2 : [실패전문개발자의 일기 - Apache vs NGINX, 그리고 NGINX 설정](https://jungyu09.tistory.com/12)
