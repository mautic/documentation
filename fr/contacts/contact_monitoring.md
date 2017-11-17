# Monitoring des contacts
Le fait de monitorer le trafic et l'activité des contacts peut être parfois technique et compliqué à comprendre. Mautic rend ce monitoring simple et facile à configurer.

## Monitoring du site web

Le tracking de tout le trafic sur votre site internet ou blog peut être fait par la simple action d'ajout d'un javascript (depuis la version 1.4) ou du pixel de tracking. Il est important de comprendre que le tracking ne sera pas effectué sur les utilisateurs de Mautic connectés. Pour vérifier si le javascript ou pixel de tracking est fonctionnel, utilisez navigation incognito ou privée avc votre navigateur ou alors déconnectez vous d'Automation avant de faire vos tests.

### Javascript (JS) tracking

Le script a été ajouté comme méthode en 1.4 et il est vivement recommandé de l'utiliser plutôt que le pixel de tracking.
Pour le mettre en oeuvre, allez dans *Configuration* > *Paramètre des pages d'atterrissage* afin de trouver le code de tracking javascript pour votre compte Mautic et insérer le après la balise `</body>` sur votre site internet. Ou alors copier le code ci dessous et changez l'URL par celle de votre instance Mautic.

```
<script>
    (function(w,d,t,u,n,a,m){w['MauticTrackingObject']=n;
        w[n]=w[n]||function(){(w[n].q=w[n].q||[]).push(arguments)},a=d.createElement(t),
        m=d.getElementsByTagName(t)[0];a.async=1;a.src=u;m.parentNode.insertBefore(a,m)
    })(window,document,'script','http(s)://yourmautic.com/mtc.js','mt');

    mt('send', 'pageview');
</script>
```

_N'oubliez pas de changer le protocole (http(s)) en http ou https en fonction du protocole utilisé par votre instance Mautic. Changez également [yourmautic.com] par le nom de domaine sur lequel est installé votre instance._

L'avantage du script est que le chargement se fait de façon asynchrone et cela évite de ralentir le chargement de la page.
Le script Javascript permet également de tracer un peu plus d'information et cela automatiquement :
- **Titre de la page** qui se trouve entre les balises `</title>`.
- **Langue de la page** définie dans le navigateur du visiteur.
- **Page Referrer** URL source d'où provient le contact.
- **URL de page** étant l'URL du site en cours.

#### Evénements mt()

Depuis la version 2.2.0, mt() supporte 2 callbacks, `onload` et `onerror` accepté comme le 4e argument. La méthode `onload` sera exécutée une fois que le pixel de tracking est chargé. Si le chargement échoue pour une raison quelconque, `onerror` sera exécuté.

```
mt('send', 'pageview', {}, {
    onload: function() {
        redirect();
    },
    onerror: function() {
        redirect();
    }
});
```

#### Cookie local du contact

Depuis la version de Mautic 2.2.0, si les CORS sont configurés pour autoriser l'accès au domaine où le mtc.js est intégré, un cookie sera placé sur le même domaine avec le nom `mtc_id`. Ce cookie aura la valeur de l'ID du contact actuellement tracé. Cela donne un accès à l'ID du contact pour le serveur afin de pouvoir communiquer plus facilement avec l'API REST.

#### Enregistrer des paramètres personnalisés

Vous pouvez attacher des paramètres personnalisés ou écraser les paramètres par défaut. Pour procéder ainsi, mettez à jour la dernière ligne du javascript comme expliquer ci après :

```
    mt('send', 'pageview', {"email": "my@email.com", "firstname": "John"});

```
Ce code enverra automatiquement les données dans Mautic sur le bon contact. Les valeurs pour ces champs devront être générées par votre système (site web).

#### Evénement Load

Comme le tracking JS est une requête chargée de façon asynchrone, vous pouvez demander au JS d'appeler une fonction quand il est chargé. Pour faire ainsi, définissez la fonction *onload* dans les options comme suivant :

```
    mt('send', 'pageview', {"email": "my@email.com", "firstname": "John"}, {onload: function() { alert("Tracking request is loaded"); }});

```

#### Fingerprint (fonctionnalité beta)

Mautic 1.4.0 introduit une fonctionnalité de tracking appelée Fingerprint. La librairie [Fingerprint2](https://github.com/Valve/fingerprintjs2) est utilisée. Cela doit fonctionner avec ou remplacer les indentifiants de tracking courants comme l'adresse IP et/ou l'ID de cookie. Cette méthode n'est pas encore ajoutée en profondeur dans le système, mais vous pouvez déjà voir plus d'informations dans la timeline du contact sur ses visites :

- **Fingerprint** - Hash unique calculé par les paramètres du navigateur.
- **Resolution** - Avec la largeur x hauteur du support utilisé.
- **Timezone Offset** - Nombre de minutes en plus ou moins d'UTC.
- **Platform** - Platforme du support. Généralement l'OS (système d'exploitation) et le processeur.
- **Adblock** - Une valeur booléenne pour savoir si le contact utilise le plugin Adblock.
- **Do Not Track** - Une valeur booléenne pour savoir si le contact ne souhaite pas que l'on pose un cookie pour le tracer.

Si vous souhaitez stocker ces informations dans un champ de contact, créez un nouveau champ personnalisé appelé de la même manière et avec le même nom que la liste ci dessus (les configurer publiquement updatable).

### Pixel de tracking

Cette méthode est secondaire depuis la version de Mautic 1.4.

```
http://yourdomain.com/mtracking.gif
```

#### Requête du pixel de tracking

Pour profiter de toute la puissance du pixel de tracking, vous pouvez passer des paramètres et informations complémentaires des requêtes web via l'URL de l'image.


#### Informations sur la page

Mautic supporte actuellement `page_url`, `referrer`, `language`, et `page_title` (notez que l'utilisation du paramètre url et title est évitée pour ne pas créer de conflit avec les champs du contact).

### Codes UTM

La prise en compte des codes UTM dans la timeline du contact a été introduite en version 1.2.1. `utm_medium`, `utm_source`, et `utm_campaign` sont utilisés pour générer le contenu de l'événement du contact.

* `utm_campaign` sera utilisé comme titre de l'événement dans la timeline.
* Les valeurs `utm_medium` correspondent aux classes Font Awesome suivantes :

<table>
<thead>
<tr>
    <th>Values</th>
    <th>Class</th>
</tr>
</thead>
<tbody>
   <tr><td>social, socialmedia</td><td>fa-share-alt if <code>utm_source</code> is not available otherwise <code>utm_source</code> will be used as the class. For example, if <code>utm_source</code> is Twitter, fa-twitter will be used.</td></tr>
   <tr><td>email, newsletter</td><td>fa-envelope-o</td></tr>
   <tr><td>banner, ad</td><td>fa-bullseye</td></tr>
   <tr><td>cpc</td><td>fa-money</td></tr>
   <tr><td>location</td><td>fa-map-marker</td></tr>
   <tr><td>device</td><td>fa-tablet if <code>utm_source</code> is not available otherwise <code>utm_source</code> will be used as the class. For example, if <code>utm_source</code> is Mobile, fa-mobile will be used.</td></tr>   
</tbody>
</table>


#### Intégrer le pixel

Si vous utilisez un CMS, le plus simple est de laisser un de nos plugins le faire pour vous (voir ci-dessous). Notez que les plugins CMS ne supportent pas tous les champs custom, les codes UTM et les tags.

Voici une liste de bouts de code qui pourraient vous aider :

HTML

```
<img src="http://yourdomain.com/mtracking.gif?page_url=http%3a%2f%2fyourdomain.com%2fyour-product-page&page_title=Some%20Cool%20Product&email=user%40theirdomain.com&tags=ProductA,-ProductB" style="display: none;"  alt="mautic is open source marketing automation" />
```

PHP

```
$d = urlencode(base64_encode(serialize(array(
    'page_url'   => 'http://' . $_SERVER[HTTP_HOST] . $_SERVER['REQUEST_URI'],
    'page_title' => $pageTitle,    // Use your website's means of retrieving the title or manually insert it
    'email' => $loggedInUsersEmail // Use your website's means of user management to retrieve the email
))));

echo '<img src="http://your-mautic.com/mtracking.gif?d=' . $d . '" style="display: none;" />';
```

Javascript

```
<script>
var mauticUrl = 'http://your-mautic.com';
var src = mauticUrl + '/mtracking.gif?page_url=' + encodeURIComponent(window.location.href) + '&page_title=' + encodeURIComponent(document.title);
var img = document.createElement('img');
img.style.width  = '1px';
img.style.height  = '1px';
img.style.display = 'none';
img.src = src;
var body = document.getElementsByTagName('body')[0];
body.appendChild(img);
</script>
```

### Champs de contact

Vous pouvez également passer des informations specifiques sur votre contact en paramétrant les champs personnalisés de Mautic comme publiquement updatable. Notez que les valeurs ajoutées au pixel de tracking doivent être encodée en URL (%20 pour un espace, %40 pour une @, etc.).

### Tags

Les tags des contacts peuvent être modifiés en utilisant le paramètre `tags`. Plusieurs tags peuvent être ajoutés en les séparant par une virgule. Pour supprimer un tag, ajoutez-y le préfixe moins -.
Par exemple, `mtracking.gif?tags=ProductA,-ProductB` ajouterait le tag ProductA au prospect et lui enleverait le tag ProductB.

### Plugins disponibles

Mautic rend votre vie encore plus facile en vous donnant accès à des plugins pour les CMS principaux. Vous pouvez en télécharger et en installer autant que vous le souhaitez.

* [Joomla!](http://mautic.org/integration/joomla)
* [Drupal](http://mautic.org/integration/drupal)
* [WordPress](http://mautic.org/integration/wordpress)
* [Typo3](http://mautic.org/integration/typo3)
* [Concrete5](http://mautic.org/integration/concrete5)
* [Grav](https://github.com/mautic/mautic-grav)

Ceux-ci sont une partie des intégrations réalisées par la communauté Mautic. De nombreuses autres intégrations seront développées dans le futur et nous encourrageons les développeurs à soumettre leurs intégrations à la communauté.

**Note :** Il est important de noter que vous n'êtes pas limités par ces plugins pour mettre le tracking en place sur votre site et/ou CMS.

### Identifier les visiteurs par tracking URL

Mautic 2.9 ajoute dans les options de Configuration pour identifier les visiteurs par URL de tracking. Si c'est activé, les visiteurs seront reconnus par les URL uniques issues des cannaux (spécialement les emails) quand aucun cookie existe déjà.

**Note :** le champ de contact email doit être identifiant unique et publiquement updatable.

### Monitoring mobile

Le fait de monitorer le comportement dans une application est relativement similaire au tracking sur une site web. Automation possède la structure nécessaire pour des applications natives (ou pseudo-natives) et applications HTML5.

En bref, utilisez des noms pour vos écrans (ex : ecran_accueil) dans votre application pour le champ page_url dans le pixel de tracking, ainsi que l'adresse email du prospect comme identifiant unique, consultez l'étape suivant pour plus de détail.

#### Les étapes dans Mautic

1. Rendrez le champ email publiquement updatable.

2. Paramétrez un formulaire, qui sera le point d'accès à votre campagne (ex. un email de bienvenue). Faites ce formulaire aussi simple que possible, puisque vous allez rePOSTer depuis votre App.

```
http://your_mautic/form/submit?formId=<form_id>
```

Vous pouvez obtenir l'ID depuis votre page Mautic (aperçu du formulaire).

3. Definissez dans vos campagnes les écrans que vous souhaitez utiliser comme déclencheur (ex. 'ecran_panier' etc.). Mautic ne cherche pas une URL "réelle" dans le formuaire 'http://<url>' pour la page_url, n'importe quelle valeur simple fonctionnera, comme par exemple :

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

#### Dans votre application

La meilleure approche est d'avoir une classe (par exemple 'mautic') qui gère vos besoins en tracking. Par exemple, cette méthode d'échantillon POST dans le formulaire d'ID 3

```
mautic.addContact("myemail@somehwere.com",3)
```

Et par la suite, pour tracer des informations d'activité dans l'application, cette échantillon fait une requête HTTP au tracker :

```
mautic.track("cart_screen", "myemail@somewhere.com")
```

Qui n'est rien de plus qu'une reqêuet HTTP vers l'URL en format GET :

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

Important : Soyez sûr dans votre application, que la requête HTTP utilise une cookie (si possible, ré-utilisez le cookie depuis la requête POST mautic.addcontact) et que vous réutilisez ce cookie d'une requête à l'autre. C'est ainsi que Mautic (et les autres logiciels de tracking) reconnaissent que c'est le même utilisateur.

### Troubleshooting

Si le tracking ne fonctionne pas, rendez-vous sur la [page troubleshooting](./../pages/troubleshooting.html) ou [Email troubleshooting](./../emails/troubleshooting.html)
