# Mautic update failed
Sometimes when updating Mautic, the process might stall or fail part way through.  This can cause a problem, because it can cause Mautic to be in-between two versions and often this can make the system unusable.

The following processes can be followed to complete the upgrade manually.

Before you commence these steps, **please ensure that you have a tested backup of your Mautic instance**

## Checking for schema updates
Mautic has a built-in tool which enables you to check the database and identify if there are any schema updates required.  Visit your-mautic-url/s/update/schema to see if there are any updates required.

If this is not possible, or your Mautic instance is down completely, follow the next tips.

If you don't have SSH access, skip down to ['I don't have SSH access'](#nossh).

## I have SSH access

Having SSH access to your server makes things much easier. Log in via command line, and change directory to the location where Mautic is installed using the command

    cd /your/mautic/directory

###1.  Try to clear the cache

When an upgrade attempt fails in the final step, it may be only the outdated cache that is causing a problem.  Use the following command to clear it manually:

    php app/console cache:clear

If this command throws a PHP error, you can try to remove the cache folder using the following command (be careful, this removes all files and folders in the path specified, so ensure you type it correctly!)

    rm -rf app/cache

If clearing the cache has not resolved your problems, continue with the next step.

###2. Trigger an update manually

The first step is to find out if there are any updates available using the following command:

    php app/console mautic:update:find

The output from this command will tell you if there are any updates to apply.  If there are, run the following command to apply them:

    php app/console mautic:update:apply

If there are no updates found, proceed to the next step.

###3. Check for outstanding database migrations

Run the following command to check for any outstanding database migrations:

    php app/console doctrine:migration:status

If there are any reported, firstly **ensure that you have a tested backup of your database before proceeding, as this command will cause changes to the database**, then run:

    php app/console doctrine:migration:migrate

###4. Check for database schema updates

If your upgrade failed during the database update step, the database schema may not be up to date.  Run the following command to check for updates:

    php app/console doctrine:schema:update --dump-sql

Running this command will tell you whether the database is up to date with the code.  If there are queries that need to be executed, **ensure you have a tested backup of your database before proceeding, as this command will cause changes to the database**, then run the following command:

    php app/console doctrine:schema:update --force

If this hasn't resolved your problem, proceed to the next step.

###5. Try to update the files manually

This step requires some manual intervention - there is no command for this part.

To update the files manually, you will have to:
1. Back up (download) all Mautic files from your server to your local computer, using FTP or the [scp command](http://manpages.ubuntu.com/manpages/precise/en/man1/scp.1.html) which is much faster.
2. Delete all Mautic files and folders.  Use FTP or the [rm command](http://manpages.ubuntu.com/manpages/precise/en/man1/rm.1.html) (use the latter with extreme caution)
3. Download the latest Mautic package from [https://www.mautic.org/download](https://www.mautic.org/download)
4. Upload the zip package to the server, to the Mautic folder, using FTP or the [scp command](http://manpages.ubuntu.com/manpages/precise/en/man1/scp.1.html) which is much faster.
5. Unzip the package with unzip 1.2.0.zip (change the filename to match the one you have uploaded).  You can then remove the zip file using the command         rm 1.2.0.zip
6. Upload app/config/local.php from your backup on your local machine to the fresh Mautic folder on the server (Mautic should now run)
7. Upload your custom data if you have some. Custom fields may be found in the following folders: media/files; plugins; themes; translations

##[I don't have SSH access](#nossh)

There is a PHP script which can do almost all steps from the section above.  You can find this script at [https://gist.github.com/escopecz/9a1a0b10861941a457f4](https://gist.github.com/escopecz/9a1a0b10861941a457f4).

The description about how to use the script can be found below the script itself.  There are some details you will need to do differently, so please read these instructions carefully.  For example, you will need to use FTP to upload and download the files.  You will have to unzip the files on your local computer and upload those files, which will take a lot longer.

##There is a PHP error when I execute a command
The best thing to do is read the error, and search for the error in your preferred search engine.  You can also search the [Mautic Forums](https://forum.mautic.org) to see if others have reported and resolved the same problem.

###Allowed memory size exhausted
This error will usually be reported as:

    PHP Fatal error:  Allowed memory size of 67108864 bytes exhausted (tried to allocate 10924085 bytes) in ...
    
This means that the memory limit that Apache has available is too low.  Edit the memory_limit in the php.ini configuration file.

###A required PHP extension is missing

    Fatal: Class 'ZipArchive' not found

This means that PHP cannot work with Zip packages - changes need to be made to your server configuration to allow unzipping of files at the command line.  Ask your hosting provider, or search for a tutorial to help with this.

###I need help

If you are stuck and need help, there are several places you can go to ask for assistance.  Remember that most people who use the Community Forums, Chat and Github are volunteers.

If you think your configuration is causing the problem, ask on the [Mautic Community Forums](https://forum.mautic.org). Search before you post, as it is likely someone might have already answered your question in the past.

You can also chat with someone in the live [Community Chat](https://www.mautic.org/slack).

In all cases, it is important that you describe the problem, and all steps you have followed to resolve the problem, in detail.  At a minimum, include the following:

* Steps to reproduce your problem - a step-by-step tutorial of how the problem arose, or how to reproduce it
* The PHP version of your server
* The error messages you are seeing - if you don't see the error message directly, search for it in the app/logs folder and in the server log.  The server log can be found in different places depending on your setup. Ubuntu servers will generally have logs in /var/log/apache2/error.log.  Sometimes your hosting provider might offer a GUI to view logs in your Control Panel.

If you don't provide the information above as a minimum, the person who might try to help you will have to ask you for it, so please save them the trouble and provide the information upfront.  Also, importantly, please be polite.  Mautic is an Open Source project, and people are giving their free time to help you.

If you are sure that you have discovered a bug and you want to report it to developers, you can do so on [Github](https://github.com/mautic/mautic/issues)
