# Import de contacts

Vos contacts peuvent être importés depuis l'interface avec un fichier au format CSV.

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

## Pré-requis

- Le fichier CSV doit être encodé en UTF8. D'autres formats peuvent générer des erreurs à l'import.

- Pour les champs booléens comme `doNotEmail` ou les champs booléens personnalisés, utilisez les valeurs `true`, `1`, `on` ou `yes` pour la valeur positive. N'importe quelle autre valeur sera considérée comme négatif.

- Dans le cas de correspondance avec des champs date/time, utilisez le formatage `YYYY-mm-dd HH:ii:ss`, par exemple : `2017:01:02 19:08:00`. Les autres formats risquent de générer des erreurs.

## Conseils

- Nommez les colonnes de votre fichier CSV de la même manière que les alias des champs dans Mautic. Cela permettra de faire une correspondance automatique et vous gagnerez un peu de temps.

## Concernant les imports de "Ne pas contacter"

Si vous faites la correspondance sur le champ des "ne pas contact", les contacts seront ni "désinscrits", ni "rebonds", mais marqué comme désinscription manuelle.
