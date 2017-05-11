# 監視対象メール
バージョン1.2.0以降、バウンスメールや購読解除リクエストを検出するためにIMAPアカウントを監視することのできる機能をMauticは提供しています。

## 監視対象の受信トレイの設定
メール監視機能を使用するには、PHPのIMAP拡張を有効化する必要があります（ほとんどの共有のホストではすでにこれがオンになっています）。Mauticの設定に移動し、監視したい受信ボックス（複数可）のアカウントの詳細を入力するだけです。

![Monitored inbox settings](/emails/media/asset-monitored-inbox-settings.png "Monitored inbox settings")

単一の受信トレイの使用、または監視対象ごとに固有の受信トレイをせってすることができます。

メッセージの取得と処理には、次のコマンドを実行します。

```
php /path/to/mautic/app/console mautic:email:fetch
```

Mauticは指定されたフォルダに見つかった各メッセージを読み取りますので、この目的のためにメールを特に作成するのが最善であることに注意してください。

Gmailでメールを送信する場合、メールのリターンパスは自動的にGmailアドレスに書き換えられます。MauticはバウンスのためにGmailアカウントを監視することができますが、Gmail以外の送信方法を使用することをおすすめします。

購読解除フォルダを選択した場合、Mauticも「List-Unsubscribe」ヘッダの一部としてメールを追加します。そのフォルダに見つかったメッセージをパースし、そのコンタクトの購読を自動的に解除します。

## バウンスメールでのコンタクトのリスト作成

これは必須ではありませんが、バウンスメールのすべてを削除する場合やバウンスメールの来たコンタクトのリストを作成する場合など、バウンスメールの来たコンタクトを簡単に選択できるようなります。

1.*コンタクト* / *リスト管理* / *新規* を開きます
2.リスト名を入力します。たとえば *バウンスメール* などです
3.*フィルタ*タブを選択します
4.新しく*バウンスメール*イコールYesフィルタを作成します
5. cronジョブにより自動的にトリガーされる `app/console mautic:segments:update` コマンドを待つか、もしくは手動で実行します

バウンスメールを持つすべてのコンタクトがこのリストに表示されます。

## Mandrillウェブフック

MauticはバウンスのためのMandrillのウェブフックをいくつかサポートしています。

1) Mandrillのアカウントにログインし、Settings -> Webhooksを開いてください

![Webhooks](/emails/media/mandrill_webhook_1.png "Mandrill webhooks")

2) Add a Webhookをクリックします

![Add Webhook](/emails/media/mandrill_webhook_2.png "Add webhook")

3) Mautic 1.2.2は次のウェブフックをサポートしています: Message is Bounced, Message is Soft-Bounced, Message is Rejected.  1.2.3では、Message is Marked as Spam と Message Recipient Unsubscribes がサポートされます。

4) `http://your-mautic.com/mailer/mandrill/callback` のように4）のようにPost To Url に入力し、Create Webhookをクリックします

5) Custom Metadataをクリックして、二つの新しいメタデータフィールド、`hashId` と `contactId` を作成します

![Add metadata](/emails/media/mandrill_webhook_5.png "Add metadata")

![Add metadata](/emails/media/mandrill_webhook_4.png "Add metadata")
