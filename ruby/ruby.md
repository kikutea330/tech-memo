Rubyのメモ
==

# Rubyのバージョン管理ツール（rbenv）のインストール
```
# rbenvのソースコード取得
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv

# パスを通す
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
$ source ~/.profile

# rbenvのビルド
$ ~/.rbenv/bin/rbenv init

# ruby-buildプラグイン（Ruby仮想化用コマンドラインユーティリティ）のインストール
$ mkdir -p "$(rbenv root)"/plugins
$ git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
```

# rubyのインストール
```
# インストール可能なバージョン確認
$ rbenv install --list

# 2.6.0（2019/1/7時点で最新の安定版）のインストール
$ rbenv install 2.6.0
$ rbenv rehash

# 2.6.0をデフォルトに設定
$ rbenv global 2.6.0

```
