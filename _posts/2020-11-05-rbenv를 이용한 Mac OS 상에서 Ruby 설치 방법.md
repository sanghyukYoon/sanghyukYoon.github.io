---
layout: post
title: rbenv를 이용한 Mac OS 상에서 Ruby 설치 방법
tags: [ruby, rbenv, MacOS]
---
   기본적으로 MacOS에는 Ruby가 설치되어 있지만 상대적으로 낮은 버전으로 설치 되어 있는 경우가 대부분이다. 또, 설치되어 있는 Ruby의 버전이 원하는 버전이 아닐 수 도 있다. 이를 해결하기 위해 rbenv를 설치 하고 Ruby의 버전 관리를 하는 방법을 알아보자.

### Homebrew를 이용한 rbenv 설치

1. 아래의 명령어를 이용하여  rbenv를 설치해 준다. 
```sh
$ brew install rbenv ruby-build
```
> ruby-build도 같이 설치되기 때문에 다른 버전의 루비도 설치 할 수 있게 된다.  

2. 아래의 명령어를 이용하여 rvenv를 초기화 하고 세팅한다.
```sh
$ rbenv init
```
 
3. ~/.zshrc에 `eval "$(rbenv init -)”` 를 추가한다.

4. 아래의 명령어를 사용하여 rbenv가 정상적으로 설치 되었는지 확인한다.
```sh
$ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
```

5. 이제 모든 세팅은 끝났다.  `rbenv install` 명령어를 사용하여 다른 버전의 Ruby를 설치 할 수 있다. 

### rbenv를 이용한 ruby 설치

1. 아래의 명령어를 사용하면 rbenv를 이용하여 설치 할 수 있는 Ruby의 버전 리스트를 볼 수 있다.
```sh
#마지막 안정화 버전 리스트 보기:
$ rbenv install -l

#모든 로컬 버전 리스트 보기:
$ rbenv install -L
```

2. 아래의 명령어를 이용해 원하는 버전의 Ruby를 설치한다.
```sh
$ rbenv install [설치하려는 Ruby의 버전]
```

3. 아래의 명령어를 이용하여 해당 버전이 잘 설치 되었는지 확인한다.
```sh
$ rbenv versions
```

4. 아래의 명령어를 이용하여 Ruby버전을 세팅 해 준다.
```sh
모든 계정의 루비 버전 변경:
$ rbenv global [변경하려는 Ruby의 버전]
해당 계정의 루비 버전만 변경:
$ rbenv local [변경하려는 Ruby의 버전]
```

6. 아래의 명령어를 이용하여 각 버전의 실행파일들을  `~/.rbenv/shims`에  배치한다.
```sh
rbenv rehash
```
> 해당 명령어에 대한 자세한 내용은[링크](http://dqn.sakusakutto.jp/2014/02/rbenv_rehash_what_it_does.html) 참조  

### rbenv를 이용한 Ruby 제거

1. 아래의 명령어를 이용하여 삭제하고자 하는 Ruby의 절대경로를 확인한다.
```sh
$ rbenv prefix [삭제하려는 Ruby 버전]
```

2. 위 명령어에서 얻은 절대경로에 위치한 디렉토리를 아래의 명령어를 이용하여 제거한다.
```sh
$ rm -rf [삭제하려는 Ruby의 절대경로]
```

### 레퍼런스
* [GitHub - rbenv/rbenv: Groom your app’s Ruby environment](https://github.com/rbenv/rbenv#uninstalling-ruby-versions)
* [rbenv rehashは何をやっているのか？ ·  DQNEO日記](http://dqn.sakusakutto.jp/2014/02/rbenv_rehash_what_it_does.html)
