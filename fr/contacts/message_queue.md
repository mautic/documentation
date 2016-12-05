## Mise en queue des messages

Quqnd une campagne avec des emails _**marketing**_ est déclenchée ou un email de masse depuis les emails de segment et qu'un contact a un règle de fréquence définie (ou avec une configuration par défaut dans le menu Configuration), l'email sera envoyé à travers un queue avant d'être envoyé.

### Priorité et nombre de tentatives

![](/contacts/media/marketing-email.png)

- Vous pouvez paramétrer la priorité à 'Elevée' ou 'Normale'. Tous les messages avec une priorité haut seront ajoutés en haut de queue. Les emails de segment sont toujours ajoutés en priorité normale.
- Le nombre de tentatives d'envoi si le message a été mis plusieurs fois en queue, lorsque le nombre maximum de tentatives est atteint, l'email ne sera pas envoyé.

### Envoi de la queue de message
Le statut reste en attente tant que les messages sont dans la queue, tous les messages en attente qui n'ont pas atteint le maximum de tentatives seront envoyés avec la commande suivante (pour les utilisateurs de Mautic Open Source).

Paramétrez votre CRONs comme suivant :

`php app/console mautic:messages:send`
