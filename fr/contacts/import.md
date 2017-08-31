# Import de contacts

Vos contacts peuvent être importés depuis l'interface avec un fichier au format CSV.
Vous pourrez choisir de le faire en streaming depuis l'interface ou de le laisser faire en tâche de fond.

Depuis Mautic 2.9, une action a été ajouté à l'historique du contact lorsqu'il est touché par un import.

## Import en streaming

Utilisez l'import depuis l'interface seulement si vous n'avez pas d'autre choix. L'import en arrière plan est recommandé.

## Import en arrière plan

Le travail en arrière plan (commande CLI déclenchée manuellement ou par tâche planifiée) ont l'avantage de ne pas avoir de limite de temps. L'import en arrière plan sera toujours plus rapide, efficace et fiable qu'en streaming depuis l'interface.

Cette option est disponible depuis la version de Mautic 2.9.x.

**Attention** : l'import en arrière plan nécessite de configurer la commande `php /path/to/mautic/app/console mautic:import` périodiquement. Ajoutez le à votre CRON tab.

Le succès d'un import ressemblera à :
```
$ app/console mautic:import
 48/48 [============================] 100%
48 lines were processed, 0 items created, 48 items updated, 0 items ignored in 4.78 s
```
S'il n'y a pas d'import dans queue, il n'y aura pas de message.

### Imports en parallèle

L'import peut prendre plusieurs minutes. Il est possible qu'un import soit toujours en cours lors du démarrage d'un second import. Pour éviter de prendre trop de ressources serveur, il existe l'option configurable `parallel_import_limit`. Par défaut seulement 1 import se fera en même temps. Cette modification peut être apportée dans votre fichier `app/config/local.php`.

### Arrêter un import en arrière plan

Rendez vous dans la liste des imports et cliquez sur l'interrupteur vert. Cela mettra l'import en statut **Stopped**. Cela mettra fin à l'import après le batch en cours.

Quand vous décidez de démarrer l'import à nouveau, vous n'avez qu'à publier à nouveau l'import et il redémarrera.

Quand l'import en arrière plan est terminé, que ce soit un succès ou un échec, vous recevrez une notification dans l'espace de notification de Mautic.

## Comment importer les contacts

1. Aller dans *Contacts*.
2. En haut à droite, vous disposez d'un menu déroulant, cliquez sur l'action *Import*.
3. Chargez le fichier CSV avec les contacts que vous souhaitez importer.
4. Choisissez les paramètres de votre fichier CSV s'il ne respecte pas les standards internationaux.
5. Chargez votre fichier CSV.
6. La page de correspondance des champs s'affiche. Vous pouvez d'abord choisir le propriétaire des contacts, le segment dans lequel vous souhaitez faire l'import et les tags à assigner à l'import. Ces paramètres sont facultatifs.
La 2nd zone concerne la correspondance entre les colonnes du fichier CSV et les champs de contact Mautic. La dernière zone vous permet de faire la correspondance avec des champs un peu spécifiques comme la *Date de création* des contacts.
7. Quand la correspondance est prête, cliquez sur le bouton d'*import*.
8. Une page avec la barre de progression s'affiche pour vous donnez le statut de votre import.
9. Lorsque l'import est terminé, les potentielles erreurs sont affichées en résultat.

## Statut des imports

Il y a différents statuts pour les imports :
- **Queued** - L'import a été créé et il est mis en queue jusqu'au lancement de la prochaine commande.
- **In Progress** - Le tavail en arrière plan a commencé mais n'est pas terminé. Vous pouvez suivre la progression dans la liste des imports.
- **Imported** - L'import a été fait avec succès.
- **Failed** - L'import a échoué.
- **Stopped** - L'import a été stoppé alors qu'il était en statut **Queued** ou **In Progress**.
- **Manual** - L'utilisateur a choisi un import depuis l'interface.
- **Delayed** - L'import a été reporté car il y en a probablement un en cours.

## Liste des imports

La liste des imports peut être trouvée quand vous allez dans les *Contacts*, cliquez sur le menu déroulant en haut à droite et choisissez *Imports en arrière plan*.

Le tableau vous affiche quelques statistiques basiques à propos des imports, ainsi que le statut des imports en cours avec leur nom. Vous y trouverez également les interrupteurs pour pouvoir désactiver les imports envoyés et les réactivés.

## Détail des imports

La page de détail des imports est accessible en cliquant sur *Details*, vous y trouverez un peu plus d'informations sur le pourcentage de l'import activé.

Retrouvez également 2 graphiques :
1. Le graphique en camembert vous montre le ratio entre les contacts créés, mis à jour et échoués.
2. La courbe montre le nombre de contacts ajoutés.

## Imports automatiques

Il y a une option dans la Configuration de Mautic > Paramètres des contacts pour définir quelle est la limite optimale pour le choix de l'import via interface ou en arrière plan. Si vous choisissez 1 000 par exemple, cela veut dire que l'import CSV depuis interface sera choisi pour mois de 1 000 lignes. Si plus, cela passera par l'action d'arrière plan. La valeur par défaut est 0 (zéro), ce qui fait que lors de l'import les contacts auront le choix entre l'import depuis l'interface ou en arrière plan.

## Pré-requis

- Le fichier CSV doit être encodé en UTF8. D'autres formats peuvent générer des erreurs à l'import.

- Pour les champs booléens comme `doNotEmail` ou les champs booléens personnalisés, utilisez les valeurs `true`, `1`, `on` ou `yes` pour la valeur positive. N'importe quelle autre valeur sera considérée comme négatif.

- Dans le cas de correspondance avec des champs date/time, utilisez le formatage `YYYY-mm-dd HH:ii:ss`, par exemple : `2017:01:02 19:08:00`. Les autres formats risquent de générer des erreurs.

## Conseils

- Nommez les colonnes de votre fichier CSV de la même manière que les alias des champs dans Mautic. Cela permettra de faire une correspondance automatique et vous gagnerez un peu de temps.

## Concernant les imports de "Ne pas contacter"

Si vous faites la correspondance sur le champ des "ne pas contact", les contacts seront ni "désinscrits", ni "rebonds", mais marqué comme désinscription manuelle.
