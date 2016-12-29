# MailChimp integration

Mautic can send contacts to MailChimp upon some contact's action or when it gain some point limit.

**Version notes**
- For Mautic 1.2.2 and older, an MailChimp app has to be created and the authentication is made via oAuth2. Client key and secret credentians are needed for authentication. Also SSL (https) connection is required.
- For Mautic 1.2.3 and later, the authentication has been changed to the API key. This documentation covers this option. This plugin is backward compatible. If the client ID is filled, the plugin will use oAuth2. If the client ID is empty, the plugin will let you insert the API key.

## Authorize

### Get MailChimp API key

1. Create a MailChimp account if you don't have one already.
2. Go to *Account* / *Extras* / *API Keys* and create a new one.
3. Copy the created API Key.

![MailChimp - create a API Key](/plugins/media/plugins-mailchimp-create-api-key.png "MailChimp - create a API Key")
![MailChimp - copy the API Key](/plugins/media/plugins-mailchimp-copy-api-key.png "MailChimp - copy the API Key")

### Authorize Mautic - MailChimp plugin

Fill in the **username** you use to log in to MailChimp and the **API key**. Save the plugin. 

## Configure the plugin

Navigate to the *Features* tab in the plugin configuration modal box. You should see this note:

> The Contact Field Mapping tab will appear after selecting a segment and will update after changing the selected segment.

![MailChimp Plugin configuration](/plugins/media/plugins-mailchimp-configure.png "MailChimp Plugin configuration")

Select the segment then. If you don't have a segment in MailChimp created yet, go to *MailChimp dashboard* / *Segments* / *Create List* and create one. Then save the plugin configuration and open it again. The *Contact Field Mapping* tab should appear now. Configure the [field mapping](./../plugins/field_mapping.html).

Other configuration options are:
- **Push contacts to this integration** - This option is checked by default. If you uncheck it, the plugin will not push contacts to MailChimp any more.
- **Enable double opt in** - If MailChimp should send a confirmation email to the contacts added by this plugin. The contacts will have to confirm that they really want to be added to the segment.
- **Send welcome email** - Whether MailChimp should sent the welcome email.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.