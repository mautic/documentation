# SMS

Cela permet à votre compte Mautic depuis la version 1.4.0 d'envoyer des SMS depuis les campagnes.

## Configurer les SMS

Avant de pouvoir envoyer des SMS depuis votre compte Mautic, il est nécessaire de connecter au routeur qui enverra les SMS [Twilio](https://twilio.com). Afin de connecter le SMS correctement, suivez les étapes suivantes :

1. Créez un compte sur Twilio.com.
2. Allez dans *Account Settings*. Vous y trouverez les *API Credentials*.
3. Ouvrez la configuration Mautic dans une autre page : Configuration > Paramètre SMS.
4. Copiez le *AccountSID* (celui ci doit être celui du compte, pas du numéro de téléphone) depuis votre compte Twilio et collez le dans le champ *Identifiant du routeur SMS* de Mautic.
5. Débloquez et copiez le *AuthToken* afin de le coller dans le champ Mautic *Mot de passe du routeur SMS*.
6. Allez dans *Products* > *Phone Numbers* dans Twilio, copiez le numéro et collez le dans le champ de Mautic *Numéro de téléphone d'envoi*. Attention, il doit être au format +33600000000.
7. Passez le champ *SMS activé ?* à *Oui* et sauvegardez le panneau de configuration Mautic.

## Créez un SMS

Un SMS peut être créé/modifier seulement depuis l'éditeur de campagne.

1. Allez dans *Campagnes*.
2. Editez une campagne existante ou créez une nouvelle.
3. Ouvrez l'éditeur de campagne.
4. Faites glisser l'action *Envoyer un SMS*.
5. Cliquez sur le bouton *Nouveau SMS*. Un formulaire dans une nouvelle fenêtre va s'afficher.
6. Remplissez *Nom interne*, *SMS* et si besoin, changez la langue. Sauvegardez.

Le nouveau SMS sera automatiquement pré-sélectionné. Vous n'avez plus qu'à utiliser l'action dans votre scénario de campagne !
