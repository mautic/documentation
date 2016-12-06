# Mautic - Device Granularity

Mautic records devices used to visit pages and open emails.

## Requirements

To detect devices Mautic uses (https://github.com/piwik/device-detector). Please be sure you have this library installed in your Mautic instance.

## Test this feature
####For Mautic pages and emails
Every page and email created with mautic should detect the device used to view a page or open an email. Emails need to be sent from a public instance of mautic in order to test open actions, or you can copy the tracking pixel URL and paste it in an incognito window of your browser to test in a local server.
####For Non-Mautic pages and emails
Any page or email that has Mautic's tracking pixel should detect the device used to view a page or open an email.

##How to use this feature
- You should see devices used to view pages in the contact's timeline
- Life cycle chart displays a graph of devices used by contacts in a particular segment
- Email details display a pie chart of devices used to open an email next to the statistics graph
- Reports of devices used per contact is now part of the reports bundle