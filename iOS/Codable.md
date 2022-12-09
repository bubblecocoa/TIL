# Codable
자신을 변환하거나 외부표현으로 변환할 수 있는 타입을 의미하는 **프로토콜**. 외부표현이란 `JSON`과 같은 타입을 의미한다. `Decodable`과 `Encodable` 프로토콜을 준수한다.
- Decodable: 자신을 외부표현에서 디코딩 할 수 있는 타입
- Encodable: 자신을 외부표현에서 인코딩 할 수 있는 타입

두 프로토콜을 준수하기때문에 Codable 프로토콜을 채택하면 디코딩과 인코딩이 모두 가능하다.