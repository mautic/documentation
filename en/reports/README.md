# Reports

Highly customizable reports can be generated through Mautic's Report menu.

## Data Sources

Choose the data source appropriate to the report you want. Each data source has a different set of available columns, filters and graphs.
 
![](/reports/media/data-source.png)

## Configuration

Each report can be customized to include the columns of choice. Filter data based on set criteria and/or set a specific order for the data.
In addition you can also group by and select different function operators to calculate fields. Note that when you select functions operators a totals row will be added to the report. This totals row will not be exported when selecting to export a report.
 
![](/reports/media/config.png)

## Graphs

Some reports have graphs available. Select the graph desired from the left list - it will move to the right and will be part of the report.

![](/reports/media/graphs.png)

## Scheduled reports

[Configure the command](./setup/cron_jobs/index.html#send-scheduled-reports)

Mautic can send you a report periodically to your email since version 2.12.0.

Since version 2.16.0 you can also send report once. This may be helpful if the report takes some time to load. The cron job will do it for you and send you the result on email.

The problem is tha email attachments cannot be too big. If the file is greater than 5MB (configurable file attachment limit) then the CSV file will be zipped. If the zip package is within the file attachment limit then it will be sent as the email attachment. If it's still too big it will move the zip file to more permanent location and the email will contain link to download it. The download link works only for logged in users.

If someone will try to download a compressed CSV report that had been deleted for whatever reason it will schedule the report to NOW again and send the user the email notification to his email address when the CSV report will be created.

The one-time report export and send can be configured 2 ways:

1. By scheduling the email:
![Edit Report Segment membership](https://user-images.githubusercontent.com/1235442/55880254-9b4e3680-5ba0-11e9-9ffb-fe822829b3d4.png)

2. By a button from the report list:
![Reports Mautic](https://user-images.githubusercontent.com/1235442/55879686-786f5280-5b9f-11e9-8b8f-2b4654b0dbe1.png)

The button is available only for non-scheduled reports as it would reset configuration for scheduled reports.

## Dashboard Widget

Each graph of each report is made available as a widget on the dashboard allowing complete customization of the dashboard. 
 
![](/reports/media/widget.png)