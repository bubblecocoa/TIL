# assert와 guard문
assert
- 특정 조건을 체크하고, 조건이 성립되지 않으면 메세지를 출력 하게 할 수 있는 함수
- assert 함수는 디버깅 모드에서만 동작하고 주로 디버깅 중 조건의 검증을 위하여 사용한다.
```swift
var value = 0
assert(value == 0) // 조건 성립하여 통과

value = 2
assert(value == 0, "값이 0이 아닙니다") // 조건 성립하지 않아 에러 출력
```
gurad 문
- 뭔가를 검사하여 그 다음에 오는 코드를 실행할지 말지 결정 하는 것
- guard 문에 주어진 조건문이 거짓일 때 구문이 실행됨
```swift
/*
gurad 조건식 else {
    //조건이 false 이면 e1se 구문이 실행되고
    return or throw or break 를 통해 이 후 코드를 실행하지 않도록 한다.
*/
func guardTest (value: Int) {
    guard value == 0 else { return }
    print("안녕하세요")
}

guardTest(value: 2) // 미출력
guardTest(value: 0) // "안녕하세요"
```
```swift
// guard문을 통한 옵셔널 바인딩
func guardTest(value: Int?) {
    guard let value = value else { return }
    print (value)
}
guardTest(value: 2) // 2
guardTest(value: nil) // 미출력
```
`if`, `let` 문법을 사용한 옵셔널 바인딩과 다르게 guard문을 사용하면 옵셔널 바인딩 된 상수를 조건문 범위 밖에서도 사용할 수 있다.