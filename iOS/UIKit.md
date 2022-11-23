# UIKit 프레임워크
사용자의 인터페이스를 관리하고 이벤트를 처리하는 것이 주 목적인 프레임워크
### 주로 사용하는 사용자 기능
- 제스처 처리
- 애니메이션
- 그림 그리기
- 이미지 처리
- 텍스트 처리
- 테이블 뷰
- 슬라이더
- 버튼
- 텍스트필드
- 알럿창

UIKit은 MVC패턴을 사용한다. 하지만 일반적인 MVC와 다르게 View와 Controller가 강하게 연결되어 있고 ViewController가 거의 모든것을 담당한다. ViewController에서는 Controller가 생명주기를 담당하기 때문에 View와 Controller를 분리하기는 어렵다.

프로젝트의 규모가 커질수록 Controller가 비대해지고 내부 구조는 복잡하게 되어 유지보수가 힘들어지는 상황이 온다. MVC 패턴의 문제점을 해결하기 위해 MVVM, VIPER 패턴 등으로 MVC의 문제점을 해결할 수 있다.
### 참고
[iOS 아키텍처 패턴 VIPER](https://bugle.tistory.com/48)