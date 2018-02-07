## Cloud Foundryとは?

[Cloud Foundry](https://www.cloudfoundry.org/) は主にRuby, Go言語によって開発されているオープンソースのPaaS(Open PaaS)です。
当初VMWare社が開発を行っていましたが、2014年にCloud Foundry Foundationに開発のガバナンスを移管されました。


### 簡易なCF上での流れ(build packを実行する場合)
1. ユーザがpush
2. Buildpackが実行される
    2-1. Detect(buildpackの実行条件と合致するかチェック)
    2-2. Compile(実行環境を構築)
    2-3. Release(実行に必要な環境変数などの情報を出力)
3. Cloud Foundryの実行ノードでアプリを起動
[参考](https://www.slideshare.net/jacopen/paas-for-beginners)


### コンポーネント
主に公式の[document](http://docs.cloudfoundry.org/concepts/architecture/index.html)を元に記述しています。
![architecture_block](img/cf_architecture_block.png)

- Routing
    - Router
        - URLによってアクセスを振り分けるコンポーネント - 実体はUbuntu上にて動作する
- Authentication
    - OAuth2 Server (UAA) and Login Server
        - 認証の管理
- App Lifecycle
    - Cloud Controller and Diego Brain
        - アプリのライフサイクルを管理する
        - push されたものを受け取る、Dropletを実行環境に受け渡す、など
    - nsync, BBS, and Cell Reps
        - appが継続して実行されるようにステータスの管理を実行する
- App Storage & Execution
    - Blobstore
        - 様々なbinary fileのレポジトリとして機能する
    - Diego Cell
        - アプリをコンテナとして実行する - Services
    - Service Brokers
        - 外部のサービスと連携したりできる(e.g. MySQL)
- Messaging
    - Consul and BBS
        - VM間のcommunicationに使われる
- Metrics & Logging
    - ログと監視メトリクスの管理


### インターフェイス
- Cloud Foundryでは`cf`CLIを利用して操作を行う。


### サポートされるランタイム
- Java
- Ruby
- Node.js
- Scala
- Go
- Python
- PHP
など

