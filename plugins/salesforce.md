# Mautic - Salesforce CRM plugin

This plugin can push a lead to Salesforce CRM when a lead makes some action. If you don't have the Salesforce CRM account yet, [create it](http://www.salesforce.com/).

## Requirements

SSH. Your Mautic instance nas to run on https. Salesforce will not allow you to create App with just http callback URL.

## Get the Salesforce client credentials

There is an [official documentation](http://feedback.uservoice.com/knowledgebase/articles/235661-get-your-key-and-secret-from-salesforce) about how to get the Key and secret although it doesn't seem to be updated.

Go to: *Setup* (tom right corner) / Build (bottom left corner) - Create / Apps / Connected Apps / New

![Salesforce CRM Create an App](/plugins/media/plugins-salesforce-create-app.png "Salesforce CRM Create an App")

Create a new app like this:
![Salesforce CRM Create an App form](/plugins/media/plugins-salesforce-create-app-form.png "Salesforce CRM Create an App form")
Make sure the Selcected OAuth Scopes are *Access and manage your fata (api)* and *Perform requests on your behalf at any time (refresh_token, offline_access)*.

Copy the Consumer Key and Secret.

![Salesforce CRM Create an App keys](/plugins/media/plugins-salesforce-create-app-keys.png "Salesforce CRM Create an App keys")

## Configure the Mautic Salesforce plugin

Insert the keys to the Mautic Salesforce plugin and authorize it.
![Salesforce CRM Authorize](/plugins/media/plugins-salesforce-authorize.png "Salesforce CRM Authorize")

Configure the [field mapping](./../plugins/field_mapping.html).

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.

## Troubleshooting

### Error: `The REST API is not enabled for this Organization.`

This means the API is not turned on in your Salesforce account. [Read more](https://help.salesforce.com/apex/HTViewHelpDoc?id=admin_userperms.htm&language=en)
