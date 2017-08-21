# Suivi social

Il est possible d'ajouter et créer des contacts dans Mautic à travers le monitoring des activités sur Twitter en suivant les mentions et les hashtags.

![](/social-monitoring/media/social-monitor.jpg)

## Pré-requis

- Le [Plugin Twitter](../plugins/twitter.md) doit être configuré.
- La commande `app/console mautic:social:monitoring` doit être déclenchée périodiquement. Ajoutez la à la [configuration de vos CRONS](../setup/cron_jobs.md).

## Hashtags

1. Allez dans *Canaux* > *Suivi social* et cliquez sur *Nouveau*
2. Selectionnez le hashtag comme méthode de suivi Twitter
3. Renseignez le hashtag que vous souhaitez suivre
4. Donnez un nom à votre suivi et sauvegardez

![](/social-monitoring/media/social-mautic.jpg)

## Mentions
Le procédé est identique que pour les hashtags. Pensez juste à changer la méthode utilisée.

![](/social-monitoring/media/social-mention.jpg)

Une fois que des contacts utiliseront ces hashtags et mentions, vous avez la possibilité de les ajouter à des segments.
Les contacts seront donc créés dans votre compte Mautic avec les informations données par Twitter.
