# Mautic - Microsoft Dynamics CRM bi-directional plugin

This plugin can push/pull contacts to and from Dynamics CRM when a contact makes some action and when manually executing the sync leads command.

If you don't have a Dynamics CRM account, follow the instructions below to create a Trial Dynamics 365 account.

## Configure the Dynamics CRM plugin

Insert your Dynamics CRM URL, the Application ID and Secret into the Mautic Dynamics integration plugin and authorize it. Set the *Publish* switch to *Yes*. Save.

![Dynamics CRM Plugin configuration](media/dynamics/858c5a2a7134.png "Dynamics CRM Plugin configuration")

Select the features you like in the Features tab. *Push contacts to this integration* checkbox and is checked by default.

Configure the [field mapping](./../plugins/field_mapping.html).

Save the plugin configuration.

## Test the plugin

Follow [these steps](./../plugins/integration_test.html) to test the integration.

#### How to create a Dynamics 365 Trial account
#### Set Up Dynamics 365:
1. Go to the [Dynamics 365 Trial website](https://www.microsoft.com/en-us/dynamics/free-crm-trial.aspx)

![image](media/dynamics/bbdb46ab545f.png)
![image](media/dynamics/8106fe116d63.png)
![image](media/dynamics/d08c1298aa54.png)
![image](media/dynamics/7084b5f865d5.png)
![image](media/dynamics/fd5952a2005f.png)

#### Set Up Azure
1. Go to the [Azure Portal](https://portal.azure.com)
2. Log in with your onmicrosoft.com account

![image](media/dynamics/4e7c9a85014f.png)

3. Go to Azure Active Directory 

![image](media/dynamics/1ecee71fe408.png)

4. Add a new Application Registration

![image](media/dynamics/72e65de87640.png)

5. Fill in the CRM Application information

![image](media/dynamics/402a6170bc22.png)

6. Click on Create
7. Click on the Application you just created

![image](media/dynamics/3570e550894a.png)

8. You will use the Application ID when configuring the plugin in Mautic

![image](media/dynamics/1f320e76452e.png)

9. Add a new Key. Use any name, click on save and copy the value. You will use it as the plugin secret in Mautic.

![image](media/dynamics/a53a371dd0fb.png)
![image](media/dynamics/5b254970ed35.png)

10. Configure the reply URLs using the callbacks from the plugin settings in Mautic. Click Save

![image](media/dynamics/e2a837fe2fc7.png)

11. Configure the Required Permissions. Click on Add 

![image](media/dynamics/a2482b3511de.png)

12. Add Dynamics CRM Online Api Access. Click Select

![image](media/dynamics/b6977cfd4de7.png)

13. Enable Dynamics CRM access for the users. Click Select and then click Done

![image](media/dynamics/7de74e72ae3d.png)

15. Activate the permissions by clicking "Grant Permissions". Click Yes

![image](media/dynamics/abc667cdd178.png)

16. Go back to Mautic
17. Authorize the plugin

![image](media/dynamics/858c5a2a7134.png)

18. Use your onmicrosoft.com account to authenticate:

![image](media/dynamics/3a66e53a9265.png)

19. The plugin is ready. You can test using "Push to Integration" form and campaign actions.
20. You can also test by executing the command: `php app/console mautic:integration:fetchleads -i Dynamics`
