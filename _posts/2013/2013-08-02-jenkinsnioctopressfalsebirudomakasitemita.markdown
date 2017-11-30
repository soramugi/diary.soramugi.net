---
layout: post
title: "jenkinsにoctopressのビルドまかしてみた"
date: 2013-08-02 10:26
comments: true
categories: 
---

快適

このブログはoctopressでやってるんだけども、毎回

    rake gen_deploy

なんて面倒臭かったので、記事書いてコミットすれば勝手にデプロイできるようにした。

githubにmasterとsourceブランチ作って設置。
masterが実際にGitHubPagesで表示するファイルを置いて、sourceで記事をビルドしたりビルドする前の記事内容を保持。

jenkinsでsourceのブランチチェックアウトしてrbenvプラグインを使用してビルドすれば良いので簡単。

ビルド時のスクリプトはこんな感じ

    bundle install --path vendor/bundle
    #git clone git@github.com:soramugi/soramugi.github.io.git _deploy
    bundle exec rake gen_deploy

初回だけcloneのコメントアウト外して実行する必要ある。

後はgithubでsourceのブランチがpushされたら実行するようにすれば良いですね。
git単体だとhook使えば出来そうだけどもGitHubのServiceHook使ってやるにはどうしよっかな。
あとjenkinsではログインしないとアクセス出来ないようになってるからセキュリティ周りも見直してビルドだけでも出来るようにするとか。

毎回記事作成するときにrakeタスク実行も面倒なので、メモする時の書式をJekyll形式に合わせるとか、octopressが合わせるようにでもいいし。

GitHubPagesキャッシュ聞いてるから反映してもtopページの即時反映はされないようですね。archivesから記事ページにいけばすぐ見られるけど。
