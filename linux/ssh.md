SSH関連のメモ
==

SSHに関連する技術のメモ

## RSAキーペアの生成
SSHクライアントとなる端末でSSH2用のキーペアを生成します。
```
$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (ユーザホーム/.ssh/id_rsa): 出力先のファイルパスを入力
Enter passphrase (empty for no passphrase): パスフレーズを入力（空でパスフレーズなし）
Enter same passphrase again: 確認用にパスフレーズを再入力
```


## 公開鍵の登録
SSHアクセス先となるリモートホストに公開鍵を登録します。
登録する公開鍵ファイルを予めリモートホストのユーザホームディレクトリに置いておく必要があります。
```
$ mkdir ~/.ssh
$ chmod 700 ~/.ssh
$ cat ~/公開鍵ファイル >> authorized_keys
$ chmod 600 ~/.ssh/authorized_keys
```


## パスフレーズの変更
秘密鍵のパスフレーズを変更します。
```
$ ssh-keygen -p
Enter file in which the key is (ユーザホーム/.ssh/id_rsa): パスフレーズを変更する秘密鍵のファイルパスを入力
Enter old passphrase: 古いパスフレーズを入力
Enter new passphrase (empty for no passphrase): 新しいパスフレーズを入力
Enter same passphrase again: 確認用にパスフレーズを再入力
Your identification has been saved with the new passphrase.
```


## リモートホストへのログイン
SSHクライアントからリモートホストへログインします。
```
ssh -p ポート番号 ユーザ名@ホスト名
```


## SSHの設定
SSHクライアント側でリモートホストに対して接続方法を設定する場合、`` ~/.ssh/config ``ファイルに書きます。
```
Host リモートホスト
    HostName      リモートホスト
    IdentityFile  リモートホストにアクセスするための秘密鍵ファイルパス
    User          リモートホストにアクセスするときのユーザ
    Port          リモートホストにアクセスする際のポート
  :
```
