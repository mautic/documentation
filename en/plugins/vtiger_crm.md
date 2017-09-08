# Mautic - vtiger CRM plugin

This plugin can push a contact to the vTiger CRM when a contact makes some action.

If you don't have a vTiger CRM account yet, [create it](https://www.vtiger.com/).

**Warning** The cloud Vtiger instances have the _Leads_ module disabled by default. This will cause error message `Permission to perform the operation is denied` on plugin edit form. Enable the _Leads_ module and the plugin load the custom field mapping form.

## Authenticate the vTiger plugin

To authenticate the Mautic plugin to be able to communicate with vTiger CRM you'll need these credentials:

- **vTiger URL** - the base (root) URL starting with http:// or https:// where your vTiger instance runs. For example `https://your_vtiger.od2.vtiger.com`.
- **vTiger username** - The username (email address usually) which you use to log in to your vTiger.
- **vTiger access key** - The access key published in your vTiger profile. To get it, go to vTiger's *My Preferences*. The *Access Key* hash is at the bottom of the page.

Fill these 3 credentials to the Mautic plugin and click Authenticate.

## Configure the vTiger CRM plugin

If you want to use the plugin, you have to publish it. Set the *Publish* switch to *Yes*.

In the Features tab is *Push contacts to this integration* checkbox and it is checked by default.

You can also configure whether you want to map Vtiger's _Leads_ to Mautic's _Contacts_ and/or Vtiger's _Organizations_ to Mautic's _Companies_.

Configure the [field mapping](./../plugins/field_mapping.html).

Save the plugin configuration.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.
