# Mautic - Social Login

Le login social dans Mautic est utilisé pour remplir et pré-remplir les formulaires, ainsi que pour créer et mettre à jour les contacts dans Mautic avec des données issues d'un profil des réseaux sociaux une fois que le contact s'est connecté.

### pré-requis
Pour le bouton de login social, vous devez activer les boutons sociaux listés ci après.

Veuillez vous rendre sur les liens suivants pour vous créer un compte sur les applications sociales avant de tenter de configurer les plugins.
- Twitter
Pour Twitter, référez vous à la [documentation Twitter](twitter.md)
- [Facebook](https://developers.facebook.com)
- [g+](https://console.developers.google.com)
- [LinkedIn](https://developer.linkedin.com)

### Authorisation du plugin

Une application doit être créée dans les différents réseaux sociaux (dans la zone développeur) pour l'authorisation. En créant votre application sociale, il vous sera demandé une *URL de Callback*. Celle ci vous est donnée dans le fenêtre de configuration de votre plugin.

Une fois votre application créée, copiez la *clé API* dans le champ *clé client* dans le plugin Mautic, ainsi que l'*API Secret* dans le champ *secret client*. Cliquez sur le bouton *Authoriser*.

N'oubliez pas de d'activer le plugin.

### Configurer le plugin

Si le plugin est correctement authorisé, vous pourrez configurer l'onglet *Fonctionnalités* et l'onglet *Mapping des champs du contact* dans la configuration du plugin.

Une fois le login social activé dans les fonctionnalités, vous devrez configurer la correspondance des champs du contact entre les différents applications. Gardez en tête que le plugin ne fait pas que pré-remplir le formulaire mais qu'il va également créer ou mettre à jour le contact en fonction de la correspondance des champs configurée ici.

*Note :* Si vous ne faites pas la correspondance des champs, le login social ne pourra pas reconnaitre le contact ou le créer.

### Login social dans les formulaires

Le bouton de login social est utilisé dans les formulaires. Pour l'utiliser, assurez vous d'avoir correctement suivi les étapes précédentes. Vous pourrez alors :
1. Créer un formulaire.
2. Choisir le champ de type "login social". Le bouton pour tous les réseaux sociaux activés apparaitra. Les boutons pour les applications non authorisées ne fonctionneront pas correctement.
3. Pour pré-remplir le formulaire, le plugin social fait la correspondance des champs avec les champs dans Mautic qui ont des noms identiques.

**Twitter**
'profileHandle','name', 'location', 'description', 'url', 'time_zone', 'lang', 'email'

**Facebook:**
'first_name','last_name','name','gender','locale','email','link',

**g+** 'profileHandle'
'nickname','occupation','skills','birthday','gender','urls','displayName','name','emails','tagline','braggingRights','aboutMe'         
'currentLocation','relationshipStatus','organizations','placesLived','language','ageRange'

**Linkedin** 'firstName','lastName','maidenName','formattedName','headline','location','summary','specialties','positions','publicProfileUrl','emailAddress'
