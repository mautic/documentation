# Mautic - Microsoft Dynamics CRM bi-directional plugin

This plugin can push/pull contacts to and from Dynamics CRM when a contact makes some action and when manually executing the sync leads command.

If you don't have a Dynamics CRM account, follow the instructions below to create a Trial Dynamics 365 account.

## Configure the Dynamics CRM plugin

1. Insert your Dynamics CRM URL, the Application ID and Secret into the Mautic Dynamics integration plugin and authorize it. Set the *Publish* switch to *Yes*. Save.

   ![Dynamics CRM Plugin configuration](media/dynamics/858c5a2a7134.png "Dynamics CRM Plugin configuration")

1. Select the features you like in the Features tab. *Push contacts to this integration* checkbox is checked by default.
1. Configure the [field mapping][field mapping].
1. Save the plugin configuration.

## Set Up Dynamics 365

### How to create a Dynamics 365 Trial account

1. Go to the [Dynamics 365 Trial website](https://www.microsoft.com/en-us/dynamics/free-crm-trial.aspx)

![image](media/dynamics/bbdb46ab545f.png)
![image](media/dynamics/8106fe116d63.png)
![image](media/dynamics/d08c1298aa54.png)
![image](media/dynamics/7084b5f865d5.png)
![image](media/dynamics/fd5952a2005f.png)

### Set Up Azure

1. Go to the [Azure Portal](https://portal.azure.com)
1. Log in with your onmicrosoft.com account

   ![image](media/dynamics/4e7c9a85014f.png)

1. Go to Azure Active Directory

   ![image](media/dynamics/1ecee71fe408.png)

1. Add a new Application Registration

   ![image](media/dynamics/72e65de87640.png)

1. Fill in the CRM Application information

   ![image](media/dynamics/402a6170bc22.png)

1. Click on Create
1. Click on the Application you just created

   ![image](media/dynamics/3570e550894a.png)

1. You will use the Application ID when configuring the plugin in Mautic

   ![image](media/dynamics/1f320e76452e.png)

1. Add a new Key. Use any name, click on save and copy the value. You will use it as the plugin secret in Mautic.

   ![image](media/dynamics/a53a371dd0fb.png)
   ![image](media/dynamics/5b254970ed35.png)

1. Configure the reply URLs using the callbacks from the plugin settings in Mautic. Click Save

   ![image](media/dynamics/e2a837fe2fc7.png)

1. Configure the Required Permissions. Click on Add

   ![image](media/dynamics/a2482b3511de.png)

1. Add Dynamics CRM Online Api Access. Click Select

   ![image](media/dynamics/b6977cfd4de7.png)

1. Enable Dynamics CRM access for the users. Click Select and then click Done

   ![image](media/dynamics/7de74e72ae3d.png)

1. Activate the permissions by clicking "Grant Permissions". Click Yes

   ![image](media/dynamics/abc667cdd178.png)

1. Go back to Mautic
1. Authorize the plugin

   ![image](media/dynamics/858c5a2a7134.png)

1. Use your onmicrosoft.com account to authenticate:

   ![image](media/dynamics/3a66e53a9265.png)

## Test the plugin

Follow [these steps][testing] to test the integration.

1. The plugin is ready. You can test using "Push to Integration" form and campaign actions.
1. You can also test by executing the command: `php app/console mautic:integration:fetchleads -i Dynamics`

[mautic]: <https://mautic.org>
[Mautic]: <https://mautic.org>

[field mapping]: <field_mapping.html>
[testing]: <integration_test.html>
[points]: <./../points>
