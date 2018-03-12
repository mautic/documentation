Manage Segments
===============

Lead lists were renamed to segments in Mautic 1.4.0.

Segments provide ways to easily organize your contacts. These segments can be
configured from a variety of fields.

When viewing all segments you will notice the column on the right which shows
the number of contacts matching that particular segment.

![](/contacts/media/contact-segments.jpg)

### Segment Filters

![](/contacts/media/segment-filters.jpg)

In addition, these filters can be combined to either be inclusive or exclusive
depending on your needs.

![](/contacts/media/multiple-segment-filters.jpg)

Once you have selected the field you can then choose the type of operation to
perform. These vary depending on the way you wish to filter your contacts.

![](/contacts/media/segment-filters-dropdown.jpg)

If you want to divide your segment based on certain criterion, and you wish to
avoid sending duplicate emails to the (sub)segments, you can view and alter them
through typing the alias name of the contact segments separated by '+' only. You
can add n contact segments to have their common, but you will always recieve the
result as the intersection of the subsets. You can then manipulate the contacts to remove them from either one subset or all, hence avoiding duplicate emails to the same leads in the subsets.

![](/contacts/media/common-leads-in-segments.jpg)

#### Date options

Date filters allow you to choose a date via DatePicker:

![](/contacts/media/segment-filters-datepicker.png)

Hovewer you can specify much more here. Mautic recognizes relative formats too (these string are not transatable):

* `+1 day` (you can use `1 day` too)
* `-2 days` (you can use `2 days ago` too)
* `+1 week` / `-2 weeks` / `3 weeks ago`
* `+5 months` / `-6 months` / `7months ago`
* `+1 year` / `-2 years` / `3 years ago`

Example (Consider that today is `2018-03-02`):
* `Date identified equals -1 week` returns all contacts identified on 2018-02-23.
* `Date identified less than -1 week` returns all contacts identified before 2018-02-23.
* `Date identified equals -1 months` returns all contacts identified on 2018-02-02.
* `Date identified greater or equal -1 year` returns all contacts identified 2017-03-02 and after.
* `Date identified greater than -1 year` returns all contacts identified after 2017-03-02.

Beside this you can specify your date with text. These formulas are **transatable**, so make sure you use them in correct format.

* `birthday` / `anniversary`
* `today` / `tomorrow` / `yesterday`
* `this week` / `last week` / `next week`
* `this month` / `last month` / `next month`
* `this year` / `last year` / `next year`

Example (Consider that today is `2018-03-02`):
* `Date identified equals last week` returns all contacts identified between 2018-02-26 and 2018-03-04 (Monday to Sunday).
* `Date identified less than last week` returns all contacts identified before 2018-02-19.
* `Date identified equals last month` returns all contacts identified between 2018-02-01 and 2018-02-28.
* `Date identified greater or equal last year` returns all contacts identified 2017-01-01 and after.
* `Date identified greater than last year` returns all contacts identified after 2017-12-31.

### Segments

Once you have created your segment, any applicable contact will be automatically
added through the execution of a cron job. This is the essence of segments.

To keep the segments current, create a cron job that executes the following
command at the desired interval:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
php /path/to/mautic/app/console mautic:segments:update --env=prod
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Through the execution of that command, contacts that match the filters will be
added and contacts that no longer match will be removed. Any contacts that were
manually added will remain part of the list regardless of filters.

### Manual Addition

In addition to segments you can also manually add any contact to a list by
clicking the Preferences button at the segments tab, use the dropdown to select a segment and add the contact to it or click on the x next to a segment in the input field to remove the contact.

### Delete all contacts in a segment

Filter the contacts in the segment. The batch delete action in the contact table allows deletion of up to 100 contacts at one time. This is a performance precaution since deleting more contacts at one time could cause issues. This feature can be used for hundreds of contacts.

![](/contacts/media/mautic-contact-batch-delete.png)

But deleting thousands of contacts this way in one segment will become a tedious task. Luckily, there is a trick how to let the background workers do the job for you.

1. Create a simple campaign which has the segment as the source \
2. Use the [Delete contact action](./../campaign/campaign_events.html#delete-contact). 

This way the `mautic:campaign:update` and `mautic:campaign:trigger` commands will delete all the contacts in the segment. As well as all the contacts which will be added to the segment in the future. Everything is done automatically in the background. The cron jobs must be configured. However, be aware that when a contact is deleted, there is no way to get it back.

![](/contacts/media/mautic-delete-contacts-in-segment.png)


