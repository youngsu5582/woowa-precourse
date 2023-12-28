1. Fork 후에 `youngsu5582/프로젝트이름`을 local로 `clone`하기

```
cd {저장할 경로 입력}
git clone https://github.com/youngsu5582/java-baseball.git
```

2. 브랜치 생성 및 전환

```
git branch {생성할 브랜치 이름}
git checkout {전환할 브랜치 이름}
git checkout -b {생성 후 전환할 브랜치 이름}
```

3. 정상적 commit & push

```
// 모든 파일 스테이징
git add . 

// 스테이징된 파일 전부 커밋하기
git commit -m "feat(GameController): 기능 잘 구현

git push origin youngsu5582
```

4. add 취소

```
git reset HEAD README.md  // README 파일을 Unstaged 상태로 변경
git reset // 모든 파일을 스테이징 취소
git checkout . // 커밋되지 않은 모든 로컬 변경 사항을 되돌림
git checkout [some_dir|file.txt] // 커밋되지 않은 변경 사항을 특정 파일이나 디렉터리로만 되돌림
```

5. commit 취소

```
// [방법 1] commit을 취소하고 해당 파일들은 staged 상태로 워킹 디렉터리에 보존
$ git reset --soft HEAD^

// [방법 2] commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에 보존
$ git reset --mixed HEAD^ // 기본 옵션
$ git reset HEAD^ // 위와 동일
$ git reset HEAD~2 // 마지막 2개의 commit을 취소

// [방법 3] commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에서 삭제
$ git reset --hard HEAD^
```

- reset 옵션
  – soft : index 보존(add한 상태, staged 상태), 워킹 디렉터리의 파일 보존. 즉 모두 보존.
  – mixed : index 취소(add하기 전 상태, unstaged 상태), 워킹 디렉터리의 파일 보존 (기본 옵션)
  – hard : index 취소(add하기 전 상태, unstaged 상태), 워킹 디렉터리의 파일 삭제. 즉 모두 취소.

6. commit 메세지 변경

```
git commit --amend
```

7. commit 로그와 수정된 파일 함께 보기

```
git log 
// q를 눌러 나가기
```

8. 특정 파일만 commit & push

```
// 작업한 파일 목록 확인하기
git status

// 기존파일의 변경내역 확인하기
git diff

// 특정 파일 Staging하기
git add <경로 및 file명> <경로 및 file명> <경로 및 file명> ...

// 특정 파일 Commit하기
git commit -m "커밋 메세지" {파일이름}

// 위의 두 개 한꺼번에 하기
git commit -am "커밋 메세지" {파일이름}

// 특정 파일 unstaged 상태 만들기
git restore --staged {파일이름}
```