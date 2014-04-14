# GitHub Cheat Sheet

이건 Git이나 GitHub의 숨겨져있는 기능이나 잘 알려지지 않은 기능들에 대한 내용이다. [Zach Holman](https://github.com/holman)씨가 Aloha Ruby Conference 2012에서 이야기한 [Git and GitHub Secrets](https://github.com/tiimgreen/github-cheat-sheet)([슬라이드](https://github.com/tiimgreen/github-cheat-sheet))와 WDCNZ 2013에서 이야기한 [More Git and GitHub Secrets](https://vimeo.com/72955426)([スライド](https://speakerdeck.com/holman/more-git-and-github-secrets))를 바탕으로 만들었다.

# 목차

 - [공백을 무시](#공백을-무시)
 - [리포지토리 클론](#리포지토리-클론)
 - [Hub - Git래퍼](#hub---git래퍼)
 - [이전 브랜치](#이전-브랜치)
 - [git.io](#git.io)
 - [Gists](#Gists)
 - [키보드 단축키](#키보드-단축키)
 - [커밋으로 이슈닫기](#커밋으로-이슈닫기)
 - [풀리퀘스트 체크아웃](#풀리퀘스트-체크아웃)

## 공백을 무시

사분을 표시하는 화면의 URL에 `?w=1`를 추가하면, 공백으로 인한 사분은 표시되지 않게되어, 코드에 의한 변경점만 확인하기 쉬워진다.

## 리포지토리 클론

리포지토리를 클론할때, URL에 `.git`는 없어도 된다.

```bash
$ git clone https://github.com/tiimgreen/github-cheat-sheet
```

## Hub - Git래퍼

[Hub](https://github.com/github/hub)는 Git의 래퍼인 커맨드 라인 툴로, 이걸 이용하면 GitHub를 커맨드라인에서 꽤 쉽게 다룰수 있게 된다.

예를들어서 다음과 같이 리포지토리 클론을 실행할 수 있다:

```bash
$ hub clone tiimgreen/toc
```

이렇게 사용하는 대신에:

```bash
$ git clone https://github.com/tiimgreen/toc.git
```

## 이전 브랜치

커맨드라인에서 바로 전에 있었던 디렉토리로 이동하려할때, 다음과 같이 하면 편하다:

```bash
$ cd -
```

비슷하게 Git에서 바로 전의 브랜치를 체크아웃하는 것도 가능하다:

```bash
$ git checkout -
# Switched to branch 'master'

$ git checkout -
# Switched to branch 'next'

$ git checkout -
# Switched to branch 'master'
```

## git.io

[git.io](http://git.io)는 GitHub가 제공하는 GitHub전용의 단축 URL서비스다.

[http://git.io/wO0xUg](http://git.io/wO0xUg)

## Gists

[Gists](https://gist.github.com/)는 적은 양의 코드를 관리하는 최적의 수단이다. 적은 코드를 위해서 리포지토리를 매번 작성할 필요가 없다. 

간단하다해도, Git리포지토리와 동일하게 움직이기 때문에 다음처럼 사용하면 보통의 리포지토리처럼 클론도 가능하다. 

```bash
$ git clone https://gist.github.com/tiimgreen/10545817
```

![Gists](http://i.imgur.com/dULZXXo.png)

## 키보드 단축키

브라우저에서 리포지토리를 볼 경우에, 단축키를 이용하면 여러가지 기능을 간단하게 사용할 수 있다.

`t`는 file explorer를 표시한다.

`w`는 branch selector를 표시한다.

`s`는 파일검색란으로 커서를 이동시킨다.

__파일검색중__(예: `https://github.com/tiimgreen/github-cheat-sheet/blob/master/README.md`)에 `y`를 누르면, 지금 참조하고 있는 URL을 고정URL로 변경한다. 만약 코드를 변경했다고 해도, 고정URL을 사용하여 변경전의 코드를 참조할 수 있게된다. 

`?`는 현재 페이지에서 사용할 수 있는 모든 단축키를 표시한다.

## 커밋으로 이슈닫기

커밋으로 이슈를 해결한 경우, 커밋메시지로 `fix/fixes/fixed` 혹은 `close/closes/closed`의 뒤에 이슈번호를 지정하면 지정한 이슈가 닫히게 된다.

```bash
$ git commit -m "Fix cock up, fixes #12"
```

이렇게 하면 #12번 이슈가 닫히고, 닫힌 이슈에는 해당 커밋의 참조가 자동으로 추가된다. 

![Closing Repo](http://i.imgur.com/URXFprQ.png)

## 풀리퀘스트 체크아웃

풀리퀘스트를 로컬리포지토리에 체크아웃하려면 우선은 다음처럼 커맨드를 실행하고 변경점을 가져온다:

```bash
$ git fetch origin '+refs/pull/*/head:refs/pull/*'
```

그리고, 풀리퀘스트를 번호(예:42)를 지정하여 체크아웃한다:

```bash
$ git checkout refs/pull/42
```

다른 방법으로는, 우선 풀리퀘스트를 remote branch로 가져올수 있다:

```bash
$ git fetch origin '+refs/pull/*/head:refs/remotes/origin/pr/*'
```

거기서 번호를 지정하여 체크아웃할 수 있다:

```bash
$ git checkout origin/pr/42
```

또한 풀리퀘스트를 가져올때, .git/config에 다음과 같은 설정을 추가하면 자동화하는 것도 가능하다:

```
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@github.com:tiimgreen/github-cheat-sheet.git
```

```
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@github.com:tiimgreen/github-cheat-sheet.git
    fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
```
