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

## Tips & Troubleshooting ##

If your environment provides a command-line specific build of php, often called `php-cli`, you may want to use that instead of `php`.  It will have a cleaner output.  On bluehost and probably some other PHP hosts, the `php` command might be setup to discard the command-line parameters to `console`, in which case you must use `php-cli` to make the cron jobs work.

To assist in troubleshooting cron issues you can pipe the output of each cron job to a specific file by adding something like `>/path/to/somefile.log 2>&1` at the end of the cron job.  Then you can look at the contents of the file to see what was printed.  If an error is occurring when running run the cron job, you will see it there, otherwise you the file will be empty or have some stats.  The modification time of the file informs you of the last time the cron job was run.  You can thus us this to figure out whether or not the cron job is running successfully and on schedule.

