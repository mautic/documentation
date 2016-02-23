# 初めに

素晴らしい！　マーケティング自動化ツールを手にしましたね。これは大きな第一歩です。次はどこで何をすればいいかとお悩みだと思います。とてもシンプルなこのガイドにそって真新しい玩具を遊び倒してください。

## ステップ　1: Mautic をインストールする

すでにZipファイルを各ダウンロードページやから入手されているか，Softaculous，Bitmani，Digital Ocean といった他の媒体からインストールされて最初のステップをクリアされたかもしれません。ダウンロードだけされていてまだインストールされてない場合はサーバへ Mautic のパッケージファイル(zip で圧縮しています)をアップロードする必要があります。次に zip ファイルを展開し，ブラウザで zip ファイルを展開したパスや URL へアクセスしてください。Mautic のインストールプロセスはとても簡単だとおわかりいただけると思います。

## ステップ 2: Cron Jobを追加する

Once you've installed Mautic you will need to create a few standard cron jobs to have your software process various tasks. These cron jobs can be created through a cPanel or added through command line. If you are unfamiliar or uncomfortable with this step then we'd recommend asking in the forums or in the live Slack chat. Here is a list of the cron jobs you'll need to create.

**Updating Lead Lists**

`php /path/to/mautic/app/console mautic:leadlists:update`

**Update Campaigns**

`php /path/to/mautic/app/console mautic:campaigns:update`

**Execute Campaign Actions**

`php /path/to/mautic/app/console mautic:campaigns:trigger`

Review [Cron Jobs](./setup) for more information on these and other optional cron jobs.

## Step 3: Download the IP lookup service database

By default, Mautic installs set to use MaxMind's free GeoLite2 IP lookup database. Due to the licensing of the database, it cannot be included with Mautic's installation package and thus must be downloaded. Click on the cogwheel in the upper right hand of Mautic to view the Admin menu then click Configuration. On the System Settings tab, find the IP lookup service option and click the "Fetch IP Lookup Data Store."

You could also choose another supported IP lookup service if you prefer.

## Step 4: Install the Tracking Pixel

After installation and setup of the cron jobs you're ready to begin tracking leads. You will need to add a single tracking pixel to the websites for each site you wish to track via Mautic. This is a very simple process and you can add this tracking pixel to your website template file, or install a Mautic integration for the more common CMS platforms. Here is an example of the tracking pixel:

`<img src="http://yourdomain.com/path/to/mautic/mtracking.gif" />`

Checkout [Lead Monitoring](./leads/lead_monitoring.html) for more details on the tracking pixel.