# NotificationCenter
등록된 이벤트가 발생하면 해당 이벤트들에 대한 행동을 취한다. 앱 내 어느곳에서든 메시지를 던질 수 있고, 받을 수 있다.
> `Delegate`를 통해서 데이터를 전달하는 것은 웹 프론트엔드 프레임워크에서 자식 -> 부모의 상태를 갱신하는것과 유사하고, `NotificationCenter`를 통해서 데이터를 전달하는 것은 `Redux`나 `Vuex`를 이용하여 전역적으로 공통된 상태를 관리하는것과 유사