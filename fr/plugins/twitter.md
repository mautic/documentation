# Mautic - Twitter plugin

Ce plugin permet :
* D'afficher le profil public et de faire correspondre les champs des contacts
* Afficher l'activité publique
* Afficher un bouton de partage depuis les pages d'atterrissage

### Pré-requis

Twitter doit approuver l'application Webmecanik Automation afin de récupérer les informations des utilisateurs Twitter.

### Autorisation du plugin

Afin de les obtenir, vous devez réaliser les étapes suivantes :
1. Avoir un compte Twitter
2. Créer une [application Twitter ici](https://apps.twitter.com)
3. Cliquer sur le bouton *Create New App*.
4. Remplir les informations demandées, Une des informations importantes est l'URL de rappel (callback) qui est affichée dans le plugin Twitter de votre compte Mautic.

Une fois l'application Twitter créée, vous obtiendrez une *clé d'authentification* (clé API) ainsi que votre *Consumer Secret* (API Secret).

### Configuration du plugin

Si l'autorisation est faite correctement, vous pouvez configurer les *Fonctionnalités* et l'onglet de *Mapping des champs de contact* dans la configuration du plugin.

Les tweets des contacts vont remonter dans la fiche de chaque contact dès que l'ID Twitter du contact est renseigné.

Utilisez le token `{sharebuttons}` lorsque vous créez des pages d'atterrissage Mautic pour afficher un bouton de partage.
