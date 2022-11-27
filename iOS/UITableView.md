# UITableView
데이터를 목록 형태로 보여줄 수 있는 가장 기본적인 UI 컴포넌트. UIScrollView를 상속받고 있어 스크롤이 가능해 리스트 형태로 많으 정보를 보여줄 수 있다.
- 여러 개의 Cell을 가지고 있고 하나의 열과 여러 줄의 행을 지니고 있으며, 수직으로만 스크롤 가능
- 섹션을 이용해 행을 그룹화하여 콘텐츠를 좀 더 쉽게 탐색할 수
있다.
- 섹션의 헤더와 푸터에 View를 구성하여 추가적인 정보를 표시할 수 있다.

`UITableViewDataSource`, `UITableViewDelegate` 프로토콜을 채택하여 구현 해주어야 한다. DataSource는 데이터를 받아 뷰를 그려주고 Delegate는 테이블뷰의 동작과 외관을 담당한다. 뷰가 변경되는 사항을 Delegate가 담당하고 뷰는 Delegate에 의존하여 뷰를 업데이트한다.

DataSource에는 총 섹션이 몇 개인지, 섹션의 행은 몇 개인지, 행이 어떤 정보를 표시 할 것인지 등을 정의할 수 있다. Delegate는 행의 높이, 행 선택시 액션 등을 정의 할 수 있다.

### UITableViewDataSource
테이블 뷰를 생성하고 수정하는데 필요한 정보를 테이블 뷰 객체에 제공
```swift
public protocol UITableViewDataSource : NSObjectProtocol {
    
    // 필수
    // 각 섹션에 표시할 행의 개수를 묻는 메소드
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int

    // 필수
    // 특정 인덱스 Row의 Cell에 대한 정보를 넣어 Cell을 반환하는 메소드
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell

    // 총 섹션 개수들 묻는 메소드
    optional func numberOfSections(in tableView: UITableView) -> Int

    // 특정 섹션의 헤더 타이틀을 묻는 메소드
    optional func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String?

    // 특정 섹션의 푸터 타이들을 묻는 메소드
    optional func tableView(_ tableView: UITableView, titleforfooterInSection section: Int) -> String?

    // 특정 위치의 행이 편집 가능한지 묻는 메소드
    optional func tableView(_ tableView: UITableView, canEditRowAt indexPath: IndexPath) -> Bool

    // 특정 위치의 행을 재정렬 할 수 있는지 묻는 메소드
    optional func tableView(_ tableView: UITableView, canMoveRowAt indexPath: IndexPath) -> Bool

    // 테이블 뷰 섹션 인덱스 타이들을 문는 메소드
    optional func sectionIndexTitles(for tableView: UITableView) -> [String]?

    // 인덱스에 해당하는 섹션을 알려주는 메소드
    optional func tableView(_ tableView: UITableView, sectionForSectionIndexTitle title: String, at index: Int) -> Int
    
    // 스와이프 모드, 편집 모드에서 버튼을 선택하면 호출 되는 메셔드
    // 해당 메소드에서는 행에 변경사항을 Commit 해야 합
    optional func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStyle, forRowAt indexPath: IndexPath)

    // 행이 다른 위치로 이동되면 어디에서 어디로 이동했는지 알려주는 메소드
    optional func tableView(_ tableView: UITableView, moveRowAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath)
}
```

### UITableViewDelegate
테이블 뷰의 시각적인 부분을 설정하고, 행의 액션 관리, 액세서리 뷰 지원. 테이블 뷰의 개별 행 편집을 도와준다.
```swift
public protocol UITableViewDelegate: UIScrollViewDelegate {
    
    // 행이 선택되었을 때 호출되는 메소드
    optional func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath)

    // 행이 선택 해제되었을 때 호출되는 메소드
    optional func tableView(_ tableView: UITableView, didDeselectRowAt indexPath: IndexPath)
    
    // 특정 위치 행의 높이를 묻는 메소드
    optional func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat
    
    // 지정된 섹션의 헤더 뷰 또는 푸터뷰에 표시할 View 가 어떤 건지 묻는 메소드
    optional func tableView(_ tableView: UITableView, viewForHeaderInSection section: Int) -> UIView?
    optional func tableView(_ tableView: UITableView, viewForFooterInSection section: Int) -> UIView?
    
    // 지정된 색션의 헤더 뷰 또는 푸터뷰의 높이를 묻는 메소드
    optional func tableView(_ tableView: UITableView, heightforHeaderInSection section: Int) -> CGFloat
    optional func tableView(_ tableView: UITableView, heightForfooterInSection section: Int) -> CGFloat
    
    // 테이블 뷰가 편집 모드에 들어갔을 때 호출되는 메소드
    optional func tableView(_ tableView: UITableView, willBeginEditingRowAt indexPath: IndexPath)
    
    // 테이블 뷰가 편집 모드에서 빠져나왔을 때 호출되는 메소드
    optional func tableView(_ tableView: UITableView, didEndEditingRowAt indexPath: IndexPath?)
    
    // 테이블 뷰가 셀을 사용하여 행을 그리기 직전에 호출되는 메소드
    optional func tableView(_ tableView: UITableView, willDisplay cell: UITableViewCell, forRowAt indexPath: IndexPath)
    
    // 테이블 뷰로부터 셀이 화면에 사라지면 호출되는 메소드
    optional func tableView(_ tableView: UITableView, didendDisplaying cell: UITableViewCell, forRowAt indexPath: IndexPath)
}
```