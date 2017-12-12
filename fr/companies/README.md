# Société

Les sociétés sont un moyen de regrouper les contacts en se basant sur la société pour laquelle ils ont travaillé.

### Champs personnalisés de société

Avec Mautic, vous avez un certain nombre de champs par défaut pour les sociétés. Vous pouvez également en configurer des personnalisés.

1. Allez dans le menu configuration (en haut à droite) > Champs personnalisés > Créez les champs dont vous avez besoin.
2. Dans la barre latérale à droite, assignez ce champ à 'Société'.

### Segments de société

Vous pouvez créer des segments basés sur des champs de société, sélectionnez simplement n'importe quel champ de société pour votre filtre de segment. Ainsi, tous les contacts qui répondent aux critères du segment y seront ajoutés.

### Identification des sociétés

Les sociétés sont identifiables avec leur Nom (Company Name), Ville (City), et Country (Pays).

### Actions de campagne sur les sociétés

Un contact peut être ajouté à une société grâce aux actions de campagne.

#### Créer/Gérer les sociétés
Pour créer ou gérer les sociétés, allez dans le menu dédié sur la gauche de votre interface. Dans cet espace, vous pouvez créer, modifier ou supprimer des sociétés.

#### Assigner des contacts à une société
Il y a différentes manières d'assigner une société à un contact :

##### Profil du contact
Vous pouvez assigner un contact à une société depuis son profil lorsque vous créez ou modifiez le contact. La dernière société assignée sera la primaire.

##### Depuis la liste des contacts
Vous pouvez assigner en masse une société à des contacts depuis la liste des contacts.

##### Depuis une campagne
Vous pouvez assigner une société à un contact identifié avec l'action de campagne 'Assigner le contact à un société'.

##### Lors de l'identification d'un contact par un formulaire
Lorsqu'un contact s'identifie à la soumission d'un formulaire, une société peut également être assignée ou créé :
 -Le champ `Company name` fait parti des champs du formulaire (obligatoire).
 -Le champ `Country` fait parti des champs du formulaire (obligatoire).
 -Le champ `City` fait parti des champs du formulaire (obligatoire).

### Scoring de société
Le score des sociétés peut être modifié par une action de campagne ou une action de formulaire. Quand une de ces actions est sélectionnée, un contact doit être identifié et avec une société associée afin de pouvoir en faire évoluer le score.

1. Sélectionnez l'action _Modifier les points de la société_ dans le formulaire ou dans la campagne
2. Lorsque le formulaire est soumis ou que l'action de campagne déclenchée, les points de la société associée au contact seront modifiés.

### Affecter une société principale

Depuis la 2.3.0, il est possible d'assigner une société principale depuis la page du contact sachant qu'un contact peut avoir plusieurs sociétés affectées.

![](/contacts/media/primary-company.png)
