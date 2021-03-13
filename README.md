# WHAT
* csvファイルを元にMySQLにデータ入れてSQLでデータ分析を行う環境のセットアップ
* MacのSQLクライアントは[Sequel Pro](http://sequelpro.com/)を利用

# HOW
※`dc` = `docker-compose`

* DockerでMySQL環境をビルド&起動
```
$ dc up -d --build
```

* Sequel ProからMySQLに接続
```
名前：MySQL-Data-Analysis
ホスト：127.0.0.1
ユーザー名：root
パスワード:root
データベース:mysql
ポート:4306
```

