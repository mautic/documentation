# iContactとの統合

Mauticは、いくつかのリードのアクション時またはポイントの上限に達したときにリードを[iContact](https://www.icontact.com) に送信することができます。

## 承認

MauticでiContactアカウントに接続するためには、iContactアプリを作成する必要があります。

iContact APPを作成するには次の[チュートリアル](https://www.icontact.com/developerportal/documentation/register-your-app/)に従ってください。

アプリを作成したら、この画面を見ることができるはずです:

![iContact - create a App Key](/plugins/media/plugins-icontact-authorization-details.png "iContact - create a App Key")

Mauticへ正確な認証情報を入力してください - iContact 統合:

- App ID = 作成したアップID
- App username = iContact アカウントのログインのユーザー名/メール（アプリ名ではなく）
- App password = アップを認証した時に選択したパスワード

![iContact - authoriztion](/plugins/media/plugins-icontact-authorization.png "iContact - authoriztion")

## プラグインの設定

プラグイン設定のモーダルボックスの *特長* タブに移動します。MauticリードにプッシュされるiContactリードリストを選択します。デフォルトで作成されたリストが一つあるはずです。

その他の設定オプションは次のとおりです:
- **この統合にリードをプッシュする** - このオプションはデフォルトでチェックされています。これをオフにすると、このプラグインはリードをMailchimpにプッシュしません。

## プラグインのテスト

[これらの手順にしたがい](./../plugins/integration_test.html) 統合をテストします。
