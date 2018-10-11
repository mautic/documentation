# Plugin Mautic - INES CRM

This plugin lets you to push contacts from Mautic to INES CRM with the _Push
contact to integration_ action or the `mautic:integration:fetchleads` command.

If you don't have an INES CRM account yet,
you can [sign up here](http://www.inescrm.fr/).


## Plugin configuration

1. Navigate to the plugins menu in the right side bar. If you do not see the
INES CRM icon, click the _Install / Updgrade Plugins_ button.

2. Click on the INES CRM icon and enter your login information, make sure to
_Publish_ the plugin, then _Save & Apply_.

3. Click on the INES CRM icon again. If you see an error message, make sure your
login information is correct. Go to the features tab and enable both Contact and
Company syncronization, then _Save & Apply_.

4. Click on the INES CRM icon one more. Map your company and contact custom
fields in their respective tabs. You may configure whether a value sent from
Mautic will replace an existing value in INES CRM.


## Features

- Use the _Push contact to integration_ feature in forms, campaigns and point
triggers to push leads to INES CRM. Note that a contact needs to have an email
address and a company to be pushed to INES.

- Add the following command to your crontab to regularly push new leads.

  `app/console mautic:integration:fetchleads --integration=InesCRM --time-interval=[TIME-INTERVAL]`


## Test the plugin

Follow [these steps](./../plugins/integration_test.html).

## Credit

This plugin has been developed by [@webmecanik](https://github.com/webmecanik)
