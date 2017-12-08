## 公開鍵の作成方法

### Linux、macOSの場合

- TL; DR
    - run `ssh-keygen -t rsa` and enter three times.

1. `ssh-keygen -t rsa`
2. Enter file in which to save the key (/Users/shunki/.ssh/id_rsa): 鍵の格納場所をしている(括弧内がデフォルト)
3. Enter passphrase (empty for no passphrase): パスワードを入力(なにも書かずにEnterはパスワードなし)
4. Enter same passphrase again: パスワードを再入力

### Windowsの場合

- Tera Term で作る場合
    - [秘密鍵と公開鍵の作成と公開鍵のサーバへの転送(Tera Term版)](https://www.adminweb.jp/web-service/ssh/index5.html)
    - ブログ中にはパスワード設定しろって書いてありますが、今回は省略しても良いです
- ssh-keygenを利用する場合
    - [WindowsでSSHの鍵を作る](https://qiita.com/digdagdag/items/9e5c061e7d86e0af9a57)
    - Gitをインストールしていると、Gitのbinディレクトリの中にssh-keygenがあるらしいのでそれを利用してLinux、macOSとほぼ同じように生成できるそうです
