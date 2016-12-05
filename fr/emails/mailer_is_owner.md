# Emails envoyés avec le nom du propriétaire du contact

Cela permet d'envoyer automatiquement des emails personnalisés aux contacts ayant un propriétaire (utilisateur Mautic) assigné. Cette fonctionnalité change l'*étiquette d'envoi de l'adresse email* (from), l'*email* et la *signature*.

## Pré-requis

- Mautic 1.3.0+
- Un routeur non-tokenized. Cette fonctionnalité ne fonctionnera pas avec les emails envoyés par API (Mandrill, Sparkpost).

## Activer les emails envoyés depuis le propriétaire

- Ouvrez la page d'administration
- Sélectionnez *Configuration*
- Choisissez l'onglet de *paramétrage des emails*
- Changer l'*émetteur de l'email est le propriétaire* à Oui
- *Sauvegardez*

## Signature

Il y a deux endroits pour configurer le texte des signatures :
1. La signature par défaut dans le panneau de Configuration, onglet de paramétrage des emails. Le texte par défaut est "Best regards,
|FROM_NAME|." La variable |FROM_NAME| sera remplacée par le nom défini dans l'onglet de paramètre de l'email. Cette siganture sera utilisée si le propriétaire du contact n'est pas renseigné.
2. Chaque utilisateur Mautic peut configurer sa propre signature sur sa page d'édition du profil. Cette signature sera utilisée quand le propriétaire du contact est connu.
3. La signature peut être placé dans le corps d'un email en y insérant la variable `{signature}`.

## FAQ

### Cela marche-t-il pour tous les emails ?

Quelques exceptions :
- L'email doit être envoyé à un contact. Si Mautic n'a pas un contact lié à l'email, il ne sait pas qui est le propriétaire du contact. Cela se produit sur les emails de test.
- Si vous envoyez un email directement depuis l'aperçu du contact, le champ *from name* et *from email* seront utilisés depuis le formulaire, pas ceux depuis les paramètres.
