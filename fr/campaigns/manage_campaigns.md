# Gestion des campagnes

### Aperçu des campagnes

L'aperçu d'une campagne vous affichera de nombreux details associés à votre campagne comme le nombre de contacts ajoutés à cette dernière, le nombre d'emails envoyés ou encore le nombre de pages vues générées grâce à cette campagne.

Des informations complémentaires vous donneront un rapide aperçu sur les décisions et actions paramétrées dans la campagne, tout comme des statistiques sur le parcours des contacts dans la campagne.

Tout comme l'ensemble des pages d'aperçu, vous verrez affiché l'historique des activités associé à cette campagne dans la barre latérale de droite.

### Création de campagne
La création d'une campagne est un processus simple qui vous demandera de choisir un nom, ajouter une déscription (facultatif), et définir la source de contacts de la campagne (segment ou formulaire de campagne). Ces campagnes peuvent être assignées à une catégorie et actives ou inactives. Toutes ces informations sont les standards de la création d'une campagne.

**Note** : La sélection des segments ne pourra se faire que sur les segments publiques. Les segments privés ne peuvent être utilisés dans les campagnes.

A partir de ces pré-requis, vous pouvez utiliser le générateur de campagne pour scénariser la relation automatisée que vous souhaitez mettre en place avec vos contacts.

### Exécution des actions de campagne

L'exécution des campagnes se fait en plusieurs étapes, l'ajout des contacts à la capagne, de déclenchement des actions et la vérification sur les "non-actions" sur les arbres décisionnels. Pour faire cela, il faut paramétrer les CRONs avec la commande suivante (pour les utilisateurs de Mautic Open Source):

```
php /path/to/mautic/app/console mautic:campaigns:trigger --env=prod
```

Si vous souhaitez exécuter la commande à des intervalles de temps spécifiques en fonction des campagnes, vous pouvez ajouter l'argument `--campaign-id=ID` à la commande.

### Mise à jour des contacts participant aux campagnes

L'ajout et suppression des contacts dans les campagnes se fait par le CRONs suivant (pour les utilisateurs de Mautic Open Source):

```
php /path/to/mautic/app/console mautic:campaigns:update --env=prod
```
