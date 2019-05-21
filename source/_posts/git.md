---
title: Git 명령어
categories: Git
tags:
  - Git
  - 협업
  - 버전관리
  - 형상관리
date: 2019-05-21 16:37:02
---

`Git` 명령어들을 다뤄본다.

## init
새로운 저장소를 만든다(대상 폴더 내에 `.git` 저장소 생성)
``` bash
$ git init
> Initialized empty Git repository in D:/seop/test-ss/.git/
```

## clone
저장소를 복제한다.
``` bash
# 로컬 저장소 복제
$ git clone /로컬/저장소/경로
# 외부 저장소 복제
$ git clone 사용자명@호스트:/원격/저장소/경로
```

## remote
현재 저장소를 원격 저장소(서버, 예: Github)에 연결한다.
``` bash
# github 저장소에 연결하기
$ git remote add origin <원격 서버 주소>

# 현재 remote 주소 보기
$ git remote -v
> origin  <현재 연결된 원격 서버 주소> (fetch)
> origin  <현재 연결된 원격 서버 주소> (push)

# remote URL 변경하기
$ git remote set-url origin <변경할 원격 서버 주소>
$ git remote -v
> origin  <변경된 원격 서버 주소> (fetch)
> origin  <변경된 원격 서버 주소> (push)
```

## status
현재 저장소의 변경 사항(상태)을 확인한다.
``` bash
$ git status
> On branch master
> Your branch is up to date with 'origin/master'.

> Changes not staged for commit:
>   (use "git add <file>..." to update what will be committed)
>   (use "git checkout -- <file>..." to discard changes in working directory)

>        modified:   scaffolds/draft.md
>        modified:   scaffolds/post.md
>        modified:   source/_drafts/hexo-theme-next.md
>        modified:   source/categories/index.md

> Untracked files:
>  (use "git add <file>..." to include in what will be committed)

>        source/_drafts/git.md

> no changes added to commit (use "git add" and/or "git commit -a")
```
(친절하게도 각각 파일들에 대해 어떻게 처리하면 좋은지 다음 명령어 들을 설명해준다.)

## add
변경된(추가/수정/삭제) 내용들을 인덱스(`Stage`)로 올린다.
``` bash
# 특정 파일
$ git add <파일 이름>

# 폴더 전체
$ git add *
# 또는 "git add ."
```

## commit
변경된 내용들을 확정(commit)한다.
``` bash
# -m, --message / <msg> 즉 "커밋 메세지" 옵션
$ git commit -m "커밋 메세지"
``` 

## push
로컬 저장소에 있는 변경 내용들을 원격 저장소에 발행(push)한다.
``` bash
$ git push origin <가지(branch) 명>
```

### TIP : 각 명령어들은 `--help` 옵션을 통해 메뉴얼 페이지로 연결이 가능하다.
예) `$ git commit --help`를 하면 `commit` 명령어에 대한 메뉴얼 페이지가 열린다.

### 참고 링크
- [git - 간편 안내서](https://rogerdudler.github.io/git-guide/index.ko.html)