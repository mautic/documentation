# Mautic - Salesforce CRMプラグイン

リードが何らかのアクションを行ったとき、このプラグインはSalesforce CRMにリードをプッシュすることができます。Salesforce CRMのアカウントをまだお持ちでないのなら、[作成してください](http://www.salesforce.com/)。

## 要件

SSH。MauticインスタンスはHTTPS上で実行されていなければなりません。SalesforceはhttpコールバックURLでのアプリケーションの作成を許可していません。

## Salesforceクライアントの認証情報の取得

更新されていないようですが、キーと認証情報を取得するための[公式のドキュメント](http://feedback.uservoice.com/knowledgebase/articles/235661-get-your-key-and-secret-from-salesforce) があります。

*Setup* (右上はし) / Build (左下はし) - Create / Apps / Connected Apps / Newを開きます。

![Salesforce CRM Create an App](/plugins/media/plugins-salesforce-create-app.png "Salesforce CRM Create an App")

このような新しいアプリを作成します。
![Salesforce CRM Create an App form](/plugins/media/plugins-salesforce-create-app-form.png "Salesforce CRM Create an App form")
Selcected OAuth Scopes が *Access and manage your fata (api)* と *Perform requests on your behalf at any time (refresh_token, offline_access)* になっていることを確認してください。

コンシューマキーとシークレットをコピーします。

![Salesforce CRM Create an App keys](/plugins/media/plugins-salesforce-create-app-keys.png "Salesforce CRM Create an App keys")

## Mautic Salesforceのプラグイン設定

Mautic Salesforceのプラグインにキーを挿入し、それを承認します。
![Salesforce CRM Authorize](/plugins/media/plugins-salesforce-authorize.png "Salesforce CRM Authorize")

[field mapping](./../plugins/field_mapping.html) を設定します。

## プラグインのテスト

[これらの手順にしたがい](./../plugins/integration_test.html) 統合をテストします。

## トラブルシューティング

### Error: `The REST API is not enabled for this Organization.`

これはこのAPIがはあなたのSalesforceアカウントでオンになっていないことを意味します。[Read more](https://help.salesforce.com/apex/HTViewHelpDoc?id=admin_userperms.htm&language=en)
