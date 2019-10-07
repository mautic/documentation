# Documentation Mautic

### Introduction
Ce guide fait office de [documentation pour Mautic](https://www.mautic.org/docs/index.html), le logiciel de marketing automation open source. Le code étant libre d'accès à chacun, en voici sa documentation. Chacun peut contribuer à rendre ces informations de meilleure qualité.

### Documentation développeur

Si vous cherchez des détails sur l'API Mautic, les webhooks, les thème ou le dévelopepemnt des plugins, rendez vous dans [la documentation développeur](https://developer.mautic.org/).

### Télécharger la documentation en PDF

[Cliquez ici](https://mautic.org/docs/mautic_docs_fr.pdf) pour télécharger ce document en PDF.

### Comment contribuer à la documentation

Ce repository est le lieux ou est stocké la documentation sous forme de [Gitbook](https://www.gitbook.com/) publié sur [www.mautic.org/docs](https://www.mautic.org/docs/index.html). La source du code est partagée sur GitHub afin que chacun puisse contribuer de la même manière que les développeurs contribuent pour le code de l'application Mautic.

#### Pourquoi nous utilisons git pour la documentation

- *versions*. Chacun peut regarder dans le passer et voir comment le texte était.
- *authorship*. Chaque ligne a un auteur identifié.
- *community contributions*. Nous travaillons tous sur le même document, pas de risque d'avoir d'impact négatif pour notre travail communautaire.

Ainsi, quelques connaissances en git sont requises pour cloner, modifier, commiter et envoyer les modifications. Vous pouvez éviter cela en utilisant l'interface web de GitHub. Si vous connaissez git, procédez comme vous le souhaitez.

#### Modifier un document dans votre navigateur

1. Faites un [Clone](https://github.com/mautic/documentation#fork-destination-box) du repository sur votre compte afin d'avoir les droits d'édition.
2. Sélectionnez un fichier à éditer. La structure du fichier est expliquée ci dessous. Maintenant, éditons le fichier *README.md* pour en voir le principe. Cliquez sur celui ci.
3. Le contenu du *README.md* devrait être visible et le bouton *Edit* (pictogramme stylo). Cliquez dessus.
4. Le contenu est écrit en [Markdown markup](https://daringfireball.net/projects/markdown/). Format de mise en forme de texte très simple.
5. Faites une modification sur le fichier. Par exemple, ajoutez à la fin `Ceci est ma première contribution`.
6. Quand vous faites une modification, descendez et constatez le bouton *Commit changes*. Ceci est important. Pour sauvegarder des modifications, vous devez décrire ce que vous avez changé et pourquoi. Par exemple `Une nouvelle ligne ajoutée dans un but de test`. Ne sauvegardez pas maintenant !
7. L'interface GitHub web ne vous donne pas accès à toutes les fonctionnalités de git, et il sera compliqué de revenir en arrière après votre modification. Il faudrait créer un nouveau commit pour modifier votre modification précédente. Ca rendrait l'historique un peu compliqué. Du coup, créons une nouvelle branche. Il y a une case à cocher "Créer une nouvelle branche...". Vous devez donner un nom à cette branche. `{yourusername}-patch-1` sera pré-rempli. Changez le par `{yourusername}-testing` par exemple. Cliquez sur *Propose file change* maintenant.
8. Voici, le changement existe dans votre clone. Pour propose ce changement au repository officiel, vous devez faire une pull request (PR). Vous avez normalement été redirigé pou faire cela. Décrivez ici votre proposition de changement et cliquez (ne le faits pas pour tester s'il vous plait) sur le bouton *Create pull request*.


#### La structure du fichier

Nous avons travaillé sur le fichier *README.md*. Ce fichier est affiché sur la page d'accueil du repository GitHub et vous êtes en train d'en lire son contenu en ce moment même.

Le fichier *SUMMARY.md* gère le menu de la documentation.

Les dossiers regroupent des sujets similaires.

#### Liens

Pour faire un lien en Markdown, procédez ainsi :

```
[link title](http://example.com)
```

Cela créera un lien externe. Si vous voulez faire des liens relatifs :

```
[these steps](./../plugins/integration_test.html)
```

#### Images

Vous pouvez stocker des images dans les dossiers assets et puis vous pouvez les afficher dans les pages de la manière suivante :

```
![alternative text here](http://example.com/images/apple.png "Tooltip text here")
```
ou avec des liens relatifs.
