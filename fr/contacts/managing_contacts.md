# Gestion des contacts

La page "Contacts" est l'interface principale à travers lequel vous pouvez voir et d'interagir avec vos contacts - les deux type de contacts anonymes et ceux avec des informations supplémentaires y sont disponibles.

## Liste des contacts

La liste de contacts est la vue format tableau par défaut de tous les contacts dans le système - par défaut, la **vue tableau** est activée, mais vous pouvez aussi choisir de passer à la **vue en cartes** qui utilise des avatars pour représenter les prospects visuellement en utilisant des "cartes". Vous devez utiliser les raccourcis clavier, vous pouvez taper "t" sur votre clavier pour changer de façon dynamique à la vue de tableau et "c" pour passer à la vue carte.

## Recherche de contacts

Les contacts peuvent être recherchés en utilisant le champs en haut de la liste, et peut être ordonnée en utilisant les titres des tableaux en cliquant sur la rubrique que vous souhaitez trier.

![](/contacts/media/contacts-search.jpg)

Le moteur de recherche permet à de nombreux types de recherche différentes et suit le même processus de recherche et les variables que l'on trouve dans tous les autres modèles de recherche. Vous pouvez en apprendre davantage sur les options puissantes de recherche disponibles sur la page de documentation de recherche.

## Ajouter un contact rapidement

Si vous avez des contacts que vous souhaitez ajouter rapidement à la main dans Mautic, et qu'ils ne sont pas dans le système dans le cadre du processus normal (par exemple en remplissant un formulaire de demande de renseignements ou ayant été importée), vous pouvez utiliser le bouton "Ajout rapide d'un contact" afin de les ajouter au système.

Vous pouvez bien sûr ajouter un contact en cliquant sur le bouton "Nouveau" ce qui ouvre le formulaire d'ajout de contact et vous permet d'ajouter beaucoup plus de détails, mais pour une saisie rapide ceci est le moyen le plus simple et le plus rapide pour obtenir le contact dans le système.

## Ajouter un contact normalement

Si vous avez des contacts à importer et vous avez le temps d'ajouter toutes les informations, cliquez sur la flèche déroulante à droite du bouton "Ajout rapide de contact" et sélectionnez "Nouveau". Cela ouvre le nouvel écran d'ajout de contact, où vous pouvez entrer toutes les informations que vous avez en tête. Utilisez les onglets en haut pour ajouter des champs personnalisés et des profils de réseaux sociaux.

## Importer des contacts

Mautic vous donne la possiblité d'importer vos contacts depuis un fichier au format CSV. C'est une bonne opportunité pour démarrer rapidement en important vos contacts en masse, même s'ils sont nombreux.

Pour vous assurer d'importer vos contacts dans les meilleurs conditions, soyez sûr d'avoir créé en amont tous les champs personnalisés dont vous avez besoin dans le menu 'Gestion des champs' afin de faire correspondre les champs que vous allez importer avec ceux disponibles dans la structure de la base de données Mautic. Cela vous évitera de perdre des informations précieuses pour votre segmentation.

Une fois que vous avez créé tous les champs de contacts nécessaires à votre import, appuyez sur le bouton en haut à droite 'Importation'.

Séléctionnez votre fichier au format CSV, vérifiez que les séparateurs (format internationnal avec une virgule, format européen par défaut avec le point virgule), pièces jointes et caractères d'échappement correspondent bien aux paramètres de votre fichier CSV afin que l'outil d'import interprète correctement la donnée.
Lors du clic sur 'Chargement' vous pourrez alors faire correspondre les champs de votre fichier CSV avec les champs paramétrés dans Mautic.

Pour l'import sur les champs de type booléen, les valeurs suivantes sont considérées comme positives : `1`, `true`, `on` et `yes`. Elles peuvent également être écrite en capitales. Toute autre valeur sera considérée comme négative.

## Modification d'un contact

Pour modifier un contact, cliquez sur son nom (où sur l'adresse IP si le visiteur est anonyme) pour ouvrir la page du contact.
Depuis cette page, vous pouvez voir l'activité récente du contact, et les notes qui lui sont attachées.

Pour modifier le contact, cliquez sur le bouton 'Modifier' en haut à droite de la page du contact.

## Contacts en doublon

Quand Mautic traque les actions d'un contact, il fusionnera automatiquement les contacts qui ont un identifiant unique en commun :
- Email _(ou n'importe quel champ du contact qui est paramétré en clé unique)_
- Cookie

Si un contact soumet un formulaire avec une adresse email, cela fusionnera le contact avec celui existant avec la même adresse email. Même si le cookie correspond à un autre contact.

Mautic fait attention automatiquement aux contacts créés par le tracking afin de ne pas faire de doublons. Vous pouvez toujours volontairement créer un doublon depuis l'interface de création de contact. Depuis Mautic 2.1.0, vous serez notifié lorsque vous essayerez de crér un contact qui a déjà un ID unique existant.
