Git関連のメモ
==

Git関連のメモです。


## Gitコマンド
### リポジトリ作成
共有用リモートリポジトリの作成
```
$ mkdir path/to/repo.git
$ cd path/to/repo.git
$ git init --bare --shared=true
```

### クローン
```
$ cd path/to/repos_dir
$ git clone リポジトリURL
```

|プロトコル|リポジトリURL|
|:--|:--|
|SSH|ssh://[ユーザ名@]ホスト名[:ポート]/path/to/repo.git/|
|Git|git://ホスト名[:ポート]/path/to/repo.git/|
|HTTP[S]|http[s]://ホスト名[:ポート]/path/to/repo.git/|
|FTP[S]|ftp[s]://ホスト名[:ポート]/path/to/repo.git/|

### インデックスに追加
ファイルを指定して追加  
```
$ git add ファイル名 [ファイル名　..]
```

``.gitignore``で指定されていないファイルを全て追加  
```
$ git add .
```

### インデックスから削除
```
$ git rm --chached ファイル名
```

### ファイルの移動・リネーム
```
$ git mv ファイル名 変更後のファイル名
```

### コミット
ファイルを指定してコミット  
```
$ git commit ファイル名
```

インデックスに登録されているファイルの変更を全てコミット
```
$ git commit -a
```

### プッシュ
```
$ git push -u リモートリポジトリ ローカルブランチ:リモートブランチ
```

### プル
```
$ git pull リモートリポジトリ ブランチ名
```

### 切り替え
ブランチの切り替え  
```
$ git checkout ブランチ名
```

ブランチを新規作成して切り替え  
```
$ git checkout -b ブランチ名 [コミット]
```

### マージ
```
$ git merge ブランチ名
```

### リセット
```
$ git reset --hard
```
|オプション|意味|
|:--|:--|
| --hard| HEADの位置・インデックス・ワーキングツリー |
| --mixed | HEADの位置・インデックス |
| --soft | HEADの位置 |

### スタッシュ
ワーキングツリーの変更を一時的に退避
```
$ git stash
```

退避した変更を元に戻す
```
$ git stash pop
```

## Git設定
### ユーザ名とメールアドレスの登録
```
$ git config --global user.name "Your Name"
$ git config --global user.email "your.email@example.com"
```

### エディタの設定
```
$ git config --global core.editor エディタ
```

### コミットメッセージのテンプレートファイル指定
```
$ git config --global commit.template path/to/template_file.txt
```

## Git hooks
### リポジトリ更新時に同サーバ内の別リポジトリを更新
Webサイト用のリモートbareリポジトリにpushした際に、公開ディレクトリのサイト資源を更新するときに使える。
1. リモートbareリポジトリのpost-update.sampleをコピーしてpost-updateを作成
  ```
  $ cd path/to/remote_repository.git/hooks
  $ cp ./post-update.sample ./post-update
  ```
2.  post-updateを編集して以下の内容を追記
  ```sh:post-update
  cd path/to/public_dir/repository
  git --git-dir=.git pull
  ```

## 既存ディレクトリをリモートリポジトリにプッシュ
GitHubにプロジェクト作って、そこに既存プロジェクトを登録したいときに使える。
1. リモートリポジトリ作成
2. 既存プロジェクトディレクトリをリポジトリ化
  ```
  $ cd path/to/project_dir
  $ git init
  ```
3. プロジェクトリポジトリのリモートリポジトリ登録
  ```
  $ git remote add origin repository_url
  ```
4. リモートリポジトリのインデックス情報取得
  ```
  $ git fetch
  ```
5. リモートリポジトリのブランチ確認
  ```
  $ git branch -a
    remotes/origin/master
  ```
6. リモートのmasterをローカルにマージ
  ```
  $ git merge origin/master
  ```
7. ローカルにmasterブランチが作成されたことを確認
  ```
  $ git branch -a
  * master
    remotes/origin/master
  ```
8. プロジェクトディレクトリ以下のファイルを追加（事前に.gitigunoreを書いておく）
  ```
  $ git add .
  ```
9. コミット
  ```
  $ git commit -a
  ```
10. リモートリポジトリにコミットを反映
  ```
  $ git push origin master
```
