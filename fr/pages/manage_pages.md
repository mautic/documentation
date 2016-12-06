# Gestion des pages d'atterrissage

### Details des pages

Quand vous visitez une page dans Mautic, vous pouvez consulter de nombreuses et riches informations en un coup d'oeil.

![](/pages/media/landing-page-overview.jpg)

Vous pouvez voir le titre de la page ainsi que sa description. En un coup d'oeil sur les graphiques, constatez le nombre d'impressions, le nombre de nouveaux visiteurs contre le nombre de visiteurs connus ainsi que le temps moyen passé sur la page par les visiteurs. Ces graphiques sont mis à jour en temps réel.

Sur la droite, vous pouvez accéder à l'URL d'hébergement de la page, ainsi qu'à une URL de prévisualisation (utile lorsque votre page n'est pas encore publiée).

Notez que vous pouvez cliquer sur le bouton détails afin d'étendre une zone avec plus de détails.

![](/pages/media/page-details.gif)

### Variantes et traductions

Comme mentionné plus tôt, vous pouvez également voir les informations sur les pages traduites dans d'autres langues et les variantes qui servent à l'A\/B testing.

Lors de la création de la page d'atterrissage, vous avez la possibilité d'ajouter une langue et une taduction parente. En sélectionnant une traduction parente, cela vous permet d'ahouter une traduction enfante de la page en cours. Si le contact a une langue de préférence paramétrée dans son navigateur ou en local, la page d'atterrissage s'affichera dans la langue paramétrée si la variante existe. Autrement, les contacts verront la page dans la langue par défaut.

Il est également possible de faire des traductions de versions A/B.

### Nouvelle page et édition de page

Lors de la création (ou la modification), vous accèderez à différents champs de paramétrage. Vous pouvez choisir des thèmes ou créer les votres pour pouvoir éditer cela sans développeur depuis le générateur de page.

![](/pages/media/landingpage-1.jpg)

Chaque partie d'un thème est éditable en drag and drop.
- Cliquez sur une boite de texte pour l'éditer
- Cliquez sur une image pour la remplacer
Une fois que vous êtes content, cliquez sur "fermer le générateur" et vous verrez un aperçu de la page.

![](/pages/media/landingpage-2.jpg)

Vous pouvez toujours modifier encore plus en détail votre page avec l'onglet contenu ou en éditant directement le code source. Vous pouvez également importer votre propre HTML.

![](/pages/media/landingpage-3.jpg)

Le générateur vous permet d'ajouter facilement des liens vers vos ressources, les autres pages d'atterrissage, et l'insertion des formulaires. Vous pouvez les insérer en utilisant les tokens habituels `{component=item}`, par exemple `{form=4}`. Une liste déroulante des valeurs possibles apparaitra lorsque vous commencerez à écrire `{`.

### Dépublication d'une page

Les pages peuvent être dépubliées et republiées plus tard en cliquant sur le boutton __publié/dépublié__ ou en configurant une date automatique de dépublication. Si votre page d'atterrissage est dépubliée et que vous souhaitez y accéder, vous arriverez sur une page 404.

#### Redirection pour les pages dépubliées

Mautic vous permet de configurer une redirection 301 (permanente) ou 302 (temporaire). La redirection fonctionnera seulement si la page d'atterrissage est dépubliée.

Note : Si vous êtes connecté à votre compte Mautic, vous verez le contenu de la page d'atterrissage même si elle est désactivée.
