# Gmail Plugin for Mautic
This plugin allows for the [Mautic Helper Chrome Extension](https://chrome.google.com/webstore/category/extensions) to keep track of emails sent to leads from within Gmail.

### Requirements

- Mautic installed on a publicly accessible URL.
- Gmail account (for email tracking).
- [Mautic Helper Chrome Extension](https://chrome.google.com/webstore/category/extensions)

### Configure the plugin
1. Install the Mautic plugin as usual. It will appear on the plugins page in Mautic.
![image](https://cloud.githubusercontent.com/assets/2924026/18927139/dc426b0e-8577-11e6-934d-d428c2bf8cef.png)

2. Click on the Gmail plugin button and enter a secret or key to validate the Mautic Helper Chrome Extension
![image](https://cloud.githubusercontent.com/assets/2924026/18927155/f336b23e-8577-11e6-99a7-9e1e5b493f5c.png)

3. Install the [Mautic Helper Chrome Extension](https://chrome.google.com/webstore/category/extensions) from the Chrome Web Store
![image](https://cloud.githubusercontent.com/assets/2924026/18927690/2c995d2c-857a-11e6-9870-c5bf5b27e3be.png)

4. Configure the extension using the options page that will automatically be displayed. (Remember to use the same secret you entered in Mautic)
![image](https://cloud.githubusercontent.com/assets/2924026/18927264/63b57608-8578-11e6-8721-07c0422ab9b8.png)

5. On the Chrome browser there will be a button that will notify of new events on the contacts timeline.
![image](https://cloud.githubusercontent.com/assets/2924026/18927593/cea645ea-8579-11e6-90e3-d760d0d0d682.png)

6. To track an email sent to a lead, click the Track Email button on the Compose window in Gmail
![image](https://cloud.githubusercontent.com/assets/2924026/18927624/e54bd2f6-8579-11e6-92f1-880fcc1c5839.png)

7. This will append a tracking GIF to the email with the following syntax:  [[MAUTIC_URL]]/index.php/gmail/tracking.gif?d=H4sIAAAAAAAEAIVRTW%2FCMAz9LRyCtgNVlFBpHHroWsRuk8ak7RpaUzqaGCUp0H8%2Fpy0TH4dJUZy892w921uLOvkCa8BGK2WLWi2dt6pUbM7PYPEcFainoFXdJKdBVvUy4quA9rxrNz9Q%2BCQ16HdgmeAenKewpfIU3lvfIO6nGyy75HNXO8LQAN3984R2X5tqMpkwnjOejrfg19%2FBJIHBJsskS3M1MOvOedChUA5HaPBAsp54a7UyBH%2BAw9YWECRrsMc6PHvFd2iR0NfW1QbcjUDwMjhctYqqq0YxkQU6SqMhNxi85GeoD8p0134zaBom%2By4ezlPMxTPFeCH5TLzI%2BdgizeEu5aIUQixmIubjSG5WAY8bC8kyC%2FvxSBX%2Flcvl3bT%2Fvr8k1oBgIQIAAA%3D%3D&sig=cf078d5b

8. The Mautic plugin will then validate the information using the secret to compare signatures and then attach that email to the contact’s profile as part of their activity history. If the lead or leads don't exist, they are created automatically
![image](https://cloud.githubusercontent.com/assets/2924026/18927644/f70f71fa-8579-11e6-91be-6acaba36e7e6.png)

## URL Parameter Length Issue
; Please note that PHP setups with the suhosin patch installed will have a                                   
; default limit of 512 characters for get parameters. Although bad practice,                                 
; most browsers (including IE) supports URLs up to around 2000 characters,                                   
; while Apache has a default of 8000.                                                                        

; To add support for long parameters with suhosin add the following to php.ini                                                         
suhosin.get.max_value_length = 5000
