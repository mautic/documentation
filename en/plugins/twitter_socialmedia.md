# Mautic - Twitter Social Media plugin

This plugin can:
 -display public profile and enable profile to lead field matching
 -display public activity
 -display share button on landing page social widget

## Requirements

Twitter needs to aprove your app in order to request the user's email. For the user's public information all you need is to create a twitter application. Twitter also requires you to hae a A fully qualified domain name (FQDN). This doesn't have to be a public domain name, so you can give you localhost a FQDN for testing.

## Get the Twitter client credentials

To get your twitter credential you first need to:

1. Have a twitter account
2. Create a twitter application [here] (https://apps.twitter.com)
3. Click on the "Create New App" button.
4. Fill in all relevant information, One important field to fill in is the callback url please NOTE that this must be a qualified domain name, even for your localhost. This does not mean it has to be a registered domain. It only needs to come in the form of a fully qualified domain name for twitter to accept it.

Once the app has been created in Twitter, you should be able to see your Consumer Key (API Key) and your 	Consumer Secret (API Secret) 

## Configure the Mautic Twitter plugin

Insert the keys to the Mautic Salesforce plugin and authorize it.
![Salesforce CRM Authorize](/plugins/media/plugins-salesforce-authorize.png "Salesforce CRM Authorize")

Configure the [field mapping](./../plugins/field_mapping.html).
####Enabled features
- Display public profile and enable profile to lead field matching
- Display public activity
- Display share button on landing page social widget
- Login Button
####Feature Specific Settings

Configure these setting as prefered.
## Test the plugin

####Test using the Social Monitor
- Create a new social monitor
- Fill a name to identify it internally
- Select monitoring method [Mention, Hashtag]
- Enter the profile name for mention, or the hashtag you wish to fillow

This should look for mentions or hashtag posted on the profile used to create the app and create contacts who have used any of these methods

####Test using a form
- Create a new form and use a field with the social login
- The field should display social network plugins that are enabled

If the user signs the form using the social network button it will create the lead and fill its social profile in the contact's details.
## Troubleshooting

When authorizing the plugin you might see that twitter will not let you authorize, this may be due to callback URL not entered correctly in the twitter app. Please make sure that the callback matches the one specified in the callback area of your plugin.