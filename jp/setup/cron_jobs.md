# Cron Job #

Mautic がメンテナンスタスクを制御するために [cron jobs](https://ja.wikipedia.org/wiki/Crontab) が必須となっています。ほとんどのウェブサーバでは cron を追加する方法を SSH， cPanel や他の変更画面で提供しています。cron job のセットアップについて不明な場合はご利用のウェブサーバのマニュアルやサポートへご相談ください。

cron job を実行する頻度はあなた次第です。共有サーバであれば15から30分程度ごとに実行するのが好ましいでしょう。共有サーバの制限により設定した時間が上書きされる場合があります。

**以下の cron job の実行時間が重ならないように設定することをおすすめします。**

## 必須 ##

### セグメント ###
**セグメントを最新状態に保ちます:**

```
php /path/to/mautic/app/console mautic:segments:update
```

デフォルトではコンタクトを300件一括処理します。サーバリソースをあまりに消費するようであれば `--batch-limit=X` オプションを使って一度に処理させるコンタクトの数を減らしてください。Xの部分は一度に処理させるコンタクトの数に置き換えてください。

`--max-contacts` オプションを使って実行するスクリプト毎に処理するコンタクトの数を制限し，消費するサーバリソースを節約できます。

### キャンペーン ###
**適用するコンタクトとともにキャンペーンを最新の状態に保ちます:**

```
php /path/to/mautic/app/console mautic:campaigns:rebuild
```

スクリプトがバッチ処理するコンタクトの数は300とデフォルトで設定されています。利用中のサーバリソースに対してこの数が多いようであれば `--batch-limit=X` オプションを使い，Xへ処理させるコンタクトの数に置き換えて調整してください。

スクリプト毎に実行させるコンタクトの数を `--max-contacts` オプションで制限し，サーバリソースの消費を押させることもできます。

**キャンペーンイベントの実行:**

```
php /path/to/mautic/app/console mautic:campaigns:trigger
```

スクリプトがバッチ処理するイベントの数は100とデフォルトで設定されている。利用中のサーバリソースに対してこの数が多いようであれば `--batch-limit=X` オプションを使い，Xへ処理させるイベントの数に置き換えて調整してください。

スクリプト毎に実行させるコンタクトの数を `--max-events` オプションで制限し，サーバリソースの消費を押させることもできます。

## オプション ##

### メールキューの処理###

ファイルシステムへメールキューを書き出しているように設定されているようであれば，処理させるには cron job が必須です。

```
php /path/to/mautic/app/console mautic:emails:send
```

### 監視中のメールを取得・処理させる ###

[Bounce Management](./../emails/bounce_management.html) を使っている場合,  

```
php /path/to/mautic/app/console mautic:email:fetch
```

### Webフック

バッチ処理にウェブフックを送るよう Mautic を設定している場合，次のコマンドを使ってペイロードを送信させます。

```
php /path/to/mautic/app/console mautic:webhooks:process
```

### MaxMind GeoLite2 IP データベースを最新に保つ

 Mautic は [MaxMind's](http://www.maxmind.com) GeoLite2 IP データベースを標準で使用しています。データベースは (クリエイティブコモンズ 表示--継承 3.0 非移植)[http://creativecommons.org/licenses/by-sa/3.0/deed.ja] でライセンスされており， Mautic のパッケージに同梱できません。データベースは Mautic の設定中に手動でダウンロードするか，自動で更新をダウンロードさせるために cron job で使用できる次のスクリプトを実行するかのいずれかとなっています (MaxMind のデータベース更新は毎月第一火曜日です)。


```
php /path/to/mautic/app/console mautic:iplookup:download
```

## 注意 ##

1.1.3 以前のリリースの場合 cron job コマンドを確実に実行させるために，コマンドへ `--env=prod` の追加が必須となっています。


## ティップスとトラブルシュート ##

ご利用のサーバで一般的に `php-cli` といわれるコマンドライン版 PHP が提供されているようであれば， `php` よりもよりクリーンな出力を求めるために `php-cli` を使いたくなるかもしれません。BlueHost や PHP を使える他のサーバでは `php` コマンドはコマンドラインパラメータを `コンソール` として破棄してしまっているかもしれません。この場合は cron job を動作させるよう `php-cli` を使用しなくてはなりません。

cron job に関連する諸問題において問題解決の一助となるのが，出力をパイプすることです。たとえば `>path/to/somefile.log 2>&1` のように各 cron job の末尾に追加し特定のファイルへ書き出すことです。これによりファイルの中に何が出力されているかを確認することができます。cron job の実行中にエラーが起こっているようであればその内容をファイル読むことで確認できます。エラーがない場合はファイルの中身は空白か他のステータスが残っているはずです。ファイルの最終更新時刻は最後に cron job が実行された時間です。これにより，cron job がスケジュール通りに正しく実行されたのかそうでないかを推測することができます。

 SSH アクセスが可能であれば，なにかしらエラーが起こっていないかを直接確認するコマンドを試してみてください。 SSH セッションのもの以外がなかったり，cron の出力が上で説明した通りだったりする場合，サーバのログを確認してみてください。次とよく似たエラーを確認ことができます: `'Warning: Invalid argument supplied for foreach()' in /vendor/symfony/console/Symfony/Component/Console/Input/ArgvInput.php:287` この場合は `php` ではなく `php-cli` か `php -d register_argc_argv=On` を使う必要があります。
