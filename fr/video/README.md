# Video avec formulaire #

Ce nouveau canal d'acquisition a été introduit dans Mautic en version 2.1. Cela permet aux utilisateurs Mautic d'intégrer des vidéos dynamiques sur leurs sites web, pages d'atterrissage et n'importe où le script de tracking Mautic est installé. Dans Mautic, les vidéos dynamiques sont des vidéos qui se lisent un temps souhaité, puis se mettent en pause en affichant un formulaire pour voir la suite. Le contact est ainsi capturé et la vidéo continue à se lire depuis là où elle avait été mise en pause.

## Utiliser les fomulaires dynamiques ##

Ce ne sont pas des objets à part entière et ces vidéos n'ont donc pas de menu spécifique. Les vidéos dynamiques peuvent être intégrées dans vos pages d'atterrissage comme contenu ou sur les pages de votre site où le script de tracking Mautic est installé.

Les libraries jQuery et Vimeo's Froogaloop sont nécessaires pour cette fonctionnalité. Elles seront automatiquement insérées dans vos pages d'atterrissage si une vidéo est détectée.

N'importe quel tag `<video>` trouvé par le javascript qui possède les attibuts `data-form-id` et `data-gate-time` sera traité comme une vidéo dynamique par le javascript de Mautic. La façon la plus simple d'utiliser les vidéos dynamiques Mautic et d'intégrer le code HTML ci dessous sur une page où le script de tracking Mautic est installé.
1. Gardez à l'esprit qu'il faudra remplacer l'ID du formulaire dans l'exemple par un ID de formulaire existant sur votre plateforme
2. Qu'il faudra que le temps de déclenchement de l'affichage du formulaire (__data-gate-time__) soit remplacé par le temps souhaité
3. L'attribut `type` dans la `<source>` peut contenir les valeurs suivantes : `video/youtube`, `video/vimeo`, ou `video/mp4`.
  * Quand vous utilisez `video/youtube` ou `video/vimeo`, vous devez modifier l'URL par celle qu vous récupérez dans votre navigateur lorsque vous visionnez la vidéo, et l'insérr dans l'attribut `src`.
  * Si vous utilisez le format `video/mp4`, utilisez l'URL complète vers la source où est hébergée la vidéo.

```html
<video width="640" height="360" data-form-id="1" data-gate-time="15">
    <source type="video/youtube" src="https://www.youtube.com/watch?v=QT6169rdMdk" />
</video>
```

Si le formulaire choisi affiche le *Message de succès à la soumission* paramétré dans *Message à afficher* lors de la configuration de votre formulaire, c'est que cela a fonctionné et le message s'affichera pendant 3 secondes.

Pour intégrer une vidéo dynamique dans votre page d'atterrissage, cliquez dans une zone de texte dans le générateur de page, dans l'éditeur Froala. Sur la ligne du haut, cliquez sur *Insérer une vidéo* à cpoté du bouton d'*insertion d'une image*.

![](/video/media/gated-video-icon.png)

## Plugin CMS

L'utilisation de la fonctionnalité de vidéo dynamique Mautic est simplifiée si vous utilisez un plugin CMS Mautic. Nous avons un plugin pour WordPress, Joomla, Drupal, Grav, et Concrete5. Vérifier que vous avez bien la dernière version du plugin sur votre CMS.

#### WordPress, Grav
```
[mautic type="video" form-id="1" gate-time="15" src="https://www.youtube.com/watch?v=QT6169rdMdk" width="640" height="320"]
```

#### Drupal, Joomla
```
{mautic type="video" form-id="1" gate-time="15" src="https://www.youtube.com/watch?v=QT6169rdMdk" width="640" height="320"}
```
