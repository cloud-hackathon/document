## Gitとは?

[Git](https://git-scm.com) はオープンソースの分散バージョン管理システムです。  
v1で保存したあと開発が進みv3に。途中でv1の方がよかったなと思ったらすぐにv1に戻すことができます。  
このシステムは、Linuxのソースコードを管理するために [リーナス](https://ja.wikipedia.org/wiki/%E3%83%AA%E3%83%BC%E3%83%8A%E3%82%B9%E3%83%BB%E3%83%88%E3%83%BC%E3%83%90%E3%83%AB%E3%82%BA) さんによって開発されました。  
先ほどアカウントを作成した [GitHub](https://github.com/) は、このGitの仕組みを利用して  
ソースコードを保存/公開できるようにしたWebサービスです。

### チーム開発とGitHub

![git](img/git.png)

Gitは、1人よりもチーム開発で使用するとありがたみが増します。  
それは、チームのメンバーが並行して同じファイルに対して修正を加えても  
他のメンバーの修正内容を取り込むための便利な機能があるからです。  

> [Git flow](http://nvie.com/posts/a-successful-git-branching-model/) というプロジェクト開発に便利なGitの使い方があり、  
> 弊社含めこの方法で開発しているところが多いです。

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
    > cloneするときのRepositoryの形式で認証方法が変わります。  
    > * SSHを使う場合(鍵は `~/.ssh/id_rsa` もしくは `~/.ssh/config` で指定したもの)  
    > `$ git clone git@github.com:{アカウント}/{リポジトリ名}.git`  
    > * HTTPSを使い都度Loginする場合  
    > `$ git clone https://github.com/{アカウント}/{リポジトリ名}.git`  
    > * HTTPSを使いTokenを使用する場合  
    > `$ git clone https://{アカウント}:{アクセストークン}@github.com/{アカウント}/{リポジトリ名}`
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

* [サルでも分かるGit入門](http://www.backlog.jp/git-guide/)
* [Gitによるバージョン管理](https://www.amazon.co.jp/dp/B01IGW562K/)


### Gitのインストール方法

Gitをインストール指定ない人は以下のURLを参考にインストールを行って下さい。

* [Gitのインストール](https://git-scm.com/book/ja/v2/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B-Git%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)
