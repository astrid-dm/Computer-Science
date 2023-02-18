## HTTP API 설계 예시

### 회원 관리 시스템의 API 설계 - POST 기반 등록

- 회원 목록 : `/members` -> **GET**
- 회원 등록 : `/members` -> **POST**
- 회원 조회 : `/members/{id}` -> **GET**
- 회원 수정 : `/members/{id}` -> **PATCH**, **PUT**, **POST**
- 회원 삭제 : `/members{id}` -> **DELETE**

### 회원 수정시 주의 사항
- 회원 정보의 일부내용 수정시 **PATCH**가  가장 권장됨
- 완전히 수정된 내용을 덮는 상황이면 **PUT**도 사용 가능하나, 하나라도 내용이 누락되면 안되므로 주의
- 그러나 게시글 수정과 관련해서는  **PUT**이 권장됨. 게시글은 부분 수정이 아닌 전체 수정으로 인식되기 때문
- 만약 이것도 저것도 애매하다면 그냥 **POST** 사용 권장
### POST
- 클라이언트는 등록될 리소스의 URI를 모름. 즉, 클라이언트는 그냥 서버에 회원을 새로 만들어달라고 요청
    - 회원 등록 : `/members` -> **POST**
    - **POST** `/members`
- 서버가 새로 등록된 리소스 URI를 결정 및 생성 
```
HTTP/1.1 201 Created
Location: /members/100
```
- 컬렉션(Collection)
    - 서버가 관리하는 리소스 디렉터리
    - 서버가 리소스의 URI를 생성하고 관리
    - 여기서 컬렉션은 `/members`
----
### 파일 관리 시스템 API 설계 - PUT 기반 등록
- 파일 목록 : `/files` -> `GET`
- 파일 조회 : `/files`/{filename} -> **GET**
- 파일 등록 : `/files/{filename}` -> **PUT**
- 파일 삭제 : `/files/{filename}` -> **DELETE**
- 파일 대량 등록 : `/files` -> **POST**
### PUT
- 클라이언트가 리소스 URI를 알고있어야 함
    - 파일 등록 : `/files/{filename}` -> **PUT**
    - **PUT** : `/files/star.jpg`
- 클라이언트가 직접 리소스의 URI를 결정 및 지정
- 스토어 (Store)
    - 클라이언트가 관리하는 리소스 저장소
    - 클라이언트가 리소스의 URI를 알고 관리
    - 여기서 스토어는 `/files`
----
### POST vs PUT
- POST
    - 리소스 생성
    - 요청 시마다, 새로운 리소스 생성
- PUT
    - 리소스의 생성과 수정
    - 요청 시마다, 같은 리소스를 반환
- 결론 : PUT은 멱등하고 POST는 멱등하지 않음
----
### HTTP FORM 사용
- HTTP FORM은 **GET**, **POST**만 지원
- AJAX같은 기술을 사용해서 해결 가능 -> 회원 API 참고
- 컨트롤 URI로 **GET**, **POST** 극복 가능
    - ex: `/members/{id}/delete` -> **POST**
