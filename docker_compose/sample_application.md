## サンプルコードを動かしてみよう

### 開発環境にログイン!

各チームごとのIPアドレスとパスワードについてはスライドをご覧ください。

```
$ ssh ninja@<YOUR TEAM ADDRESS>
```

### サンプルコードをセットアップする

ハッカソン用にいくつかの [サンプルコード](https://github.com/cloud-hackathon) を用意しています。  
言語別にレポジトリが分かれているのでお好きなものをご利用ください。  
ただし、言語によってサンプルコードの内容が違います。  

* [golang-apps](https://github.com/cloud-hackathon/golang-apps) : Revelを使ったチャットアプリ
* [javascript-apps](https://github.com/cloud-hackathon/javascript-apps) : Hubotを使ったボットアプリ
* [ruby-apps](https://github.com/cloud-hackathon/ruby-apps) : Railsを使ったチャットアプリ
* [python-apps](https://github.com/cloud-hackathon/python-apps) : Djangoを使ったフツーのWebアプリ

では、試しに [python-apps](https://github.com/cloud-hackathon/python-apps) をダウンロードしてみましょう。  
先ほど説明した `git clone` コマンドを使います。  
方式が幾つかありますが、楽&誰でも入れるVMなのでToken形式がオススメです。  

```
$ git clone https://github.com/cloud-hackathon/python-apps.git
```

### コンテナを動かしてみよう

では、サンプルコードを動かしてみましょう。  
まずは先ほどダウンロードした `django-plane` のディレクトリに移動します。  

```
$ cd python-apps/django-plane
$ ls
Dockerfile  README.md  docker-compose.yaml  img  src
$ cat docker-compose.yaml
version: '2'
services:
  web:
    build: .
    ports:
      - "8080:8080"
    volumes:
      - "$PWD/src:/code"
```

この `docker-compose.yaml` を実行するには、 `docker-compose up` コマンドを使います。  

```
$ docker-compose up

# カレントディレクトリにあるDockerfileのビルド
Building web
Step 1 : FROM python:2.7.13-alpine
 ---> c80455665c57
Step 2 : ENV PYTHONUNBUFFERED 1

~~ 省略 ~~~

Step 8 : ENTRYPOINT /code/docker-entrypoint.sh
 ---> Using cache
 ---> 97aa91549ddf
Successfully built 97aa91549ddf

# djangoの起動(以下Log)
Starting djangoplane_web_1
Attaching to djangoplane_web_1
web_1  | + ./projectname/manage.py migrate
web_1  | Operations to perform:
web_1  |   Synchronize unmigrated apps: staticfiles, home, django_extensions, messages, compressor
```

これだけでDjangoのアプリケーションが立ち上がりました。  
実際にブラウザから `http://<VM IP ADDRESS>:8080` をみてみましょう。  

このような画面が見えましたか?  
何も表示されないなど、何か問題がありましたらお近くのスタッフまでお声がけください。  

![django](https://github.com/cloud-hackathon/python-apps/blob/master/django-plane/img/screenshot.png)
