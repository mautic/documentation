# Custom date field to trigger a campaign

In the condition based on a contact field value, select the required date field. After selecting it, select "date" as operator.
Then select the required value from drop-down.

Note: In "Anniversary" option only day and month value of the field is considered.

Usage:

One thing to remember is that campaign conditions are evaluated immediately.  So if the date in the field matches the condition, then the positive action is executed.  If the date doesn’t match, the negative action is executed.   The contact doesn’t kind of “hang around” waiting for the condition to be true.

In order to run campaigns based on a particular date where a contact may or may not be "included" today:
- create a segment with a filter where the date field = TODAY.
- initiate the campaign based on that segment.
- as people move in and out of the segment, the campaign will run.
- you can elimiate the condition since the segment is changing daily.
- note:  this will NOT work for an anniversary - only an actual date.

Of course if someone appears again at a later date in that segment because the value of the date is changed, they’ll still only go through the campaign once and hence will NOT be included in the campaign again.
