## Hubotとは?

### Botとは?

チャットに常駐して、発言に応じて応答を返したり、決められた条件に従って発言して  
参加者に通知したりするようなプログラムのことをBotと呼びます。  
Botを使うことで、定型的な処理を自動化したり、人工無能のような受け答えをさせることで  
チャットを楽しくしたりすることができます。

TwitterのBotを想像してもらうと分かりやすいでしょうか。  
「特定のキーワードに反応する」「リプライを返す」「定期的に呟く」など、やることは同じです。

### Hubotとは?

Hubotとは、GitHubが開発したBotフレームワーク(枠組み)です。  
CoffeeScript(またはJavaScript)で処理を書くことで、簡単に機能を拡張できます。  
また、Slackや [Typetalk](https://www.typetalk.com/ja/) など、複数のサービスに対応させることができます。

「フレームワーク」なので、実際の処理部分だけの開発で済みます。  
Botとしての基本的な機能(チャットの取得と発言など)は、Hubotが提供してくれます。

### HubotでBotを作ってみる

Hubotを動作させるためにNode.jsとnpmをインストールします。  
Windowsの方は [nodistでNode.jsをバージョン管理](https://qiita.com/satoyan419/items/56e0b5f35912b9374305) を参考にしてください。  
(参考: [Hubot のインストール](https://qiita.com/bouzuya/items/11c0c6da2b3ad54b827f) )

```
$ brew install node
$ npm install npm@latest -g
```

次に、ジェネレータを使ってHubotの雛形を作成します。  
対話形式でHubotの初期設定をしますが、 `Bot adapter` は `slack` を入力し、  
それ以外はデフォルト値(Enterキーを押す)か、お好みの設定でOKです。  
( `Overwrite package.json?` と聞かれた場合は `y` を入力してください。)

```
$ mkdir myhubot
$ cd myhubot
$ npm init
$ npm install yo generator-hubot --save
$ node_modules/.bin/yo hubot
```

終わったら、まずはターミナル上でHubotを実行してみましょう。  
こんな感じで `myhubot` (Bot名)に続けてコマンドを打つと、対応する結果を返してくれます。

```
$ bin/hubot
myhubot> myhubot ping
myhubot> PONG
myhubot> myhubot time
myhubot> Server time is: Thu Nov 30 2017 11:13:58 GMT+0900 (JST)
```

### Hubotスクリプトで機能を追加してみる 

簡単なスクリプトを作ってHubotに機能を追加してみます。  
「hello」「Hello」と話し掛けると「World!」と返してくれるようにしましょう。  
(参考: [Hubot スクリプトを追加インストールしよう & 自分だけの Hubot スクリプトをつくろう](https://qiita.com/bouzuya/items/4c0206d72ff22ade9339) )

`scripts/hello.coffee` を下記の内容で作成してください。

```coffee
module.exports = (robot) ->
  robot.respond /hello/i, (msg) ->
    msg.send 'World!'
```

では、実際に動かして確認してみます。

```
$ bin/hubot
myhubot> myhubot hello
myhubot> World!
```

### HubotをSlackで動作させてみる

HubotをSlackに接続して、チャットサービス上で動作させてみます。  
[Slack Appを追加してみよう](integration.md) に従ってトークンを取得し、  
`HUBOT_SLACK_TOKEN` という環境変数に設定してHubotを起動します。

```
$ HUBOT_SLACK_TOKEN=xoxb-abcdefghijklmnopqrstuvwxyz0123456789 bin/hubot -a slack
```

![myhubot](../img/myhubot.png)

説明は以上です! Slackにはアタッチメント、ボタン、メニュー、ダイアログなどの機能があったり、  
Hubotスクリプトはnpmで追加できたりするので、面白いアイデアを実装してみてください。
