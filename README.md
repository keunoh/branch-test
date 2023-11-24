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
- 브랜치 합치기 실습 : 병합 커밋 및 충돌 해결
  - 1단계 : master 브랜치를 땡겨와서 feature/cart 브랜치에서 병합한다.
  - 2단계 : feature/cart 브랜치에서 병합한 병합 커밋을 master 브랜치에 반영한다.
  - TIP : 물론 [master] 브랜치에서 바로 병합해도 괜찮습니다. 충돌이 나더라도 [master] 브랜치에서 바로 해결하면 됩니다.
  - 다만 다른 사람이 불편해지는 상황을 방지하기 위해서 나만 스는 [feature/cart] 브랜치에서 먼저 병합하는 것입니다.
- 이렇게 남의 원본저장소를 내 계정의 원격저장소로 복사해오는 명령어는 포크(fork) 입니다.
- [upstream] 원본저장소에 있는 커밋 히스토리를 받아오는 것입니다. 이것을 패치[Fetch]라고 합니다.
- 패치는 간단히 말하자면 '새로고침' 기능인데요, 패치를 하면 원본저장소 이력을 업데이트합니다.
- 동료 개발자가 [master] 브랜치에 커밋 5개를 올렸는데, 내 소스트리에는 아직 그 이력이 안 보일 때 패치를 하면 이력이 보입니다.
- 이력만 가져오는 거니까 내 코드에는 아무 영향이 없습니다.
- [amend] : 방금 했던 커밋을 수정할 수 있음, 원격저장소까지 푸시했더라도요
- [master] 브랜치에 있는 다른 변경사항 말고 딱 그 버그를 고친 커밋만 반영하려고 합니다. 아직 다른 기능들은 출시할 시점이 아니거든요. 이럴 때 체리픽[cherry-pick] 기능을 쓰면 됩니다.
- 해당 커밋에 대하여 체리 픽하면 현재 브랜치에 해당 커밋만 가져와서 현재 브랜치에 반영할 수 있다.
- [reset] : 옛날 커밋으로 브랜치를 되돌리고 싶어요
  - [Mixed] : 이 모드는 원하는 커밋으로 이력을 되돌리긴 하지만, 이 다음에 추가했던 모든 변경사항을 작업 공간으로 뽑아줍니다.
  - [Soft] : [Mixed]와의 차이는 변경사항이 스테이지 위에 있는지 아래에 있는지의 차이입니다. [Mixed] 모드는 변경사항을 스테이지 아래로 둬서 다시 무엇을 스테이지 위로 Add 할지 고민할 수 있고, [Soft] 모드는 변경하상을 스테이지 위로 둬서 다시 당장 커밋할 수 있다는 차이점이 있답니다.
  - [Hard] : 모든 기억을 지우며 브랜치를 되돌리기. 복권 사기 전의 과거로 돌아갔는데 머릿속의 복권 번호 기억까지 다 날아간 상태입니다.
    - [feat/b] 브랜치가 깔끔하게 과거로 돌아간 것을 볼 수 있습ㄴ다. 하지만 원격 브랜치인 [origin/feat/b]에는 아직 두 번째 컴시이 남아있네요. 푸시를 하면 되겠죠. 강제 푸시는 나만 쓰는 브랜치에서만 해야 한다는 것을 잊지마세요.
- [revert] : 커밋의 변경사항을 되돌리는 새로운 커밋 만들기
- [stash] : 변경사항을 잠시 다른 곳에 저장하고 싶어요, 커밋은 안 만들래요
  - 참고로 stash에는 tracked 상태(추적중 - 한번이라도 Git에 올렸던 상태)인 파일들만 들어갑니다. 새로 만든 파일은 untracked 상태니까 들어가지 않겠죠.
- 중요한 점은 '에러가 발생했네?'하며 끝내면 안 된다는 겁니다. 대체로 입문자는 본인이 의도한 대로 실행되면 만족해하지만 반대로, 의도대로 되지 않으면 좌절하는 경우가 많습니다.
- 문제는 이 지점입니다. 잘 되든, 잘 되지 않든 반드시 꼼꼼하게 메시지를 읽어야 하는데, 이 메시지를 읽지 않고 넘어간다는 것이지요.
- CLI 명령 실행 결과 화면에 나오는 메시지는 중요합니다. 다시 한 번 당부 드립니다. 귀찮더라도 화면에 나오는 메시지를 읽어 주세요!
- 로컬저장소가 있는 현재 폴더, 다시 말해서 일반적인 작업 폴더를 Git 용어로 뭐라고 할까요? Git에서는 작업 폴더를 '워킹트리'라고 합니다.
- git log 예쁘게 (원기올때)
  - git log --oneline --graph --all --decorate
- 좋은 커밋 메시지의 7가지 규칙
  - 제목과 본문을 빈 줄로 분리한다.
  - 제목은 50자 이내로 쓴다.
  - 제목을 영어로 쓸 경우 첫 글자는 대문자로 쓴다.
  - 제목에는 마침표를 넣지 않는다.
  - 제목을 영어로 쓸 경우 동사원형(현재형)으로 시작한다.
  - 본문을 72자 단위로 줄바꿈한다.
  - 어떻게 보다 무엇과 왜를 설명한다.
- pull = fetch + merge
- 커밋하면 커밋 객체가 생깁니다. 커밋 객체에는 부모 커밋에 대한 참조와 실제 커밋을 구성하는 파일 객체가 들어 있습니다.
- 브랜치는 논리적으로는 어떤 커밋과 그 조상들을 묶어서 뜻하지만, 사실은 단순히 커밋 객체 하나를 가리킬 뿐입니다. 
- HEAD는 현재 작업 중인 브랜치를 가리킵니다.
- 브랜치는 커밋을 가리키므로 HEAD도 커밋을 가리킵니다.
- 결국 HEAD는 현재 작업 중인 브랜치의 최근 커밋을 가리킵니다.
- rebase의 원리
  - HEAD와 대상 브랜치의 공통 조상을 찾는다.
  - 공통 조상 이후에 생성한 커밋들(C4, C5 커밋)을 대상 브랜치 뒤로 재배치한다.
- git status로 clean한 상태는 '워킹트리 = 스테이지 = HEAD' 커밋이라는 점을 꼭 기억하기 바랍니다.
