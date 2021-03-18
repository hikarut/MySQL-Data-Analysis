# What
* csvファイルを元にMySQLにデータ入れてSQLでデータ分析を行う環境のセットアップ
* MacのSQLクライアントは[Sequel Pro](http://sequelpro.com/)を利用
* [Docker](https://docs.docker.jp/docker-for-mac/install.html)を事前にインストールする

# How
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

### ※注意
* MySQL8系だとログイン認証がデフォルトで`caching_sha2_password`になっており、Sequel Proなどのクライアントからログインできない
* 解決策としてはMySQLの5.7系を使うか、認証を`mysql_native_password`に変える
  * [Sequel ProでMySQLにログインできない](https://qiita.com/ysk1o/items/7f0ca12ced72363f9448)
* 今回の方法ではMySQLのデフォルト認証を`mysql_native_password`にしてMySQL8.0を利用しています
  * 理由としてはwith句がMySQL8.0以上じゃないと使えないので分析のしやすさを考慮してMySQL8.0を利用します
* またSequel Proを使うとMySQL8.0の環境に接続できない様なので、以下参考にSequel Proのテストビルドバージョンを使う様にしています
  * [MySQL8.0.x に Sequel Pro で接続する](https://qiita.com/ucan-lab/items/b68db1db931c954da921)
