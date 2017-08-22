# Points

Les points permettent de donner de la valeur à certains prospects. Ces points peuvent déclencher des actions.

### Gestion des actions

L'ajout de point en fonction d'actions permet de changer la somme totale des points d'un prospect. Ces actions peuvent avoir un impact positif ou négatif sur les points du prospect.

Sur la capture d'écran ci-dessous, vous pouvez constater une liste des actions auxquelles vous pouvez attribuer des points.

![](/points/media/new-point-action.jpg)

### Gestion de déclencheurs

Les déclencheurs sont des événements liés lorsqu'un prospect atteint un nombre de points.

Lorsque vous mettez en place un déclencheur, vous avez la possibilité d'appliquer la règle à tous les prospects ou uniquement les futurs prospects qui répondront à ce critère.

![](/points/media/new-point-trigger-action.jpg)

### Gestion des catégories de score

Les catégories de score ont été introduits dans Mautis pour permettre aux utilisateurs de tracer les modification de points au sein de "categories" spécifiques multiples.
Selon le secteur de votre activité, si votre portefeuille de services concerne de multiples solutions différentes, il peut être intéressant de tracer l'intêret des visiteurs par Business Unit ou par Offre de solutions.

Un visiteur peut en effet visiter la page "Solution A" de votre site internet et ne souhaitera pas être embarqué dans une campagne marketing par défaut qui lui présentera d'autres solutions comme la "Solution B".

Créer une catégorie de score vous permettra de désigner des catégories spécifiques sur les Contacts et les Sociétés.

Vous pouvez accéder aux catégories de score actuellement définies en cliquant sur le lien "Gestion des catégories de score" dans le menu Points.

![](/points/media/list-scorecategory.jpg)

Veuillez noter qu'une entrée par défaut "Score Global" sera toujours présent de base and représente le champ de score général que vous retrouvez directement les pages Comptes et Contacts, au dessus des scores de catégories. 

Ce champ score global ne peut pas être édité ou ou supprimé du système comme il s'agit d'un champ de base du système implémenté dans Mautic.

Créer une nouvelle catégorie de score ne requiert que quelques informations

![](/points/media/new-scorecategory.jpg)

Entrez le nom de la catégorie de score, selectionnez l'ordre d'affichage (voir ci-dessous) et selectionnez si une modification du score de cette Catégorie affecte le score Global (Oui/Non) et si oui dans quelle proportion (Ratio, entrer un pourcentage).

Si l'impact du score global est mis à Non, toute modification du score de la catégorie ne modifiera pas le Score Global.
Si l'impact du score global est mis à Oui, la quantité de points ajoutée/retirée à la catégorie de score spécifique sera également répercutée au score global, multiplié en amont par le ratio choisi.

Par exemple : Lorsque vous ajouter 100 points à la catégorie de score "Business Unit 1", vous pouvez ajouter 100 points au score global en activant le switch et en indiquant un ratio de "100%".

#### Score Categories Order

Order in Score Categories are only used for convenience purposes on the Contacts/Companies screen to display the Score Categories in the specified order and then by alphabetical names, this allow Mautic users to choose to display a Score Category labelled "Service" before a less important Score Category labelled "Product" for example.

So Score Categories display order is defined by the combination of the category's order and then by the Score Category's name (in case two Score Categories contains the same order value)

![](/points/media/contacts-scorecategories-order.jpg)

#### Deletion of a Score Category used in Mautic

When used in Point Action, Point Trigger, on a Form's action or a Campaign, the Score Category defined can't be deleted from the database, that's why the checkbox option will be greyed out.
Anyway if you try to select the delete dropdown, a popup message will warn you how and where the score category is used and will prompt you first to edit the necessary actions before being allowed to delete the score category.

![](/points/media/delete-scorecategory.jpg)
