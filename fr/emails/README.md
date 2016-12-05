# Emails ###

Les emails peuvent être créés pour être utilisés dans les campagnes ou associés à des segments de contacts. Ils permettent d'avoir une intéraction directe avec vos clients, prospects ou autres interlocuteurs.

### Formats d'emails ###

![](/emails/media/types.png)

Il y a 2 types d'emails.

#### Emails de template ###

Les emails de template emails peuvent être utilisés dans les campagnes, les actions de formulaire, les déclencheurs de points, etc. Ceux-ci peuvent être envoyés plusieurs fois à un même contact (à travers différentes actions).

#### Emails de segment (de masse) ###

Ces emails sont typiquement les emails de newsletter marketing. Vous devrez choisir un (ou des) segments qui seront la cible de cet email, ce qui vous donnera le montant de personnes en attente de l'envoi de l'email. Notez que chaque contact ne peut recevoir l'email qu'une fois - c'est comme une liste de mailing.

Vous deviez initialement envoyer ces emails manuellement depuis l'interface. Depuis la version 2.2.0, un nouveau CRON est disponible pour lancer ces emails automatiquement aux dates paramétrées ! Voir [Envoyer des emails de masse automatiquement (ex. emails de sgment)](./../setup/cron_jobs.html#send-scheduled-broadcasts-e-g-segment-emails) pour plus de détail sur cela.

### Format des emails ###

Les emails peuvent ête créés en HTML importé ou en format texte basique pour être envoyé à vos contacts. Vous pouvez également importer et créer vos propres thèmes. C'est un point essentiel pour construire les chaines relationnelles avec vos contacts.

### Dévlivrabilité des emails ###

Les emails sont délivrés en utilisant la méthode définie dans le panneau de configuration. Si vous êtes l'administrateur système pour votre entreprise, vous devrez alors configurer le protocole email. Mautic s'intègre avec de tous les serveurs SMTP tout comme de nombreux routeurs email comme Mailjet, Mandrill, Sendgrid, et Amazon SES.

Le système peut envoyer les emails immédiatement ou les traiter sous forme de queue pour les enovyer en masse avec un CRON.

#### Envoi immédiat ###

C'est l'envoi par défaut. Mautic envoi l'email dès qu'il est disponible. Si vous pensez envoyer un grand nombre d'emails, nous vous recommandons d'utiliser le système de queue. Envoyer les emails immédiatement risque de ralentir le temps de réponse de votre interface Mautic si vous utilisez un service d'envoi d'email externe à Mautic. Egalement, envoyer en grand nombre d'emails en une fois risque d'augmenter significativement le besoin en ressources de votre serveur PHP.

#### Envoi en queue ###

Cela est recommandé si vous souhaitez envoyer beaucoup d'emails. Mautic va enregistrer et stocket les emails dans une liste jusqu'à ce que la commande d'envoi ci après soit envoyée (pour les utilisateurs de Mautic Open Source). Vous pouvez choisir l'intervalle de temps entre chaque envoi :

```
php /path/to/mautic/app/console mautic:email:process --env=prod
```

Certains routeurs ont des limites d'envoi d'email par période. Si c'est le cas pour vous, ou si vous souhaitez modérer le volume d'envoi, vous pouvez paramétré les volumes et délais dans le panneau de configuration Mautic.

### Variables de contact dans les emails ###

Vous avez la possibilité d'ajouter n'importe quel champ de contact dans le contenu de vos emails. Cela sera automatiquement remplacé lors de l'envoi de l'email par la bonne valeur du contact.
Pour procéder, ajoutez dans votre email la variable sous le format `{leadfield=alias}`. Par exemple pour le prénom, il faudra mettre `{leadfield=firstname}`, pour le titre `{leadfield=title}`.

### Tracking d'ouverture des emails ###

Chaque email envoyé par Mautic sera complété d'un pixel de tracking unique. Cela permet à Mautic de voir quand un prospect ouvre un email et donc pourra probablement via l'éditeur de campagne, déclancher des actions spécifiques pour ce type de comportement. Notez que cette technologie ne fonctionne que pour les clients email supportant le HTML et le chargement des images.

### Tracking des liens des emails ###

Les clics sur chaque lien dans un email sont tracés et leur décompte est affiché en bas de chaque page d'aperçu d'un email.

### Désinscription ###

Mautic gère directement et automatiquement les désinscriptions. Si vous utilisez le générateur d'email, vous n'aurez qu'à glisser-déposer le text de désinscription ou l'URL de désinscription dans l'email. Ou alors, de la même manière qu'un champ variable, ajouter le texte `{unsubscribe_text}` ou `{unsubscribe_url}` directement dans votre email.
Les contacts désinscrits seront automatiquement exclus des listes d'envoi. Vous n'avez rien à faire de plus.

### Version en ligne ###

Mautic gère également l'hébergement d'une version en ligne de l'email en cas de mauvaise visualisation de l'email dans le client email du contact. Pour cela, ajouter l'URL suivante comme lien sur votre texte de version en ligne, `{webview_url}`.
