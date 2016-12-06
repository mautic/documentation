# Mautic - vtiger CRM plugin

This plugin can push a contact to the vTiger CRM when a contact makes some action.

If you don't have the vTiger CRM account yet, [create it](https://www.vtiger.com/).

## Authenticate the vTiger plugin

To authenticate the Mautic plugin to be able to communicate with vTiger CRM you'll need these credentials:

- **vTiger URL** - the base (root) URL starting with http:// or https:// where your vTiger instance run. For example `https://your_vtiger.od2.vtiger.com`.
- **vTiger username** - The username (email address usually) which you use to log in to your vTiger.
- **vTiger access key** - The access key published in your vTiger profile. To get it, go to vTiger's *My Preferences*. The *Access Key* hash is in the bottom of the page.

Fill these 3 credentials to the Mautic plugin and click Authenticate.

## Configure the vTiger CRM plugin

If you want to use the plugin, you have to publish it. Set the *Publish* switch to *Yes*.

In the Features tab is just *Push contacts to this integration* checkbox and it is checked by default.

Configure the [field mapping](./../plugins/field_mapping.html).

Save the plugin configuration.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.
