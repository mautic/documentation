# Cron Jobs #

Mautic requires a few [cron jobs](https://en.wikipedia.org/wiki/Cron) to handle some maintenance tasks. Most web hosts provide a means to add cron jobs either through SSH, cPanel, or another custom panel. Please consult your host's documentation/support if you are unsure on how to setup cron jobs.

How frequently you run the cron jobs is up to you. Many shared hosts prefer that you run scripts every 15 or 30 minutes and may even override the scheduled times to meet these restrictions. Consult your host's documentation if they have such a restriction. 

**It is recommended that you stagger the following required jobs so as to not run the exact same minute.**

## Required ##

### Lead Lists ###
**To keep the smart lists current:**

```
php /path/to/mautic/app/console mautic:leadlists:update
```

By default, the script will process leads in batches of 300. If this is too many for your server's resources, use the option `--batch-limit=X` replacing X with the a number of leads to process each batch.

You can also limit the number of leads to process per script execution using `--max-leads` to further limit resources used.

### Campaigns ###
**To keep campaigns updated with applicable leads:**

```
php /path/to/mautic/app/console mautic:campaigns:update
```

By default, the script will process leads in batches of 300. If this is too many for your server's resources, use the option `--batch-limit=X` replacing X with the a number of leads to process each batch.

You can also limit the number of leads to process per script execution using `--max-leads` to further limit resources used.

**To execute campaigns events:**

```
php /path/to/mautic/app/console mautic:campaigns:trigger
```

By default, the script will process events in batches of 100. If this is too many for your server's resources, use the option `--batch-limit=X` replacing X with the a number of events to process each batch.

You can also limit the number of leads to process per script execution using `--max-events` to further limit resources used.

## Optional ##

### Process Email Queue ###

If the system is configured to queue emails to the filesystem, a cron job is required to process them.

```
php /path/to/mautic/app/console mautic:email:process
```

### Fetch and Process Monitored Email ###
 
If using the [Bounce Management](./../emails/bounce_management.html),  
 
```
php /path/to/mautic/app/console mautic:fetch:email
```

### Webhooks

If Mautic is configured to send webhooks in batches, use the following command to send the payloads:

```
php /path/to/mautic/app/console mautic:webhooks:process
```

### Update MaxMind GeoLite2 IP Database
 
Mautic uses [MaxMind's](http://www.maxmind.com) GeoLite2 IP database by default. The database is licensed under the (Creative Commons Attribution-ShareAlike 3.0 Unported License)[http://creativecommons.org/licenses/by-sa/3.0/] and thus cannot be packaged with Mautic. The database can be downloaded manually through Mautic's Configuration or the following script can be used as a cron job to automatically download updates. (MaxMind updates their database the first Tuesday of the month).
 
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

