## 環境構築

### とりあえず必要なもの
```
$ sudo apt-get update
$ sudo apt-get -y install build-essential libssl-dev libsqlite3-dev zsh git curl
```

### zsh
```
$ chsh
Password:
Changing the login shell for vagrant
Enter the new value, or press ENTER for the default
        Login Shell [/bin/bash]: /bin/zsh
```

### Zsh + Prezto
```
$ git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
# zshの設定ファイルがすでにある場合はどっかに退避しておく
$ setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
```

### Ruby
```
# rbenv
$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
# ruby-build
$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
```

```
~/.gemrc

gem: --no-rdoc --no-ri
```

```
.zshrc

export PATH=$HOME/.rbenv/bin:$PATH
eval "$(rbenv init -)"
```

```
$ source ~/.zshrc
$ rbenv install 2.1.2
$ rbenv rehash
$ rbenv global 2.1.2
```


※参照
http://dev.classmethod.jp/tool/zsh-prezto/



### Padrinoプロジェクト作成
```
$ cd /home/vagrant
$ gem install bundler padrino
$ padrino g project -d activerecord -e slim soccer_rss_app
$ cd soccer_rss_app
$ padrino g plugin coffee  // coffeescriptプラグイン
$ bundle install
$ rbenv rehash
```
