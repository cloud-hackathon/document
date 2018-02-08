## HubotをCloud Foundryにデプロイしてみよう

### cf(Cloud Foundry Client)のダウンロード

下記のリンクから各OS向けのcfをダウンロードして  
解凍したバイナリをPATHの通ったディレクトリ( `/usr/local/bin` や `C:\Windows` など)に配置してください。

- [Debian/Ubuntu](https://cli.run.pivotal.io/stable?release=debian64&version=6.21.1&source=github-rel)
- [RedHat/CentOS](https://cli.run.pivotal.io/stable?release=redhat64&version=6.21.1&source=github-rel)
- [Windows](https://cli.run.pivotal.io/stable?release=windows64&version=6.21.1&source=github-rel)
- [macOS](https://cli.run.pivotal.io/stable?release=macosx64&version=6.21.1&source=github-rel)

### 初期設定

最初に、Cloud Foundryにログインします。  
(URL、API鍵、API秘密鍵、スペースはSlackでお伝えします。)

```
$ cf login -a [URL] -u [API鍵] -p [API秘密鍵]
Space> [スペース]
```

### Cloud Foundryにアプリをデプロイする

今回はサンプルとして [Hubotとは?](../slack/hubot.md) で作成したBotをデプロイします。  
`cf push` でソースコードをアップロードすると、デプロイが始まります。

```
$ cd myhubot
$ npm install --save coffee-script
$ cf push myhubot
$ cf set-env myhubot HUBOT_SLACK_TOKEN xoxb-abcdefghijklmnopqrstuvwxyz0123456789
$ cf restart myhubot
```

`cf app myhubot` でデプロイしたアプリの状態を確認できます。  
`state` (状態)が `running` (実行)になっていれば :+1: です。

```
$ cf app myhubot
```

### アプリのログを覗いてみる

```
$ cf logs myhubot --recent
```

### 参考文献

- [20.1. Shared CFのご利用方法 : Enterprise Cloud Knowledge CenterEnterprise Cloud 2.0 Tutorial 2.18.12 ドキュメント](https://ecl.ntt.com/documents/tutorials/rsts/Paas/shared/index.html)
