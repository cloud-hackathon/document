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
