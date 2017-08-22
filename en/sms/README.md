# Text Messages

This new channel was added in Mautic 1.4.0. It allows Mautic to send text messages from campaigns.

## Configure Text Messages

Before you start to send text messages from your Mautic, it needs to be connected to the service which can send them. The first and default implemented service is [Twilio](https://www.twilio.com). In order to configure the text messages correctly, follow these steps:

1. Create an account at Twilio.com.
2. In Mautic, go to *Settings* (cog icon) > *Plugins*.
3. Open *Twilio* plugin and activate it.
4. Copy the *Account SID* from Twilio account and paste it to *Account SID* field in the Twilio plugin configuration.
5. Unlock and copy the *Auth Token* and paste it to *Auth Token* field in the Twilio plugin configuration.
6. Go to *Products* > *Phone Numbers* in Twilio, copy the number and paste it to the *Sending Phone Number* field in Mautic.
7. Select the *Text Message Enabled?* switch to *Yes* and save the Mautic configuration.

## Create a new Text Message

A Text Message can be created/modified only via Campaign Builder.

1. Go to *Campaigns*.
2. Edit an existing campaign or create a new one.
3. Open the Campaign Builder.
4. Add a *Send Text Message* action to the cancas.
5. Click the *New Text Message* button. The form in a new browser window will appear.
6. Fill in the *Internal Name*, *Text Message* and if required, change the language. Save it.

The new Text message will be pre-selected so you can save the *Send Text Message* action as well. You can use the action in your Campaign dripflow.
