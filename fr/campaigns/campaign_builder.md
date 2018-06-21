# Générateur de campagne

Le générateur de campagne Mautic vous ouvre zone de travail blanche sur laquelle vous pourrez mettre en place votre scenario. L'interface simple et épurée vous aidera à déposer vos actions et décisions.

### Sources

La première chose à faire, est de sélectionner d'où viennent les contacts qui vont être ajoutés à la campagne. Il y a deux options : les segments et les formulaires de campagne.

![](/campaigns/media/contact-sources.png)

Une fois la source choisie, l'étape suivant est d'ajouter les actions de campagne, les decisions et/ou les décisions :

![](/campaigns/media/events.png)

### Actions

Les actions de campagne sont les objets que vous allez ajouter à votre campagne. Ceux-ci s'appliqueront aux contacts qualifiés à votre campagne. Les actions peuvent être les suivantes ; ajuster les points des contacts, changer les campagnes dans lesquelles le contact est présent, modifier les listes dans lesquelles le contact appartient, envoyer un email, changer une valeur du contact, envoyer un SMS, etc.

Lors de la création d'une campagne, vous choisirez une de ces actions pour démarrer votre scénario. Dans la majorité des cas, votre campagne démarrera par l'envoi d'un courriel à l'une de vos listes.

![](/campaigns/media/send-email-delay.png)

Vous noterez que lorsque vous ajouter l'envoi d'un courriel à votre campagne, vous pourrez choisir un *délai* pour l'envoi du courriel.

![](/campaigns/media/send-email-delay-nonaction.png)

Après avoir ajouté une action à votre campagne, vous y lierez probablement une décision.

### Décisions

Les décisions représentent les actions initiées par les contacts. Ces décisions peuvent être initiée par le contact ou basé sur sa non-action. Les décisions sont liées au téléchargement d'une ressource, l'ouverture d'un courriel, la soumission d'un formulaire, la visite d'une page du site web ou d'un page de destination.+

La décision est la réponse à une action donnant lieu à deux issues.+

![](/campaigns/media/decision-anchors.gif)

Ces deux issues sont représentées par les points rouge et vert sur l'objet décision. Vous pouvez utiliser chacune de ces deux issues. Ce processus correspond à un **arbre de décision**.

__Il est important de comprendre qu'un contact doit déjà faire partir de la campagne afin de pouvoir prendre part à un décision. De plus, une campagne ne peut jamais démarrer par une décision.__

#### Décision initiée par l'action du contact (point vert)

Les actions attachées au point vert sont considerées comment étant à l'iniative du contact.

Cela prend part d'un résultat du comportement d'un contact comme l'ouverture d'un courriel ou la soumission d'un formulaire. Les actions de campagne connectées seront executées (ou prévues si un délai est paramétré) au moment où le contact aura le comportement attendu par la décision.

#### Décision initiée par la non-action du contact (point rouge)

Les actions attachées au point rouge sont considerées comme la conséquence d'une non-action de la part du contact.

Utilisez le délai d'une action de campagne, pour définir à partir de combien de temps de non-action le contact doit être qualifié dans la branche négative de la décision.

Pour déclencher cet événement, voir [Exécution des événements de campagne](https://mautic.org/docs/en/campaigns/manage_campaigns.html#executing-campaign-actions).

#### Exemple

Pour vous donner un exemple simple d'un arbre de décision, imaginez un courriel envoyé à une liste où la décision liée est l'ouverture du courriel. Il y a deux issues, si le contact ouvre le courriel le contact rentrera dans la branche verte de la décision pour rejoindre la prochaine action de campagne selon votre scénario. En revanche, si le contact n'ouvre pas l'email et que vous désirez mettre en place une action différente comme un courriel de relance au bout de 30 jours si le courriel reste non-ouvert, liez-y l'envoi d'un courriel pour seconde action de campagne avec un délai paramétré de 30 jours.


### Conditions

Les conditions permettent de mettre en place différentes actions de campagne en fonction de la donnée associée au contact. par exemple, une condition peut être ajoutée pour exécuter une action de campagne différente si le contact a une adresse email ou pas (on peut imaginer envoyer plutôt un SMS).

__Le délai que vous pouvez ajouter sur une condition est attendu avant de vérifier la condition, peu importe le délai paramétré sur l'action suivante attachée à la condition. Le délai paramétré sur l'action de campagne attachée ne sera pas attendu pour vérifier le statut de la condition.__

Actuellement, il y a 2 types de conditions
1. Conditions sur la valeur d'un Champ de contact.
2. Conditions sur la valeur d'un Champ de formulaire.

#### Condition positive (point vert)

Les actions de campagne attachées au point vert de la condition sont considérés comme la réponse positive à la condition.

#### Condition négative (point rouge)

Les actions de campagne attachées au point rouge de la condition sont considérés comme la réponse négative à la condition.
