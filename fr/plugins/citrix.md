# Plugins Citrix

## Description

Ces différents plugins permettent de récupérer et envoyer des données depuis GotoMeeeting, GotoWebinar, GotoTraining et GoToAssist.

## Fonctionnalités

1. Crée les inscrits dans GoToWebinar et GoToTraining en fonction des décisions de campagne, des données du contact et de l'negistrement depuis les formulaires Mautic.
2. Renvoie les inscrits et participants depuis Citrix dans les segments et les campagnes.
3. Affiche la participation aux webinaire et formations (training) comme information complémentaire dans le fil d'activité du contact.
4. Envoi des emails avec les boutons de démarrage des événements GoToMeeting, GoToTraining et GoToAssist.

## Instructions
1. Activez le plugin de votre choix

![image](https://cloud.githubusercontent.com/assets/2924026/19797584/54467954-9ca9-11e6-8e31-f80f7469fe84.png)

2. Activez l plugin avec les clés API Citrix Developer

![image](https://cloud.githubusercontent.com/assets/2924026/19797588/5c6ce640-9ca9-11e6-981c-a98a728e1712.png)

3. Renseignez la "Consumer Keys" depuis le site développeur de Citrix

![image](https://cloud.githubusercontent.com/assets/2924026/19797595/612744f0-9ca9-11e6-90b0-566fdff69ef4.png)

4. De nouveaux filtres de segments sont désormais disponibles

![image](https://cloud.githubusercontent.com/assets/2924026/19797599/655fb6ce-9ca9-11e6-9d27-9ec295068a1a.png)

5. Vous pourrez sélectionner les événements passés

![image](https://cloud.githubusercontent.com/assets/2924026/19797600/69dd3604-9ca9-11e6-8212-7a0a383bff34.png)

6. De nouveaux types de champs sont disponibles dans les formulaires

![image](https://cloud.githubusercontent.com/assets/2924026/19798154/9954bf30-9cac-11e6-8173-06acc0ca1fa1.png)

7. Le champ affiche les événements disponibles à venir (le formulaire vérifira que vous avez bien utilisé tous les champs obligatoires à l'inscription aux événements)

![image](https://cloud.githubusercontent.com/assets/2924026/19797605/72ec51e4-9ca9-11e6-8416-be31a013c8d1.png)

8. Une nouvelle action de formulaire est disponible

![image](https://cloud.githubusercontent.com/assets/2924026/19797611/7699f9c2-9ca9-11e6-96f5-d90dcafcbd3f.png)

9. Chaque action permet vous permet de choisir d'afficher un seul événement ou de laisser le visiteur choisir parmis la liste d'événements depuis le formulaire.

![image](https://cloud.githubusercontent.com/assets/2924026/19797613/7b25eb68-9ca9-11e6-99c7-d9f4053136ac.png)

10. Voici un exemple de formulaire qui laisse le choix au visiteur

![image](https://cloud.githubusercontent.com/assets/2924026/19797614/7eea2f02-9ca9-11e6-86dd-c895bb0d65c3.png)

11. L'action d'envoi du lien de participation à l'événement nécessite d'utiliser un Token pour insérer le lien dans le contenu de l'email (sur le bouton par exemple)

![image](https://cloud.githubusercontent.com/assets/2924026/19797615/82b326f2-9ca9-11e6-9d30-1324b7efd49a.png)

12. Il existe de nouvelles conditions dans les campagnes (*inscrit* et *à participé*)

![image](https://cloud.githubusercontent.com/assets/2924026/19797618/8693fb8e-9ca9-11e6-8ae2-44b67f05769e.png)

13. Vous pouvez déclencher des actions spécifiques depuis les campagnes

![image](https://cloud.githubusercontent.com/assets/2924026/19797619/8a501b68-9ca9-11e6-8232-d5c23b9cf445.png)

14. Voici un exemple de campagne qui envoie le lien pour un rendez-vous préliminaire après l'inscription du contact à un webinaire

![image](https://cloud.githubusercontent.com/assets/2924026/19797623/8d7b1252-9ca9-11e6-9370-b3f05cc08ee1.png)

15. Dans cet exemple, le formulaire a été soumis

![image](https://cloud.githubusercontent.com/assets/2924026/19797632/9122e614-9ca9-11e6-991c-70b2033ea6c9.png)

16. L'événement est inscrit dans le fil d'actualité du contact

![image](https://cloud.githubusercontent.com/assets/2924026/19797638/9484bb7a-9ca9-11e6-9a18-62eab010378e.png)

17. L'email avec le lien de participation à l'événement (injecté grace au token) et vue dans le navigateur

![image](https://cloud.githubusercontent.com/assets/2924026/19797642/986c9c30-9ca9-11e6-9233-5e826f2520b9.png)

18. Lorsque le contact clique sur le lien, il sera redirigé vers l'événement et il démarrera

![image](https://cloud.githubusercontent.com/assets/2924026/19797644/9c6e43ce-9ca9-11e6-8f45-ec36b19502fa.png)

19. Ceci est un exemple d'un webinaire où le contact a participé

![image](https://cloud.githubusercontent.com/assets/2924026/19797647/a012bfb4-9ca9-11e6-8d27-92edfb071bfb.png)

20. Quand le CRON qui synchronise les données est activé, il récupère les données de participations et d'événements

![image](https://cloud.githubusercontent.com/assets/2924026/19797652/a435ee36-9ca9-11e6-9936-17cd19384452.png)

#### Les exemples ci dessus utilisent GoToMeeting et GoToWebinar, les méthodologies sont identiques pour GoToTraining et GoToAssist

### Paramétrage du CRON
Le CRON à paramétrer pour la synchronisation des données est :

`php app/console citrix:sync`

##### Usage
citrix:sync [options]

#### Options
* -p, --product[=PRODUCT]  Product to sync (webinar, meeting, training, assist)
* -i, --id[=ID]            The id of an individual registration to sync
