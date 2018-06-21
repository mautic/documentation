# 初めに

素晴らしい！　マーケティング自動化ツールを手にしましたね。これは大きな第一歩です。次はどこで何をすればいいかとお悩みだと思います。とてもシンプルなこのガイドにそって真新しい玩具を遊び倒してください。

## ステップ1: Mautic をインストールする

Zipファイルを各ダウンロードページから入手するか，Softaculous，Bitmani，Digital Ocean といった他の媒体からインストールして最初のステップは終わっているかもしれませんが、ダウンロードだけされていてまだインストールされてない場合はサーバへ Mautic のパッケージファイル(zip で圧縮しています)をアップロードする必要があります。次に zip ファイルを展開し，ブラウザで zip ファイルを展開したパスや URL へアクセスしてください。Mautic のインストールプロセスはとても簡単だとおわかりいただけると思います。

## ステップ2: Cron Job を追加する

Mautic をインストールするとタスクを処理するために基本的な cron job を作る必要があります。これらの cron job は cPanel やコマンドラインから作成・追加できます。この手の作業にあまりなじみがない，得意ではない場合はフォーラムや Slack で是非相談してみてください。作成が必要な cron job を以下に列挙します。

**セグメントの更新**

`php /path/to/mautic/app/console mautic:segments:update`

**キャンペーンの更新**

`php /path/to/mautic/app/console mautic:campaigns:rebuild`

**キャンペーンアクションの実行**

`php /path/to/mautic/app/console mautic:campaigns:trigger`

この機能や他の cron job について、詳しくは [Cron Jobs](./cron_jobs.html) をご確認ください。

## ステップ 3: IP Lookup サービスのデータベースをダウンロードする

標準では Mautic は MaxMind の フリーの GeoLite2 IP lookup database を使うよう設定します。データベースのライセンスにより Mautic のインストールパッケージに含めることができません。したがって別途ダウンロードが必要となってきます。管理メニューを開くには Mautic の右上にある歯車のアイコンをクリックし、管理画面に訪問します。システム設定タブに IP Lookup サービスオプションがあります。 "IP Lookup データベースを取り込む" をクリックしてください。

また、サポートされている好みの IP Lookup サービスプロバイダーを選択することもできます。

## ステップ 4: トラッキング JavaScript をインストールする

cron job のインストールとセットアップが終わると，コンタクトを追跡する準備が整います。 Mautic で追跡したい各サイトのWebサイトにシンプルな JavaScript を追加する必要があります。とても簡単なプロセスですし，テンプレートファイルや他の CMS プラットフォームへ Mautic インテグレーションをインストールすることもできます。サンプルのトラッキング JavaScript はこのようになります:

``` <script> (function(w,d,t,u,n,a,m){w['MauticTrackingObject']=n; w[n]=w[n]||function(){(w[n].q=w[n].q||[]).push(arguments)},a=d.createElement(t), m=d.getElementsByTagName(t)[0];a.async=1;a.src=u;m.parentNode.insertBefore(a,m) })(window,document,'script','http(s)://yourmautic.com/mtc.js','mt'); mt('send', 'pageview'); </script> ``` 

上記スクリプトのサイトURL (http(s)://yourmautic.com/mtc.js をあなたのサイトのURLに置換) を変更する必要があります。

トラッキングピクセルについての詳しい内容は  [コンタクトのモニタリング](./../contacts/contact_monitoring.html) をご確認ください。
