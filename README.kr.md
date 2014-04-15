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
 - [이슈의 상호링크](#이슈의-상호링크)
 - [Markdown파일 구문강화](#markdown파일-구문강화)
 - [특정 유저에 의한 커밋이력](#특정-유저에-의한-커밋이력)
 - [브랜치끼리의 비교](#브랜치끼리의-비교)
 - [이모티콘](#이모티콘)
 - [이미지 또는 애니메이션GIF](#이미지-또는-애니메이션GIF)
 - [재빠른 인용](#재빠른-인용)
 - [Git 스테이터스의 스타일링](#git-스테이터스의-스타일링)
 - [Git 로그의 스타일링](#git-로그의-스타일링)
 - [커밋로그 검색](#커밋로그-검색)
 - [머지된 브랜치](#머지된-브랜치)
 - [신속한 라이센스 설정](#신속한-라이센스-설정)
 - [TODO리스트](#todo리스트)
 - [관련링크](#관련링크)
 - [추천하는 .gitconfig](#추천하는-gitconfig)
   - [Aliases](#aliases)
   - [커맨드의 자동수정](#커맨드의-자동수정)
   - [색설정](#색설정)

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

## 이슈의 상호링크

같은 리포지토리에 다른 이슈끼리 링크를 걸고 싶을 경우에는, `#`에 이슈번호를 지정하면 된다. 이렇게 하면 자동적으로 링크된다.

서로 다른 리포지토리인 경우에는 `user_name/repo_name#ISSUE_NUMBER`와 같이 지정하면 된다.(예: `tiimgreen/toc#12`)

## Markdown파일 구문강화

예를들어 Markdown파일에 Ruby코드를 구문강화를 하고싶다면 다음처럼 하면 된다:

    ```ruby
    require 'tabbit'
    table = Tabbit.new('Name', 'Email')
    table.add_row('Tim Green', 'tiimgreen@gmail.com')
    puts table.to_s
    ```

이렇게 하면 다음처럼 표시되게 된다:

```ruby
require 'tabbit'
table = Tabbit.new('Name', 'Email')
table.add_row('Tim Green', 'tiimgreen@gmail.com')
puts table.to_s
```

GitHub에서는 [Linguist](https://github.com/github/linguist)를 사용하여 언어를 판별하고 구문강화를 표시한다. 구문강화가 서포트하고 있는 언어리스트는 [언어정의YAML파일](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml)을 참고하면 된다.

## 특정 유저에 의한 커밋이력

특정 유저에 의한 특정 리포지토리에 커밋한 이력만을 참조하고싶을 경우에는, `?author=username`을 URL에 붙히면 볼 수 있다.

```
https://github.com/rails/rails/commits/master?author=dhh
```

## 빈 커밋

`--allow-empty`옵션을 붙히면, 코드에 변화가 없더라도 커밋할 수 있다. 

```bash
$ git commit -m "Big-ass commit" --allow-empty
```

![Trololol](http://img1.wikia.nocookie.net/__cb20130905205853/flylikeabird3/images/0/0c/Mexican_troll_face_by_mariodude12312-d5mtl9z.png)

## 브랜치끼리의 비교

GitHub에서 브랜치비교는 다음 URL을 사용하면 된다:

```
https://github.com/user/repo/compare/{range}
```

`{range}`를 `master...4-1-stable`와 같이 사용한다:

```
https://github.com/rails/rails/compare/master...4-1-stable
```

`{range}`는 다음처럼 날짜를 지정하여 사용할 수도 있다:

```
https://github.com/rails/rails/compare/master@{1.day.ago}...master
https://github.com/rails/rails/compare/master@{2014-10-04}...master
```
master 브랜치와 지정한 기간 혹은 일시의 비교를 할 수 있다.

## 이모티콘

이모티콘은 풀리퀘스트나 이슈, README에 `:name_of_emoji:`를 이용하여 사용할 수 있다:

```
:smile:
:poop:
:shipit:
:+1:
```

:smile:
:poop:
:shipit:
:+1:

GitHub에서 서포트하고 있는 이모티콘의 리스트는 [Emoji cheat sheet for Campfire and GitHub](http://www.emoji-cheat-sheet.com/)나 [All-Github-Emoji-Icons](https://github.com/scotch-io/All-Github-Emoji-Icons)에서 확인할 수 있다.

GitHub에서 사용되어지고 있는 이모티콘 탑5는 다음과 같다:

1. :shipit: `:shipit:`
2. :sparkles: `:sparkles:`
3. :-1: `:-1:`
4. :+1: `:+1:`
5. :clap: `:clap:`

## 이미지 또는 애니메이션GIF

이미지나 애니메이션GIF는 커밋의 커맨트나 README에서 사용된다:

```
![Alt Text](http://image_url.com/image.jpg)
```

![Chuck Norris](http://gifs.joelglovier.com/chuck-norris/chuck-norris.gif)

모든 이미지는 GitHub에 케쉬되기 때문에, 이미지의 호스트에 문제가 있어도 문제없이 표시될꺼다.

## 재빠른 인용

이슈의 쓰래드에 다른 사람의 커맨트를 인용하여 커맨트를 작성하려고 할때, 인용하려는 문장을 선택한 상태에서 `r`을 누르면, 선택한 문장이 블럭인용기법으로 텍스트박스안에 복사된다.

![Quick Quote](http://i.imgur.com/TzpMIOA.png)

## Git 스테이터스의 스타일링

```bash
$ git status
```

![git status](http://i.imgur.com/o3PEHAA.png)

이렇게 표시하는것도 가능하다:

```bash
$ git status -sb
```

![git status -sb](http://i.imgur.com/xNI1bT0.png)

## Git 로그의 스타일링

```bash
$ git log --all --graph --decorate --oneline --abbrev-commit
```

![git log --all --graph --decorate --oneline --abbrev-commit](http://i.imgur.com/RUPycwI.png)

주: 이건 [다음](#aliases) 문법을 이용하여 Alias(단축커맨드)로 추가할 수 있다.

## 커밋로그 검색

git검색은 지금까지의 커밋메시지에서서의 검색을 지원하며, 그중 가장 최신의 결과를 표시해준다.

```bash
$ git show :/query
```

`query`에는 검색하고싶은 조건을 입력하여, 최신 결과를 찾아주고 사분까지 자세하게 표시해준다.

```bash
$ git show :/typo
```

![git show :/query](http://i.imgur.com/SA0oZbE.png)

주: 종료하려면 `q`를 누른다.

## 머지된 브랜치

```bash
$ git branch --merged
```

이렇게하면 현 브랜치에 이미 머지된 브랜치의 리스트가 표시된다.

반대로 아직 머지되지 않은 브랜치를 표시하려면 다음처럼 하면 된다:

```bash
$ git branch --no-merged
```

## 신속한 라이센스 설정

GitHub상에서 리포지토리를 생성하는 경우, 이미 설정해둔 라이센스를 추가할 수 있다:

![Licese](http://i.imgur.com/Chqj4Fg.png)

이미 존재하고 있는 리포지토리의 경우, 웹 인터페이스에서 파일을 작성하는 걸로 추가할 수 있다. `LICENSE`라는 이름으로 파일명을 입력하면, 템플릿을 선택하는 옵션이 표시된다:

![License](http://i.imgur.com/fTjQict.png)

`.gitignore`도 동일하게 작성할때 추가하는것도, 나중에 추가하는것도 가능하다.

## TODO리스트

이슈나 풀리퀘스트에서 다음처럼(공백에 주의) 작성하면 체크박스를 만들 수 있다:

```
- [ ] Be awesome
- [ ] Do stuff
- [ ] Sleep
```

![TODO List](http://i.imgur.com/k2qZi56.png)

이 체크박스가 체크되는 동시에 Markdown소스도 갱신된다:

```
- [x] Be awesome
- [x] Do stuff
- [ ] Sleep
```

## 관련링크
[관련링크](https://help.github.com/articles/relative-links-in-readmes)는 Markdown문서내에서의 인터널 링크를 할경우 많이 사용된다.

```markdown
[Link to a header](#awesome-section)

[Link to a file](docs/readme)
```
절대링크는 URL이 변경(예:리포지토리 이름변경, 유저명변경, 프로젝트forked)되면 같이 변경을 시켜줘야한다. 상대링크를 사용하면 문서관리가 유용해진다.

## 추천하는 .gitconfig

`.gitconfig`는 모든 설정을 포함하고 있는 파일이다.

### Aliases

Alias는 Git을 실행하기 편이하게 스스로 설정가능한 도우미기능이다. 예를들어 `git a`로 `git add --all`를 실행할수 있도록 설정을 할 수 있다.

Alias를 추가하려면 `~/.gitconfig`을 열어서 다음과 같이 기입을 하면된다:

```
[alias]
	co = checkout
	cm = commit
	p = push
	# Show verbose output about tags, branches or remotes
	tags = tag -l
	branches = branch -a
	remotes = remote -v
```

또는 커맨드라인에서 다음처럼 설정할 수도 있다:

```bash
$ git config alias.new_alias git_function
```

예:

```bash
$ git config alias.cm commit
```

주: Alias가 다수의 커맨드를 지정하게 되는 경우라면 quote를 사용한다:

```bash
$ git config alias.ac 'add -A . && commit'
```

몇몇 추천하는 Alias:

| Alias | Command | 설정방법 |
| --- | --- | --- |
| `git cm` | `git commit` | `git config --global alias.cm commit` |
| `git co` | `git checkout` | `git config --global alias.co checkout` |
| `git ac` | `git add . -A` `git commit` | `git config --global alias.ac '!git add -A && git commit'` |
| `git st` | `git status -sb` | `git config --global alias.st 'status -sb'` |
| `git tags` | `git tag -l` | `git config --global alias.tags 'tag -l'` |
| `git branches` | `git branch -a` | `git config --global alias.branches 'branch -a'` |
| `git remotes` | `git remote -v` | `git config --global alias.remotes 'remote -v'` |

### 커맨드의 자동수정

만약 `git comit`이라고 잘못된 커맨드를 입력했을 경우, 다음과 같은 출력을 보게 될 것이다:

```bash
$ git comit -m "Message"
# git: 'comit' is not a git command. See 'git --help'.

# Did you mean this?
# 	commit
```

`comit`이라고 잘못 입력했을지라도 `commit`을 실행시키고 싶을 경우, 자동수정 설정을 유효화 해두면 된다:

```bash
$ git config --global help.autocorrect 1
```

이 설정으로 다음과 같은 출력을 볼 수 있다:

```bash
$ git comit -m "Message"
# WARNING: You called a Git command named 'comit', which does not exist.
# Continuing under the assumption that you meant 'commit'
# in 0.1 seconds automatically...
```

### 색설정

Git의 출력을 컬러풀하게 하려면 다음처럼 설정을 하면 된다:

```bash
$ git config --global color.ui 1
```

# 공유

[Twitter](https://twitter.com/intent/tweet?source=webclient&text=http%3A%2F%2Fgithub.com%2Ftiimgreen%2Fgithub-cheat-sheet%20-%20GitHub%20Cheat%20Sheet)로 트윗해주세요. [한국어번역](https://twitter.com/intent/tweet?source=webclient&text=http%3A%2F%2Fgithub.com%2Fwanybae%2Fgithub-cheat-sheet%20-%20GitHub%20Cheat%20Sheet)도 잘 부탁드립니다.

# 역주

이 글은 [GitHub Cheat Sheet](https://github.com/tiimgreen/github-cheat-sheet)의 한국어 번역본입니다.
