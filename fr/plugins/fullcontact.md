# Plugin Mautic - FullContact

Ce plugin permet de :

- Récupérer les données depuis FullContact par l'API contacts et sociétés dans Mautic.

### Pré-requis

- Une instance Mautic installée sur une URL publiquement accessible. Ce plugin ne fonctionne pas en "localhost" (des callbacks depuis FullContact vers Mautic sont nécessaires).
- Obtenir une [clé API FullContact](https://portal.fullcontact.com/signup)

### Autorisation du plugin
![image](https://cloud.githubusercontent.com/assets/2924026/20350951/db8137e4-abde-11e6-8c93-7d4561b27f48.png)

### Usage
Sur les pages contacts et sociétés, il y a deux boutons : un sur le menu de liste déroulante, et un autre dans la barre d'outil en haut :
![image](https://cloud.githubusercontent.com/assets/2924026/20355065/110eec8a-abee-11e6-90f6-c1d6228ed995.png)
![image](https://cloud.githubusercontent.com/assets/2924026/20401066/57993bb0-acc5-11e6-8f3e-16d51cb24c57.png)

Lors du clic sur un de ces boutons, une fenêtre s'ouvrira:
![image](https://cloud.githubusercontent.com/assets/2924026/20521683/01b85e50-b072-11e6-9da3-fa664fdebc49.png)
![image](https://cloud.githubusercontent.com/assets/2924026/20521701/1ca56712-b072-11e6-868b-8a7806304d20.png)

Quelques instants plus tard, si des informations ont été trouvées, les détails des contacts et sociétés sertont téléchargé dans votre instance Mautic.
