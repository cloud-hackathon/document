## その他サンプルアプリのデプロイ手順

[ここ](../slack/links.md) の `サンプルになりそうなBot` に記載されているSlack Appのデプロイ方法を一部まとめます。

### ruboty-bot

```
$ git clone https://github.com/cloud-hackathon/ruby-apps.git
$ cd ruby-apps/ruboty-bots

$ rbenv install 2.3.1
$ rbenv global 2.3.1
$ gem install bundler --no-ri --no-rdoc
$ bundle install --jobs=4 --path=vendor/bundler --binstubs=vendor/bin

$ SLACK_TOKEN=xoxb-abcdefghijklmnopqrstuvwxyz0123456789 bundle exec ruboty --load app.rb
# ローカルでBotを起動し、Slackで動作確認

$ cf login -a <URL> -u <api key> -p <api secret key>
$ cf push <app name>
# Cloud FoundryにBotをデプロイし、Slackで動作確認
```

### slack-tetris

```
$ git clone https://github.com/cloud-hackathon/slack-tetris.git
$ cd slack-tetris

# direnvやpyenvなどでpython3系をインストール&設定
$ python -V
Python 3.6.2

# 依存パッケージのインストール
$ pip install -r requirements.txt 

# 取得したslack-tetrisディレクトリのmanifest.ymlに環境変数を追加する (下記の1.と5.を参照)
# https://raw.githubusercontent.com/cloud-hackathon/slack-tetris/master/README.md

$ cf login -a <URL> -u <api key> -p <api secret key>
$ cf push <app name>

# Cloud FoundryアプリのURLを取得する
$ cf app <app name> | grep urls
urls: tetris-cliquish-dualism.lab3.tamac.me # コピーする

# SlackのEvent SubscriptionsにURLを登録しSubscribe to Bot EventsにMessageイベント3つを追加する
# Slackで動作確認
```
