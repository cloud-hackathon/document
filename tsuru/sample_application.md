## Hubotをtsuruにデプロイしてみよう

### tsuru-clientのダウンロード

[tsuru/tsuru-client](https://github.com/tsuru/tsuru-client/releases/tag/1.4.0) から各OS向けのtsuru-clientをダウンロードして  
解凍したバイナリをPATHの通ったディレクトリ( `/usr/local/bin` や `C:\Windows` など)に配置してください。

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
$ tsuru app-create myhubot nodejs
```

今回はPlatform(アプリケーションの実行基盤)に `nodejs` を使用していますが、下記の言語も選択可能です。

* `buildpack`
* `go`
* `java`
* `nodejs`
* `php`
* `python`
* `ruby`

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
