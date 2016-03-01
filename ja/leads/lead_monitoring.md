# リードの監視
リード似ついての活動状況やトラフィックをモニターする行為は多少テクニカルで苛々するときがあります。 Mautic はこのモニタリングをシンプルにそして簡単に設定できます。

### ウェブサイト監視
ウェブサイトへのトラフィックすべてをモニタリングするにはトラッキングピクセルを追加するだけ十分です。 Mautic へログイン済みのユーザについてのトラフィックはモニタリングできないため，トラフィックの記録をとるという事は重要な事です。トラッキングピクセルが動作しているかどうかは incognito や プレイべーとブラウジングウィンドウ，または Mautic からログアウトして確認してみてください。

```
http://yourdomain.com/mtracking.gif
```

### ピクセルクェリをトラッキングする
トラッキングピクセルを最大限に活用するには画像の URL を介してウェブリクエストの情報を渡す事をおすすめします。

#### ページ情報
Mautic は `page_url`，`referrer`，`lnaguage`と`page_tititle`をサポートしています(`url`と`title`の同時使用はリードフィールド上でコンフリクトを起こすためおすすめしません)。


#### UTM コード

バージョン1.2.1からリードタイムライン上で UTM コードのサポートが開始されました。`utm_medium`，`utm_source`，そして`utm_campaign`はタイムラインエントリーのコンテンツを生成するために使用されます。

`utm_campaign`はタイムラインエントリーのタイトルとして使用されます。。

`utm_medium`の値は Font Awesome Class に従います:
 
<table>
<thead>
<tr>
    <th>値</th>
    <th>クラス</th>
</tr>
</thead>
<tbody>
   <tr><td>ソーシャル，ソーシャルメディア</td><td>fa-share-alt if <code>utm_source</code> is not available otherwise <code>utm_source</code> will be used as the class. For example, if <code>utm_source</code> is Twitter, fa-twitter will be used.</td></tr>
   <tr><td>Eメール，ニュースレター</td><td>fa-envelope-o</td></tr>
   <tr><td>バナー，広告</td><td>fa-bullseye</td></tr>
   <tr><td>CPC</td><td>fa-money</td></tr>
   <tr><td>ロケーション</td><td>fa-map-marker</td></tr>
   <tr><td>デバイス</td><td>fa-tablet if <code>utm_source</code> is not available otherwise <code>utm_source</code> will be used as the class. For example, if <code>utm_source</code> is Mobile, fa-mobile will be used.</td></tr>   
</tbody>
</table>

#### リードフィールド
Mautic のリードフィールドを誰にでも更新可能な状態にする事でリードに対し特定の情報を流す事ができます。トラッキングピクセルの URL に含まれる値はエンコードされていなくてはなりません(スペースは%20へ，@は%40など)。

#### タグ
リードのタグはクエリーパラメータの`tags`を使うことで変更ができます。コンマを使って複数のタグを区切れます。タグを削除するにはタグの前にハイフン(マイナス記号)を付けてください。

たとえば`mtracking.gif?tags=ProductA,-ProductB` というタグはリードに対してプロダクトAを追加し，プロダクトBを削除することになります。

### ピクセルの埋め込み
なにかしらの CMS を使っているのであれば我々のプラグインを使ってピクセルを埋め込むのが一番簡単です(以下参照)。プラグインはすべてのリードのフィールド，UTM コードやリードタグをサポートしているわけでは無い点にご注意ください。

以下に示すコードコードスニペットが役に立つと思います:

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

#### 提供中のプラグイン
Mauticは，多くの既存の CMS へキーインテグレーションを提供することにより，リードのモニタリングがさらに簡単になります。ウェブサイトへトラッキングピクセルを自動的に追加するには，次のプラグインのいずれかをダウンロードし使用してください。

* [Joomla!](http://mautic.org/integration/joomla)
* [Drupal](http://mautic.org/integration/drupal)
* [WordPress](http://mautic.org/integration/wordpress)
* [Typo3](http://mautic.org/integration/typo3)
* [Concrete5](http://mautic.org/integration/concrete5)

Mautic コミュニティで作成されたほんの一部です。将来にはもっと追加されるでしょうし，デベロッパに自身のインテグレーションを登録するよう働き掛けています。

**注意:** ウェブページのトラッキングのためにプラグインを使ったりトラッキングピクセルをHTMLページに直接埋め込んだりする事でなんら制限を受ける事はありません。

### モバイルモニタリング
アプリ上での出来事をモニタリングすることとウェブサイトでの出来事をモニタリングすることは本質的によく似ています。 Mautic はプラットフォームに関係なくネイティブ(もしくは擬似ネイティブ)なアプリと HTML5 ラッパーベースのアプリのために必要なビルディングブロックが含まれています。

すなわち，アプリ上で指定されたスクリーンビュー(例: main_screen) を page_url フィールドとしてトラッカー上で使用したり，リードのメールアドレスをユニークな識別子として使ったりする事ができます。詳しくは次のセクションをご参照ください。


####  Mautic でのステップ

1. メールフィールドを誰でも編集可能な状態にしてください。こうすることでトラッキング Gif 画像をさまざまなメールアドレスから呼び出すことができ，Mautic がトラッキング Gif 画像を正しく認識させる事になります。

2. フォームをセットアップしてください。このフォームはキャンペーンへアクセスするポイントになります(例: 新規リードのメールアドレス)。フォームはできるだけシンプルに，またはアプリから POST する事がでるように，してください。POST ができる典型的なフォームの URL はこのようなものです: 

```
http://your_mautic/form/submit?formId=<form_id>
```

You can get the ID from the mautic URL as you view / edit the form in the Mautic interface (or in the forms tables, last column), and you can get the form fields by looking at the HTML of the 'Manual Copy' of the HTML in the forms editing page.


3. Define in your campaigns the screens you want to use as triggers (e.g. 'cart_screen' etc.). Mautic is not looking for a real URL in the form 'http://<url>' for page_url, any typical string would do. Like this:

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

#### In your App

A best-in-class approach is to have a class (say 'mautic') that handles all your tracking needs. For example, this sample method call would POST to the form with ID 3 - see previous section (note: for conciseness and ubiquity, these sample lines are written in JavaScript / ECMAScript-type language, use similar call in your mobile App language of choice).

```
mautic.addLead("myemail@somehwere.com",3)
```

And then, to track individual user activity in the App, this sample call would make an HTTP request to the tracker:

```
mautic.track("cart_screen", "myemail@somewhere.com")
```

Which is nothing more than an HTTP request to this GET-formatted URL (as also shown in previous section):

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

Important: Make sure in your App, that the above HTTP request is using a cookie (if possible, re-use the cookie from the mautic.addLead POST request prior) AND that you reuse this cookie from one request to the next. This how Mautic (and other tracking software) knows that it's really the same user. If you can't do this, you may run in the (unlikely but possible) case where you have multiple leads from the same IP address and Mautic will merge them all into a single lead as it can't tell who is who without a cookie.

### Other Online Monitoring

There are several other ways to monitor lead activity and attach points to those activities. Website monitoring is only one way to track leads. Other lead monitoring activities can consist of forum posts, chat room messages, mailing list discussion posts, GitHub/Bitbucket messages, code submissions, social media posts, and a myriad of other options.

### Troubleshooting

If the tracking doesn't work, take a look at [Page troubleshooting](pages/troubleshooting.html) or [Email troubleshooting](emails/troubleshooting.html)
