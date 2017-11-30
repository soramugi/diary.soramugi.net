---
layout: post
title: "Twitterの1日をまとめてタグに変換する「TWordTag」作った"
published: true
date: 2014-02-02 12:20
comments: true
tags: 
categories: 
---

TWordTag
<http://www.twordtag.com>

GitHub
<https://github.com/soramugi/twordtag>

Travis CI
<https://travis-ci.org/soramugi/twordtag>

Coveralls
<https://coveralls.io/r/soramugi/twordtag?branch=master>

Source Documentation
<http://soramugi.github.io/twordtag/>

## 概要

Twitterの1日分のツイートを取得、ツイートから名詞を抜き出してtagとして保存。1日を単語で振り返る事が出来るサービスです。

heroku上で稼働しています。ソースコードはGitHubのパブリックリポジトリ。セキュリティとかまずいコードがある時はプルリクとか送って欲しいな(願望)

## なんで作ったか

1日のまとめを作りたかった。
圧縮新聞的な。

その日一日の単語を抜き出して並べたり出現回数を表示してみれば、その日一日の興味を見返せると思って作ってみたけど、まだまだ精度が高くないかな。

抜き出した単語(tag)を検索して、他の人との繋がりや共通点が解れば良いなとtag形式にしてみた。

## 今後

定期的にtagの作成タスクをjenkinsで仕込んだので
<http://qiita.com/soramugi/items/1873eda8bd3aa0e0e6ef>

基本放置運用。

tagが作成されたらTwitterで通知されるのでじんわりと何となく広まって行けば良いと思ってる。

見向きもされなかったらそれまでだったということでこれまた放置。

herokuの無料プランで動かしているのでDBの行数制限あるので、人気でたらherokuに課金してDBの行数増やしたりとかかな。やる価値あると思えればやろう。

タグ表示のUIがもうちょっと良い表示方法あるかなと思ったのだけれど、あんまり良いアイデアないし、適材適所として「いい方法がある人、やりたいと思っている人」が改修できるようにオープンソースとして公開している

<https://github.com/soramugi/twordtag>

「このアプリ凄い楽しい！」って思っている人がコード書いた方がパフォーマンス上がるし、楽しいと思う。
それに、そういう人が居ると解ると自分自身も楽しい。

ソースコードがオープンになっているのでセキュリティ的にデメリットかもしれないけど、メリットの方が大きいと感じたのでやってみる事にした。(そもそもプライベートリポジトリで作るとTravisCIが無料で使えないってのがデカい)

知り合いにセキュリティ面での指摘をしてもらったりとかもしておこう。
