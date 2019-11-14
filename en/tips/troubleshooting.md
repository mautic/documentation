# General troubleshooting

Follow these steps to solve your issue as fast as possible.

## My Mautic is acting weird

Even through the effort of the dev and test teams, it might happen. At first, let's try a few tricks which might fix it fast.

### 1. Clear the cache

There are several ways to do that. The easiest is to go to the `/app/cache` folder and delete its content. If you want to do it via CLI command, navigate to the Mautic root folder and run `rm -rf app/cache/*`. The new cache files will generate itself after the next Mautic refresh in the browser.

It might happen that the files won't generate itself. It can be caused by the wrong folder permission and Mautic doesn't have permission to write the new cache files. Contact your sysadmin and ask them to fix it for you.

Tip: Don't execute Mautic commands as the root user yourself and do not run Mautic commands in the root crontab. This way all the files which will be created by the command will have the root as the author and Mautic won't be able to rewrite those files.

### 2. Try to fix the database schema

Go to `http://[your-mautic-url]/s/update/schema`. It will update your database schema if there are some known updates to be applied.

## Nope, it didn't help

Alright. Let's figure out what the issue really is.

### Check the logs

#### Mautic logs

Please do not report the following two errors:

> The site is currently offline due to encountering an error. If the problem persists, please contact the system administrator

or

> Uh oh! I think I broke it.

Those are generic error messages which provide absolutely no valuable information about the cause of the error. It is on purpose. The detailed error message isn't displayed in the production environment because if it did, it could tell possible crackers some valuable information about your server, Mautic or integration which they could use to attack it. That's why this generic error message is shown instead and the real error message is logged into the logs. Long story short, that's why reporting it doesn't make any sense.

There are different logs in your system which could tell us more. Let's start from the Mautic log.

If your Mautic administration works, go to the Admin menu (click the __cog icon__ in the top right side corner), then __System Info__, then __Log__. You will see the error messages recorded by Mautic today.

If your Mautic administration doesn't work, open the logs in via the file system. Go to `[mautic_root]/app/logs` folder. You should see one file for every day called `mautic_prod-YYYY-mm-dd.php`. Open the latest one.

#### Server logs

I don't have experience with all operating systems and servers. I can tell you that Apache2 saves the server logs at Ubuntu in `/var/log/apache2/error.log`. If you don't know where the server logs are stored, contact your sysadmin or try to google it.

#### MySql logs

If your Mautic says it is not able to connect to MySql for some reason, you can check what information is stored in the MySql log. Again, I can only advise where the log is in Ubuntu: `/var/log/mysql/error.log`. But to be honest, the database connection error is in 90% of cases caused by wrong credentials.

#### The log file is too big

If the log is so big that a normal editor cannot open it and you have the CLI access, try to read only the few last rows of it with command `tail [mautic_root]/app/logs/mautic_prod-YYYY-mm-dd.php`. You have to add the current date instead of the `YYYY-mm-dd` part. If you want to see more rows than the default is, use the `-n 40` attribute at the end of the command to see the last 40 rows.

#### But I don't understand the error message

Take a deep breath and try to read the error messages. Some error messages actually have the solution written in them. Look at this one:

```
Fatal: Automatically populating $HTTP_RAW_POST_DATA is deprecated and will be removed in a future version. To avoid this warning set 'always_populate_raw_post_data' to '-1' in php.ini and use the php://input stream instead. - in file Unknown - at line 0 [] []
```

You see the advice in it?

> To avoid this warning set 'always_populate_raw_post_data' to '-1' in php.ini

But you still don't know what it means? Simplest thing in this case is to contact your sysadmin and tell them just that.

#### Let's look at some examples

__Errors:__
```
PHP Fatal error:  Allowed memory size of 67108864 bytes exhausted (tried to allocate 10924085 bytes) in ...
```
```
Fatal: Maximum execution time of 120 seconds exceeded - in file ...
```
__Solution:__
This means Mautic needs more memory / time than your server limit is. Again, contact your sysadmin and consult your possibilities.

__Error:__
```
Fatal: Class 'ZipArchive' not found
```
__Solution:__
It can be ZipArchive, MCrypt or any other PHP module missing. Again, consult you know who to install it.

__Error:__
```
PHP Parse error:  syntax error, unexpected T_OBJECT_OPERATOR in
```
__Solution:__
This usually means your PHP is outdated. Check what [Mautic requirements](https://www.mautic.org/download/requirements/) are.

__Error:__
```
exception 'RuntimeException' with message 'Unable to create the cache directory ...
```
__Solution:__
It means that the file permissions aren't right and Mautic cannot write the cache files.

__Error:__
```
mautic.WARNING: IP LOOKUP: The file "../app/cache/prod/../ip_data/GeoLite2-City.mmdb
```
__Solution:__
It means that you just didn't download the IP lookup library. Go to Mautic's Configuration, scroll to the bottom and click the button to download it.

__Error:__
```
Uncaught PHP Exception Doctrine\DBAL\DBALException: "An exception occurred while executing 'INSERT INTO
```
__Solution:__
This is a SQL error. It might either mean that your database schema is outdated or there is a bug in some part of Mautic. In the first case, the step 2 from this article should fix it. In the second case, look at the error reporting below.

__Error:__
```
PHP Fatal error: Call to a member function isRendered() on a non-object in ...
```
__Solution:__
Usually means a bug.

### How and where to report a bug

Help your fellow developers and report the bug correctly the first time. Go to [GitHub issue tracker](https://github.com/mautic/mautic/issues) and answer at least the following 3 questions:

Mautic version:
PHP version:
Steps to reproduce the error:

And paste in the error message(s) obviously.
