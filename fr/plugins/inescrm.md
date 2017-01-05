# Plugin Mautic - INESCRM

Ce plugin permet de pousser les contacts vers INESCRM quand un contact fait une ou plusieurs actions. Le plugin permet également de récupérer les contacts présents dans le CRM. On parle alors de synchronisation bi-directionnelle.
Si vous ne voyez pas ce plugin dans votre instance Mautic, Vérifiez que vous avez une version plus récente que la 2.6.0.

Si vous n'avez pas de compte chez INESCRM, [créez en un ici](http://www.inescrm.fr/).

## Configuration du plugin INESCRM dans Mautic

1. Dans le menu de *configuration* > *champs personnalisés*, ajouter deux champs supplémentaires, de type *Texte* ou *Nombre*, qui serviront à mémoriser pour chaque contact leur références dans INESCRM.
Ils peuvent être nommés librement (par exemple `ID contact INES` et `ID client INES`) et appartenir à n'importe quel groupe de champs.

2. Dans le menu de *configuration* > *plugins*, si l'icone "INESCRM" n'est pas présent, cliquer sur *Install / Upgrade Plugins*.
Cliquer sur l'icone INESCRM et configurer l'intégration à l'aide de vos codes d'accès au CRM : *Compte*, *Utilisateur*, *Mot de passe*. Puis tester la connexion.

3. Lorsque la connexion est OK, enregistrer la configuration, la fermer puis l'ouvrir à nouveau.
L'onglet *Mapping des champs du contact* doit être présent.
Dans cet onglet, affecter aux champs `Référence contact chez INES` et `Référence société chez INES` les champs Mautic créés à l'étape 1.
Puis affecter parmis les autres champs proposés ceux qui doivent être synchronisés avec INESCRM.
A noter que certains champs sont présents en doubles (par exemple l'adresse) car ils peuvent être synchronisés soit avec un contact INES, soit avec un client INES.

4. Activez les fonctionnalités souhaitées dans l'onglet *Fonctionnalités*.

5. Dans l'onglet *Enable/Auth*, mettre le commutateur *Published* sur `ON`.

## Fonctionnalités

* L'option *Envoyer les contacts dans intégration* active la fonction du même nom présente dans les actions de formulaire, les campagnes et les déclencheurs de points.
* L'option *Synchronisation de tous les leads* permet d'injecter dans INESCRM tous les contacts ayant au minimum un email et une société. Pour fonctionner, elle nécessite la mise en place d'une tâche planifiée (CRONJOB) sur le serveur :
`php app/console crm:ines [--number-of-leads-to-process=]`
Le paramètre `number-of-leads-to-process` indique le nombre maximum de leads à synchroniser à chaque appel.
* Le bouton *Voir journal de bord* affiche la file d'attente, limitée à 200 lignes, des dernières synchronisations planifiées, réussies ou échouées. Cette file d'attente n'est utilisée que par le mode "full-sync" du plugin.
En cas d'erreur lors de la synchro d'un lead, le script ré-essayera une synchro au prochain appel. Au bout de 3 tentatives infructueuses, la ligne passe en 'FAILED' et est ignorée pour les prochaines synchronisations.
* Les champs cochés en dernière partie de l'onglet **features** deviennent non écrasables : la valeur de ces champs dans Mautic n'affecte le champ correspondant dans INESCRM que s'il n'est pas encore renseigné.

## Synchronisation initiale

Lorsque le mode *Synchronisation de tous les leads* est actif, le cronjob se charge de vérifier, à chaque fois que la file d'attente est vide, s'il existe des contacts dans Mautic qui n'ont jamais été synchronisés, et en ajoute une partie (les 100 premiers rencontrés) à la file d'attente.
Ce qui permet de ne pas se soucier de la synchronisation initiale, qui se fait automatiquement et progressivement, à partir du moment où le cronjob est en place.

## Configuration du plugin Mautic dans INESCRM

# TEXT MISSING

## Testez le plugin

Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.

## Informations avancées pour développeurs

### Lecture des champs mappés via l'API Mautic

EndPoint : GET /api/ines/getMapping

Paramètres : aucun

En sortie :

```
array(
	'mapping' => array(
		0 => _config_champ_1_,
		1 => _config_champ_2_,
		1 => _config_champ_3_,
		...
	)
)
```

Où _config_champ_x_ a la structure suivante :

```
array(
	'concept' => 'contact' | 'client',
	'inesFieldKey' => 'PrimaryMailAddress',
	'isCustomField' => 0 | 1,
	'atmtFieldKey' => 'email',
	'isEcrasable' => 0 | 1
)
```

* L'attribut *concept* indique si le champ en question est lié à un contact ou à une société.
* L'attribut *inesFieldKey* correspond au nom interne du champ côté INES, tel qu'il est nommé dans les balises XML des WS.
* L'attribut *isCustomField* indique s'il s'agit d'un champ personnalisé (au sens INES du terme) ou non.
* L'attribut *atmtFieldKey* correspond au nom interne dans Mautic du champ mappé.
* L'attribut *isEcrasable* indique si les valeurs présentes dans INES peuvent être écrasées par une valeur Mautic différente ou non.
Il est donné à titre indicatif car c'est Mautic qui s'occupe du filtrage lors des mises à jour des contacts et clients chez INES.

### Notes

* Les champs non mappés se sont pas retournés. L'attribut *atmtFieldKey* est donc toujours renseigné.
* Deux champs sont toujours présents dans la réponse et ont pour attribut *inesFieldKey* les valeurs *InternalContactRef* et *InternalCompanyRef*. Ils indiquent les champs Mautic utilisés pour stocker les `InternalRef` des contacts et des clients.

## Crédit

Ce plugin a été développé par [@webmecanik](https://github.com/webmecanik) et [@jcdeveloppement](https://github.com/jcdeveloppement).
