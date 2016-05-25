# Mautic - vtiger CRMプラグイン

コンタクトが何らかのアクションを行ったときに、このプラグインはvTiger CRMにコンタクトをプッシュすることができます。

vTiger CRMのアカウントをまだお持ちでないのなら、[作成して](https://www.vtiger.com/) ください。

## vTigerプラグインの認証

vTiger CRMと通信することができるようにMauticプラグインを認証するには以下の認証情報が必要になります。

- **vTiger URL** - http:// もしくは https:// で始まるvTigerインスタンスが稼働しているベース(ルート)URLです。例えば `https://your_vtiger.od2.vtiger.com` です。
- **vTiger username** - vTigerへのログイン時に使用するユーザー名(通常はメールアドレス)。
- **vTiger access key** - vTigerプロフィールに公開されているアクセスキー。これを取得するには、*My Preferences*にアクセスしてください。*アクセスキー*ハッシュはそのページの下部にあります。

Mauticプラグインにこれ​​らの3個の認証情報を入力し、認証をクリックします。

## vTiger CRMプラグインの設定

このプラグインを使用するにはこれを公開する必要があります。*公開スイッチ* を *はい* に設定します。

機能タブには *この統合をコンタクトにプッシュ* のチェックボックスだけで、デフォルトではチェックが入っています。

[field mapping](./../plugins/field_mapping.html)を設定します。

プラグインの設定を保存します。

## プラグインのテスト

[これらの手順にしたがい](./../plugins/integration_test.html) 統合をテストします。
