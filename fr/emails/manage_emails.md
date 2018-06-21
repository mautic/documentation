# Gestion des emails

### Aperçu d'un email

L'aperçu d'un email vous permet d'avoir en un coup d'oeil de nombreuses informations à propos du succès ou d'un échec d'un email. Vous pouvez rapidement avoir un regard sur le nombre d'ouvertures, les rebonds, les clics sur les liens ou autres statistiques.+

### Création d'un email

La création d'un email peut se faire de 3 manières différentes ;
1. grâce au générateur de campagne en ayant sélectionné un thème prédéfini
2. en important votre code HTML
3. ou en créant un email au format texte

Les emails sont à utiliser dans vos campagnes, ou directement grâce aux emails de segment en sélectionnant un segment de contacts associé.

### Traductions

Lors de la création de l'email, vous avez la possibilité d'ajouter une langue et une taduction parente. En sélectionnant une traduction parente, cela vous permet d'ahouter une traduction enfante de l'email en cours. Si le contact a une langue de préférence paramétrée, il recevra l'email dans la langue paramétrée si la variante existe. Autrement, les contacts recevront l'email dans la langue par défaut.

Il est également possible de faire des traductions de versions A/B.

### Emails de segments

Lorsque vous créez un email de segment, vous pouvez directement lors de sa configuration, sélectionner un ou plusieurs segments auxquels vont être adressés l'email.

![](/emails/media/email-segments.jpg)

Ce type d'email ne peut pas être utilisé dans une campagne. Il est plutôt adapté à vos emails de type newsletter.

### Le générateur d'email

Le générateur d'emails vous donne accès à une interface graphique qui ne nécessite pas de connaissance en HTML grâce à ses fonctionnalités en glisser-déposer.

Il vous donne accès rapide aux ressources, pages d'atterrissage, et tout autres champs considérables comme importants. ils sont tous accessible avec des tokens du type `{component=item}`, par exemple `{contactfield=company}`. Une liste déroulante avec les options va apparaitre lorsque vous allez commencer à écrire le caractère `{`.

Un token peut avoir une valeur par défaut lorsque le contact n'a pas de valeur renseigné dans le champ. La valeur par défaut peut être spécifiée après le caractère `|` de la manière suivante : {contactfield=company|Default text}.

Les tokens peuvent être utilisés dans l'objet des emails.

### Encodage des images en Base64

Depuis Mautic 1.4, il y a une configuration Mautic dans la zone de paramétage des emails. Vous pouvez demander à Mautic d'encoder toutes les images en base64.

![](/emails/media/base64-images.jpg)

### Désactivation du pixel de tracking

Vous pouvez désactiver l'ajout de pixel de tracking, cela peut parfois aider à l'affichage des autres images qui sont bloquées par certains clients emails lors de l'insertion de pixels de tracking.
