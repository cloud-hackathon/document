# Cloud Hackathon

* [Cloud Hackathon](#cloud-hackathon)
   * [はじめに](#はじめに)
   * [Githubのアカウント作成](#githubのアカウント作成)
      * [新規登録](#新規登録)
      * [APIトークンの取得](#apiトークンの取得)
   * [そもそもGitとは?](#そもそもgitとは)
      * [チーム開発とGithub](#チーム開発とgithub)
      * [チートシート](#チートシート)
      * [もっとGitを知るには?](#もっとgitを知るには)
   * [サンプルコードを動かしてみよう](#サンプルコードを動かしてみよう)
      * [開発環境にログイン!](#開発環境にログイン)
   * [サンプルコードをセットアップする](#サンプルコードをセットアップする)
   * [コンテナとは?](#コンテナとは)
   * [Dockerとは?](#dockerとは)
      * [Dockerの概要](#dockerの概要)
      * [Dockerイメージを作ってみよう](#dockerイメージを作ってみよう)
      * [コンテナを組み合わせて使うには?](#コンテナを組み合わせて使うには)
   * [コンテナを動かしてみよう](#コンテナを動かしてみよう)
   * [開発サイクルを回してみよう](#開発サイクルを回してみよう)
   * [その他](#その他)
      * [開発マシン情報](#開発マシン情報)
      * [サンプルコード一覧](#サンプルコード一覧)


## はじめに

これから、皆さんにはコンテナを使った開発を手を動かしつつ試してもらいます。  
以下を前提に進めますのでご確認ください。  
何かありましたら、周りのスタッフ又はSlackでご質問ください。

* 指定されたWi-Fiに接続していること
* 自分が割り当てられたチーム名がわかること
* チームのSlackチャネルに参加していること
* SSH可能なターミナルが起動できること

## Githubのアカウント作成

コンテナを動かすその前に...。  
今回は、コードの管理に[Github][1]を使用するので先にアカウントを作成していきます。  
すでに取得済みの方は、新規登録を飛ばして[APIトークンの取得](#APIトークンの取得)をしてください。  

### 新規登録

1. [Github Sign up][3]にアクセス
2. ユーザー名, メールアドレス, パスワード入力して `Create an account` をクリック
3. プラン選択では`Free`でOK
4. 登録したメールアドレスに登録確認メールが届いていることを確認
5. 登録確認用URLをクリック
6. 完了👏

### APIトークンの取得

1. [Settings - Token][4] にアクセス
2. 右上の`Generate new token`ボタンをクリック
3. 『Token description』には適当な説明を入力
4. scopeは一番上の`repo`(Full control of private repositories)を選択
5. `Generate token`ボタンをクリック
6. 表示されたトークンを保存(あとで使います!)

## そもそもGitとは?

[Git][5]はオープンソースの分散バージョン管理システムです。  
v1で保存したあと開発が進みv3に。途中でv1の方がよかったなと思ったらすぐにv1に戻すことができます。  
このシステムは、Linuxのソースコードを管理するために[リーナス][6]さんによって開発されました。  
先ほどアカウントを作成した[Github][1]は、このGitの仕組みを利用してソースコードを保存/公開できるようにしたWebサービスです。

### チーム開発とGithub

![git](img/git.png)

Gitは、1人よりもチーム開発で使用するとありがたみが増します。  
それは、チームのメンバーが並行して同じファイルに対して修正を加えても  
他のメンバーの修正内容を取り込むための便利な機能があるからです。  

> [Git flow][9]というプロジェクト開発に便利なGitの使い方があり、
> 弊社含めこの方法で開発しているところが多いです

### チートシート

今回のハッカソンで使われると思われるコマンドだけピックアップしてみました。  
他にやりたいことがあれば、スタッフに聞いてみてください。

* Gitの設定

   ```
   $ git config --global user.name <YOUR NAME>
   $ git config --global user.email <YOUR EMAIL>
   ```

* リモート(Githubとか)からレポジトリをダウンロード

   ```
   $ git clone <REPOSITORY PATH>
   ```
   
> cloneするときのRepositoryの形式で認証方法が変わります
> ■ SSHを使う場合(鍵は~/.ssh/id_rsa, もしくは~/.ssh/configで指定したもの)
> $ git clone git@github.com:{アカウント}/{リポジトリ名}.git
> ■ HTTPSを使い都度Loginする場合
> $ git clone https://github.com/{アカウント}/{リポジトリ名}.git
> ■ HTTPSを使いTokenを使用する場合
> $ git clone https://{アカウント}:{アクセストークン}@github.com/{アカウント}/{リポジトリ名}

* ファイルの追加(インデックス登録)

   ```
   # 指定したファイルを追加
   $ git add <FILE NAME>
   # すべてのファイルを追加
   $ git add --all
   ```

* 変更内容を確定させる(コミット)

   ```
   $ git commit -m '<MESSAGE>'
   ```

* 変更内容をリモートにアップロード

   ```
   $ git push origin <BRANCH_NAME>
   ```
   
* すべての変更内容をリモードからダウンロード

   ```
   $ git pull
   ```

### もっとGitを知るには?

今回の説明内容はいろいろな情報を省いている(非推奨なこともやっている)ので、  
Gitを本格的に使ってみたいなと思った方は、以下のサイトや本を参考にしてください。  
特に本の方はチーム開発での流れを追いつつそこで必要なGitを学べるので優秀です。

* [サルでも分かるGit入門][7]
* [Gitによるバージョン管理][8]

## サンプルコードを動かしてみよう

### 開発環境にログイン!

各チームごとのIPアドレスとパスワードについてはスライドをご覧ください。

```
$ ssh ninja@<YOUR TEAM ADDRESS>
```

## サンプルコードをセットアップする

ハッカソン用にいくつかの[サンプルコード](サンプルコード一覧)を用意しています。  
言語別にレポジトリが分かれているのでお好きなものをご利用ください。  
ただし、言語によってサンプルコードの内容が違います。  

* [golang-apps][0]: Revelを使ったチャットアプリ
* [javascript-apps][10]: Hubotを使ったボットアプリ
* [ruby-apps][22]: Railsを使ったチャットアプリ
* [python-apps][23]: Djangoを使ったフツーのWebアプリ

では、試しに[python-apps][23]をダウンロードしてみましょう。  
先ほど説明した`git clone`コマンドを使います。  
方式が幾つかありますが、楽&誰でも入れるVMなのでToken形式がオススメです。  

```
$ git clone https://github.com/cloud-hackathon/python-apps.git
```

早速動かしたいところですが、先にDockerについてご説明します。  


## コンテナとは?

コンテナとは、OS上に隔離された空間(サンドボックス)を作成し、その中で別の環境を実行できる技術です。  
コンテナにはCPUやメモリなどのリソースが割り当てられ、プロセスの実行環境が分離されます。  
(namespaceやcgroupsというLinuxカーネルの技術を使っています。)

[VMWare Player][18]や[Oracle VirtualBox][19]などのハイパーバイザ型の仮想化と比較して高速・軽量という特徴があります。
ハイパーバイザではハードウェアをシミュレートして仮想マシンを動作させているため、  
オーバーヘッドが大きくなりがちです。

コンテナではカーネル(OSの基本的な部分)を共有し実行環境を分離しているだけなので、オーバーヘッドが小さいです。  
そのため、起動・停止が高速だったり、1台のサーバ上で大量のコンテナを動かしたりできます。

![container](img/container.jpg)

* [コンテナ技術の基礎知識][11]
* [注目を浴びる「Dockerコンテナ」、従来の仮想化と何が違うのか？][12]

## Dockerとは?

### Dockerの概要

🐳 [Docker][13]とは、コンテナを動かすためのオープンソースソフトウェアです。  
コンテナの中身(Dockerイメージ)を作る仕組みや、コンテナの実行環境を提供しています。  

Dockerイメージとは、コンテナとして動かすOSとアプリケーションをまとめたものです。  
軽量でどこでも同じように動くという特徴があるため、アプリケーションを配布するのに向いています。  
[Docker Hub][16]というWebサイトがあり、様々なDockerイメージが公開されています。  

![container_as_a_service](img/container_as_a_service.png)

* [巷で話題のDockerとは?][14]
* [Containers As A Service (CaaS) As Your New Platform For Application Development And Operations][17]

### Dockerイメージを作ってみよう

Dockerfileを使えば、Dockerイメージを簡単に作ることができます。  
ベースとなるイメージを指定し、イメージを作るために必要なコマンドを記述します。  
例えば、[Ubuntu][20]上で `hello-world.rb` というスクリプトを動かすコンテナを考えます。  
Rubyをインストールして、スクリプトをコンテナに追加するだけで完成です。  

```dockerfile
FROM ubuntu:16.04

RUN apt-get update && \
    apt-get -y upgrade && \
    apt-get -y install ruby

ADD hello-world.rb

CMD ruby hello-world.rb
```

```
$ docker build -t hello-world .
$ docker run hello-world
```

* [Dockerイメージの理解とコンテナのライフサイクル][15]

### コンテナを組み合わせて使うには?

Dockerでは、メンテナンス性を高めるために、コンテナで実行する機能を小さくしようと言われています。
例えばWebアプリケーションの場合、アプリ用のコンテナと、データベース用のコンテナは分けることが多いです。
このように複数のコンテナで構成されるサービスを動かしたいときに便利なのが[Docker Compose][16]です。
docker-composeを使うことで、複数のコンテナを一度に起動できるだけでなく、依存関係の解決もしてくれます。
(先にデータベース用のコンテナを起動してから、アプリ用のコンテナを起動するなど。)

起動するコンテナとその設定は `docker-compose.yml` という[YAML][21]形式のファイルに記述します。
例えば `web` と `database` というコンテナを起動する場合は、以下のような内容になります。
`web` では8080番ポートが接続され、カレントディレクトリが `/code` にマウントされます。
また、 `web` が依存する `database` が先に起動されます。

```yaml
version: '2'
services:
  web:
    build: .
    ports:
      - "8080:8080"
    volumes:
      - "$PWD:/code"
    depends_on:
      - database
  database:
    image: mysql
```

## コンテナを動かしてみよう

では、サンプルコードを動かしてみましょう。  
まずは先ほどダウンロードした`django-plane`のディレクトリに移動します。  

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

この `docker-compose.yaml` を 実行するには、`docker-compose up`コマンドを使います。  

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
実際にブラウザから`http://<VM IP ADDRESS>:8080`をみてみましょう。  

このような画面が見えましたか?  
何も表示されないなど、何か問題がありましたらお近くのスタッフまでお声がけください。  

![django](https://github.com/cloud-hackathon/python-apps/blob/master/django-plane/img/screenshot.png)


## 開発サイクルを回してみよう

### 基本的な流れ

1. サンプルコードをダウンロード
1. docker-composeで起動
1. コードを修正
1. docker-composeで再起動
1. 以降3,4を繰り返す

### コードの修正方法

以下のような方法があります。チームで好きなやり方を決めてください。

1. VM内に入って直接コードを修正する
  * Pros. そのまま実行&確認できる
  * Cons. エディタ...
1. ローカルのエディタで修正してGit経由でコードを更新する
  * Pros. 普段の環境でコードを書ける
  * Cons. Gitコマンドがある程度使えること & 動作確認に時間がかかる)
1. エディタのリモート編集機能を使って直接サーバー上のコードを修正する
  * Pros. 普段の環境でコードが書ける & サーバ上で動作確認可能
  * Cons. エディタによってやり方が違う

### 実際にやってみよう

基本的な流れがわかったところで、実際にやってみましょう。  
(まだDjangoアプリが起動中の方は`Ctrl-C`で停止してください。)  
`views.py`のファイルを編集して、ホーム画面のメッセージを変えてみます。

```
$ vi src/projectname/home/views.py
```

とりあえず`Hello World!`にしてみました。

```
$ git diff
diff --git a/django-plane/src/projectname/home/views.py b/django-plane/src/projectname/home/views.py
old mode 100644
new mode 100755
index 3ad2890..9a0112a
--- a/django-plane/src/projectname/home/views.py
+++ b/django-plane/src/projectname/home/views.py
@@ -6,6 +6,6 @@ class HomeView(TemplateView):

     def get(self, request, *args, **kwargs):
         context = {
-            'some_dynamic_value': 'This text comes from django view!',
+            'some_dynamic_value': 'Hello World!',
         }
-        return self.render_to_response(context)
\ No newline at end of file
+        return self.render_to_response(context)

```

再び`docker-compose up`を実行してブラウザにアクセスしてみてください。  
メッセージが変わっているはずです。  

説明は以上になります。  
何かありましたら遠慮なくスタッフにお聞きください。  
Happy Hacking!  


## その他

### よくありそうなQ&A

* 修正したのに変更が反映されない
  > Dockerfileやインストールするパッケージを変更している場合は
  > イメージを再ビルドする必要があります。`docker-compose up --build` をお試しください。

* ローカルでcurlを叩いても`接続が拒否されました`と表示される
  > コンテナ内のアプリケーションの起動アドレスが`127.0.0.1`になっていませんか?
  > ポートフォワーディングする場合は`0.0.0.0`で起動する必要があります。
  
* ブラウザから表示されない  
  > 起動するポート番号は正しいですか?
  > 本環境では、ポート8080-8089番のみ許可されています。

### 開発マシン情報

Name|Value
----|-----
VM|[Cloudn FLAT Compute][2] / 2CPU / 4GB RAM / 15G DISK
OS|Ubuntu 16.04
公開ポート|22, 8080-8090


[0]: https://github.com/cloud-hackathon/golang-apps
[1]: https://github.com/
[2]: http://www.ntt.com/business/services/cloud/iaas/cloudn.html
[3]: https://github.com/join?source=header-home
[4]: https://github.com/settings/tokens
[5]: https://git-scm.com
[6]: https://ja.wikipedia.org/wiki/%E3%83%AA%E3%83%BC%E3%83%8A%E3%82%B9%E3%83%BB%E3%83%88%E3%83%BC%E3%83%90%E3%83%AB%E3%82%BA
[7]: http://www.backlog.jp/git-guide/
[8]: https://www.amazon.co.jp/dp/B01IGW562K/
[9]: http://nvie.com/posts/a-successful-git-branching-model/
[10]: https://github.com/cloud-hackathon/javascript-apps
[11]: https://thinkit.co.jp/story/2015/08/11/6285
[12]: http://cn.teldevice.co.jp/column/detail/id/102
[13]: https://www.docker.com
[14]: https://thinkit.co.jp/story/2015/08/05/6284
[15]: http://www.slideshare.net/zembutsu/docker-images-containers-and-lifecycle
[16]: https://docs.docker.com/compose/
[17]: https://blog.docker.com/2016/02/containers-as-a-service-caas/
[18]: http://www.vmware.com/products/player/playerpro-evaluation.html
[19]: https://www.virtualbox.org
[20]: https://www.ubuntu.com
[21]: https://ja.wikipedia.org/wiki/YAML
[22]: https://github.com/cloud-hackathon/ruby-apps
[23]: https://github.com/cloud-hackathon/python-apps
