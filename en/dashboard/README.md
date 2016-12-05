# Dashboard

Mautic 1.4.0 brought a customizable dashboard where each user can compose widgets with information she/he wants to track.  Mautic 2.0 brought a number of enhancements to the Dashboard.

## Date range filter

All the widgets will display data in the selected global date range filter at the top of the widget list. The default date range is set from 30 days ago to today. Line charts will change the time unit automatically depending on the day count selected in the date range filter like this:

Date range is equal 1 day: Hours
Date range is between 1 and 31 days: Days
Date range is between 32 and 100 days: Weeks
Date range is between 101 and 1000 days: Months
Date range is greater than 1001 days: Years
 
The only exceptions of widgets which display the same information independent on the date range are *Upcoming emails* and *Recent activity*.

## Widgets

*Warning: Do not create too many widgets. It can slow the dashboard page load down. If you have performance issues, decrease the amount of widgets.*

A new widget can be added to your dashboard when you click on the "Add widget" button. In the "Add wigteg" form which appears after each widget will let you define:

- **Name**: Describe what the widget displays. If not filled, Mautic will call it the same as the widget type you select.
- **Type**: Select what information you want to display from the predefined widget types.
- **Width**: Select how wide the widget should be. The options are 25%, 50%, 75%, 100%. Default option is 100%. The optimal width for line charts is 100%, for tables 50%, for pie charts 25%.
- **Height**: Each widget can have different height. 5 heights are predefined. The dashboard will look best if you select a constant height for each widget in one row.

Some widgets have additional options:

**Created contacts in time**
- Show all contacts: Displays one line with all created contacts.
- Only identified: Displays one line with only created identified contacts.
- Only anonymous: Displays one line with only created visitors.
- All identified vs anonymous: displays 2 lines with created identified and visitors.
- Top segments: Displays up to 6 lines with contacts added to the top 6 segments. If no such segment exist for the selected date range, the chart will not be displayed.
- Top segments with Identified vs Anonymous: Displays up to 6 lines of the top 3 segments for the selected date range. Each segment will show 2 lines with identified and visitors.

**Emails in time**
- Only sent emails: Displays 1 line with sent emails.
- Only opened emails: Displays 1 line with opened emails.
- Only failed emails: Displays 1 line with failed emails.
- Sent and opened emails: Displays 2 lines with sent and opened emails.
- Sent, opened and failed emails: Displays 3 lines with sent, opened and failed emails.

**Page visits in time**
- Total visits - Displays 1 line with all visits (page hits).
- Unique visits - Displays 1 line with unique visits (contacts).
- Total and unique visits - Displays 2 lines with unique and all visits.

### Widget ordering

Each widget can change its location by drag&dropping. The handle is its name.

## Dashboard export

Each dashboard as you configure it can be exported to a single file. You can make a backup for another time, send it to a colleague or share it online. It exports only the widget configuration. Not the data in them.

## Dashboard import

If you export a dashboard, you can then upload it and import it again in the Dashboard Import page.

Stock Mautic installation comes with 3 pre-defined dashboards. The one called *default.json* is imported automatically, when your dashboard doesn't contain any widget. The other 2 predefined dashboards are there as an example. You can export and import any other dashboard and then switch between them. Pre-defined dashboards can be:

Previewed - It will display the dashboard widgets for preview. It will load in them actual Mautic data. Nothing is saved or changed by the Apply button.
Applied - It applies the dashobard as your dashboard. Warning: Your current widgets will be deleted by this action! Export the current dashboard if you want to get back to it later.
Deleted - It will delete the predefined dashboard.

## Widget cache

The WidgetDetailEvent automatically caches the widget detail data for a period of time defined in the configuration. Default cache expiration period is 10 minutes.

## Dashboard Permissions

If a Mautic user doesn't have the see others or see own permissions for a bundle, she/he won't be able to create widgets for said bundle. However, the widget can still be visible at hers/his dashboard. For example if a user creates the widgets and then the admin removes the permission or via import. In that case the widget is there, but with a message that the user doesn't have permission to see the data.

If a Mautic user has permission to see only his/hers own data from a bundle, he/she will see only his/hers own data in the Dashboard widgets. For example only contacts which he/she owns, page hits of the pages he/she created and so on.
