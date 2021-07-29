## Git 내부 객체

> git은 내부적으로 commit, tree, blob, tag의 4가지 오브젝트 타입을 관리한다.

- 객체명은 SHA1로 40자리로 해쉬된다. 따라서 내용이 같으면 객체명이 같다.
  - 개체들이 담긴 파일명 = git이 개체 컨텐츠 내용을 참고해 생성하는 40자리 문자열
    - git에 "hello.txt"라는 파일을 하나 추가
      - "hello.txt" 내용 전부를 해시테이블에 넣어, 40자리의 해시값을 뽑아내 파일명으로 사용
      - **blob**에는 파일명인 "hello.txt"라는 문자열이 저장되지 않음
        - 대신 디렉토리 구조를 나타내는 **tree**에서 "hello.txt"라는 문자열을 찾을 수 있음
    - 파일명 중 앞 2글자는 디렉토리 이름으로, 나머지 38글자를 파일이름으로 사용
- 객체들은 `.git/objects`에 개별 파일들로 존재한다.
  - 하나의 commit, 하나의 tree, 하나의 blob, 하나의 tag는 각각 하나의 파일
  - 두개의 commit은 두개의 파일
- 내용은 `git cat-file –p 객체명`으로 볼 수 있다.

<img width="530" alt="스크린샷 2021-07-30 오전 12 32 17" src="https://user-images.githubusercontent.com/63178953/127521066-2d2f384b-ce81-40e6-87e5-166f1a431fa9.png">

### **1. blob**

**blob(binary large object)**

- `git add`할 때 생성
- 파일 전체 내용
  - 파일이름, 형식 등 메타정보는 저장 X
- 사이즈 : 컨텐츠의 용량을 bytes로 표시
- 컨텐츠 : 텍스트, 이미지, 음악, 단순 이진 파일...등 다양한 형식의 파일

### **2. tree**

**tree**

- `git commit`할 때 생성
- 타입, 객체명, 파일명, 객체 접근권한 등
- 사이즈 : 트리 오브젝트의 용량을 bytes로 표시
  > tree : 하위 디렉토리의 트리 객체를 재귀적으로 참조
  > blob : 한 디렉토리에 있는 모든 blob을 담음

### **3. commit**

**commit**

- `git commit`할 때 생성
- tree객체명, 부모commit 객체명, 작성자, 커밋실행자, 로그메시지, 커밋날짜
  - commit할때 git config에 있는 name과 email이 반영됨

> tree : 해당 커밋에서의 dir/file의 상태를 알 수 있다.

### **4. tag**

**tag**

- `git tag`할 때 생성
- 커밋객체명, 객체종류, 태그명, tagger, 태그메시지, PGP 서명정보

**git init**

- `init`으로 저장소를 초기화할 때, `objects` 디렉토리를 만들고 그 밑에 `pack`, `info` 디렉토리도 만든다.

```bash
$ git init test
Initialized empty Git repository in /tmp/test/.git/
$ cd test
$ find .git/objects
.git/objects
.git/objects/info
.git/objects/pack
```
