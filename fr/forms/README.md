# Formulaires

Les formulaires ont un rôle crucial dans le Marketing Automation. On les utilise pour récuperer des informations sur les contacts. Tout d'abord, respectons une règle d'or sur le web : je donne avant de demander ! La bonne pratique est d'avoir une récompense à offrir à vos visiteurs afin qu'ils soient motivés à vous laisser leur adresse email en échange d'une contrepartie assez interessante : un contenu dit riche. Par exemple ce sont des livres blancs, des simulateurs, des configurateurs, des périodes d'essai...+

Vous allez donc pouvoir créer des formulaires directement via la plateforme Mautic et les ajouter sur vos pages d'atterrissage Mautic ou les intégrer directement sur votre site !

![](/forms/media/kinds-of-forms.jpg)

Un **Formulaire de campagne** permet de qualifier directement les soumetteurs dans une campagne.

Les **Formulaires autonomes** permettent d'effectuer des actions dès la soumission comme l'ajout à un segment, la notification, etc. mais ne qualifie pas directement les contacts dans les campagnes.

## Erreurs sur les formulaires

### Le message d'erreur ne s'affiche pas ou la redirection ne se fait pas à la soumission du formulaire

Cela est généralement dû à cause d'une erreur d'URL. Vous pouvez vérifier cela en vous rendant sur la prévisualisation du formulaire. Ouvrez le navigateur avec l'inspecteur en appuyant sur F12 sur Windows et Linux ou Option+Command+I sur Mac. Allez dans l'onglet Console et vous devriez vous une erreur 404.

Pour corriger cela, allez dans la configuration Mautic Configuration et assurez vous que le champ **URL du site** correspond à la bonne adresse URL de votre instance Mautic (ce que vous voyez avant `/s/config/edit`) incluant le protocole http:// ou https://. Sauvegardez la configuration.

Rendez vous dans Composants / Formulaires et cliquez sur "reconstruire les formulaires".

![](/forms/media/rebuild.png)

L'erreur 404 devrait disparaitre et les formulaires fonctionner à nouveau.
