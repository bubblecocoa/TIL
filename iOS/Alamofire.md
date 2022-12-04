# Alamofire
Swift 기반의 HTTP 네트워킹 라이브러리.

URLSession에 기반한 라이브러리로, 네트워킹 작업을 단순화하고 네트워킹을 위한 다양한 메소드와 JSON parsing을 제공한다.
- 연결 가능한 request, response 메소드를 제공한다.
- URL, JSON 형태 파라미터 인코딩을 지원한다.
- file data stream, `multipart/form-data` 등 업로드 기능을 제공한다.
- HTTP Response 검증과 광범위한 단위테스트 및 통합테스트를 보장한다.

Swift에서 기본적으로 제공하는 `URLSession`을 통해서도 HTTP 통신이 가능하지만, `Alamofire`를 사용하면 코드의 간소화, 가독성 측면에서 도움을 주고 여러 기능을 직접 구축하지 않아도 쉽게 사용할 수 있다.

`request`메소드에 url, 메소드, 파라미터, 헤더 등등 요청에 필요한 정보를 쉽게 설정할 수 있다. `HTTPMethod`에는 `REST API`에 이용되는 `GET`, `POST`, `PUT`, `DELETE`가 정의되어 있으며, 요청을 만들때 리퀘스트 메소드 파라미터에 HTTP 메소드를 전달할 수 있다. 요청에 대한 응답은 `response`메소드를 이용하여 핸들링한다. 6개의 response 메소드가 정의되어 있으며, 응답이 완료되면 `completionHandler`가 호출된다. 응답 메소드는 요청 메소드에 체이닝하여 사용한다.