## 클라이언트에서 서버로 데이터 전송
---
**데이터 전송은 크게 2가지**
### Query Parameter를 통한 데이터 전송
💡 Query Parameter란?
``` java
// 예시 - 아이디가 123인 user의 데이터를 가져온다
/users?id=123
```
- `GET`
- 주로 정렬 필터(검색어)
- `GET`도 Message Body로 데이터를 요청할 수는 있으나, 아직 지원하지 않는 브라우저도 있어서 실무에서는 사용 X
- 정적 데이터(ex : 이미지 데이터, 텍스트)의 경우, Query Parameter가 아닌 Path Variable(리소스 경로)로 조회
```
GET /static/star.jpg
```
### Message Body를 통한 데이터 전송
- `POST`, `PUT`, `PATCH`
- 회원 가입, 상품 주문, 리소스 등록, 리소스 변경
<br/><br/>
## HTML Form 데이터 전송 (별로 안중요)
- HTML Form submit시 `POST` 전송
    - ex) 회원 가입, 상품 주문, 데이터 변경
- Content-Type : application/x-www-form-urlencoded 사용
    - form의 내용을 메시지 바디를 통해 전송 (key=value, Query Parameter 형식)
    - 전송 데이터를 url encoding 처리
        - ex) abc김 -> abc%EA%B9%80
- HTML Form은 `GET` 전송도 가능
- Content-Type : multipart/form-data
    - 파일 업로드 같은 바이너리 데이터 전송시 사용
    - 다른 종류의 여러 파일과 폼의 내용 함께 전송 가능 (그래서 이름이 multipart)
- 참고 : HTML Form 전송은 `GET`, `POST`**만 지원**
<br/><br/>
## HTML API 데이터 전송
- 웹 클라이언트
    - HTML에서 Form 전송 대신 자바 스크립트를 통한 통신에 사용 (AJAX)
    - ex) Reach, Vue.js같은 웹 클라이언트와 API 통신
- `POST`, `PUT`, `PATCH`: 메시지 바디를 통한 데이터 전송
- `GET`: 조회, 쿼리 파라미터로 데이터 전달 
- Content-Type: application/json을 주로 사용 (사실상 표준)
    ex : TEXT, XML, JSON등
