### VIP
----
- 가상의 IP
- 하나의 호스트에 여러 개의 IP 주소를 할당
- 특성 서버 그룹의 대표 IP
- 실제 물리적 네트워크 인터페이스에는 해당하지 않는 IP 주소
![image](https://github.com/Astrid-DM/Computer-Science/assets/65839810/98f6a378-1ba0-4775-aeb5-f20c9d80b991)

<br>

### MMM (Multi Master Replication Master)
----
- Perl 기반의 Auto Failover Open Source
- *Master(Active)와 Master(Standby)의 양방향 복제*
- *Master(Standby)는 데이터가 변경되지 않도록 MMM 모니터로부터 읽기모드로 제어됨*
- DB 서버에서 Agent를 실행하고 MMM Monitor에서 통신하는 방식으로 DB 서버의 Health Check와 Failover를 실행
- NHN에서 운영중인 대표적인 이중화 방안
![image](https://github.com/Astrid-DM/Computer-Science/assets/65839810/abf7d1d3-1d7f-4f7c-b8fc-d1530d6f802a)
<br>
