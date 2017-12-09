## 困ったときのQ&A

### tsuruでアプリを動かすために必要なファイル

[Concepts#Application](https://docs.tsuru.io/stable/understanding/concepts.html#applications) より、

* アプリのソースコード
    * Python、Ruby、Go、PHP、JavaScript、Javaなど
* `Procfile`
    * アプリを実行するためのコマンドを記述します
    * [procfile · herokaijp/devcenter Wiki](https://github.com/herokaijp/devcenter/wiki/procfile)
* `requirements.txt` や `Gemfile` や `package.json`
    * アプリが依存するライブラリのリスト
    * デプロイ時に `pip install` や `bundle install` や `npm install` が実行されます 
* `requirements.apt` (オプション)
    * アプリが依存するパッケージのリスト
    * アプリはUbuntu 14.04ベースのDockerコンテナ上で動作します
* `.python-version` (Pythonのみ)
    * アプリが使用するPythonのバージョン
    * 選択可能なバージョンは2.7.13、3.5.3、3.6.1、3.6.2

### アプリを `git push` できない

下記の設定が正しく行われているか確認しましょう。

```
# * default (https://example.com:8080) になっていること
$ tsuru target-list

# git pushで使用する公開鍵が登録されていること
$ tsuru key-list

# git@example.com:[アプリ名].gitが登録されていること
$ git remote -v
```
