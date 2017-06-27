# Plugin Mautic - INESCRM

Ce plugin permet de pousser les contacts vers INESCRM quand un contact fait une ou plusieurs actions.
Si vous ne voyez pas ce plugin dans votre instance Mautic, Vérifiez que vous avez une version plus récente que la 2.6.0.

Si vous n'avez pas de compte chez INESCRM, [créez en un ici](http://www.inescrm.fr/).

## Configuration du plugin INESCRM dans Mautic

1. Dans le menu de *configuration* > *champs personnalisés*, ajouter deux champs supplémentaires, de type *Texte* ou *Nombre*, qui serviront à mémoriser pour chaque contact leur références dans INESCRM.
Ils peuvent être nommés librement (par exemple `ID contact INES` et `ID client INES`) et appartenir à n'importe quel groupe de champs.

2. Dans le menu de *configuration* > *plugins*, si l'icone "INESCRM" n'est pas présent, cliquez sur *Install / Upgrade Plugins*.
Cliquez sur l'icone INESCRM et configurez l'intégration à l'aide de vos codes d'accès au CRM : *Compte*, *Utilisateur*, *Mot de passe*. Puis tester la connexion.

3. Lorsque la connexion est OK, enregistrez la configuration, la fermer puis l'ouvrir à nouveau.
L'onglet *Mapping des champs du contact* doit être présent.
Dans cet onglet, affectez aux champs `Référence contact chez INES` et `Référence société chez INES` les champs Mautic créés à l'étape 1.
Puis affectez parmis les autres champs proposés ceux qui doivent être synchronisés avec INESCRM.
A noter que certains champs sont présents en doubles (par exemple l'adresse) car ils peuvent être synchronisés soit avec un contact INES, soit avec une entreprise INES.

4. Activez les fonctionnalités souhaitées dans l'onglet *Fonctionnalités*.

5. Dans l'onglet *Enable/Auth*, mettre le commutateur *Published* sur `ON`.

## Fonctionnalités

* L'option *Envoyer les contacts dans intégration* active la fonction du même nom présente dans les actions de formulaire, les campagnes et les déclencheurs de points.
* L'option *Synchronisation de tous les leads* permet d'injecter dans INESCRM tous les contacts ayant au minimum un email et une société. Pour fonctionner, elle nécessite la mise en place d'une tâche planifiée (CRONJOB) sur le serveur :
`php app/console crm:ines [--number-of-leads-to-process=]`
Le paramètre `number-of-leads-to-process` indique le nombre maximum de leads à synchroniser à chaque appel.
* Le bouton *Voir journal de bord* affiche la file d'attente, limitée à 200 lignes, des dernières synchronisations planifiées, réussies ou échouées. Cette file d'attente n'est utilisée que par le mode "full-sync" du plugin.
En cas d'erreur lors de la synchronisation d'un lead, le script ré-essayera une synchronisation au prochain appel. Au bout de 3 tentatives infructueuses, la ligne passe en 'FAILED' et est ignorée pour les prochaines synchronisations.
* Les champs cochés en dernière partie de l'onglet **features** deviennent non écrasables : la valeur de ces champs dans Mautic n'affecte le champ correspondant dans INESCRM que s'il n'est pas encore renseigné.

## Synchronisation initiale

Lorsque le mode *Synchronisation de tous les leads* est actif, le cronjob se charge de vérifier, à chaque fois que la file d'attente est vide, s'il existe des contacts dans Mautic qui n'ont jamais été synchronisés, et en ajoute une partie (les 100 premiers rencontrés) à la file d'attente.
Ce qui permet de ne pas se soucier de la synchronisation initiale, qui se fait automatiquement et progressivement, à partir du moment où le cronjob est en place.

## Testez le plugin

Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.

## Crédit

Ce plugin a été développé par [@webmecanik](https://github.com/webmecanik) et [@jcdeveloppement](https://github.com/jcdeveloppement).
