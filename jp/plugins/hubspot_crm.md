# Mautic - Hubspot CRMプラグイン

コンタクトが何らかのアクションを行ったとき、このプラグインはコンタクトをHubspot CRMにプッシュすることができます。Mauticにこのプラグインがない場合は、バージョンが最新になっているか確認してください。このプラグインはMautic 1.2.3で追加されました。

まだHubspotCRMのアカウントをお持ちでない場合は、[作成してください](http://www.hubspot.com/crm) 。

## HubspotのAPIキー

HubspotのAPIキーを生成するには、[https://app.hubspot.com/hapikeys](https://app.hubspot.com/hapikeys) ご覧ください。

## HubspotCRMプラグインの設定

Hubspotプラグインの設定を開き、*HubspotAPIキー*入力フィールドにAPIキーを貼り付けます。また、プラグインを使用したい場合はそれを公開する必要があります。*公開スイッチ* を *はい* に設定します。

![Hubspot CRM Plugin configuration](/plugins/media/plugins-hubspot-crm-configuration.png "Hubspot CRM Plugin configuration")

機能タブには *この統合をコンタクトにプッシュ* のチェックボックスだけで、デフォルトではチェックが入っています。

[field mapping](./../plugins/field_mapping.html)を設定します。

プラグインの設定を保存します。

## プラグインのテスト

[these steps](./../plugins/integration_test.html) にしたがい、統合をテストします。

## トラブルシューティング

連絡先が作成されていない場合は、テストしようとしているメールアドレスが有効なものであることを確認してください。Hubspotはそのメールアドレスが有効であるときだけ新しい連絡先を作成します。

## クレジット

このプラグインは[@gpassarelli](https://github.com/gpassarelli)によって開発されました。
