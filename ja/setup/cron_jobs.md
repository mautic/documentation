# Cron Job #

Mautic がメンテナンスタスクを制御するために [cron jobs](https://ja.wikipedia.org/wiki/Crontab) が必須となっています。ほとんどのウェブサーバでは cron を追加する方法を SSH， cPanel や他の変更画面で提供しています。cron job のセットアップについて不明な場合はご利用のウェブサーバのマニュアルやサポートへご相談ください。

cron job を実行する頻度はあなた次第です。共有サーバであれば15から30分程度ごとに実行するのが好ましいでしょう。共有サーバの制限により設定した時間が上書きされる場合があります。

**以下の cron job  の実行時間が重ならないように設定することをおすすめします。**

## 必須 ##

### リードリスト ###
**スマートリストを最新状態に保ちます:**

```
php /path/to/mautic/app/console mautic:leadlists:update
```

デフォルトではリードを300件一括処理します。サーバリソースをあまりに消費するようであれば　`--batch-limit=X` オプションを使って一度に処理させるリードの数を減らしてください。Xの部分は一度に処理させるリードの数に置き換えてください。

`--max-leads`オプションを使って実行するスクリプト毎に処理するリードの数を制限し，消費するサーバリソースを節約できます。

### キャンペーン ###
**適用するリードとともにキャンペーンを最新の状態に保ちます:**

```
php /path/to/mautic/app/console mautic:campaigns:update
```

スクリプトがバッチ処理するリードの数は300とデフォルトで設定されています。利用中のサーバリソースに対してこの数が多いようであれば `--batch-limit=X` オプションを使い，Xへ処理させるリードの数に置き換えて調整してください。

スクリプト毎に実行させるリードの数を `--max-leads` オプションで制限し，サーバリソースの消費を押させることもできます。

**To execute campaigns events:**

```
php /path/to/mautic/app/console mautic:campaigns:trigger
```

スクリプトがバッチ処理するイベントの数は100とデフォルトで設定されている。利用中のサーバリソースに対してこの数が多いようであれば `--batch-limit=X` オプションを使い，Xへ処理させるイベントの数に置き換えて調整してください。

スクリプト毎に実行させるリードの数を `--max-events` オプションで制限し，サーバリソースの消費を押させることもできます。

## オプション ##

### メールキューの処理###

ファイルシステムへメールキューを書き出しているように設定されているようであれば，処理させるには cron job が必須です。

```
php /path/to/mautic/app/console mautic:email:process
```

### 監視中のメールを取得・処理させる ###
 
[Bounce Management](./../emails/bounce_management.html) を使っている場合,  
 
```
php /path/to/mautic/app/console mautic:fetch:email
```

### Webフック

バッチ処理にウェブフックを送るよう Mautic を設定している場合，次のコマンドを使ってペイロードを送信させます。

```
php /path/to/mautic/app/console mautic:webhooks:process
```

### MaxMind GeoLite2 IP データベースを最新に保つ
 
 Mautic は [MaxMind's](http://www.maxmind.com) GeoLite2 IP データベースを標準で使用しています。データベースは (クリエイティブコモンズ 表示--継承 3.0 非移植 ライセンス)[http://creativecommons.org/licenses/by-sa/3.0/deed.ja] でライセンスされてて
 
 The database is licensed under the (Creative Commons Attribution-ShareAlike 3.0 Unported License)[http://creativecommons.org/licenses/by-sa/3.0/] and thus cannot be packaged with Mautic. The database can be downloaded manually through Mautic's Configuration or the following script can be used as a cron job to automatically download updates. (MaxMind updates their database the first Tuesday of the month).
 
```
php /path/to/mautic/app/console mautic:iplookup:download
```

## Note ##

For releases prior to 1.1.3, it is required to append ` --env=prod` to the cron job command to ensure commands execute correctly.

## Tips & Troubleshooting ##

If your environment provides a command-line specific build of php, often called `php-cli`, you may want to use that instead of `php` as it will have a cleaner output.  On BlueHost and probably some other PHP hosts, the `php` command might be setup to discard the command-line parameters to `console`, in which case you must use `php-cli` to make the cron jobs work.

To assist in troubleshooting cron issues, you can pipe the output of each cron job to a specific file by adding something like `>/path/to/somefile.log 2>&1` at the end of the cron job. Then you can look at the contents of the file to see what was printed. If an error is occurring when running run the cron job, you will see it there, otherwise the file will be empty or have some stats. The modification time of the file informs you of the last time the cron job ran. You can thus use this to figure out whether or not the cron job is running successfully and on schedule.

If you have SSH access, try to run the command directly to see if any errors are generated. If there is nothing printed from either in a SSH session or in the cron output from above, check the server's logs. If you see similar errors to `'Warning: Invalid argument supplied for foreach()' in /vendor/symfony/console/Symfony/Component/Console/Input/ArgvInput.php:287`, you either need to use `php-cli` instead of `php` or try using `php -d register_argc_argv=On`.
` 

