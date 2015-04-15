# Manage Campaigns

### Campaign Overview

The campaign overview will show you many details of your campaign including the number of leads which have been added to a campaign, the number of emails sent, and the number of page views resulting from the campaign.

Additional information includes a quick overview of what decisions and actions are available on a campaign, as well as a grid layout overview of all the leads on a campaign.

As with many of the other overview screens you can view the recent activity taken place on the campaign.

### Basic Campaign Creation
Creating campaigns is an easy process which involves picking a name, creating a description, and defining the lead lists to associate with the campaign. These campaigns can then be assigned a category and defined publishing information. All of these are rather standard aspects of a new campaign creation.

**Note**: The lead list selection will only show public lists. This means any lead lists created by individuals within the company marked as private will not be available for campaigns.

### Advanced Campaign Creation

The basics of campaign creation are handled easily by the initial screen but the finer details of building a campaign occur within the campaign builder. This might be considered advanced campaign creation but every campaign does need to use the campaign builder.


#### Triggering Campaign Events ####
Actions based on a lead's non-action (the red decision point) must be triggered by the system. To do so, create a cron job that executes the following command at the desired interval:

```
php /path/to/mautic/app/console mautic:campaigns:trigger --env=prod
```

That command will find and execute scheduled events and/or non-action events that have passed the specified time frame. 

If you want to execute the command at different intervals for specific campaigns, you can pass the `--campaign-id=ID` argument to the command.
