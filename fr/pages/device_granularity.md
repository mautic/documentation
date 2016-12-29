# Granularité des supports

Mautic enregistre les supports utilisés par vos visiteurs sur les pages d'atterrissage et les emails

## Pré-requis

Pour détécter le support utilisé par le visiteur, Mautic utilise (https://github.com/piwik/device-detector). Soyez sûrs d'installer cette library dans votre instance Mautic (pour les utilisateurs de Mautic Open Source).

## Test de la fonctionnalité

#### Pour les emails et pages Mautic

Chaque page d'atterrissage et email issus de Mautic doivent être tracés. A l'ouverture d'un email, les informations doivent être enregistrées sur le contact.

#### Pour les emails et pages qui ne sont pas issues de Mautic

A partir du moment où vous intégrez le pixel de tracking Mautic, le tracking du support utilisé par le navogateur sera effectué.

## Comment utiliser la fonctionnalité

- Dans le fil d'actulité du contact sera enregistré le support utilisé par le contact lors de ses visites de page ou l'ouverture de ses emails
- Les graphiques de cycle d'achat peuvent afficher les supports utilisés en fonction des segments
- La page de détail d'un email affiche en plus de ses statistiques un camembert sur les supports utilisés pour les ouvreurs de l'email en question
- Dans le menu rapport, vous avez maintenant la possibilité de créer de nouveaux graphiques en fonction du support utilisé par le contact
