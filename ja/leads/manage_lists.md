# リストを管理する

リストはリードの管理を簡単にします。リストはさまざまなフィールドを用いて設定が可能です。

すべてのリストを表示する際，右側のカラムに注意してください。このカラムはリードの各項目に対応しているリード数を表示しています。

When viewing all lead lists you will notice the column on the right which shows the number of leads matching that particular list.

![](http://drop.dbh.li/image/3v3F2v280n1z/Image%202014-11-16%20at%209.32.16%20PM.png)

### リストフィルター

![List Filter](http://drop.dbh.li/image/3j350h370g0t/Image%202014-11-16%20at%209.13.39%20PM.png)

加えて，これらのフィルタは必要に応じて包括的または排他的に組み合わせる事ができます。

![](http://drop.dbh.li/image/2u090o1n252V/Image%202014-11-16%20at%209.16.12%20PM.png)

最初にフィールドを選択することで次にどのような操作を行うかを選択する事ができます。リードをフィルタリングするための方法によって異なります。

![](http://drop.dbh.li/image/3o0a32313h07/Image%202014-11-16%20at%209.26.57%20PM.png)

### スマートリスト
リストを作成することで任意の適用可能なリードが自動的に cron job の実行により追加されます。これは、スマートリストのがスマートリストたる所以です。

スマートリストを常に最新の状態に保つには，任意の間隔で次のコマンドを実行できるよう cron job を作成ししてください。
```
php /path/to/mautic/app/console mautic:leadlists:update --env=prod
```

Through the execution of that command, leads that match the filters will be added and leads that no longer match will be removed. Any leads that were manually added will remain part of the list regardless of filters.

### Manual Addition

In addition to smart lists you can also manually add any lead to a list by clicking the Lists button then selecting the radio toggle on the lead detail view.
