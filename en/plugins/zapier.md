# Mautic Zapier Integration

This integration integrates any Mautic instance with 1.100+ third party web services via the [Zapier](https://zapier.com) web automation service.

## Requirements

Zapier account. Free or Paid. [View Zapier pricing](https://zapier.com/pricing/).

## Installation

There is no need to install any additional plugin to your Mautic instance. Zapier works with the API and webhooks already available within Mautic.

### Setup Oauth2 Authentication in Mautic for Zapier 3.x

This new version of the app improves authentication by implementing the Oauth2 protocol

1. Open the admin menu
2. Go to Mautic's global configuration > API Settings
3. Set __API enabled?__ to __Yes__.
4. Save the configuration.
5. Go to Mautic's global configuration > API Credentials > __Oauth2__
6. Create new __Oauth2___ application with redirect URI: __tba__
7. Copy Public Key and Secret Key of your created app

![How to enable the API](https://user-images.githubusercontent.com/462477/74520415-cc616b00-4f17-11ea-8dbe-f6dd8a0a6cfc.png)

__Note__: **Refresh token lifetime (in days)**  means how many days need app to refresh token. If your app will not have any activity in that period, you have to re-authorize it again. 

![New Oauth2 application](https://user-images.githubusercontent.com/462477/74520342-a1771700-4f17-11ea-866f-5be1c895f0f9.png)

Zapier will be able to create actions and triggers with your Mautic installation.

## Sign up for a Zapier account

1. Go to the [Zapier website](https://zapier.com).
2. Select the "Sign Up for Free" button.

Or log into your existing Zapier account.

## Setup and configuration

The configured Zapier integrations are called Zaps. The main types of Zaps are Triggers and Actions.

- Triggers send data about some actions that happen in Mautic in realtime to Zapier. Zapier then transforms the data and sends it to the next app you have configured in the Zap.
- Actions send data from some other app into Mautic.

### Supported Triggers
- [x] **New Contact** - _contains contact info and field values_
- [x] **Updated Contact** - _contains contact info and field values_
- [x] **Contact Points Changed** - _contains contact info, point value and field values_
- [x] **Email Viewed** - _contains contact info and field values and info about the email_
- [x] **New Page Hit** - _contains contact info and field values, info about the page hit and the page itself_
- [x] **New Form Entry** - _contains contact info and field values, info about the form and about the submission including submitted values_

### Supported Actions
- [x] **Create or Update Contact**

### 1. Find Mautic integration

If you want some inspiration or speed up the process of creating a Zap use preconfigured Mautic Zap templates:
<div id="zapier-widget"></div>
<script src="https://zapier.com/apps/embed/widget.js?services=mautic&html_id=zapier-widget"></script>

### 2. Choose a Trigger or Action

At this point choose which Trigger or Action you need. Each trigger will get you some data about the Mautic event (page hit, email viewed, form submitted) and about the contact who did the event.

![Choose action or trigger](https://www.mautic.org/wp-content/uploads/2018/02/trigger-or-action.png)

### 3. Authorize Mautic instance

Once you choose to use Mautic integration you'll need to authorize your Mautic to it.

<img src="https://user-images.githubusercontent.com/462477/74520761-848f1380-4f18-11ea-82be-152c00020995.PNG" width="300"> 

![Mautic Zap auth](https://user-images.githubusercontent.com/462477/74520761-848f1380-4f18-11ea-82be-152c00020995.PNG)

### 4. Select an item for Triggers

Triggers will ask you to choose which entity you want to record events about. This step is required for Form Submission trigger because every form has different form fields, but it's optional for others. If you skip this step for for example Page Hits trigger Zapier will process all page hit events.

![Select entity](https://www.mautic.org/wp-content/uploads/2018/02/select-entity.png)

Zapier will let you test the integration you just configured.

### 5. Map fields

Now map the Mautic fields to the fields of the other app. In the image below is an example of mapping Mautic fields from Mautic's New Form Entry Trigger to GMail's Send Email Action.

![Map fields](https://www.mautic.org/wp-content/uploads/2018/02/map-fields.png)

That's it! Now if a contact submits a Mautic form the contact gets an email. Okay, so Mautic can do that on its own, but you get the general idea.

## How does this work

This happens when you create a new action or trigger at Zapier.

1. Zapier creates a new webhook via Mautic API at your Mautic instance specifically for this one Zap. Mautic will then send all events related to the trigger or action type to Zapier.
2. Zapier lets you map Mautic fields to the fields of the integration you want to connect to Mautic.
3. Once you make your Zap active Mautic will start receiving data (in the case of actions) and sending data (in the case of triggers).

## Integration development

Even this integration is developed as an open source software as is usual with Mautic community. Learn more at https://github.com/mautic/mautic-zapier.
