# Contenu dynamique web

Mautic 2.0 a introduit la possibilité de d'intégrer du contenu dynamique sur les pages web pour les contacts anonymes et identifiés.

Voici les différentes étapes à suivre pour le paramétrage.

## Paramétrage
### Ajouter le contenu par défaut
![](/dwc/media/dwc-default.jpg)

### Ajouter un contenu alternatif souhaité
Vous pouvez paramétrer autant d'objets que souhaités. La valeur par défaut sera distribuée par la décision "Request Dynamic Content" dans une campagne. Si vous souhaitez afficher un contenu différent en fonction d'un critère, vous créez cela dans l'action "Pousser du contenu dynamique".

### Ajouter la demande de contenu dynamique
La clé de cet étape est de nommer le "slot". Cela peut être n'importe quoi mais doit être constent entre les campagnes.
![](/dwc/media/dwc-pull-request.jpg)

### Ajouter l'affichage du contenu dynamique
Si vous souhaitez distribuer du contenu en fonction de certains critères.  
1. Si le contact est connu, ils recoivent le contenu de la notification.
2. S'il rempli le critère (dans l'exemple ci dessous - s'il est du Canada), un contenu différent peut être affiché dans le navigateur.  
3. S'il est inconnu, il vera l'information inégrée dans le contenu web dynamique de la page (voir ci dessous).
![](/dwc/media/dwc-push.jpg)

### Finalement, inclure la varible de contenu dynamique dans votre page web
```
<div class="mautic-slot" data-slot-name="dwc">Texte dans le html -
cela s'affiche si le contact est inconnu</div>
```
Notez que le data-slot-name correspond au "slot" dans la campagne.

Regardez la vidéo tuto : (https://www.youtube.com/watch?v=eChzJm5yBUk)

## Traductions

Le contenu web dynamique support des contenus traduits. Lorsque vous créez/modifiez un objet contenu web dynamique, vous avez une option pour ajouter une taduction et choisir l'objet parent.
