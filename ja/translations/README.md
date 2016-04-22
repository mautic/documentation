# 翻訳

Mauticは世界中のコミュニティによって使用されていて、どんな言語にもローカライズすることができます。ご自分の言語が見つからない場合は、Mauticを翻訳する方法についてのセクションを見てみましょう。

## Mauticで言語を選択する方法

言語は2箇所で選択することができます。

### 1. デフォルト言語

Mautic設定でデフォルトの言語を設定することができます。デフォルトでは `English - United States` に予め設定されています。ご自分のプロフィールでご自分の言語を設定していない場合はすべてのユーザーでこの言語で表示されます。

1. 右上にあるの歯車アイコンをクリックして右の管理メニューを開きます。
2. *設定*メニュー項目を選択します。
3.デフォルトの言語を選択します。
4. 設定を保存します。

![Select the default language](/translations/media/translations-select-language.png "Select the default language")

### 2.ユーザー言語

ユーザーは自分の言語を設定し、デフォルトの言語設定をオーバーライドすることができます。これにより、同じMauticインスタンス上で複数言語のチームで作業できます。

1.右上のユーザー名をクリックしてユーザメニューを開きます。
2.*アカウント*メニュー項目をクリックしてください。
3.ユーザーの言語を選択します。
4.ユーザープロファイルを保存します。

![Select the user language](/translations/media/translations-select-user-language.png "Select the user language")

## Mauticの翻訳方法

Mauticはどんな言語にでも翻訳することができます。Mauticはコミュニティプロジェクトなので、コミュニティメンバーならだれでも任意の言語に翻訳することができます。翻訳は [Transifex](https://www.transifex.com/mautic/mautic/) ウェブアプリで行われています。

1.まだお持ちでなければ [Transifex](https://www.transifex.com/mautic/mautic/) でアカウントを作成します。
2.すでにプロジェクトが作成されていないかどうか[言語リスト](https://www.transifex.com/mautic/mautic/) を見てみましょう。
3.お使いの言語がなければその言語を作成するか、もしくは既存の言語を適用します。

翻訳プロセスについての疑問があれば、公式の [Transifex Documentation](http://docs.transifex.com/tutorials/txeditor/) を見てみましょう。

## 言語の更新方法

言語がダウンロードされていなければ、設定が保存されるたびに言語が自動的にダウンロードされます。トリッキーですが、すでにダウンロードされている場合はMauticはその言語をダウンロードしないということです。そのため、言語を更新するには:

1.SFTPやSSHでMauticファイルシステムを開きます。
2.Mauticルートフォルダに *translasions* というフォルダがあるはずです。それを開きます。
3.*translations*フォルダに言語が格納されています。更新したい言語のフォルダを削除します。
4.Mauticの設定画面を開き、削除した言語で保存します。

言語が最新の翻訳で再度ダウンロードされるはずです。翻訳はTransifexから一日一回の割合で生成されています。

翻訳について質問がある場合は [Slack #Translations channel](https://www.mautic.org/slack/) に参加してみてください。
