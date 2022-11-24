# UINavigationController
## Content View Controller
- 화면을 구성하는 뷰를 직접 구현하고 관련된 이벤트를 처리하는 뷰 컨트롤러

## Container View Controller
- 하나 이상의 Child View Controller를 가지고있다.
- 하나 이상의 Child View Controller를 관리하고 레이아웃과 화면 전환을 담당한다.
- 화면 구성과 이벤트 관리는 Child View Controlle에서 한다.
- Container View Controller는 대표적으로 Navigation Controller와 TabBar Controller가 있다.

Navigation Controller는 계층구조로 된 content를 순차적으로 보여주는 Container View Controller이다. `Navigation Stack`이라 칭하는 정렬된 배열을 사용하여 자식 뷰 컨트롤러를 관리한다. 배열의 첫번째 뷰 컨트롤러는 루트 뷰를 의미하고 스택의 가장 밑에 있다. 배열의 마지막 뷰 컨트롤러는 스택의 최상단을 의미하고 현재 화면에 보이게 된다.
> Navigation Stack은 LIFO 특성의 스택이다.

개발자는 세그웨이를 사용하거나 UINavigationController 메소드를 사용하여 스택으로부터 뷰 컨트롤러를 추가/제거할 수 있다.

사용자는 뒤로가기 버튼이나 왼쪽 엣지 스와이퍼 제스쳐를 이용하여 최상단 뷰 컨트롤러를 제거할 수 있다.

### Navigation Bar
Navigation Controller로 구현 시 화면 상단에 항상 보여지는 바. 루트를 제외한 모든 뷰 컨트롤러에 뒤로가기 버튼이 있다.

구성요소
- 네비게이션 바
- 버튼 아이템
- 타이틀
- 프롬프트

자식 뷰 컨트롤러마다 다른 구성요소로 네비게이션 바를 구현할 수 있다.