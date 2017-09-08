# Gestion des segments

Les listes de prospects ont été renommées en segment lors de la version de Mautic 1.4.0.

Les segments permettent d'organiser vos contacts le plus simplement possible. Ces segments peuvent être soit figées (sans variables) soit dynamiques en y ajoutant toute association de filtres.

Quand vous verrez la liste des segments, vous pourrez constater que la colonne de droite vous indique le nombre de contacts qui remplissent chacune de vos listes.

![](/contacts/media/contact-segments.jpg)

### Filtres de segment

![](/contacts/media/segment-filters.jpg)

Ces filtres peuvent être combinés de façon inclusive ou exclusive en fonction de vos besoins.

![](/contacts/media/multiple-segment-filters.jpg)

Une fois le champ sélectionné, vous pourrez choisir le type d'opération à appliquer. Cela dépendra de votre besoin et de la manière dont vous souhaiterez filtrer vos contacts.

![](/contacts/media/segment-filters-dropdown.jpg)

![](/contacts/media/common-leads-in-segments.jpg)

### Segments

Une fois paramétrés, les critères de segmentation seront appliqués et n'importe quel contact correspondant aux critères sera automatiquement ajouté à au segment lors du CRONs (tache planifiée automatiquement). De la sorte, vos contacts se qualifient de segment en segment, sans avoir à faire la moindre action !

Si le contact ne répond plus aux critères, il sera automatiquement exclu du segment.

Pour déclencher le CRON, paramétrer la commande suivante (pour les utilisateurs de Mautic Open Source):

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
php /path/to/mautic/app/console mautic:segments:update --env=prod
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Ajout manuel de contact à un segment

En plus de la gestion dynamique des segments, vous pouvez également ajouter vos contacts manuellement en cliquant sur le bouton 'Segments' en haut à droite sur la fiche d'un contact.
Un contact ajouté manuellement à un segment y restera même s'il ne répond pas aux critères de filtres.
