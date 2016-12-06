# Troubleshooting des pages d'atterrissage

## Le tracking des visites ne fonctionne pas

Le tracking des visites sur la page fonctionne grâce au pixel de tracking. C'est simplement une image de 1 pixel au format .gif dans le code source de la page. Quand la page est chargée par un navigateur, elle charge le pixel avec elle. Le chargement de l'image permet à Mautic de tracer qui est en train de la visiter.
Si le tracking ne fonctionne pas, vérifiez les points suivants :

1. Le tracking n'est pas pris en compte lorsque vous êtes en même temps connecté à votre plateforme Mautic afin de ne pas altérer les statistiques. Soyez donc sûr d'être déconnecté de votre compte Mautic ou utilisez alors un navigateur en mode incognito lors de vos tests.
2. Le pixel de tracking n'est pas dans votre page. Mautic ne peut tracer que les pages qui contiennent ce pixel de tracking dans le code source.
3. Le pixel de tracking est configuré incorrectement. Vous pouvez confirmer cela grâce aux outils de développement de votre navigateur. En chargeant la page que vous souhaitez traquer, ouvrez la console (pressez sur F12), allez sur l'onglet Network et rafraichissez votre page. Vous constaterez toutes les requêtes effectuées par votre page. Filtrez les requêtes pour ne garder que les images et trouver celle qui se nomme mtracking.gif. A-t-elle le statut 200 ? Si ce n'est pas le cas, le lien de l'image vers votre compte Mautic est probablement incorrect.

[Plus d'infos sur le pixel de tracking](./../contacts/contact_monitoring.html)
