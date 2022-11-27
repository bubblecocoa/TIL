# UIStackView
열 또는 행에 View 들의 묶음을 배치할 수 있는 간소화된 인터페이스

스택뷰는 오토레이아웃을 이용하여 디바이스의 스크린 사이즈나 어떠한 변화에 맞춰 동적인 UI를 구성할 수 있다.

복잡한 레이아웃을 구성시 일일이 오토레이아웃 제약조건을 사용하면 제약조건이 많아져 복잡해지고 관리하기 힘들어진다. 때로는 원하는대로 UI구성이 안될수도 있다.

스택뷰를 사용하면 오토레이아웃 제약조건을 많이 설정하지 않아도 쉽게 UI 구성이 가능하다.

> 웹에서 `flex`의 `flex-direction: column;` `flex-direction: row;` 구조를 만드는 것과 유사하다.
## StackView의 속성
- Axis
- Distribution

### Axis
StackView의 방향을 결정하는 속성.
`Vertical`은 서브뷰들을 세로로 배치하고 `Horizontal`은 서브뷰들을 가로로 배치한다.

### Distribution
StackView 안에 들어가는 뷰들의 사이즈를 어떻게 분배할지 설정하는 속성.

- `Fill`: 스택뷰의 방향에 따라 가능한 공간을 모두 채우기 위해 서브뷰들의 크기를 재조정한다. 서브뷰들이 스택뷰 사이즈를 초과하면 각 뷰의 compression resistance priority에따라 각 뷰의 크기를 감소시킨다. pritory가 낮은 뷰의 크기가 먼저 감소된다. 서뷰뷰들의 크기가 스택뷰의 크기에 미달한다면 각 뷰의 hugging priority에 따라 각 뷰를 늘려 스택뷰를 채운다. priority가 낮은 뷰의 크기가 먼저 증가한다.
- `Fill Proportionally`: 스택뷰의 방향에 따라 스택뷰가 가지고있던 크기에 비례하여 공간을 차지하도록 만들어준다.
- `Equal Spacing`: 스택뷰의 방향에 따라 서브뷰들의 간격을 균등하게 배치한다.
- `Equal Centering`: 스택뷰의 방향에 따라 각 서브뷰들의 중앙과 중앙간의 거리를 동일하게 만든다.

### Alignment
스택뷰의 서브뷰들을 어떤식으로 정렬할지 결정하는 속성
- `Fill`: 스택뷰의 방향이 Horizontal일 경우 상-하 공간을 채우기 위해, Vertical일 경우 좌-우 공간을 채우기 위해 서브뷰들을 늘린다.
- `Leading`: Vertical 스택뷰에서 서브뷰들이 스택뷰의 Leading에 맞춰 정렬한다. 서브뷰들이 스택뷰의 왼쪽에 정렬된다.
- `Trailing`: Vertical 스택뷰에서 서브뷰들이 스택뷰의 오른쪽에 정렬된다.
- `Top`: Horizontal 스택뷰에서 서브뷰들이 스택뷰의 상단에 정렬된다.
- `Bottom`: Horizontal 스택뷰에서 서브뷰들이 스택뷰의 하단에 정렬된다.
- `First Baseline`: 서브뷰들의 first baseline에 맞춰 스택뷰가 서브뷰들을 정렬한다. Horiziontal에서만 사용 가능하다.
- `Last Baseline`: 서브뷰들의 last baseline에 맞춰 스택뷰가 서브뷰들을 정렬한다. Horiziontal에서만 사용 가능하다.
- `Center`: 스택뷰 방향에 따라 서브뷰들의 중앙을 스택뷰의 중앙에 맞춰 정렬한다.

### Spacing
스택뷰 안에 들어가는 뷰들의 간격을 조정하는 속성.