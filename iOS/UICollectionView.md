# UICollectionView
데이터 항목의 정렬된 컬렉션을 관리하고 커스텀한 레이아웃을 사용해 표시하는 객체

테이블뷰는 리스트 형태로만 표현이 가능하지만 컬렉션뷰는 리스트 뿐만 아니라 슬라이드와 같이 다양한 형태로 표현이 가능하다.

`Supplementary View`와 `Cell`로 구성되어있다.
셀은 컬렉션 뷰의 콘텐츠를 표시하고 컬렉션뷰는 컬렉션뷰 데이터소스 객체에서 표시할 셀의 정보를 가져온다.
Supplementary 뷰는 헤더와 푸터처럼 섹션에 대한 정보를 표시한다.
`Decoration View`는 컬렉션 뷰에 대한 배경을 꾸밀때 사용한다.

### UICollectionViewLayout
컬렉션 뷰 내의 아이템 배치 및 시각적 스타일을 결정한다. 레이아웃 객체는 셀, Supplementary View, 컬렉션 뷰의 바운드, 내부의 데코레이션 뷰의 위치를 결정하고 시각적 상태의 정보를 컬렉션 뷰에 제공한다.

### UICollectionViewFlowLayout
클래스의 레이아웃 객체를 사용하여 셀을 원하는 형태로 정렬할 수 있다. flow layout은 셀의 선형 경로를 배치하는데, 최대한 행을 따라 많은 셀을 채우다가 행에 더이상 셀을 넣을 수 없게 되면 새로운 행을 계속 배치해 나간다.

**구성단계**
1. Flow 레이아웃 객체를 작성하고 컬렉션 뷰에 이를 할당한다.
2. 셀의 width, height 를 정한다.
3. 필요한 경우 셀들 간의 좌우 최소 간격, 위아래 최소 간격을 설정한다.
4. 색션에 header 와 footer 가 있다면 이것들의 크기를 지정한다.
5. 레이아웃의 스크롤 방향을 설정한다.

셀과 행간의 간격 이외에 `UIEdgeInsetsMake`를 통해 섹션 자체에 간격을 줄 수 있다.

### UICollectionViewDataSource
컬렉션 뷰로 보여지는 컨텐츠들을 관리하는 객체. 데이터소소를 정의하기 위해서는 해당 프로토콜을 준수해야한다. 데이터소스는 컬렉션뷰에 몇개의 섹션이 있는지, 특정 섹션에 몇개의 셀이 있는지, 특정 섹션이나 셀의 컨텐츠를 보여주기 위해 어떤 뷰를 사용할 것인지의 정보를 컬렉션뷰에 제공하는 역할을 한다. 필수 구현
```swift
public protocol UICollectionViewDataSource : NSObjectProtocol {
    // 지정된 섹션에 표시할 셀의 개수를 묻는 메서드
    func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int

    // 컬렉션뷰의 지정된 위치에 표시할 셀을 요청하는 메서드
    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell

    // 섹션의 개수를 묻는 메서드
    optional func numberOfSections(in collectionView: UICollectionView) -> Int
}
```

### UICollectionViewDelegate
컨텐츠의 표현, 사용자와의 상호작용과 관련된 것들을 관리하는 객체. 데이터소스와 다르게 구현하지 않아도 상관없다.