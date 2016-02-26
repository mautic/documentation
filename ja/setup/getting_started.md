# 初めに

素晴らしい！　マーケティング自動化ツールを手にしましたね。これは大きな第一歩です。次はどこで何をすればいいかとお悩みだと思います。とてもシンプルなこのガイドにそって真新しい玩具を遊び倒してください。

## ステップ　1: Mautic をインストールする

すでにZipファイルを各ダウンロードページやから入手されているか，Softaculous，Bitmani，Digital Ocean といった他の媒体からインストールされて最初のステップをクリアされたかもしれません。ダウンロードだけされていてまだインストールされてない場合はサーバへ Mautic のパッケージファイル(zip で圧縮しています)をアップロードする必要があります。次に zip ファイルを展開し，ブラウザで zip ファイルを展開したパスや URL へアクセスしてください。Mautic のインストールプロセスはとても簡単だとおわかりいただけると思います。

## ステップ 2: Cron Jobを追加する

Mautic をインストールするとタスクを処理するために基本的な cron job を作る必要があります。これらの cron job は cPanel やコマンドラインから作成・追加できます。この手の作業にあまりなじみがない，得意ではない場合はフォーラムや Slack で是非相談してみてください。作成が必要な cron job を以下に列挙します。

**リードリストの更新**

`php /path/to/mautic/app/console mautic:leadlists:update`

**キャンペーンの更新**

`php /path/to/mautic/app/console mautic:campaigns:update`

**キャンペーンアクションの実行**

`php /path/to/mautic/app/console mautic:campaigns:trigger`

詳しくは [Cron Jobs](./setup) を確認してfor more information on these and other optional cron jobs.

## Step 3: Download the IP lookup service database

By default, Mautic installs set to use MaxMind's free GeoLite2 IP lookup database. Due to the licensing of the database, it cannot be included with Mautic's installation package and thus must be downloaded. Click on the cogwheel in the upper right hand of Mautic to view the Admin menu then click Configuration. On the System Settings tab, find the IP lookup service option and click the "Fetch IP Lookup Data Store."

You could also choose another supported IP lookup service if you prefer.

## Step 4: Install the Tracking Pixel

After installation and setup of the cron jobs you're ready to begin tracking leads. You will need to add a single tracking pixel to the websites for each site you wish to track via Mautic. This is a very simple process and you can add this tracking pixel to your website template file, or install a Mautic integration for the more common CMS platforms. Here is an example of the tracking pixel:

`<img src="http://yourdomain.com/path/to/mautic/mtracking.gif" />`

Checkout [Lead Monitoring](./leads/lead_monitoring.html) for more details on the tracking pixel.