## Slack app

Slack appの開発を始める前に[開発者向けドキュメント][1]を見てみましょう。
App capabilitiesセクションにある通り、開発者は様々な方法でSlack appを実現することができます。

1. `Incoming Webhooks`: Webhook経由で指定のチャンネルにメッセージを投稿する
2. `Slash Commands`: ユーザからのコマンドに合わせたタスクを実行する
3. `Bot User`: ユーザと対話しながらタスクを実行する
4. `Internal Integrations`: 他者に公開しないドメスティックなSlack appの総称
5. `Message Buttons`: メッセージにボタンを追加する
6. `Real Time Messaging and Events`: 条件を満たしたときにメッセージを投稿する
7. `Permission Scope`: Slack appの権限を管理する
8. `OAuth`: Slack appを認証する
9. `App Directory`: Slack appを他者に公開する

開発者向けドキュメント右上のTutorialsにまとまっているハウツーをこなしていくとSlack appの開発について段々と理解が深まります。
しかし、今回は短い時間の中で成果を出さなければならないので、Slack appの中でも比較的メジャーなBot Userの開発フローをまとめました。

開発者向けドキュメント右上のYour Appsに遷移して新しいBot Userを開発していきましょう。

1. [Your Apps][2]にアクセスする
  ![your_apps](../img/slack/1_your_apps.png)

2. Create New Appボタンを押し、Slack appの名前と紐付けるWorkspaceを入力し、Create Appボタンを押す
  ![create_new_app](../img/slack/2_create_new_app.png)

3. 作成したAppのBasic Informationページにリダイレクトされる
  ![basic_information](../img/slack/3_basic_information.png)

4. Add features and functionalityのBotsパネルを押しAdd a Bot Userボタンを押す
  ![bot_user](../img/slack/4_bot_user.png)

5. Display nameとDefault usernameを入力しAdd Bot Userボタンを押す
  ![add_bot_user](../img/slack/5_add_bot_user.png)

6. 左メニューからBasic Informationに戻りInstall your app to your workspaceのInstall App to Workspaceを押す
  ![install_app](../img/slack/6_install_app.png)

7. 追加されるBotのusernameを確認してAuthorizeボタンを押す
  ![authorize](../img/slack/7_authorize.png)

8. 取得したTokenを控えつつ好きな言語・フレームワークでBotを実装する
    ![authorize](../img/slack/8_token.png)
    * Javascript/Ruby/Pythonなどさまざまな言語で実装されたSlack appサンプル集を用意しています。
    * これらをベースにするもよし、一から開発するもよしです。
    * ここではHubotを利用して簡単なBotを作成したとします。

9. Bot UserをInviteするためにPublic Channelを作成する
    ![authorize](../img/slack/9_add_channel.png)
    * Slackアプリを起動しChannelsの右にある+ボタンを押して新しいPublic Channelを追加しましょう。

10. 作成したPublic ChannelにBot UserをInviteする
    ![authorize](../img/slack/10_invite_bot.png)
    * 作成したPublic Channelを開きinfoマークを押して右メニューを表示させMembersのInvite more peopleから作成したBot Userを追加しましょう。

11. localhostでHubotを実行する
    * Hubotを実行してからSlackで動作確認してみましょう。
    * 問題なければSlack appをPaaSにデプロイしてみんなに自慢しましょう！

[1]: https://api.slack.com/slack-apps
[2]: https://api.slack.com/apps
