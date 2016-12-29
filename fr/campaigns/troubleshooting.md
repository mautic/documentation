# Troubleshooting des campagnes

## Les visites de page ne sont pas reconnues

Il peut xister plusieurs raisons pour cela :

1. Soyez sûrs qu vous n'effectuez pas des tests de visite de pages en étant connecté à votre compte Mautic. Mautic ignore les activités de ses utilisateurs. Utilisez alors la navigation privée, un autre navigateur ou déconnectez vous de Mautic.
2. Assurez vous que le contact que vous essayez de tracer est bien rentré dans la campagne. Le moyen le plus simple est d'aller voir dans l'historique d'activité du contact.
3. Les campagnes sont exécutées sous formes de taches récurrentes et un contact ne peut être considéré plusieurs fois pour une même action. Si le contact a déjà réuni les conditions d'une décision sur le tracking d'une URL, une décision sur le même critère plus tard ne sera pas automatiquement vérifiée pour la visite déjà considérée.
4. Assurez vous que l'URL que vous tracez est _exactement_ l'URL visitée ou utilisez les étoiles `*` pour un portion d'URL.

Par exemple, si vous avez comme URL `http://example.com` et que le tracking enregistre `http://example.com/index.php?foo=bar`, la décision de la campagne ne sera pas exécutée. Cependant, si vous utilisez `http://example.com*` comme URL, cela correspondra et déclanchera l'événement de campagne.

Un autre exemple, si vous avez une campagne A et une campagne B. Vous souhaitez utiliser la même base d'URL tout en la différencient avec des paramètres. Pour la campagne A, vous pouvez utiliser la décision de visite d'URL avec `http://example.com/my-page?utm_campaign=A*` et pour la campagne B, `http://example.com/my-page?utm_campaign=B*`. Ainsi, le contact n'aura le déclencheur que sur la campagne à laquelle le critère correspond. Si vous souhaitez que le contact soit concerné pour les deux campagnes, utilisez `http://example.com/my-page*`.
