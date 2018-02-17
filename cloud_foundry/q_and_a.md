## 困ったときのQ&A

### `cf push` 後のヘルスチェックで失敗してデプロイできない

`Procfile` に下記のように `web` プロセスを指定している場合、 `$PORT` がListenしているか確認されます。  
(Cloud Foundryがアプリのコンテナ起動後に、自動でヘルスチェックを行います。)  
RubotyなどHTTPをListenしないBotの場合は、 `cf push` 時に `--health-check-type none` を付与すれば無効化できます。

* [CF Dev - \[cf-dev\] What are the process type in Procfile supported by CloudFoundry?](http://cf-dev.70369.x6.nabble.com/cf-dev-What-are-the-process-type-in-Procfile-supported-by-CloudFoundry-td6697.html)

### cfコマンドでbus errorが発生

Mac OSのバージョンによってはエラーが発生することがあるので下記公式リンクから最新のcf-cliをインストールしてください

* download [here](https://cli.run.pivotal.io/stable?release=macosx64&source=github)

* [document for installation](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html#pkg-mac)
