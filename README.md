# サービスに関して

- 名称：China inbenory2

# 環境構築

```
docker desktopをインストールする。
$ git clone git@github.com:china-inventory2/china-inventory2.git
$ cd china-inventory2

初回時はこれ（imageがなければimageビルドから）コンテナの起動までを行う。初回は起動に失敗すると思います。
$ docker-compose up

Gemfileに変更を加えた場合はこれですが、Gemをインストールする場合は事前にご連絡ください。
$ docker-compose build

DB関連
$ docker-compose run app bundle exec rails db:reset
$ docker-compose run app bundle exec rails db:create
$ docker-compose run app bundle exec rails db:migrate

作業を終了する時はコンテナを終了させます。
$ docker-compose stop

2回目以降からは以前に作ったコンテナを起動させます。
$ docker-compose start

2回目以降start起動するとデタッチドモードになってログを確認できません。見たいときはこれ。-fを外せばtailしない。
$ docker-compose logs -f

それぞれのコンテナのターミナルに直接アクセス  ●●●はコンテナID
$ docker exec -it ●●● /bin/bash

railsコマンドを使用するときはvendor/bundle配下のrailsを使うようにします。
$ docker-compose run app bundle exec rails ●●●●●●●●● ~

モデルでのテストコードを作っていく場合は下記のようにして
$ docker-compose run app bundle exec rails g rspec:model model_name

コントローラーでのテストコードを作っていく場合は下記のようにする。コントローラー名にsをつけるのを忘れずに。
$ docker-compose run app bundle exec rails g rspec:controller controllers_name

```
# Dockerの操作マニュアルはこちら
```
https://qiita.com/okyk/items/a374ddb3f853d1688820
```
# Rspecの操作マニュアルはこちら
```
一番良かった参考書
https://leanpub.com/everydayrailsrspec-jp/read

models_spec 初めてRSpecでRailsアプリのモデルをテストする
https://qiita.com/y4u0t2a1r0/items/ae4d832fbfb697b4b253

controllers_spec
※やらなくていい    けど後学のために載せときます。
https://qiita.com/y4u0t2a1r0/items/f875bc5a07895ff1cd27

features_spec、アプリの利用者が使うものと全く同じフォームを使ってテストできます。
https://nyoken.com/rspec-feature-capybara

requests_spec リクエストに対するレスポンスが仕様に沿っているか検証します。
※コントローラースペックの代わりに現在はこちらのテストをします。
https://qiita.com/t2kojima/items/ad7a8ade9e7a99fb4384

モデルにあるファイルアップロード機能や、メール送信機 能、ジオコーディング(緯度経度)連携のテストの仕方
説明しきれず、、コレを買うといいかも
https://leanpub.com/everydayrailsrspec-jp/read
```
# etc...
```
何かあれば適宜追加します。
```
