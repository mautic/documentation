# Mailchimp integration

Mautic can send leads to Mailchimp upon some lead's action or when it gain some point limit.

**Version notes**
- For Mautic 1.2.2 and older, an Mailchimp app has to be created and the authentication is made via oAuth2. Client key and secret credentians are needed for authentication. Also SSL (https) connection is required.
- For Mautic 1.2.3 and later, the authentication has been changed to the API key. This documentation covers this option. This plugin is backward compatible. If the client ID is filled, the plugin will use oAuth2. If the client ID is empty, the plugin will let you insert the API key.

## Authorize

### Get Mailchimp API key

1. Create a Mailchimp account if you don't have one already.
2. Go to *Account* / *Extras* / *API Keys* and create a new one.
3. Copy the created API Key.

![Mailchimp - create a API Key](/plugins/media/plugins-mailchimp-create-api-key.png "Mailchimp - create a API Key")
![Mailchimp - copy the API Key](/plugins/media/plugins-mailchimp-copy-api-key.png "Mailchimp - copy the API Key")

### Authorize Mautic - Mailchimp plugin

Fill in the **username** you use to log in to Mailchimp and the **API key**. Save the plugin. 

## Configure the plugin

Navigate to the *Features* tab in the plugin configuration modal box. You should see this note:

> The Lead Field Mapping tab will appear after selecting a list and will update after changing the selected list.

![Mailchimp Plugin configuration](/plugins/media/plugins-mailcimp-configure.png "Mailchimp Plugin configuration")

Select the lead list then. If you don't have a lead list in Mailchimp created yet, go to *Mailchimp dashboard* / *Lists* / *Create List* and create one. Then save the plugin configuration and open it again. The *Lead Field Mapping* tab should appear now. Configure the [field mapping](/plugins/field_mapping.html).

Other configuration options are:
- **Push leads to this integration** - This option is checked by default. If you uncheck it, the plugin will not push leads to Mailchimp any more.
- **Enable double opt in** - If Mailchimp should send a confirmation email to the leads added by this plugin. The leads will have to confirm that they really want to be added to the list.
- **Send welcome email** - Whether Mailchimp should sent the welcome email.

## Test the plugin

Follow [these steps](/plugins/integration_test.html) to test the integration.