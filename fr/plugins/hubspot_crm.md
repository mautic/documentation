# Mautic - Hubspot CRM plugin

This plugin can push a contact to Hubspot CRM when a contact makes some action. In case you don't see this plugin in your Mautic instance, make sure you run the latest version. This plugin had been added to Mautic 1.2.3.

If you don't have the Hubspot CRM account yet, [create it](http://www.hubspot.com/crm).

## Hubspot API key

Visit [https://app.hubspot.com/hapikeys](https://app.hubspot.com/hapikeys) to generate your Hubspot API key.

## Configure the Hubspot CRM plugin

Open the Hubspot Plugin configuration and paste the API key into the *Hubspot API key* input field. Also, if you want to use the plugin, you have to publish it. Set the *Publish* switch to *Yes*.

![Hubspot CRM Plugin configuration](/plugins/media/plugins-hubspot-crm-configuration.png "Hubspot CRM Plugin configuration")

In the Features tab is just *Push contacts to this integration* checkbox and it is checked by default.

Configure the [field mapping](./../plugins/field_mapping.html).

Save the plugin configuration.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.

## Troubleshooting

If the contact hasn't been created, make sure that the email address you'd tested it with is valid. Hubspot will create a new contact only when its email address is valid.

## Credit

This plugin had been developed by [@gpassarelli](https://github.com/gpassarelli).
