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

#### Ordre des catégories de score

L'ordre dans les catégories de score sont utilisés uniquement sur la fiche de Contacts/Sociétés afin d'afficher les catégories de score dans un ordre spécifique différent de l'ordre de base alphabétique, Mautic utilisant alors la combinaison du champ Ordre + l'ordre alphabétique du nom (la combinaison des deux critères est utilisée lorsque deux catégories existent avec le même ordre spécifié).

Grâce à ce champ, vous êtes en mesure d'afficher une catégorie nommée "Service" avant une catégorie "moins importante" nommée "Produit".

![](/points/media/contacts-scorecategories-order.jpg)

#### Suppression d'une catégorie de score utilisée dans Mautic

Lorsqu'une catégorie de score est utilisée dans la gestion des actions, des déclencheurs, sur les actions d'un formulaire ou d'une campagne, elle ne peut pas être supprimée de la base de donnée. C'est pourquoi, la case à cocher de selection dans la vue liste sera grisée.
Si vous essayez tout de même de supprimer la catégorie (en utilisant le menu déroulant par exemple), un message popup avertira l'utilisateur ou la catégorie de score est utilisée afin de permettre la modification du paramétrage actuel de l'outil avant la suppression de la catégorie de score.

![](/points/media/delete-scorecategory.jpg)
