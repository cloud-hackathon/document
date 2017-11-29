## Githubのアカウント作成

コンテナを動かすその前に...。  
今回は、コードの管理に[Github](https://github.com/)を使用するので先にアカウントを作成していきます。  
すでに取得済みの方は、新規登録を飛ばして[APIトークンの取得](#APIトークンの取得)をしてください。  

### 新規登録

1. [Github Sign up](https://github.com/join?source=header-home)にアクセス
2. ユーザー名, メールアドレス, パスワード入力して `Create an account` をクリック
3. プラン選択では`Free`でOK
4. 登録したメールアドレスに登録確認メールが届いていることを確認
5. 登録確認用URLをクリック
6. 完了👏

### APIトークンの取得

1. [Settings - Token](https://github.com/settings/tokens) にアクセス
2. 右上の`Generate new token`ボタンをクリック
3. 『Token description』には適当な説明を入力
4. scopeは一番上の`repo`(Full control of private repositories)を選択
5. `Generate token`ボタンをクリック
6. 表示されたトークンを保存(あとで使います!)
