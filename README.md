# README

* 説明
  * Dockerで動くRails
  * [commitの差分](https://github.com/junara/railsapp/commit/8fb3d86dc9c8e7adea2a8f4fe4be3d284f742506)を追うとDocker使うための準備がわかります。
  * webpackerの導入はしていません。

* 事前準備
  * Dockerがインストールされている
  * 以下のサイトからインストールできます。
    * [Docker Desktop (Mac)](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

# 手順

railsを起動するまでの手順

* Dockerをbuildする。（railsが入ったimageが作成されます）
```console
> docker-compose build
```

* Dockerとtdb （postgresql）を起動する。（上記で作ったimageからrailsを起動するとともに、データベースサーバーも起動します）

```console
> docker-compose up -d
```

* （Dockerとは関係無いけど）DBを初期化する

```aidl
> docker-compose exec web rails db:migrate:reset
```

# 検証

[localhost:3000](http://localhost:3000)にアクセスして接続されれば成功です。

# 終了方法

```aidl
> docker-compose exec web down
```
# EXTRA heroku への deploy
## 事前準備
heroku CLIがインストールされていて、herokuにログインできている。
## 手順
* heroku アプリを作る。アプリ名　__railsappdocker__ は、固有の名前に変更して下さい

```
heroku create railsappdocker
```

* herokuにpushする

```
git push heroku master
```

* 確認する 

```
heroku open
```

