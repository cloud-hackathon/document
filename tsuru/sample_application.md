## Hubotをtsuruにデプロイしてみよう

### tsuru-clientのダウンロード

[tsuru/tsuru-client](https://github.com/tsuru/tsuru-client/releases/tag/1.4.0) から各OS向けのtsuru-clientをダウンロードして  
解凍したバイナリをPATHの通ったディレクトリ( `/usr/local/bin` や `C:\Windows` など)に配置してください。

### 初期設定

最初に、tsuruにログインし、パスワードを変更します。  
(URL、メールアドレス、初期パスワードはSlackでお伝えします。)

```
$ tsuru target-add default https://example.com:8080 -s
$ tsuru login
$ tsuru change-password
```

### 公開鍵の作成

自由に利用できる公開鍵を持っていない方は以下のように作成して下さい。  
(本日用に作成することを推奨します。)

- [公開鍵の作成方法](../ssh_keygen.md)

### 公開鍵の登録

GitリポジトリにSSHでpushするための公開鍵を登録します。  

```
$ tsuru key-add default ~/.ssh/id_rsa.pub
```

### tsuruでアプリを作成する

今回はサンプルとして [Hubotとは?](../slack_bot/hubot.md) で作成したBotをデプロイします。  
tsuruでアプリケーションを作成するとリポジトリのアドレスが得られます。

```
$ tsuru app-create myhubot buildpack
```

今回はPlatform(アプリケーションの実行基盤)に `buildpack` を使用していますが、下記の言語も選択可能です。

* [buildpack](https://github.com/tsuru/platforms/tree/master/buildpack)
* [go](https://github.com/tsuru/platforms/tree/master/go)
* [java](https://github.com/tsuru/platforms/tree/master/java)
* [nodejs](https://github.com/tsuru/platforms/tree/master/nodejs)
* [php](https://github.com/tsuru/platforms/tree/master/php)
* [python](https://github.com/tsuru/platforms/tree/master/python)
* [ruby](https://github.com/tsuru/platforms/tree/master/ruby)
* [static](https://github.com/tsuru/platforms/tree/master/static)

### Gitでアプリをデプロイする

`git push` でソースコードをアップロードすると、デプロイが始まります。  
Dockerイメージのビルドが成功すると、Dockerコンテナが起動します。  
( `tsuru app-info` でUnitのStatusがstartingになっていれば 👌 です。)

```
$ cd myhubot
$ git init
$ git add .
$ git commit -m 'first commit' 
$ git remote add tsuru git@example.com:myhubot.git 
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
