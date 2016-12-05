# Troubleshooting des emails

## L'ouverture d'un email n'est pas tracée

L'ouverture des emails est tracée par le pixel de tracking. lorsqu'un email est ouvert par un client email comme Outlook, Thunderbird ou GMail, le client essaye de charger l'image.

Certains clients email désactivent le chargement automatique des images, et les utilisateurs doivent cliquer sur un bouton du type "Charger les images" afin de les charger dans le message. Si les images ne sont pas chargées (peu importe la raison), Mautic ne pourra pas détecter que le courriel a été ouvert.

## Le tracking des clics dans un email ne fonctionne pas

Avant l'envoi d'un email, Mautic remplace tous les liens avec une clé unique pour chaque destinataire. Si le prospect clique sur un lien, il sera redirigé vers Mautic. Mautic enregistre l'action de clic et redirige vers la page originale. C'est assez rapide pour que l'utilisateur ne s'en rende pas compte.
Si le clic n'est pas enregistré, vérifiez :

1. Votre serveur Mautic est sur une URL publique. Le tracking ne fonctionne pas en hébergement local.
2. Vérifiez que l'email a été envoyé par une campagne ou un email de segment sur un contact existant. Les emails envoyés par l'action *Envoyer un test*, et *Email direct* (depuis la page du contact) ou depuis *aperçu de l'email dans les actions de formulaires* ne remplacent pas les liens par des liens tracés.
3. Vérifiez le http ou https de l'attribut `href` est valide. Cela doit commencer par http:// or https://.
4. Que vous n'avez pas ouvert la page du lien dans un navigateur en mode Incognito. Lire plus à propos des [Troubleshooting des pages](./../pages/troubleshooting.html).
5. Vérifiez si le lien dans l'email a été remplacé par un lien de tracking Mautic. Si ce n'est pas le cas, rapportez le sur https://github.com/mautic/mautic/issues avec un maximum de détails (Mautic version, PHP version, quel est l'URL avant envoi, l'URL après envoi).

## Le lien de désinscription ne fonctionne pas

Le lien de désinscription ne fonctionne pas lors des emails de test.
