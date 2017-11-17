# コンタクトのモニタリング

コンタクトのトラフィックやアクティビティのモニターは、時には技術的で理解するのにてこずることがあります。Mauticはこのモニタリングを簡単、容易に設定できます。

## ウェブサイトモニタリング

ウェブサイトにJavaScriptファイル(Mautic 1.4以降)を読み込むか、もしくはトラッキングピクセルを追加することによってウェブサイト上のすべてのトラフィックを監視することができます。ログインしているMauticユーザーからのトラフィックはモニターされませんので、ご注意ください。JavaScript/ピクセルが作動していることを確認するには、ブラウザのシークレットウインドウまたはプライベートウィンドウを使用するか、単にテスト前にMauticからログアウトしてください。

### Javascript (JS) トラッキング

JSトラッキングメソッドはMautic 1.4から実装され、ウェブサイトトラッキングとして主要な方法として推奨しています。これを利用するには*Mautic設定* > *ランディングページ設定* にあるあなたのMauticインスタンス用のJSトラッキングコードをトラッキングしたいウェブサイトの `<body/>` の前に挿入します。もしくは以下のコードをコピーし、URLをご自分のMauticインスタンスのものに変更します。

```
<script>
    (function(w,d,t,u,n,a,m){w['MauticTrackingObject']=n;
        w[n]=w[n]||function(){(w[n].q=w[n].q||[]).push(arguments)},a=d.createElement(t),
        m=d.getElementsByTagName(t)[0];a.async=1;a.src=u;m.parentNode.insertBefore(a,m)
    })(window,document,'script','http(s)://yourmautic.com/mtc.js','mt');

    mt('send', 'pageview');
</script>
```

_Mauticで利用するスキームに応じてhttpもしくはhttpsどちらかのスキーム(http(s))への変更を忘れないようにしてください。また、 [yourmautic.com] をご利用のドメインに変更してください。_

JSトラッキングの利点は、読み込みに長い時間がかかるかもしれないトラッキングのリクエストを非同期で読み込めることで、これによりトラッキングしているウェブサイトの速度低下を招きません。JSはまた、より多くの情報を自動的にトラッキングできます:

- **ページタイトル** は`</title>`タグの間のテキストです。
- **ページの言語** はブラウザで指定されている言語です。
- **ページリファラー** はそのコンタクトがどのウェブサイトから来たのか、そのウェブサイトのURLです。
- **ページURL** カレントウェブサイトのURLです。

#### カスタムパラメータのトラッキング

トラッキングピクセルクエリーは、カスタムなパラメータを付加したり、可能なページビューアクションの自動生成されたパラメータを上書きしたりできます。これを行うには、上のJSコードの最後の行を次のようにしてください:

```
    mt('send', 'pageview', {"email": "my@email.com", "firstname": "John"});

```
このコードにより、自動化されたすべてのデータをMauticに送り、メールとファーストネームを追加します。これらのフィールドの値はシステムによって生成される必要があります。

#### ロードイベント

JSトラッキングリクエストは通常は非同期で読み込まれますが、リクエストが読み込まれた時に JS を読み込むことも出来ます。その場合は、 onload 関数をオプションに下記のように入れて下さい。

```
    mt('send', 'pageview', {"email": "my@email.com", "firstname": "John"}, {onload: function() { alert("Tracking request is loaded"); }});

```

#### フィンガープリント (ベータ機能)

Mautic 1.4.0ではフィンガープリントと呼ばれるトラッキング機能が追加されました。これは[Fingerprint2](https://github.com/Valve/fingerprintjs2) を利用しています。現行のIPアドレスとcookie IDのようなトラッキング識別子と一緒に、もしくはこれを置き換えて動作します。このメソッドはまだシステムに深く組み込まれているわけではありませんが、コンタクト詳細のページヒットイベントのタイムラインですでに多くの情報を参照することができます:

- **Fingerprint** - ブラウザの設定と他の環境変数から算出される一意のハッシュ。
- **Resolution** - デバイス表示解像度の幅と高さ。
- **Timezone Offset** - UTCからのプラスもしくはマイナスの時差。
- **Platform** - デバイスのプラットフォーム。通常はOSとプロセッサーの種類。
- **Adblock** - コンタクトが広告ブロックのプラグインをブラウザで使用しているか否かの真偽値。
- **Do Not Track** - DNTがオンになっているか否かの真偽値。

これらの値をコンタクト詳細フィールドに保存したい場合、上記リストと同じ毎小のカスタムフィールドを新規に作成し、そのフィールドを公開更新可能にします。また、このフィンガープリントフィールドを一意にして、将来のフィンガープリントトラッキングをシミュレートすることも可能です。この機能はテストされていないので、本番環境では最初にテストしてから使用するようにしてください。

### トラッキングピクセルでのトラッキング

この機能はMautic 1.4からは非推奨になり、Mautic 2.0では削除されます。

```
http://yourdomain.com/mtracking.gif
```

#### トラッキングピクセルクエリー

トラッキングピクセルを最大限に活用するために、画像のURLを通じてウェブリクエストの情報を渡すことをお勧めします。

#### ページの情報

Mauticはいまのところ `page_url`, `referrer`, `language`, そして `page_title`をサポートしています。 ( `url` と `title` はコンタクトフィールドとのコンフリクトのため廃止予定ですのでご注意ください。)

### UTMコード

コンタクトタイムラインでのUTMコードのサポートはバージョン1.2.1で導入されました。 `utm_medium`、` utm_source`、および `utm_campaign`はタイムラインのエントリの内容を生成するために使用されます。

`utm_campaign`はタイムラインエントリのタイトルとして使用されます。

`utm_medium`の値は次のFont Awesome クラスにマップされます。

<table>
<thead>
<tr>
    <th>値</th>
    <th>クラス</th>
</tr>
</thead>
<tbody>
   <tr><td>ソーシャル、ソーシャルメディア</td><td>fa-share-alt  <code>utm_source</code> は利用できなければ <code>utm_source</code> がクラスとして利用されます。例えば <code>utm_source</code> がTwitterなら、 fa-twitter が利用されます。</td></tr>
   <tr><td>メール、ニュースレター</td><td>fa-envelope-o</td></tr>
   <tr><td>バナー、広告</td><td>fa-bullseye</td></tr>
   <tr><td>cpc</td><td>fa-money</td></tr>
   <tr><td>ロケーション</td><td>fa-map-marker</td></tr>
   <tr><td>デバイス</td><td>fa-tablet <code>utm_source</code> が利用できなければ <code>utm_source</code> がクラスとして利用されます。例えば <code>utm_source</code> がモバイルなら、fa-mobile が利用されます。</td></tr>   
</tbody>
</table>

#### ピクセルの埋め込み

CMSを使用している場合、最も簡単な方法はプラグインのどれかを利用することです。プラグインは、コンタクトフィールド、UTMコード、もしくはコンタクトタグのすべてをサポートしていない可能性もあるのでご注意ください。

例としていくつかのコードをご紹介します:

HTML

```
<img src="http://yourdomain.com/mtracking.gif?page_url=http%3a%2f%2fyourdomain.com%2fyour-product-page&page_title=Some%20Cool%20Product&email=user%40theirdomain.com&tags=ProductA,-ProductB" style="display: none;"  alt="mautic is open source marketing automation" />
```

PHP

```
$d = urlencode(base64_encode(serialize(array(
    'page_url'   => 'http://' . $_SERVER[HTTP_HOST] . $_SERVER['REQUEST_URI'],
    'page_title' => $pageTitle,    // Use your website's means of retrieving the title or manually insert it
    'email' => $loggedInUsersEmail // Use your website's means of user management to retrieve the email
))));

echo '<img src="http://your-mautic.com/mtracking.gif?d=' . $d . '" style="display: none;" />';
```

Javascript

```
<script>
var mauticUrl = 'http://your-mautic.com';
var src = mauticUrl + '/mtracking.gif?page_url=' + encodeURIComponent(window.location.href) + '&page_title=' + encodeURIComponent(document.title);
var img = document.createElement('img');
img.style.width  = '1px';
img.style.height  = '1px';
img.style.display = 'none';
img.src = src;
var body = document.getElementsByTagName('body')[0];
body.appendChild(img);
</script>
```

### コンタクトフィールド

Mauticのコンタクトフィールドを公開更新可能に設定すると、特定の情報をコンタクトに渡すことができます。トラッキングピクセルに付加する値はURLエンコード(スペースは%20、@は%40など)しておく必要があります。

### タグ

コンタクトのタグは`tags`クエリーパラメータを利用して変更することができます。タグが複数ある場合はコンマで区切ります。タグを取り除くにはダッシュ(マイナスマーク)を前に付けます。

例えば、`mtracking.gif?tags=ProductA,-ProductB` はコンタクトにProductAタグを追加し、ProductBを取り除きます。

### 使用可能なプラグイン

Mauticでは多くの既存のコンテンツ管理システムにキーの統合を提供することで、これをさらに容易にしています。ダウンロードして次のプラグインのいずれかを使用することにより、ウェブサイトにこのトラッキングピクセルを自動的に追加します。

* [Joomla!](http://mautic.org/integration/joomla)
* [Drupal](http://mautic.org/integration/drupal)
* [WordPress](http://mautic.org/integration/wordpress)
* [Typo3](http://mautic.org/integration/typo3)
* [Concrete5](http://mautic.org/integration/concrete5)

これらはすでにMauticコミュニティによって作成されている統合のほんの一部です。将来的にはさらに追加されでしょう。また、開発者は自分の統合を提案するようおすすます。

**注:** ウェブサイトのトラッキングはこれらのプラグインによって限定されるものではなく、任意のHTMLページ上で直接トラッキングピクセルを置くことができることに留意してください。

### モバイルモニター

アプリで発生していることのモニターは本質的には、ウェブサイト上で発生していることのモニターに似ています。Mauticには、プラットフォームに関係なく、ネイティブな（または擬似ネイティブ）とHTML5ラッパーベースのアプリのために必要なビルディング・ブロックが含まれています。

簡単に言うと、トラッカーのpage_urlフィールドとしてアプリ内の名前付けしたスクリーンビュー(例えば、main_screen)と一意の識別子としてコンタクトのメールアドレスを使います。詳細は次のインストラクションを御覧ください。


#### Mauticでのステップ

1.メールフィールドをパブリックに編集できるようにします。これにより可変のメールをともなったトラッキングGIFへの呼び出しがMauticによって正常に認識されます。

2.フォームをセットアップします。これがキャンペーンのアクセスポイントになります（例えば新しいコンタクトへのメール）。このフォームはアプリからPOSTするので、出来る限りシンプルにします。 POSTする一般的なフォームのURLは次のようになります

```
http://your_mautic/form/submit?formId=<form_id>
```

Mauticインターフェイス内(もしくはフォームテーブルの最後のカラム)のフォームを閲覧 / 編集することによりMauticのURLからIDを収得することができ、フォーム編集ページ内のHTMLの「手動コピー」のHTMLを見ることによりフォームフィールドを取得することができます。


3.キャンペーンでトリガーとして使用する画面を設定します（例えば、「cart_screen」など）。Mauticはpage_urlのためには 'http://<url>' 形式の実際のURLは探しません。通常の文字列を探します。例えば:

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

#### アプリ内では

一番いいアプローチは、すべてのトラッキングニーズを処理するクラス（例えば 'mautic'）を持たせることです。たとえば、次のサンプルのメソッド呼び出しはID 3でフォームにPOSTします - 前節を御覧ください（注意: 簡潔性と普遍性のため、これらのサンプルはJavaScript / ECMAScriptタイプの言語で書かれています。アプリではお使いの言語で似たような呼び出しを使用してください。

```
mautic.addContact("myemail@somehwere.com",3)
```

そして、アプリ内の個々のユーザアクティビティを追跡するため、このサンプルコールではトラッカーへのHTTP要求を行っています:

```
mautic.track("cart_screen", "myemail@somewhere.com")
```

これは（前のセクションで示したように）GET形式URLへのHTTPリクエスト以外の何ものでもありません。

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

重要: 上記のHTTPリクエストがcookie(可能なら、mautic.addcontact POSTリクエストからのcookieを再利用)を使用していること、そしてこのcookieを一つのリクエストから次のリクエストまで再利用しているをアプリ内で確認してください。これにより、それが本当に同一のユーザーであることをMautic(と、その他のトラッキングソフトウェアでも)が認識できます。これを行うことができない場合、同じIPアドレスから複数のコンタクトがアクセスしたらMauticはcookieなしでは誰がどのコンタクトなのか判別ができないので単一のコンタクトに統合してしまうことがあります(めったにはないでしょうが、可能性はあります)。

### その他のオンラインモニタリング

コンタクトのアクティビティをモニターし、それらのアクティビティにポイントを付与する方法は他にもいくつかあります。ウェブサイトのモニターはコンタクトを追跡するための一つの方法にすぎません。コンタクトのその他のアクティビティモニターは、フォーラムの投稿、チャットルームでのメッセージ、メーリングリストのディスカッションの投稿、GitHub/Bitbucketでのメッセージ、コードの提案、ソーシャルメディアの投稿、およびその他の無数のオプションで構成することができます。

### トラブルシューティング

トラッキングが機能しない場合は [トラブルシューティングのページ](./../pages/troubleshooting.html) もしくは [メールのトラブルシューティング](./../emails/troubleshooting.html)を御覧ください。
