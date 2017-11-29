## サンプルコードを動かしてみよう

### 開発環境にログイン!

各チームごとのIPアドレスとパスワードについてはスライドをご覧ください。

```
$ ssh ninja@<YOUR TEAM ADDRESS>
```

### サンプルコードをセットアップする

ハッカソン用にいくつかの[サンプルコード](https://github.com/cloud-hackathon)を用意しています。  
言語別にレポジトリが分かれているのでお好きなものをご利用ください。  
ただし、言語によってサンプルコードの内容が違います。  

* [golang-apps](https://github.com/cloud-hackathon/golang-apps): Revelを使ったチャットアプリ
* [javascript-apps](https://github.com/cloud-hackathon/javascript-apps): Hubotを使ったボットアプリ
* [ruby-apps](https://github.com/cloud-hackathon/ruby-apps): Railsを使ったチャットアプリ
* [python-apps](https://github.com/cloud-hackathon/python-apps): Djangoを使ったフツーのWebアプリ

では、試しに[python-apps](https://github.com/cloud-hackathon/python-apps)をダウンロードしてみましょう。  
先ほど説明した`git clone`コマンドを使います。  
方式が幾つかありますが、楽&誰でも入れるVMなのでToken形式がオススメです。  

```
$ git clone https://github.com/cloud-hackathon/python-apps.git
```

早速動かしたいところですが、先にDockerについてご説明します。  
