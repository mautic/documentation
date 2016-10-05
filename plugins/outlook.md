# Mautic - Outlook plugin

This plugin allows for the Outlook Add-In to keep track of emails sent to leads.

The Add-In source code can be found at [https://github.com/virlatinus/MauticOutlookPlugin/](https://github.com/virlatinus/MauticOutlookPlugin/)

### Requirements

- Mautic installed on a publicly accessible URL.
- Microsoft Outlook 2016.
- [Mautic Outlook Add-In for Outlook 2016](https://github.com/mautic/mautic/files/402928/Mautic.Outlook.Plugin.Setup.zip)

### Configure the plugin

1. Install the Mautic plugin as usual. It will appear on the plugins page in Mautic.
![image](https://cloud.githubusercontent.com/assets/2924026/17381507/7f871a1e-5989-11e6-8277-8ae83c70f7d7.png)

2. Click on the Outlook plugin button and enter a secret or key to validate the Outlook Add-In
![image](https://cloud.githubusercontent.com/assets/2924026/17422110/16d49c56-5a6c-11e6-9cd2-5d11e0c87df4.png)

3. Run the [Mautic Outlook Add-In Installer](https://github.com/mautic/mautic/files/402928/Mautic.Outlook.Plugin.Setup.zip) on a Windows machine with Outlook 2016

4. On the Outlook 2016 Options window, select Add-Ins and click on the Add-In Options button
![image](https://cloud.githubusercontent.com/assets/2924026/17381486/65994096-5989-11e6-9080-f56f27e2f752.png)

5. Type in the URL of the Mautic application, the same secret you used on the Mautic plugin page and click OK
![image](https://cloud.githubusercontent.com/assets/2924026/17422140/6e2ff32e-5a6c-11e6-96e2-230b9418ca42.png)

6. To track an email sent to a lead, click the Track Email button on the New Email window
![image](https://cloud.githubusercontent.com/assets/2924026/17436619/8dfe2a54-5ad5-11e6-829b-d0b90aebf63f.png)

7. This will append a tracking GIF to the email with the following syntax:  [[MAUTIC_URL]]/index.php/outlook/tracking.gif?d=H4sIAAAAAAAEAIVRTW%2FCMAz9LRyCtgNVlFBpHHroWsRuk8ak7RpaUzqaGCUp0H8%2Fpy0TH4dJUZy892w921uLOvkCa8BGK2WLWi2dt6pUbM7PYPEcFainoFXdJKdBVvUy4quA9rxrNz9Q%2BCQ16HdgmeAenKewpfIU3lvfIO6nGyy75HNXO8LQAN3984R2X5tqMpkwnjOejrfg19%2FBJIHBJsskS3M1MOvOedChUA5HaPBAsp54a7UyBH%2BAw9YWECRrsMc6PHvFd2iR0NfW1QbcjUDwMjhctYqqq0YxkQU6SqMhNxi85GeoD8p0134zaBom%2By4ezlPMxTPFeCH5TLzI%2BdgizeEu5aIUQixmIubjSG5WAY8bC8kyC%2FvxSBX%2Flcvl3bT%2Fvr8k1oBgIQIAAA%3D%3D&sig=cf078d5b

8. The Mautic plugin will then validate the information using the secret to compare signatures and then attach that email to the contact’s profile as part of their activity history. If the lead or leads don't exist, they are created automatically
![image](https://cloud.githubusercontent.com/assets/2924026/17436673/f4b6029e-5ad5-11e6-8905-4aaa0ff4202c.png)

  ![image](https://cloud.githubusercontent.com/assets/2924026/17436865/5b02fd26-5ad7-11e6-9a71-b26709964553.png)

  ## URL Parameter Length Issue
  ; Please note that PHP setups with the suhosin patch installed will have a                                   
  ; default limit of 512 characters for get parameters. Although bad practice,                                 
  ; most browsers (including IE) supports URLs up to around 2000 characters,                                   
  ; while Apache has a default of 8000.                                                                        

  ; To add support for long parameters with suhosin add the following to php.ini                                                         
  suhosin.get.max_value_length = 5000
  
