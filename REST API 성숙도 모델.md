# 2022-06-10
Rest API: 내꺼가 아니라 남의꺼랑 실행시킴

-리소스 
엘리먼트는 컬렉션의 하나하나 데이터 
컬렉션은 엘리먼트의 모음 

정보 가공방법? 
C R U D 
이거를 메소드라고 부름 

Create는 Post (생성)
Read는 get 
Update는 put(전체내용) , patch(부분내용)
DELETE delete 

REST API 디자인방법 총 4단계의 모델 

0단계 HTTP 사용 
1단계 개별 리소스와의 통신준수
2단계 HTTP 메소드 원칙 준수
3단계 HATEOAS원칙 준수 

3단계 까지는 지키키 어려우므로 2단계까지 적용해도 좋은 API 디자인이라고 볼 수 있음 (HTTP API)


REST 성숙도 모델 0단계 

단순히 HTTP 프로토콜을 사용하기만 해도 됨 (REST API를 작성하기 위한 기본 단계)

REST 성숙도 모델 1단계

개별 리소스와의 통신을 준수해야 함 
모든 리소스는 개별 리소스에 맞는 앤드포인트를 사용해야되며 요청을 해서 받은 리소스에 대해 응답해야 된다는것이 핵심

ex/ POST /doctors/허준 에서 /doctors/허준 이라는 엔드포인트 사용 
    POST /slots/123 에서 /slot/123으로 실제 변경되는 리소스를 엔드포인트로 사용 
엔드포인트 작성시에는 리소스에 집중해 명사형태로 작성 

REST 성숙도 모델 2단계
CRUD에 맞게 적절한 http 메서드를 사용하는 것을 중점에 둠 

CREAT는 POST
READ는 GET
UPDATE는 PUT(전체내용), PATCH(부분내용)
DELETE는 delete 

http메서드 사용 유의사항 
1. get 메서드는 서버의 데이터를 변화시키지 않는 요청에 사용해야함 
2. post 메서드는 요청마다 새로운 리소스를 생성하고 put메서드는 요청마다 같은 리소스를 반환해야함 (멱등성 유의)
3. put 메서드와 patch 메서드 구분하여 사용해야함 

REST 성숙도 모델 3단계
HATEOAS(Hypertext As The Engine Of Application State) 즉 표현되는 하이퍼미디어 컨트롤 적용 
응답에 리소스의 URI를 포함한 링크요소를 삽입하여 작성해야함 

Open API? : 누구나 사용할 수 있도록 공개된 api 하지만 open api도 이용 수칙이 존재 (데이터를 JSON 형태로 응답)

API Key? :  API를 이용하기 위한 열쇠 즉 서버의 문을 여는 열쇠 서버 운용하는 데에 비용이 발생하기 때문에 원하는 이용자만 api에 접근할 수 있도록 하기 위해 만들어짐 
              데이터를 요청할 때 API KEY를 같이 전달해야ㅕ 원하는 응답을 받을 수 있는 구조 