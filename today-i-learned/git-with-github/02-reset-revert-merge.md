---
description: 'Git 소스를 되돌리는 Reset, Revert & 충돌(Conflict) 났을 때 Merge 하는 법'
---

# 02.Reset, Revert, Merge

![https://docs.google.com/presentation/d/13aWrWTDqEDjEamyhkrvo3ulrNQ9jP26DigCopPeAGJg/edit\#slide=id.g3eb7fcfc70\_1\_0](https://lh3.googleusercontent.com/nDtDqrXimM6cRtwKTbY3bNCW_Xvh6S_H_CVL5Fqq6eSLjRlleWwMYRWgIl6Um8Waw_bcUrjyc3IfMkMG5DZuyBw99Ac-tlPoK1eR8uBdzDWShkbF04xuDE03VxjJFc5SMWYIhEXqrCU)

> _※ Visual Studio Code\_GitLens 설치_

```bash
$ git log
# 그래프형태로 log 보기
$ git log --graph --oneline
$ git reset --[hard | sort | mixed]
# (주의) hard는 완전히 되돌림(commit했던 흔적까지 모두 지워짐)!!!
$ git revert # history만 변경(history가 쌓임), 소스는 그대로
```

```bash
$ git reset [revision_number]
$ git revert [revision_number]
$ git reset --hard [revision_number]
```

