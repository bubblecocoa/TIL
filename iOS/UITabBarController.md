# UITabBarController
다중 선택 인터페이스를 관리하는 컨테이너 뷰 컨트롤러로, 선택에 따라 어떤 자식 뷰 컨트롤러를 보여줄 것인지가 결정하는 역할을 한다.

### UITabBar
앱에서 서로 다른 하위작업, 뷰, 모드 사이의 선택을 할 수 있도록, 탭바에 하나 혹은 하나 이상의 버튼을 보여주는 컨트롤러

보통 `UITabBarController`와 함께 사용되지만, 앱에서 독립적인 컨트롤로 사용할 수 있다. 항상 화면의 하단에 위치하며, 1개 혹은 1개 이상의 `UITabBarItem`객체를 표시한다. 인터페이스의 요구에 맞춰 이미지나 색상을 변경할 수 있다. 탭바 아이템을 선택함에 따라 앱에서 그에 상응하는 행동을 구현할 수 있다.

`UIViewController`를 상속받아 뷰속성을 가진다. 해당 뷰는 탭바 뷰와 커스텀 컨텐츠를 포함한 뷰다.