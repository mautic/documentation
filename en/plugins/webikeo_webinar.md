# Mautic - Webikeo CRM plugin

This plugin can push/pull a Subscription to/from Webikeo webinars.

## Requirements

- A Webikeo API account.

## Get the Webikeo client member credentials
Paid Webikeo account


## Configure the Mautic Webikeo plugin

Insert the keys to the Mautic Webikeo plugin and authorize it.
Configure the plugin.
Please map all fields marked in red, as these are required fields.

### Features
Enabled features:
You can pull and push webinar sbuscriptions from the integration.

Push a contact as a subscription to a webinar can be done through a form or a campaign.

Webinar attendance can be checked through a campaign decision. 

Mautic segments can also be created with contacts that have attended, have not attended or have subscribed to a webinar.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.


###In Mautic Segments 
You can create a mautic segments composed of contacts that are subscribed to a Webikeo webinar. There are 3 states to build a webinar segment [Attended webinar, Did not attend webinar, Is subscribed to webinar] To do this create a segment filter **Selecting the type of webinar option** you need to filter by, then in the filter properties select the name of the webinar you wish to get contacts from.
If a contact doesn't exist in Mautic it will create it with the matchedup fields selected in the plugin configuration.
 