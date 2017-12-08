## その他サンプルアプリのデプロイ手順

[ここ](../slack/links.md) の `サンプルになりそうなBot` に記載されているSlack Appのデプロイ方法を一部まとめます。

### slack-tetris

```
$ git clone https://github.com/cloud-hackathon/slack-tetris.git
$ cd slack-tetris
$ # direnvやpyenvなどでpython3系をインストール&設定
$ python -V
Python 3.6.2
$ pip install -r requirements.txt # 依存パッケージのインストール
$ export SLACK_API_TOKEN=xoxb-...
$ export BOT_NAME=<bot name>
$ python bot.py
$ # Slackで動作確認
$ tsuru target-add default http://example.com -s
$ tsuru login
$ tsuru app-create <app name> python -t test
$ tsuru env-set SLACK_API_TOKEN=xoxb-...
$ tsuru env-set BOT_NAME=<bot name>
$ tsuru key-add default ~/.ssh/id_rsa.pub
$ git remote add tsuru git@example.com:slack-tetris.git
$ git push tsuru master
$ # Slackで動作確認
```

### mahjong_chatbot

```
$ git clone https://github.com/kozyszoo/mahjong_chatbot.git
$ cd mahjong_chatbot
$ rbenv install 2.3.0
$ rbenv global 2.3.0
$ gem install bundler
$ bundle install
$ export SLACK_TOKEN=xoxb-... # for local
$ bundle exec ruboty -l mahjang.rb # for local
$ # Slackで動作確認
$ echo 'web: bundle exec ruboty -l mahjang.rb' > Procfile
$ git add
$ git commit -m ""
$ tsuru target-add default http:// -s
$ tsuru login
$ tsuru app-create <your app name> ruby -t hackathon
$ tsuru env-set SLACK_TOKEN=xoxb-... -a <your app name>
$ git remote add tsuru <your repository>
$ git push tsuru master
$ # Slackで動作確認
```
