# Mautic - Hubspot CRM plugin

This plugin can push a lead to Hubspot CRM when a lead makes some action. In case you don't see this plugin in your Mautic instance, make sure you run the latest version. This plugin had been added to Mautic 1.2.3.

If you don't have the Hubspot CRM yet, [create it](http://www.hubspot.com/crm).

## Hubspot API key

Visit [https://app.hubspot.com/hapikeys](https://app.hubspot.com/hapikeys) to generate your Hubspot API key.

## Configure the Hubspot CRM plugin

Open the Hubspot Plugin configuration and paste the API key into the *Hubspot API key* input field. Also, if you want to use the plugin, you have to publish it. Set the *Publish* switch to *Yes*.

![Hubspot CRM Plugin configuration](/plugins/media/plugins-hubspot-crm-configuration.png "Hubspot CRM Plugin configuration")

In the Features tab is just *Push leads to this integration* checkbox and it is checked by default, so we are done here. Save it.

## Test the plugin

Let's test the plugin to ensure that the it is configured properly. A lead can be pushed to integration via these places:

- The Campaign Builder has the *Push lead to integration* action which can be used in the Campaign dripflow.
- The Standalone Form has the *Push lead to integration* action which can be used after a standalone form is submitted.
- The Point Trigger has the *Push lead to integration* action which can be triggered when a lead achieves some point limit.

Use any of those triggers to test the plugin and see if the lead appears in the Hubspot CRM. Here is how the Standalone Form action can be configured:

![Push to Hubspot CRM form action](/plugins/media/plugins-push-to-hubspot-crm-form-action.png "Push to Hubspot CRM form action")

After you have your form with some fields and the Push to Hubspot CRM action, go to the form public URL at http://[yourmautic]/form/[formID], fill in some sample lead information and submit it. Then check the Hubspot CRM if the new contact has been created.
