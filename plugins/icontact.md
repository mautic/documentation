# iContact integration

Mautic can send leads to [iContact](https://www.icontact.com) upon some lead's action or when it gain some point limit.

## Authorize

In order to connect your iContact account with your Mautic, you'll have to create a iContact app. 

Follow the [tutorial](https://www.icontact.com/developerportal/documentation/register-your-app/) how to create your iContact APP.

When you have your app created, you should be able to see this screen:

![iContact - create a App Key](/plugins/media/plugins-icontact-authorization-details.png "iContact - create a App Key")

Fill it the right credentials to Mautic - iContact integration:

- App ID = the Application ID you've created
- App username = the username / email you log into your iContact account. (Not the App name)
- App password = The password you've chosen when approving the app.

![iContact - authoriztion](/plugins/media/plugins-icontact-authorization.png "iContact - authoriztion")

## Configure the plugin

Navigate to the *Features* tab in the plugin configuration modal box. Select the iContact lead list where the Mautic leads should be pushed into. There should be one list created by default.

Other configuration options are:
- **Push leads to this integration** - This option is checked by default. If you uncheck it, the plugin will not push leads to Mailchimp any more.

## Test the plugin

Follow [these steps](/plugins/integration_test.html) to test the integration.
