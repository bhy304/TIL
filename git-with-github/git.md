---
description: 'Git 설치 및 설정, add, commit, push, pull, clone'
---

# 01.Commit, Push, Pull

> 버전관리시스템\(Version Control System\), 소스 형상 관리\(SCM\)

## Git 시작하기

#### Download git client

{% embed url="https://git-scm.com/downloads" %}

#### Git client 설치시 

1. **Choosing the default editor used by Git - Use Vim 선택**

![](../.gitbook/assets/image%20%281%29.png)

**2. Adjusting your PATH environment - Use Git from the Windows Command Prompt 선택**

![](../.gitbook/assets/image%20%282%29.png)

## Git Structure

![](../.gitbook/assets/git_structure.jpg)

> **git remote** : 현재 프로젝트에 등록된 리모트 저장소를 확인할 수 있음. 이 명령은 리모트 저장소의 단축 이름을 보여준다. 저장소를 Clone하면 origin이라는 리모트 저장소가 자동으로 등록되기 때문에 origin이라는 이름을 볼 수 있다.

> **git remote -v** : 단축이름과 URL 확인

> **git remote add origin** : 리모트 저장소 추가

## GitHub New Repository

{% hint style="info" %}
GitHub 가입 및 로그인하기!
{% endhint %}

New repository

![](../.gitbook/assets/image%20%283%29.png)

![](../.gitbook/assets/image%20%284%29.png)

![](../.gitbook/assets/image%20%285%29.png)

{% hint style="info" %}
마크다운 사용법 익히기 [https://gist.github.com/ihoneymon/652be052a0727ad59601](https://gist.github.com/ihoneymon/652be052a0727ad59601)
{% endhint %}

## Git Config\(환경 설정\)

{% hint style="info" %}
git bash 실행
{% endhint %}

```bash
$ git config --list
$ git config user.name
# 모든 디렉터리에 git config 설정해주기
$ git config --global user.name <github-name>
$ git config --global user.email <email>
$ git config --list # 설정이 잘 됐는지 확인, user.name과 user.email이 list에 있으면 됨.
$ git config --list | grep "user.name"
$ cat ~/.gitconfig
```

## 로컬 저장소 만들기\(initialize local repository\)

```bash
$ cd <work-dir>
$ git init
Initialized empty Git repository in C:/workspace/python/hello/.git/
$ ls -al
# .gitignore 파일 작성
$ vi .gitignore
$ cat .gitignore
.vscode
.txt
# repository에 파일 add(commit이 아니다)
$ git add --all 
# 파일 한 개만 올리기
$ git add hello.py #git add <파일명> 또는 git add .
$ git commit -am "first commit python"
$ git branch # branch 확인
$ git remote add origin https://github.com/bhy304/hellopython.git
```

```bash
$ git push -u origin master
To https://github.com/bhy304/hellopython.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/bhy304/hellopython.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

```bash
$ git pull
warning: no common commits
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/bhy304/hellopython
 * [new branch]      master     -> origin/master
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> master
```

```bash
# -f 옵션 : reject 무시하고 push 
$ git push -fu origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 288 bytes | 28.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0)
To https://github.com/bhy304/hellopython.git
 + 8004fca...55cd045 master -> master (forced update)
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

