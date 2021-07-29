### **git**

> git 용어들
> <img width="419" alt="스크린샷 2021-07-29 오후 1 54 48" src="https://user-images.githubusercontent.com/63178953/127433917-50acb4b4-f9fa-42b0-ab4a-1cee72455520.png">

- `작업 디렉토리` : 실제 파일로 이루어짐
- `인덱스` : staging area 역할
- `HEAD` : 최종 확정본 (commit)
- `branch` : 격리된 상태로 코드 작성할 때 사용
- `fetch` : 원격저장소 내용을 로컬로 받아옴
- `merge` : 원격저장소 내용을 로컬에 반영

> git 명령어 : 저장소 관리, 변경 사항 추가/수정/삭제
> ⇒ 참고자료 [http://rogerdudler.github.io/git-guide/index.ko.html](http://rogerdudler.github.io/git-guide/index.ko.html)

- `git init` : 새로운 git 저장소 생성
- `git clone 경로` : 저장소 복제
- `git add 파일명` : 파일을 인덱스에 추가 (staging area)
- `git commit -m '설명'` : 변경내용 확정 (= HEAD에 반영, 원격엔 아직 반영X)
- `git push` : 변경 내용을 원격서버로 올림 (발행)
- `git remote add` : 원격 서버 주소 git에게 알려줌
- `git checkout -b` : 브랜치 생성 후 갈아타기
- `git branch -d` : 브랜치 삭제
- `git pull` : 원격저장소 변경사항을 로컬에 반영
- `git merge` : 다른 브랜치 내용을 현재 브랜치에 병합
  - 충돌 발생시 해결부터!
- `git diff 기존브랜치 비교브랜치` : 병합전, 변경내용 비교
- `git tag 꼬리표 확정본식별자` : 꼬리표 달기
- `git log` : 확정본 식별자 확인
- `git checkout — 파일명` : 로컬 변경사항 되돌리기
  - 이미 인덱스(staging area)에 추가된 변경사항, 새로 생성한 파일은 그대로 남음
- `git fetch origin` → `git reset —hard origin/master` : 로컬 모든 변경사항 포기하고 원격저장소 최신이력 가져오기

### **용어**

**저장소 관련**

> remote, local, init, clone
> <img width="494" alt="스크린샷 2021-07-29 오후 1 55 15" src="https://user-images.githubusercontent.com/63178953/127433961-3dfcd8d0-94f2-4ecd-bbfb-2fae181ea44d.png">

**상태 관리**

> git repository, staging area, working directory
> <img width="501" alt="스크린샷 2021-07-29 오후 1 56 26" src="https://user-images.githubusercontent.com/63178953/127434050-2a264e8b-e4d9-4bf4-964e-b9359c9c3c94.png">

**파일 관련**

> Untracked, Unmodified, Modified, Staged
> <img width="641" alt="스크린샷 2021-07-29 오후 1 56 43" src="https://user-images.githubusercontent.com/63178953/127434071-1ef29f87-28ea-4717-a134-4da39dc26d09.png">

- Git은 파일을 크게 **Tracked, Untracked** 두 상태로 분류
  1. Tracked: Git이 관리해주는 상태
  2. Untracked: Git이 관리하지 않는 상태

**Untracked File**

- Git저장소엔 있지만, Git으로 관리되지 않음
  - 방금 추가하거나, 쓸모없는 파일
  - 손상되어도 Git으로 복구 불가

**Tracked File**

- Git이 관리해주는 파일(Tracked File)
- Tracked File의 세가지 상태
  1. **Unmodified** : 파일이 수정되지 않음 (= 최근 저장 상태 그대로)
  2. **Modified** : 파일이 수정됨 (= 최근 저장한 파일과 달라짐)
  3. **Staged** : 파일을 저장할 예정 (= 이 파일을 저장할 것)

**상태변화 예시**
<img width="669" alt="스크린샷 2021-07-29 오후 1 57 11" src="https://user-images.githubusercontent.com/63178953/127434109-4410c6e9-c5c9-4ded-a613-bc6cc1849af6.png">

- `git status` : 파일들의 상태 확인
  - 생성만하고 add하지 않은 new.js ⇒ `untracked file`
  - add한 ref.js ⇒ `staged file`
  - 이미 커밋하고 수정한 test.js ⇒ `modified file`
