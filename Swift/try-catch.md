# try-catch
Swift는 에러가 발생하면 다음과 같은 일급 객체를 제공한다.
- 발생 (throwing)
- 감지 (catching)
- 전파 (propagating)
- 조작 (manipulating)

Swift에서 에러는 에러 프로토콜을 따르는 타입의 값으로 표현된다. 에러 프로토콜은 요구사항이 없는 빈 프로토콜이다. Swift의 열거형은 오류 원인을 나누고 해당 오류의 특성에 대한 추가정보를 만드는데 적합하다.
```swift
// 에러 프로토콜을 채택한 열거형
enum PhoneError: Error {
    case unknown
    case batteryLow(batteryLevel: Int)
}

throw PhoneError.batteryLow(batteryLevel: 20)
```
### 오류를 처리하는 4가지 방법
- 함수에서 발생한 오류를 해당 함수를 호출한 코드에 전파
  - 함수 실행문 뒤에 `throws` 키워드를 작성한다.
  - 만약 반환값이 필요하면 throws 뒤에 `-> 반환값` 을 작성한다.
  ```swift
  func checkPhoneBatteryStatus(batteryLevel: Int) throws -> String {
      guard batteryLevel != -1 else { throw PhoneError.unknown }
      guard batteryLevel > 20 else { throw PhoneError.batteryLow(batteryLevel: 20) }
      return "배터리 상태가 정상입니다."
  }
  ```
- do-catch 구문을 이용
  ```swift
  /*
  do {
    try 오류 발생 가능코드
  } catch 오류 패턴 {
    처리 코드
  }
  */
  do {
    try checkPhoneBatteryStatus(batteryLevel: -1)
  } catch PhoneError.unknown {
    print("알 수 없는 에러입니다.")
  } catch PhoneError.batteryLow(let batteryLevel) {
    print("배터리 전원 부족 남은 베터리 : \(batteryLevel)%")
  } catch {
    print("그 외 오류 발생 : \(error)")
  }
  ```
- 옵셔널로 처리
  ```swift
  let status = try? checkPhoneBatteryStatus(batteryLevel: 30)
  print(status) // Optional("배터리 상태가 정상압니다.")

  let status2 = try? checkPhoneBatteryStatus(batteryLevel: -1)
  print(status) // nil
  ```
- 오류 없음 확신
  - `nil`이 반환되는 경우 런타임 에러로 프로그램이 종료될 수 있다.
  ```swift
  let status3 = try! checkPhoneBatteryStatus(batteryLevel: 30)
  print(status2) // "배터리 상태가 정상압니다."
  ```