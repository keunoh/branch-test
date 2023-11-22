- 클라우드컴퓨팅은 데이터 처리 혹은 데이터 저장을 내 컴퓨터가 아닌 외부의 다른 컴퓨터로 하는 것을 의미합니다.
- [.git] 폴더에는 Git으로 생성한 버전들의 정보와 원격저장소 주소 등이 들어 있는데요, [.git] 폴더를 우리는 로컬저장소라고 부릅니다.
- Git에서는 이렇게 생성된 각 버전을 커밋(Commit)이라고 부릅니다.
- 커밋에는 상세 설명을 적을 수 있습니다. 설명을 잘 적어 놓으면 내가 이 파일을 왜 만들었는지, 왜 수정했는지 알 수 있고, 해당 버전을 찾아 그 버전으로 코드를 바꿔 시간 여행을 하기도 수월합니다.
- 이렇게 만들어둔 커밋으로 우리는 언제든 시간 여행을 할 수 있습니다. 개발을 하다가 요구사항이 바뀌어서 이전 커밋부터 다시 개발하고 싶다면 Git을 사용해 그 커밋으로 돌아가면 되겠죠?
- 이처럼 checkout 명령어를 사용해서 원하는 시점으로 파일을 되돌릴 수 있습니다.
- 이렇게 로컬저장소의 커밋을 원격저장소로 push 명령어를 사용해서 올리는 일을 푸시한다라고 합니다.
- 원격저장소의 코드와 버전 전체를 내 컴퓨터로 내려받는 것을 클론이라고 합니다. 클론을 하면 최신 버전뿐만 아니라 이전 버전들과 원격저장소 주소 등이 내 컴퓨터의 로컬저장소에 저장됩니다.
- [Download ZIP]으로도 소스코드를 똑같이 받을 수 있지만 그러면 원격저장소와 버전 정보가 제외되니 꼭 클론을 통해 받아주세요.
- pull은 원격저장소에 새로운 커밋이 있다면 그걸 내 로컬저장소에 받아오라는 명령어입니다.
- 소스트리 그래프의 왼쪽에는 [master]라는 꼬리표가, 하나 이전 버전인 '개발자 목록 추가' 커밋 왼쪽에는 [origin/master]라는 꼬리표가 붙어 있습니다.
  - 이는 매우 중요한 의미를 담고 있는데, 내 컴퓨터의 로컬저장소의 버전은 '티셔츠, 기능 리스트 추가'인데 반해 원격저장소의 버전은 하나 이전의 버전인 '개발자 목록 추가' 상태라는 것입니다.
- 종합하자면 Git으로 관리하는 파일은 총 네 가지 상태를 가지게 됩니다.
  - untrcked 
    - 추적 안됨
  - tracked
    - 수정 없음
    - 수정함
    - 스테이지됨
- [HEAD]라는 특수한 포인터가 그 비법입니다. 브랜치 혹은 커밋을 가리키는 포인터죠. 우리는 [HEAD]를 이용해서 브랜치 사이를 마음대로 넘나들 수 있습니다.
- 브랜치의 최신 커밋이 아닌 과거 커밋으로도 [HEAD]를 이동시킬 수 있습니다. 다만, 이 경우에는 [master]브랜치의 포인터와 [HEAD]가 떨어져있기에 '분리된 HEAD(Detached HEAD)' 상태가 됩니다.
- 협업을 하기 위해선 브랜치를 어떻게 사용해야 할까요?
  - 협업자는 커밋을 올릴 브랜치를 각각 만들고
  - 자신이 만든 브랜치로 이동한 다음
  - 브랜치에 커밋을 올리고
  - 코딩이 완료되면 브랜치를 합치면 됩니다.
- 규칙
  - [master] 브랜치에는 직접 커밋을 올리지 않는다(동시에 작업하다 꼬일 수 있으니)
  - 기능 개발을 하기 전에 [master] 브랜치를 기준으로 새로운 브랜치를 만든다.
  - 이 브랜치 이름은 [feature/기능이름] 형식으로 하고 한 명만 커밋을 올린다.
  - [feature/기능이름] 브랜치에서 기능 개발이 끝나면 [master] 브랜치에 이를 합친다.
