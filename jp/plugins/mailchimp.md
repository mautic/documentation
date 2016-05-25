# MailChimpの統合

Mauticは、いくつかのコンタクトのアクション時またはポイントの上限に達したときにコンタクトをMailChimpに送信することができます。

** バージョンノート **
- Mautic 1.2.2およびそれ以前の場合は、MailChimpアプリの作成とOAuth2経由での認証が必要でした。認証のため、クライアントの鍵と秘密認証が必要とされます。また、SSL (HTTPS) 接続が必要です。
- Mautic 1.2.3以降の場合、認証はAPIキーに変更されました。このドキュメントではこのオプションをカバーしています。このプラグインには下位互換性があります。クライアントIDが入力されている場合はこのプラグインはOAuth2を使用します。クライアントIDが空の場合、このプラグインはAPIキーの入力を促します。

## 承認

## MailChimp APIキーの取得

1.まだお持ちでない場合はMailChimpアカウントを作成します。
2.*Account* / *Extras* / *API Keys* を開き、新たに作成します。
3.作成したAPIキーをコピーします。

![MailChimp - create a API Key](/plugins/media/plugins-mailchimp-create-api-key.png "MailChimp - create a API Key")
![MailChimp - copy the API Key](/plugins/media/plugins-mailchimp-copy-api-key.png "MailChimp - copy the API Key")

### Mauticの承認 - MailChimpプラグイン

MailChimpへのログインに使用している **ユーザー名** と **APIキー** を入力してください。プラグインを保存します。

## プラグインの設定

プラグイン設定のモーダルボックスの *特長* タブに移動します。以下のメモを参照してください:

> コンタクトフィールドマッピングタブはリストを選択した後に表示され、選択されたリストを変更した後に更新されます。

![MailChimp Plugin configuration](/plugins/media/plugins-mailchimp-configure.png "MailChimp Plugin configuration")

その後、コンタクトリストを選択します。MailChimpにコンタクトリストがまだ無い場合、*MailChimp dashboard* / *Segments* / *Create List* を開き、作成します。その後、プラグインの設定を保存して再度開きます。*コンタクトフィールドマッピング*タブが表示されているはずです。[field mapping](./../plugins/field_mapping.html) を設定します。

その他の設定オプションは次のとおりです:
- **この統合にコンタクトをプッシュする** - このオプションはデフォルトでチェックされています。これをオフにすると、このプラグインはコンタクトをMailChimpにプッシュしません。
- **ダブルオプトインを有効化** - MailChimpがこのプラグインによって追加されたコンタクトへ確認メールを送信するかどうか。コンタクトが自分を本当にリストに追加するかどうかを確認する必要があります。
- **ウェルカムメールを送る** - MailChimpがウェルカムメールを送信するかどうか。

## プラグインのテスト

[これらの手順にしたがい](./../plugins/{0/}integration_test.html) 統合をテストします。
