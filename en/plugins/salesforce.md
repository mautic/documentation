# Mautic - Salesforce CRM plugin

This plugin can push a contact to Salesforce CRM when a contact makes some action. If you don't have the Salesforce CRM account yet, [create it](http://www.salesforce.com/).

## Requirements

SSH. Your Mautic instance nas to run on https. Salesforce will not allow you to create App with just http callback URL.

## Get the Salesforce client credentials

There is an [official documentation](http://feedback.uservoice.com/knowledgebase/articles/235661-get-your-key-and-secret-from-salesforce) about how to get the Key and secret although it doesn't seem to be updated.

Go to: *Setup* (top right corner) / Build (bottom left corner) - Create / Apps / Connected Apps / New

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

### Features
Enabled features:
You can pull leads and/or push leads from and to the integration.

Push leads is done through a form or a campaign.

Pull leads is done through command line and it can be setup as a cronjob.

Feature specific settings:
Select the objects you wish to pull or push records from. You can push contacts to the Leads object in salesforce. you can also push activities (contact's timeline records) to a custom object in salesforce.

Pulling records will be done from Leads and/or Contacts objects in records.

### Command line script to pull records from Salesforce
To pull records from salesforce you need to use a command from CLI. Use this command:

Used to pull records from the Leads object in Salesforce

- php app/console mautic:integration:fetchleads

Used to push activities to the Salesforce custom object described below
 - mautic:integration:pushleadactivity

Parameters both commands take:

**--time-interval** This parameter is used to setup the amount of time we want to pull records from. Possible entries: "10 days", "1 day", "10 minutes", "1 minute".  Maximun time interval "29 days".

**--integration**=Salesforce  to use with salesforce integration.  In future this command may be used for other integrations.

## Setting up Mautic's custom object in Salesforce
To be able to push activities to the salesforce integration you first need to setup a custom object in your salesforce instance. Please setup the object as it is described below.  (Note: these are two underscores with no space between - not rendered well in Github).

Custom object name: Mautic\__timeline (API  name: Mautic_timeline\__c)

API names of fields:
- ActivityDate\__c : Date/Time
- contact_id\__c : Lookup(Contact)
- Description\__c  : Long Text Area(131072)
- WhoId\__c : Lookup(Lead)
- MauticLead\__c : Number(18, 0) (External ID)
- Mautic_url\__c : URL(255)

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.

## Troubleshooting

### Error: `The REST API is not enabled for this Organization.`

This means the API is not turned on in your Salesforce account. [Read more](https://help.salesforce.com/apex/HTViewHelpDoc?id=admin_userperms.htm&language=en)
