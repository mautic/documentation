# Web Notifications

<<<<<<< HEAD
Web notifications integrate [One Signal](https://onesignal.com/). Using your ownOne Signal accounts, you can now push a notification to their browser (with the contacts permission). Enable these in Mautic's Configuration to see them listed under Channels in the menu.
=======
Web notifications  integrate [One Signal](https://onesignal.com/). Using your ownOne Signal accounts, you can now push a notification to their browser (with the contacts permission). Enable these in Mautic's Configuration to see them listed under Channels in the menu.
>>>>>>> mautic/master

For more informations see [One Signal documentation](https//documentation.onesignal.com/docs/web-push-setup)

#### Setup

##### 1. Create [One Signal](https://onesignal.com/) account and app

<<<<<<< HEAD
##### 2. Setup app Website Push Platforms in you app
=======
##### 2. Setup app  Website Push Platforms in you app
>>>>>>> mautic/master

![](/notifications/notification-setup1.PNG)

Google Chrome and Mozilla Firefox configuration example

![](/notifications/notification-setup2.PNG)

Apple Safari (macOS) configuration example

![](/notifications/notification-setup3.PNG)

<<<<<<< HEAD
##### 3. Setup Mautic

Enable Web Notification and copy keys from OneSignal to your Mautic > Settings > Configuration - Web Notification Settings tab
=======
##### 3. Setup Mautic 

Enable Web Notification and copy  keys from OneSignal to your Mautic > Setings > Configuration - Web Notification Settings tab
>>>>>>> mautic/master

![](/notifications/notification-setup4.PNG)

![](/notifications/notification-setup5.PNG)

##### 4. Test

<<<<<<< HEAD
All visitors with supported browser will be ask receive notification on all you Mautic landing pages. Create campaign and use Push Website notification action.
=======
All visitors with supported browser will be ask receive notificion on all you Mautic landing pages.  Create campaign and use Push Website notification action.
>>>>>>> mautic/master

#### Welcome Notifications

Option to allow disable welcome notifications.
<<<<<<< HEAD
For more informations see [One Signal documentation](https://documentation.onesignal.com/docs/welcome-notifications)
=======
For more informations see [One Signal documentation](https://documentation.onesignal.com/docs/welcome-notifications) 
>>>>>>> mautic/master

### gcm_sender_id

Option gcm_sender_id is a shared key used for push notifications.
Use default value 482941778795. Previously it required your own key. Due backwards compatibility is editable (for older Mautic).
<<<<<<< HEAD
=======
  
>>>>>>> mautic/master
