# リストを管理する

Lists provide ways to easily organize your leads. These lists can be configured from a variety of fields.

When viewing all lead lists you will notice the column on the right which shows the number of leads matching that particular list.

![](http://drop.dbh.li/image/3v3F2v280n1z/Image%202014-11-16%20at%209.32.16%20PM.png)

### List Filters

![List Filter](http://drop.dbh.li/image/3j350h370g0t/Image%202014-11-16%20at%209.13.39%20PM.png)

In addition, these filters can be combined to either be inclusive or exclusive depending on your needs.

![](http://drop.dbh.li/image/2u090o1n252V/Image%202014-11-16%20at%209.16.12%20PM.png)

Once you have selected the field you can then choose the type of operation to perform. These vary depending on the way you wish to filter your leads.

![](http://drop.dbh.li/image/3o0a32313h07/Image%202014-11-16%20at%209.26.57%20PM.png)

### Smart Lists

Once you have created your list any applicable lead will be automatically added through the execution of a cron job. This is the essence of smart lists.

To keep the smart lists current, create a cron job that executes the following command at the desired interval:

```
php /path/to/mautic/app/console mautic:leadlists:update --env=prod
```

Through the execution of that command, leads that match the filters will be added and leads that no longer match will be removed. Any leads that were manually added will remain part of the list regardless of filters.

### Manual Addition

In addition to smart lists you can also manually add any lead to a list by clicking the Lists button then selecting the radio toggle on the lead detail view.
