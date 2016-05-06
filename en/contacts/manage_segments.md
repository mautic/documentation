# Manage Segments

In Mautic 1.4, lead lists were renamed to segments.

Segments provide ways to easily organize your contacts. These segments can be configured from a variety of fields.

When viewing all segments you will notice the column on the right which shows the number of contacts matching that particular segment.

![](http://drop.dbh.li/image/3v3F2v280n1z/Image%202014-11-16%20at%209.32.16%20PM.png)

### Segment Filters

![List Filter](http://drop.dbh.li/image/3j350h370g0t/Image%202014-11-16%20at%209.13.39%20PM.png)

In addition, these filters can be combined to either be inclusive or exclusive depending on your needs.

![](http://drop.dbh.li/image/2u090o1n252V/Image%202014-11-16%20at%209.16.12%20PM.png)

Once you have selected the field you can then choose the type of operation to perform. These vary depending on the way you wish to filter your contacts.

![](http://drop.dbh.li/image/3o0a32313h07/Image%202014-11-16%20at%209.26.57%20PM.png)

### Segments

Once you have created your segment, any applicable contact will be automatically added through the execution of a cron job. This is the essence of segments.

To keep the segments current, create a cron job that executes the following command at the desired interval:

```
php /path/to/mautic/app/console mautic:segments:update --env=prod
```

Through the execution of that command, contacts that match the filters will be added and contacts that no longer match will be removed. Any contacts that were manually added will remain part of the list regardless of filters.

### Manual Addition

In addition to segments you can also manually add any contact to a list by clicking the Segments button then selecting the radio toggle on the contact detail view.
