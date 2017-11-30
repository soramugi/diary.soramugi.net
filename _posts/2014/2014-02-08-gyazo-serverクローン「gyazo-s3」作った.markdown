---
layout: post
title: "gyazo-serverクローン「gyazo-s3」作った"
published: true
date: 2014-02-08 01:26
comments: true
tags: 
categories: 
---

みんな大好き車輪の再発明

[@mitukiii](http://twitter.com/mitukiii)さんが作成したRailsのGyazoサーバー

<https://github.com/mitukiii/gyazo-server>

が「何これ最高じゃん」と使っていたんだけど、仕様上サーバーのファイルシステムそのままを使うので
heroku使えないなーって思い新しく作ってみました。

リポジトリ

<https://github.com/soramugi/gyazo-s3>

サンプル

<http://pic.soramugi.net>

herokuで使う目的なのでS3で画像のホスト、設定ファイルはENV指定でオッケーです。
以下の手順で環境の構築が出来ます。

    git clone git@github.com:soramugi/gyazo-s3.git
    cd gyazo-s3
    heroku create
    heroku config:set SECRET_KEY_BASE=$(rake secret)
    heroku config:set S3_BUCKET=S3_BUCKET
    heroku config:set AWS_ACCESS_KEY_ID=AWS_ACCESS_KEY_ID
    heroku config:set AWS_SECRET_ACCESS_KEY=AWS_SECRET_ACCESS_KEY
    heroku config:set GYAZO_ID=$(cat ~/Library/Gyazo/id)
    heroku config:set TITLE=GyazoS3
    git push heroku master
    heroku run rake db:migrate
    heroku open

アップロードしたファイルの削除はcurlで

    curl -X DELETE -d "id=$(cat ~/Library/Gyazo/id)" http://localhost:3000/20131020031935f52.jpg

既存のgyazoクライアントの設定ファイル、定数値を変更するだけでそのまま画像のキャプチャーが出来ます。

    vi /Applications/Gyazo.app/Contents/Resources/script

```
HOST = 'hugehgue.herokuapp.com'
CGI = '/items'
```

ローカルに存在するファイルをアップロードする時はgistにあげてあるスクリプトを使います。

    git clone https://gist.github.com/7821435.git
    cd 7821435
    vi gistfile1.rb

以下の値を設定
```
ID   = 'YOUR GYAZO ID'
HOST = 'YOUR HOST'
CGI  = '/items'
```
    ruby gistfile1.rb ~/Downloads/hugehuge.png


ほとんど[@mitukiii](http://twitter.com/mitukiii)のコードを応用しているので足を向けて寝られません。
