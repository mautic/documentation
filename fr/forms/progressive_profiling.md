# Progressive Profiling

Cette fonctionnalité a été ajoutée à Mautic en version 2.1.0.

Progressive profiling makes your forms smarter by asking for the most important information and don't have yet at the time. This way your contacts won't feel overwhelmed by long forms and saves time by answering questions Mautic already knows the answer to. Progressive Profiling lets you improve the form conversion rate.

## Configuration

Il y a deux manières pour configurer un champ qui doit s'affiche seulement quand vous le souhaitez. Cette configuration se fait dans l'onglet __Comportement__ lors du paramétrage du champ d'un formulaire. Le comportement (Progressive Profiling) peut être configuré pou tous les types de champs sauf pour le champ _email_ et le _button_. L'email doit être toujours présent car il sert de clé unique et le tracking de Mautic ne garanti pas un suivi parfait à 100%. Et le bouton toujours visible sous peine de ne pouvoir soumettre le formulaire, cela va de soit !

Nous vous recommandons d'utiliser le champ email sur tous vos formulaires.

### 1. Afficher le champ seulement si la valeur n'est pas encore connue

Mautic va chercher à 2 endroits avant de générer le formulaire pour le visiteur courant :

#### 1.1 Soumissions de formulaire précédentes

Mautic va d'abord chercher dans l'historique des soumissions de formulaire du contact, et s'il trouve un résultat pour le champ, il le masquera. Il y a une limitation sur l'historique cherché, voir ci après.

#### 1.2 Valeur du profil du contact

Si le formulaire est lié à un champ du contact, Mautic va vérifier si une valeur est présente dans le champ du contact utilisé. Si c'est le cas et que vous l'avez configuré, le champ de formulaire sera masqué.

### 2. Afficher le champ après X soumissions

Si vous souhaitez demander au contact des informations additionnelles seulement à sa deuxième soumission, vous pouvez le paramétrer. Par exemple, pour une première soumission de formulaire, vous pouvez demander le nom et le prénom, puis à la seconde soumission masquer ces champs pour afficher les suivants comme le nom de l'entreprise et le téléphone.

## Les limites du Progressive Profiling

### Limite dans la recherche de l'historique

Les formulaires Mautic sans progressive profiling sont rapides. Le HTML du formulaire est généré qu'une fois, stocké dans le "cache" HTML et utilisé pour les prochains affichages. Quand le progressive profiling est activé sur tous les champs d'un formulaire, le HTML du formulaire sera différent pour chaque contact. Cela peut même changer pour un même contact entre deux soumissions. Ainsi, le système de cache standard utilisé sur la majorité des pages web ne peut être utilisé ici et cela prendra un peu plus de temps à être généré.

Il y a une limite de 200 soumissions dans lesquelles Mautic recherche des valeurs existantes. Cette limite a été ajoutée afin d'éviter que des formulaire mettent beaucoup trop de temps à charger quand un contact a des centaines de soumissions au compteur. Cette limite pourra parfois rendre visible des champs que vous auriez espérés masqués.

### L'intégration du formulaire

Les formulaires progressive profiling ne fonctionneront pas si vous utilisez l'intégration HTML statique (pour les raisons expliquées ci dessus). Cela fonctionne en aperçu, insertion en Javascript et iframe.

### The kiosk mode limit

Lrogressive Profiling features are turned off if you switch the form to the Kiosk Mode. The form always creates a new contact on each submission in the Kiosk Mode. It doesn't track the device from which the form was submitted.

The Progressive Profiling options under the Behavior tab will still be accessible in the Form Builder so you could easily switch the Kiosk mode off and use the Progressive Profiling features again.
