# Tableau de bord

Le tableau de bord Mautic est désormais complètement personnalisable par chaque utilisateur via un système de widget.

## Intervalle de temps

Tous les widgets seront affichés en fonction de l'intervalle de temps sélectionné tout en haut de la liste des widgets affichés. L'intervalle de temps par défaut est de 30 jours depuis aujourd'hui. Les unités des graphiques seront automatiquement changées en fonction du nombre de jours sélectionnés dans l'intervalle de temps :

* Intervalle de 1 jour : Heures
* Intervalle de 1 à 31 jours : Jours
* Intervalle de 32 à 100 jours : Semaines
* Intervalle de 101 à 1000 jours : Mois
* Intervalle supérieur à 1001 jours : Années
Quelques exceptions sur certains widgets qui afficheront les mêmes informations sans prendre en compte l'intervalle de temps *Emails à venir* et *Activité récente*.

## Widgets

*Attention : Ne créez pas trop de widget. Cela peut ralentir le chargement de la page du tableau de bord. Si vous avez des problèmes de performance, réduisez le nombre de widgets.*

Vous pouvez ajouter un widget en cliquant sur le bouton "Ajouter un widget". Au clic sur "Ajouter un widget", un formulaire apparaitra afin de pouvoir définir les options suivantes :
A new widget can be added to your dashboard when you click on the "Add widget" button. In the "Add wigteg" form which appears after each widget will let you define:

- **Nom** : Décrivez le nom que vous souhaitez donner au widget. Si ce champ n'est pas rempli, Automation lui donnera le même nom que le type du widget.
- **Type** : Sélectionnez le type d'information que vous souhaitez afficher.
- **Largeur** : Sélectionnez la taille de votre widget. Les options sont 25%, 50%, 75% ou 100% de largeur de la page. Par défaut, la valeur sélectionée sera 100%. La valeur optimale pour un graphique est de 100%, les tableaux de 50%, les camemberts 25%.
- **Hauteur** : Les widgets peuvent avoir 5 tailles prédéfinies.

Certains widgets peuvent avoir des options additionnelles :

**Contacts créés dans le temps**
- Affiche tous les contacts : Affiche tous les contacts créés sur une courbe d'évolution.
- Seulement identifés : Affiche une courbe avec les contacts identifiés.
- Seulement anonymes : Affiche une courbe avec les contacts anonymes.
- Tous les identifés vs. anonymes : Affiche 2 courbes avec les contacts identifiés et anonymes.
- Top segments : Affiche jusqu'à 6 courbes avec des contacts ajoutés aux top 6 des segments.
- Top segments avec les identifiés vs. anonymes : Affiche jusqu'à 6 courbes du top 3 des segments.

**Emails dans le temps**
- Emails envoyés seulement : Affiche 1 courbe avec les emails envoyés.
- Emails ouverts seulement : Affiche 1 courbe avec les emails ouverts.
- Emails rebonds seulement : Affiche 1 courbe avec les emails rebonds.
- Emails envoyés et ouverts : Affiche 2 courbes avec les emails envoyés et ouverts.
- Emails envoyés, ouverts et rebonds : Affiche 3 courbes avec les emails envoyés, ouverts et rebonds.

**Visites de page dans le temps**
- Toutes les visites - Affiche 1 courbe avec toutes les visites.
- Visites uniques - Affiche 1 courbe avec les visiteurs uniques (contacts).
- Total et visites uniques - Affiche 2 courbes avec les visiteurs uniques et tous les visiteurs.

### Classement des Widgets

Vous pouvez déplacer les widgets en glisser-déposer. Pour procéder, cliquer sur le nom et faites glisser.+

## Export du tableau de bord

Chaque tableau de bord configuré peut être exporté dans un fichier. Vous pouvez vous en servir comme sauvegarde, le partager avec vos collègues ou le publier. Il n'exporte que la configuration, pas les données associées.

## Import du tableau de bord

Si vous faites des exports, vous pouvez par la suite importer le fichier.

Dans l'installation Mautic il y a 3 tableaux de bord pre-definis. Celui nommé *default.json* est celui paramétré par défaut quand votre tableau de bord est vierge. Les deux autres pré-définis sont des exemples. Vous pouvez exporter et importer d'autres modèles et naviguer entre chaques.

Aperçu - Cela affichera les informations en aperçu. Rien ne sera sauvegarder avant d'appuyer sur le bouton "Appliquer".
Appliquer - Cela applique le modèle à votre tableau de bord. Attention : vos Widgets en cours seront supprimés ! Exportez la mise en forme actuelle si vous souhaitez la sauvegarder et la réimporter plus tard.
Supprimer - Cela supprimera le modèle sélectionné.

## Cache sur les Widgets

Le WidgetDetailEvent enregistre le détail des informations dans le cache pour une période de temps définie dans le panneau de configuration. Le cache par défaut est de 10 minutes.

## Autorisations sur le tableau de bord

Si un utilisateur Mautic n'a pas les droits pour voir les informations d'un bundle (contact, segments, etc.), il ne pourra pas créer de Widget qui regroupe les données de ce bundle. En revanche, le Widget restera visible si les droits de l'utilisateurs sont modifiés après la création du Widget.
