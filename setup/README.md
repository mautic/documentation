# Cron Jobs #

Mautic requires a few cron jobs to handle some maintenance tasks.

## Required ##

### Lead Lists ###
**To keep the smart lists current:**

```
php /path/to/mautic/app/console mautic:leadlists:update --env=prod
```

By default, the script will process leads in batches of 300. If this is too many for your server's resources, use the option `--batch-limit=X` replacing X with the a number of leads to process each batch.

You can also limit the number of leads to process per script execution using `--max-leads` to further limit resources used.

### Campaigns ###
**To keep campaigns updated with applicable leads:**

```
php /path/to/mautic/app/console mautic:campaigns:update --env=prod
```

By default, the script will process leads in batches of 300. If this is too many for your server's resources, use the option `--batch-limit=X` replacing X with the a number of leads to process each batch.

You can also limit the number of leads to process per script execution using `--max-leads` to further limit resources used.

**To execute campaigns events:**

```
php /path/to/mautic/app/console mautic:campaigns:trigger --env=prod
```

By default, the script will process events in batches of 100. If this is too many for your server's resources, use the option `--batch-limit=X` replacing X with the a number of events to process each batch.

You can also limit the number of leads to process per script execution using `--max-events` to further limit resources used.

## Optional ##

If the system is configured to queue emails, a cron job is required to process them.

```
php /path/to/mautic/app/console mautic:email:process --env=prod
```