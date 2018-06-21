# Mautic - Connectwise CRM plugin

This plugin can push/pull a contact to/from Connectwise Manage.

## Requirements

- A Connectwise Manage account.
- Connectwise company id
- Connectwise api member with administrative role

## Get the Connectwise client member credentials

You will need your company id in order to authenticate the Connectwise plugin.
To create a new API member you will need to use the thick client. you can dowload [here](https://university.connectwise.com/university/pageview.aspx?short_name=workstation-installation). Go to: *System/member* and you can create a new API member there. You will also have a link to get your public and private keys.

Copy the public and secret keys.


## Configure the Mautic Connectwise plugin

Insert the keys to the Mautic Connectwise plugin and authorize it.
![Connectwise CRM Authorize](./../plugins/media/connectwiseauth.png "Connectwise CRM Authorize")

Configure the [field mapping](./../plugins/field_mapping.html).
Please map all fields marked in red, as these are required fields.

### Features
Enabled features:
You can pull contacts  from the integration.

Push leads is done through a form or a campaign.

Pull leads is done through command line and it can be setup as a cronjob.

Feature specific settings:
Select the objects you wish to pull or push records from. You can push contacts to the Contacts modules in connectwise.

Pulling records will be done from Contacts module in Connectwise to contacts in Mautic records and Companies from Connectwise will be pulled into Mautic companies.

### Command line script to pull records from Connectwise
To pull records from Connectwise you need to use a command from CLI. Use this command:

Used to pull records from the Leads object in Connectwise

- php app/console mautic:integration:fetchleads


Parameters both commands take:

**--time-interval** This parameter is used to setup the amount of time we want to pull records from. Possible entries: "10 days", "1 day", "10 minutes", "1 minute".  Maximun time interval "29 days".

**--integration**=Connectwise to use with Connectwise integration.  In future this command may be used for other integrations.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.

##Connectwise Contact Activities

![Connectwise CRM Activites](./../plugins/media/connectwise-activites.png "Connectwise CRM activities")
You can create new contact activities in Connectwise through a campaign action. To do so follow these steps.

1. Create a new campaign or use an existing one.
2. Use a push to integration action and select Connectwise. You should see the option to push activites.
3. Select No if you only wish to push campaign contacts to your Connectwise integration.
4. Select Yes and fill in required fields if you wish to push contacts and ativities related to each campaign contact. Activity name and member owner are required fields.

![Connectwise CRM Action](./../plugins/media/connectwise-action.png "Connectwise CRM campaign action")

###In Mautic Segments 
You can create a mautic segments composed of contacts that are in a Connectwise campaign group. To do this create a segment filter **Integration Campaign Member** option, then in the filter properties select the name of the campaign group you wish to get group members from.
 ![Connectwise CRM segment filter](./../plugins/media/segment-filter.png "Connectwise CRM segment filter")
 ![Connectwise CRM campaign groups](./../plugins/media/connectwise-campaign-segment.png "Connectwise CRM campaign filters")  
