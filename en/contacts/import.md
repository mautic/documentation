# Contact Import

Contacts can be imported via the user interface from a CSV file. You can import from the browser or in the background via a cron job.

> Background import is recommended.

Since Mautic 2.9, when the import creates or updates a contact, you'll see that action in the contact events history.

## How to configure an import

1. Go to *Contacts*.
1. In the top right corner above the table of Contacts open the sub menu of actions and select the *Import* option.
   > **ProTip**
   > The direct URL is `https://example.com/s/contacts/import/new`
1. Upload the CSV file with contacts you want to import.
1. Adjust the CSV settings if your CSV file use something else as a delimiter, enclosure and so on.
1. Upload your CSV file.
1. The field mapping page should show up.  The first set of options will let you select owner, segment and tags to assign globally to all imported contacts.  The second set of options will let you map the columns from your CSV to Mautic contact custom fields. The third set of options will let you map columns from your CSV to special contact attributes like *Date Created* and so on.
1. When your field mapping is ready, click one of the the *Import* buttons (described below).

## Browser import

Larger CSV files have to be imported in batches to avoid hitting server (PHP) memory and execution time limits.  When importing in the browser, your browser is controlling the batches.  When one finishes, the javascript starts a new one. This means the browser window **has** to stay opened and connected to the internet the whole time.

Use the browser import method only if you don't have any other choice.  Background import is recommended.

## Background import

Background import jobs (CLI command triggered manually or via a cron job) have the advantage of benevolent time limits. A CSV background import is not restarted every batch (1 batch = 100 rows by default) - the last row imported is saved, and the next batch continues from that point.  Background imports will always be faster and more reliable than browser imports.

This option is available since Mautic 2.9.

**Warning** background import require the command `php /path/to/mautic/app/console mautic:import` to run periodically. Add it to your [cron jobs][cron].

Successful result of the background job can look like this:

```console
$ app/console mautic:import
 48/48 [============================] 100%
48 lines were processed, 0 items created, 48 items updated, 0 items ignored in 4.78 s
```

If there is no import waiting in the queue, there won't be message.

### Parallel import

The import can take several minutes. It's possible that one import will still run when the other will be started. To prevent running out of server resources, there is the `parallel_import_limit` configurable option. By default only 1 import will run at the same time. This option can be changed when you add it to your `app/config/local.php` file.

### How to stop a background import

Go to the list of imports and click on the green switch. This switch is used through the Mautic UI to unpublish items. It's similar for imports. The import will change its status to **Stopped**. It will finish importing the current batch and than it stops the import.

When you decide to start the import again, you can simply publish it again and the background job will continue with the import.

When the background job finishes, either successfully or if it fails, you'll get a notification in the Mautic's notification area about it.

## Import job status

There are several potential statuses for import jobs:

- **Queued** - The import was created and queued for background processing. At this stage the import is waiting for the background job to start the import.
- **In Progress** - The background job started the import and it hasn't finished yet. You can see the progress in the list of the imports.
- **Imported** - The import was successfully processed.
- **Failed** - The import failed for some reason. Most usual cause may be that the uploaded CSV file was removed or Mautic doesn't have permission to read it. Or the import was unresponsive for more than 2 hours.
- **Stopped** - The import has been stopped by the user when it was in the **Queued** or **In Progress** states.
- **Manual** - The user selected to import in the browser "manually". It's similar to **In Progress**.
- **Delayed** - The background job wanted to start the import, but the import process could not start. So it's delayed for later. The reason when this could happen is when the parallel import limit was hit. The import will start ASAP.

## List of imports

The list of imports can be found when you go to the *Contacts* area, open the action menu above the contacts table and choose the *Background imports* option.

The direct URL is `https://example.com/s/contacts/import/1`

The table will show you basic statistics about all imports, what are the current statues and what was the CSV file name. There is also the switch which will enable you to stop and start **Queued** or **In Process** imports.

## Import detail

The import detail page holds more detailed statistics and import configuration when you click on *Details* like import speed and how the import has been configured.

There are also 2 charts:

1. The pie chart shows the ratio between created, updated and failed rows.
1. The line chart shows how many contacts has been added per minute.

The main content area displays information about rows which were ignored for some reason (if any). The table will tell you what row in the CSV file it was and what was the reason, so you can fix those rows and import again.

In the right column you can see who created the import and when and also when the background job (System) updated the statistics after every batch was completed.

## Automatic import option decision

There is an option in the Global Mautic Configuration / Contact Settings to define what is the optimal limit of browser import vs background import. If you insert for example 1000, that means that if the import CSV will have less than 1000 rows, it will be imported in the browser, if it will have more rows, it will be queued to be imported by the background job. Default value is 0 (zero), which means it will show you 2 Import buttons instead of one and you'll have to decide what import option to use during every import.

## Requirements

- The CSV file must be in UTF8 encoding. Other encodings may cause troubles while importing. Read the documentation of your spreadsheet program on how to export a spreadsheet to UTF8. Google Sheets encodes to UTF8 automatically, Libre/Open Office lets you choose before export.

- In case of boolean values like `doNotEmail` or custom boolean field, use values `true`, `1`, `on` or `yes` as TRUE value. Anything else will be considered false.

- In case of date/time values, use [ISO8601] notation i.e. `YYYY-MM-DD hh:mm:ss`
    - Example: `2019-01-02 19:08:42`.
    <!-- For PHP DateTime notation: `YY-MM-DD HH:II:SS`) -->
    <!-- See MySQL in the Localized Notations at https://www.php.net/manual/en/datetime.formats.compound.php -->
    - Other formats may work too, but they may be problematic.

## Tips

- Name the column names the same as Mautic contact custom field names. This way Mautic automatically pre-selects the mapping for you. For example if you name the first name column as `firstname`, this field will be mapped automatically.

- If your CSV contains thousands of contacts or more, divide such CSV into several smaller CSV files to avoid memory issues and slow import speed.

> ProTip
> If using a Linux system, see the GNU parallel command. (sudo apt install parallel)
>
>     ```console
>     cat big_contact_list.csv | parallel --header : --pipe -N 1000 'cat > split_list_part{#}.csv'
>     ```
>
> This will generate files:
>
> split_list_part1.csv
> split_list_part2.csv
> …
> split_list_part10.csv

## FAQ

Q: My import times out. What can I do about that?
A: Either use the background job to import or change the batch limit to smaller number than 100.

Q: If I import *Do Not Contact* values, is that stored as a bounce or a unsubscription?
A: It's stored as a manual unsubscription. It's the same thing as if the contact was marked as *Do Not Contact* from the Contacts page.

![Do Not Contact](media/do-not-contact.png)

[cron]: <./../setup/cron_jobs.html>
[ISO8601]: <https://en.wikipedia.org/wiki/ISO_8601>
