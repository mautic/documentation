## How to test an integration

If you want to test an integration plugin to ensure that it is configured properly, you have 3 options how to do that. A lead can be pushed to integration via these places:

- The Campaign Builder has the *Push lead to integration* action which can be used in the Campaign dripflow.
- The Standalone Form has the *Push lead to integration* action which can be used after a standalone form is submitted.
- The Point Trigger has the *Push lead to integration* action which can be triggered when a lead achieves some point limit.

Use any of those triggers to test the plugin and see if the lead appears in the integration. Here is how the Standalone Form action can be configured:

![Push to Hubspot CRM form action](/plugins/media/plugins-push-to-hubspot-crm-form-action.png "Push to Hubspot CRM form action")

After you have your form with some fields (for example an email and a first name field) and the Push to an integration (e.g. Hubspot CRM) action, go to the form public URL at http://[yourmautic]/form/[formID], fill in some sample lead information and submit it. Then check the integration if the new lead has been created.

## Troubleshooting

If the first name value hasn't been transferred, make sure you mapped the form field value to the lead field value in the form field configuration.
