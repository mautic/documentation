# Gestion des formulaires

La page de création d'un nouveau formulaire vous permet de créer le formulaire de votre choix avec les champs qui sont adaptés à votre besoin afin de collecter les informations sur vos visiteurs et les convertir en contacts. Après avoir créé les champs nécessaires, vous pouvez définir les actions que vous souhaiterez déclancher à la soumission du formulaire.

### Aperçu du formulaire

L'aperçu général vous permet d'obtenir des informations rapidement sur l'évolution des soumissions du formulaire dans le temps afin de facilement faire vos analyses. Le bas de la page met en avant les contacts ayant soumis le formulaire et les actions liées au formulaire.+

### Champs de formulaire

Un formulaire peut contenir autant de champs que souhaité. Il existe différents formats qui mettront automatiquement en place un controle du format des données saisies par le visiteur.

![](/forms/media/new-form.jpg)

#### Formulaire multi-étape

Les formulaires multi étape sont disponibles depuis la version 2.2.0. Cela vous permet de créer un formulaire sur plusieurs pages. Les informations seront enregistrées à la soumission de la dernière page.

Chaque page vous donnera l'opportunité d'ajouter un bouton "précédante"/"suivante".

![](/forms/media/page-break.png)

### Actions du formulaire

Les actions du formulaire dont les actions déclanchées à la soumission du formulaire. Vous pouvez définir de multiples actions à déclencher pour chaque soumission de formulaire.

![](/forms/media/form-actions.jpg)

#### Envoi des informations dans un autre formulaire

Les résultats d'un formulaire Mautic peuvent être renvoyés dans une application tierce en utilisant la nouvelle action "Envoyer les résultats dans un autre formulaire".
Un email peut être envoyé si cela échoue.

En plus de la forme de la donnée, un tableau de `mautic_form` avec les détails comme l'ID, le nom, et l'URL d'où le formulaire a été soumis en plus du `mautic_contact` contenant les informations soumises par le contact dans le formulaire.

![](/forms/media/repost.png)

### Création et mise à jour des contacts via les formulaires

Afin que vos formulaires créent ou mettent à jour vos contacts, (pour mettre à jour, l'adresse email doit correspondre à un contact déjà existant), il faudra faitre correspondre le champ du formulaire avec un champ de contact existant dans votre plateforme Automation.

**Attention, cette action est indispensable si vous souhaitez collecter l'information et déclancher des actions dépendentes des données associées à vos contacts.** En effet, le contacts doit être créé ou mis à jour avant d'être ajouté à un segment, poussé dans votre CRM, qualifié pour une campagne, etc.+

![](/forms/media/rebuild.png)

#### Mode kiosque

Le mode kiosque est utile lorsque vous savez qu'un formulaire va être soumis par plusieurs personnes depuis un même support (ordinateur ou mobile). Par exemple, si vous avez un ipad sur un salon ou lors d'un conférence pour toute votre équipe commerciale, chaque soumission va créer un nouveau contact. Si le mode kiosque n'était pas activé le même contact serait mis à jour chaque soumission.

#### Indexation de la page du formulaire

Mautic introduit en 2.15.0 la possibilité de désactiver l'indexation de la page du formulaire par les moteurs de recherches. Ainsi, vous pouvez décider si les pages `http(s)://yourmauticurl.com/form/{formid}` sont indexées ou non.

### Intégration du formulaire

Il y a 3 moyens d'intégrer un formulaire sur une page de votre site web. Vous pouvez copier l'intégralité du code généré ou vous pouvez intégrer le code sur votre site de façon dynamique en utilisant le javascript ou l'iframe. Vous pouvez également intégrer votre formulaire sur une page d'atterrissage créée dans Automation.

![](http://drop.dbh.li/image/2M1q3T2T0Z0u/Image%202014-11-17%20at%204.20.56%20PM.png)

**Il est recommandé de ne pas coller le code d'intégration du formulaire deux fois sur une même page, cela risque de créer des erreurs à la soumission du formulaire lorsqu'il y a des champs obligatoires.**

### Résultats du formulaire

Sur la page d'aperçu global d'un formulaire vous pouvez cliquer sur le bouton en haut à droit 'Résultats'. Cela vous emmènera sur une page où vous pourrez facilement classer et filtrer les résultats, ainsi que les exporter dans différents formats (xls, html, csv).

### Prévisualisation du formulaire

La prévisualisation du formulaire vous permettra de constater rapidement à quoi ressemblera votre formulaire une fois intégré. Gardez en tête que la mise en forme du formulaire est controlée par la CSS de votre site web et que le rendu final sera probablement bien différent une fois intégré sur votre site.

### Style du formulaire

Il est possible de choisir un thème pour un formulaire. Si vous procédez ainsi et que le thème supporte les formulaires, le formulaire apportera son propre style CSS.
Il est également possible de ne pas choisir de thème et d'appliquer un style CSS directement sur votre site web.

### Pré-remplir un formulaire avec des valeurs

Il est possible de pré-remplir les valeurs de champ avec des paramètres dans une URL.

Vous pouvez récupérer l'alias du champ du contact dans la table Contacts -> Manage Fields (directement en SQL). Le nom du champ du formulaire y est stocké. Par exemple, voici un échantillon html pour un formulaire. Le nom à utiliser est `mauticform[FIELDNAME]`.

```
<div class="mauticform-row mauticform-email mauticform-row-email" id="mauticform_email">
    <label id="mauticform_label_email" for="mauticform_input_email" class="mauticform-label" "="">Email</label>
    <input id="mauticform_input_email" name="mauticform[email]" value="" class="mauticform-input" type="email">
</div>
```

#### Pré-remplir les valeurs dans un email

Ajoutez les tokens {leadfield=FIELDALIAS|true}, un paramètre pour chaque valeur que vous souhaitez préremplir dans le formulaire depuis un lien issu d'un email. La valeur `|true` explique à Mautic d'encoder la valeur de l'URL.
```
{pagelink=1}&email={leadfield=email|true}
```
