# Mautic - Zoho CRMプラグイン

コンタクトが何らかのアクションを行ったとき、このプラグインは Zoho CRMにコンタクトをプッシュすることができます。

vTiger CRMのアカウントをまだお持ちでないのなら、[作成して](https://www.zoho.com/crm/)ください。

## Zoho CRMプラグインの設定

Zohoのアカウント作成時のメールアドレスとパスワードをMautic Zohoの統合プラグインへ入力し、承認します。*公開スイッチ* を *はい* に設定します。保存します。

![Zoho CRM Plugin configuration](/plugins/media/plugins-zoho-authorization.png "Zoho CRM Plugin configuration")

Zohoの2段階認証が有効になっている場合は、アプリケーション固有のパスワードを生成して使用する必要があります。
(https://www.zoho.com/mail/help/adminconsole/two-factor-authentication.html#alink5)

機能タブには *この統合をコンタクトにプッシュ* のチェックボックスだけで、デフォルトではチェックが入っています。

[field mapping](./../plugins/field_mapping.html)を設定します。

プラグインの設定を保存します。

## プラグインのテスト

[これらの手順にしたがい](./../plugins/integration_test.html) 統合をテストします。
