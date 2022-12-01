# URLSession
특정한 url을 이용하여 데이터를 다운로드하고 업로드하기 위한 API

앱은 하나 이상의 `URLSession` 인스턴스를 생성하며 각 인스턴스는 관련 데이터 전송자 그룹을 조정한다. 기본 구조로 request와 response를 가지고있다. URLSession은 `URLSessionConfiguration`를 통해 생성할 수 있으며, 생성된 URLSession을 통해 한 개 이상의 `URLSessionTask`를 생성할 수 있다. URLSessionTask를 통해 실제 서버와 통신할 수 있다.

## 세션의 종류
- 공유 세션
- 기본 세션
- 임시 세션
- 백그라운드 세션

### 공유 세션(Shared Session)
싱글톤으로 사용할 수 있다. 기본 요청을 하기 위한 세션. 직접 생성한 생성만큼 맞춤 설정을 할 수 없지만 쉽게 만들어 사용할 수 있다.
```swift
URLSession.shared()
```

### 기본 세션(Default Session)
공유 세션과 유사하게 작동하지만 직접 원하는 설정을 할 수 있다. 캐시와 쿠키 인증등을 디스크에 저장한다. 순차적으로 데이터를 처리하기 위해 Delegate를 지정할 수 있다.
```swift
URLSession(configuration: .default)
```

### 임시 세션(Ephemeral Session)
공유 세션과 비슷하지만 캐시, 쿠키, 사용자 인증정보를 디스크에 저장하지 않는다. 메모리에 올려 세션을 연결하고, 세션 만료시 데이터가 사라진다.
```swift
URLSession(configuration: .ephemeral)
```

### 백그라운드 세션(Background Session)
앱이 실행되지 않는동안 백그라운드에서 컨텐츠 업로드 및 다운로드를 수행할 수 있다.
```swift
URLSession(configuration: .background)
```

## URLSessionTask
- URLSessionDataTask: 데이터 객체를 사용하여 데이터를 요청하고 응답받는다. 주로 짧고 빈번하게 요청하는 경우에 사용한다.
- URLSessionUploadTask: 데이터 객체 또는 파일 형태의 데이터를 업로드하는 작업을 수행한다. 앱이 실행되지 않았을 때 백그라운드 업로드를 지원한다.
- URLSessionDownloadTask: 데이터를 다운로드 받아 파일형태로 저장하는 작업을 수행한다. 앱이 실행중이지 않을때는 백그라운드 다운로드를 지원한다.
- URLSessionStreamTask: TCP/IP 연결을 만들때 사용하는 테스크
- URLSessionWebSocketTask: 웹소켓 프로토콜 표준을 통해 통신하는 테스크

## URLSession Life Cycle
1. Session Configuration을 결정하고, Session을 생성
2. 통신할 URL과 Request 객체를 설정
3. 사용할 Task를 결정하고 그에 맞는 Completion Handler나 Delegate 메소드들을 작성
4. 해당 Task를 실행
5. Task 완료 후 Completion Handler 클로저가 호출이 됨