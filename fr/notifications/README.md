# Notifications web

Les notifications web sont intégrées avec [One Signal](https://onesignal.com/). En utilisant votre compte One Signal, vous pouvez pousser des notifications sur le navigateur de votre visiteur s'il en donne la permission. Activez cette fonctionnalité dans le panneau de configuration Mautic pour voir les notifications web apparaitre dans le menu Canaux.

Pour plus d'information, se référer à la [documentation de One Signal](https//documentation.onesignal.com/docs/web-push-setup)

#### Paramétrage

##### 1. Créez un compte [One Signal](https://onesignal.com/)

##### 2. Paramétrez une application web push

![](/notifications/notification-setup1.PNG)

Exemple de configuration Google Chrome et Mozilla Firefox

![](/notifications/notification-setup2.PNG)

Exemple de configuration Safari (macOS)

![](/notifications/notification-setup3.PNG)

##### 3. Paramétrage dans Mautic

Activez les notification web et copiez les clés d'identification OneSignal dans Mautic > Configuration > Paramètres - Notification web

![](/notifications/notification-setup4.PNG)

![](/notifications/notification-setup5.PNG)

##### 4. Test

Tous les visiteurs avec un navigateur suffisament à jour recevront une notification sur vos pages d'atterrissage Mautic. Utilisez les campagnes pour paramétrer une action de notification web.

#### Notification d'accueil

Il y a une option pour activer/désactiver une notification d'accueil.
Pour plus d'informations, voir la [documentation One Signal](https://documentation.onesignal.com/docs/welcome-notifications)

### gcm_sender_id

L'option gcm_sender_id est une clé paratagée pour les notifications push.
Utilisez la valeur par défaut 482941778795.
