### GET
- 리소스 조회
- ex : `GET /search?q=hello&lr=ko`
- 서버에 전달하고 싶은 데이터는 query(쿼리 파라미터, 쿼리 스트링)를 통해서 전달
- 메세지 바디(ex : `Request Body`)를 사용해서 데이터를 전달할 수 있지만, 지원하지 않는 곳이 많아서 권장하지 않음
    - GET은 멱등성을 보장하기 때문

### POST
- 요청 데이터 처리, 주로 등록에 사용
    1. 새 리소스를 생성(등록) : 서버가 아직 식별하지 않은 새 리소스 생성
    2. 요청 데이터 처리 : 결제완료 -> 배달시작 -> 배달완료 처럼 단순히 값 변경을 넘어 프로세스의 상태가 변경되는 경우
    3. 다른 메서드로 처리하기 애매한 경우 : ex) JSON으로 조회 데이터를 넘겨야 하는데, GET 메서드를 사용하기 어려운 경우, 애매하면 POST 
- 메세지 바디(ex : `Request Body`)를 통해 서버로 요청 데이터 전달
- 서버는 요청 데이터를 처리
    - 메세지 바디를 통해 들어온 데이터를 처리하는 모든 기능을 수행

### PUT 
- 리소스를 대체, 해당 리소스가 없으면 생성
    - ex : 등록된 게시글 수정
- POST와의 차이점은 클라이언트가 리소스의 위치를 알고 URI를 지정
    - ex : `PUT /members/100`
    - ex : `POST /members`
- 리소스를 대체한다는 것이 큰 특징
![PUT1](https://github.com/Astrid-DM/Computer-Science/blob/main/WEB/Image_Folder/Screen%20Shot%202022-09-12%20at%208.34.26%20PM.png)
![PUT2](https://github.com/Astrid-DM/Computer-Science/blob/main/WEB/Image_Folder/Screen%20Shot%202022-09-12%20at%208.34.34%20PM.png)

### PATCH
- PUT과 유사하나, PUT처럼 리소스를 완전히 대체하는 것이 아닌 리소스를 부분 변경
![PUT1](https://github.com/Astrid-DM/Computer-Science/blob/main/WEB/Image_Folder/Screen%20Shot%202022-09-12%20at%208.34.26%20PM.png)
![PATH](https://github.com/Astrid-DM/Computer-Science/blob/main/WEB/Image_Folder/Screen%20Shot%202022-09-12%20at%208.35.21%20PM.png)

### DELETE
- 리소스 삭제
