## Hubotをtsuruにデプロイしてみよう

### tsuru-clientのダウンロード

[tsuru/tsuru-client](https://github.com/tsuru/tsuru-client/releases/tag/1.4.0) から各OS向けのtsuru-clientをダウンロードして  
解凍したバイナリをPATHの通ったディレクトリ( `/usr/local/bin` や `C:\Windows` など)に配置してください。

### 初期設定

最初に、tsuruにログインし、パスワードを変更します。  
(URL、メールアドレス、初期パスワードはSlackでお伝えします。)

```
$ tsuru target-add default http://example.com:8080 -s
$ tsuru login
$ tsuru change-password
```

### 公開鍵の登録

GitリポジトリにSSHでpushするための公開鍵を登録します。  

```
$ tsuru key-add default ~/.ssh/id_rsa.pub
```

### tsuruでアプリを作成する

今回はサンプルとして [Hubotとは?](../slack_bot/hubot.md) で作成したBotをデプロイします。  
tsuruでアプリケーションを作成するとリポジトリのアドレスが得られます。

```
$ tsuru app-create myhubot nodejs
```

### Gitでアプリをデプロイする

`git push` でソースコードをアップロードすると、デプロイが始まります。  
Dockerイメージのビルドが成功すると、Dockerコンテナが起動します。  
( `tsuru app-info` でUnitのStatusがstartingになっていれば 👌 です。)

```
$ cd myhubot
$ git init
$ git add .
$ git commit -m 'first commit' 
$ git remote add tsuru git@hico.cloud:myhubot.git 
$ tsuru env-set HUBOT_SLACK_TOKEN=xoxb-abcdefghijklmnopqrstuvwxyz0123456789
$ git push tsuru master
```

### アプリのログを覗いてみる

```
$ tsuru app-log
```

### アプリのコンテナの中に入ってみる

```
$ tsuru app-shell  
```
