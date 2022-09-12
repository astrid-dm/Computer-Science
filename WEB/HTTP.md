### 인터넷을 키고 URL을 입력해서 화면에 보여지기까지 일어나는 과정
1. 브라우저 주소창에 www.google.com을 입력
2. 브라우저가 www.google.com의 IP주소를 찾기 위해 캐시에서 DNS 기록을 확인
3. 만약 요청한 URL(www.google.com)이 캐시에 없다면, ISP의 DNS 서버가 DNS 쿼리로 www.google.com을 호스팅하는 서버의 IP 주소를 찾음 
4. 브라우저가 해당 서버와 TCP 연결을 시작
5. 브라우저가 웹서버에 HTTP 요청을 보냄
6. 서버가 요청을 처리하고 응답을 보냄
7. 서버가 HTTP 응답을 보냄 
8. 브라우저가 HTML 컨텐츠를 보여줌

### 1. 브라우저 주소창에 www.google.com을 입력

### 2. 브라우저가 www.google.com의 IP주소를 찾기 위해 캐시에서 DNS 기록을 확인
* `DNS(Domain Name System)`는 인터넷 전화번호부와 같다.
  사람이 핸드폰으로 누군가에게 전화를 걸때, 번호를 입력하기보다 상대방의 이름으로 전화번호부에서 찾듯이, 
  인터넷은 DNS를 통해 `www.google.com`으로 목적지를 찾지, `142.251.220.78`(구글의 IP주소)으로 목적지를 찾지는 않음
* 캐시에서 DNS 기록을 찾는 방법은 다음 4가지
    * 브라우저 캐시 확인 (내가 이전에 방문한 웹 사이트 기록을 일정 기간동안 브라우저가 저장함)
    * 브라우저 OS 캐시 확인 (OS도 DNS 레코드 캐시를 저장)
    * 브라우저 라우터 캐시 확인 (컴퓨터에도 원하는 DNS 레코드가 없다면, 브라우저는 라우터에서 DNS 기록을 저장한 캐시 확인)
    * ISP(Internet Service Provider) 캐시 확인 
* 캐시가 많은 곳에서 유지됨에 따라 개인 정보 보호에 위험할 수는 있지만, 네트워크 트래픽을 규제하고 데이터 전송 시간을 개선하는데 도음이 됨

### 3. 만약 요청한 URL(www.google.com)이 캐시에 없다면, ISP의 DNS 서버가 DNS 쿼리로 www.google.com을 호스팅하는 서버의 IP 주소를 찾음
* DNS 쿼리의 목적은 웹 사이트에 대한 올바른 IP 주소를 찾을 때 까지 인터넷에서 여러 DNS 서버를 검색하는 것
* 필요한 IP 주소를 찾거나, 찾을 수 없다는 오류 응답을 반환할 때까지 한 DNS 서버에서 다른 DNS 서버로 검색이 반복적으로 계속되기 때문에 이 유형의 검색을 `재귀적 질의(Recursive Query)`라고 함
* 이때 DNS 서버를 `DNS 리커서 (DNS Recursor)`라고도 부름 

### 4. 브라우저가 해당 서버와 TCP 연결을 시작
* 브라우저가 올바른 IP 주소를 수신하면 IP 주소와 일치하는 서버와 연결해 정보를 전송
* `인터넷 프로토콜(IP)`을 사용하여 이러한 연결을 구축
* 사용할 수 있는 인터넷 프로토콜은 여러가지가 있지만, 대표적으로 HTTP 요청에서는 `TCP(Transmission Control Protocol)`라는 전송 제어 프로토콜을 사용
* TCP/IP는 `3-way HandShake`라는 연결과정을 통해 이루어짐 (SYN -> SYN/ACK -> ACK)
    1. 클라이언트는 인터넷을 통해 서버에 SYN 패킷을 보내 새 연결이 가능한지 여부를 물음 
    2. 서버에 새 연결을 수락할 수 있는 포트가 있는 경우, SYN/ACK 패킷을 사용하여 SYN 패킷의 SYN(승인)으로 응답
    3. 클아이언트는 서버로부터 SYN/ACK 패킷을 수신하고 ACK 패킷을 전송하여 승인

### 5. 브라우저가 웹 서버에 HTTP 요청을 보냄
![HTTP Request](https://velog.velcdn.com/images%2Fkhy226%2Fpost%2F5a45f724-f443-4c35-8c62-ade5b3e3e9cb%2F스크린샷%202021-09-27%20오전%202.29.49.png)
* TCP 연결이 설정되면 데이터 전송이 시작됨 (www.google.com 웹 페이지를 요청하는 GET 요청이 보내짐)
* POST 요청의 경우 브라우저 식별 (User-Aget), 수락할 요청 유형 (Accept 헤더) 및 추가 요청을 위해 TCP 연결을 유지하라는 연결 헤더와 같은 추가 정보도 포함됨

### 6. 서버가 요청을 처리하고 응답(Response)을 보냄

### 7. 서버가 HTTP 응답을 보냄
![HTTP Response](https://velog.velcdn.com/images%2Fkhy226%2Fpost%2Ff51ea757-1bd1-45b3-b6bc-17cd82035c0c%2F스크린샷%202021-09-27%20오전%202.48.43.png)
* 응답을 보면 `Status Code` 헤더에 상태 코드가 숫자로 표시됨. 이것은 우리에게 Response의 상태틑 알려줌
     * 1xx (Information Response): 정보 메시지만을 나타낸다. 서버가 요청을 받았으며 서버에 연결된 클라이언트는 계속해서 작업을 하라는 뜻
    * 2xx (Successful Response): 서버와의 요청이 성공함을 나타냄
    * 3xx (Redirection Message) : 요청 완료를 위해 추가 작업 조치가 필요함을 의미함. 위 사진의 301(Moved Permantly)는 요청한 리소스의 URI가 변경 되었음을 뜻함
    * 4xx (Client Error Response) : 클라이언트의 Request에 에러가 있음을 의미
    * 5xx (Server Error) : 서버 측의 오류로 request를 수행할 수 없음

### 8. 브라우저가 HTML 컨텐츠를 보여줌
