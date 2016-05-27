# リードのモニター
リードのトラフィックやアクティビティのモニターは、時には技術的で理解するのにてこずることがあります。Mauticはこのモニタリングを簡単、容易に設定できます。

### ウェブサイトモニタリング

ウェブサイトにひとつのトラッキングピクセルを追加することによってウェブサイト上のすべてのトラフィックを監視することができます。ログインしているMauticユーザーからのトラフィックはモニターされませんので、ご注意ください。ピクセルが作動していることを確認するには、ブラウザのシークレットウインドウまたはプライベートウィンドウを使用するか、単にテスト前にMauticからログアウトしてください。

```
http://yourdomain.com/mtracking.gif
```

### トラッキングピクセルクエリー

トラッキングピクセルを最大限に活用するために、画像のURLを通じてウェブリクエストの情報を渡すことをお勧めします。

#### ページの情報

Mauticはいまのところ `page_url`, `referrer`, `language`, そして `page_title`をサポートしています。 ( `url` と `title` はリードフィールドとのコンフリクトのため廃止予定ですのでご注意ください。)

#### UTMコード

リードタイムラインでのUTMコードのサポートはバージョン1.2.1で導入されました。 `utm_medium`、` utm_source`、および `utm_campaign`はタイムラインのエントリの内容を生成するために使用されます。

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

#### リードフィールド

また、Mauticのリードがパブリックに更新可能なように設定しておけばリードに特定の情報を渡すことができます。トラッキングピクセルへの値の追加はURLエンコード(%20 がスペース、 %40 が @ など)になりますのでご注意ください。

#### タグ

リードのタグは `tags` クエリパラメータを使用して変更することができます。複数のタグはカンマで区切ってください。タグを削除するには、ダッシュ（マイナス記号）を前に付けます。

たとえば、 `mtracking.gif?tags=ProductA,-ProductB` はリードにProductAタグを追加して、ProductBを取り除くことになります。

### ピクセルの埋め込み

CMSを使用している場合、最も簡単な方法はプラグインのどれかを利用することです。プラグインは、リードフィールド、UTMコード、もしくはリードタグのすべてをサポートしていない可能性もあるのでご注意ください。

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

#### 使用可能なプラグイン

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

簡単に言うと、トラッカーのpage_urlフィールドとしてアプリ内の名前付けしたスクリーンビュー(例えば、main_screen)と一意の識別子としてリードのメールアドレスを使います。詳細は次のインストラクションを御覧ください。


#### Mauticでのステップ

1.メールフィールドをパブリックに編集できるようにします。これにより可変のメールをともなったトラッキングGIFへの呼び出しがMauticによって正常に認識されます。

2.フォームをセットアップします。これがキャンペーンのアクセスポイントになります（例えば新しいリードへのメール）。このフォームはアプリからPOSTするので、出来る限りシンプルにします。 POSTする一般的なフォームのURLは次のようになります

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

重要: 上記のHTTPリクエストがcookie(可能なら、mautic.addContact POSTリクエストからのcookieを再利用)を使用していること、そしてこのcookieを一つのリクエストから次のリクエストまで再利用しているをアプリ内で確認してください。これにより、それが本当に同一のユーザーであることをMautic(と、その他のトラッキングソフトウェアでも)が認識できます。これを行うことができない場合、同じIPアドレスから複数のリードがアクセスしたらMauticはcookieなしでは誰がどのリードなのか判別ができないので単一のリードに統合してしまうことがあります(めったにはないでしょうが、可能性はあります)。

### その他のオンラインモニタリング

リードのアクティビティをモニターし、それらのアクティビティにポイントを付与する方法は他にもいくつかあります。ウェブサイトのモニターはリードを追跡するための一つの方法にすぎません。リードのその他のアクティビティモニターは、フォーラムの投稿、チャットルームでのメッセージ、メーリングリストのディスカッションの投稿、GitHub/Bitbucketでのメッセージ、コードの提案、ソーシャルメディアの投稿、およびその他の無数のオプションで構成することができます。

### トラブルシューティング

トラッキングが機能しない場合は [トラブルシューティングのページ](./../pages/troubleshooting.html) もしくは [メールのトラブルシューティング](./../emails/troubleshooting.html)を御覧ください。
