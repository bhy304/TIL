---
description: Git Branch
---

# 03.Branch

## Branch

```bash
# branch 만들기
$ git branch <branch-name>
$ git branch # branch 전체 보기
# checkout(전환) 
$ git checkout <branch-name>
$ git push origin <branch-name>
$ git log
```

## Master로 Merge

```bash
$ git checkout master # master로 전환
$ git diff <branch-name> 
$ git merge <branch-name>
```

## Branch 삭제

```bash
# local branch 삭제
$ git branch -d <branch-name>
$ git branch
# remote branch 삭제
$ git push --delete origin <branch-name>
```

## Branch 보기

```bash
# 로컬(PC) 브랜치 보기
$ git branch
# 서버(GitHub) 브랜치 보기
$ git branch -r 
# 양쪽 모두 보기
$ git branch -a
# 서버의 특정 브랜치 가져오기
$ git checkout -t origin/<branch-name>
# 특정 브랜치 pull 하기
$ git pull origin <branch-name>
```

※ 브랜치 생성 및 변경 전에 commit 잊지 말것!

```bash
$ git checkout -p <branch-name><file-name> #patch
```

### GitHub Collaborator & folk

* collaborator : Repository의 공동 작업자
* folk : 다른 사람의 Repository 연결하기 
* ※ 주의 : folk된 repository의 경로는 원본과 다름!!

