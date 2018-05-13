MySQL関連のメモ
==

## MySQL 5.6のインストール

## MySQL関連のshコマンド
### 接続
```
$ mysql -u ユーザ -p (-P ポート) データベース名
```

### ダンプ取得
```
$ mysqldump -u ユーザ名 -p --opt --hex-blob --default-character-set=文字セット データベース名 > ダンプファイル名
```

|オプション|意味|
|:--|:--|
| --opt | --add-drop-table --add-locks --create-options --disable-keys --extended-insert --lock-tables --quick --set-charset の短縮形。 |
| --hex-blob | バイナリカラムを 16 進変換 |
| --default-character-set | デフォルト文字セットを指定 |
| --add-drop-table | DROP TABLE ステートメントを CREATE TABLE ステートメントの前に追加 |
| --add-locks | LOCK TABLES と UNLOCK TABLES ステートメントで各テーブルダンプを囲む |
| --create-options | すべての MySQL に固有なテーブルオプションを CREATE TABLE ステートメントに含める |
| --disable-keys | 各テーブルについて、キーを無効にするステートメントおよび有効にするステートメントで INSERT ステートメントを囲む |
| --extended-insert | 複数の VALUES リストを含む、複数行 INSERT 構文を使用 |
| --lock-tables | テーブルをダンプする前にすべてロック |
| --quick | サーバーからのテーブルについて、一度に 1 行ずつ取得 |
| --set-charset | SET NAMES default_character_set を出力に追加 |

※``https://dev.mysql.com/doc/refman/5.6/ja/mysqldump.html``から引用

### ダンプ適用
```
$ mysql -u ユーザ名 -p データベース名 < ダンプファイル名
```

### バージョン確認
```
$ mysql --version
```

### サービス起動・停止・状態確認
```
$ service mysqld [start|stop|status]
```


## MySQLコマンド
### データベース関連
データベース作成
```
mysql> CREATE DATABASE データベース名 DEFAULT CHARACTER SET 文字セット;
```

データベース一覧表示
```
mysql> SHOW DATABASES;
```

データベースへ接続
```
mysql> USE データベース名;
```

### ユーザ関連
ユーザ作成
```
mysql> CREATE USER ユーザ名@ホスト名 IDENTIFIED BY 'パスワード';
```

ユーザ確認
```
mysql> SELECT host, user FROM mysql.user;
```

ユーザに特定DBへの全アクセス権限付与
```
mysql> GRANT ALL PRIVILEGES ON データベース名.* TO ユーザ名@ホスト名 IDENTIFIED BY 'パスワード';
```

パスワード変更
```
mysql> SET PASSWORD FOR ユーザ名@"ホスト名"=password('パスワード');
```

ユーザ削除
```
mysql> DROP USER ユーザ名@ホスト名
```

### プロセス管理
実行中プロセス表示（FULLをつけると実行中のクエリも全表示）
```
mysql> SHOW (FULL) PROCESSLIST;
```

プロセス停止
```
mysql> KILL プロセスID
```

### テーブル情報
カラム一覧表示
```
mysql> SELECT COLUMN_NAME, DATA_TYPE, IS_NULLABLE
    ->   FROM INFORMATION_SCHEMA.COLUMNS
    ->  WHERE table_schema = 'データベース名'
    ->    AND table_name = 'テーブル名';
```
