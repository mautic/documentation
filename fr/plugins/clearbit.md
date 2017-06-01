# Plugin Mautic - Clearbit

Ce plugin permet de :

- Récupérer les données depuis Clearbit par l'API contacts et sociétés dans Mautic.

### Pré-requis

- Une instance Mautic installée sur une URL publiquement accessible. Ce plugin ne fonctionne pas en localhost (des callbacks depuis Clearbit vers Mautic sont nécessaires).
- Obtenir une [clé API Clearbit](https://dashboard.clearbit.com/signup)

### Autorisation du plugin
![image](https://cloud.githubusercontent.com/assets/2924026/20487375/ad68a34a-afc8-11e6-8c49-776579476817.png)

### Utilisation
Sur les pages contacts et sociétés, il y a deux boutons : dans le menu de liste déroulante, et un autre dans la barre d'outil en haut :
![image](https://cloud.githubusercontent.com/assets/2924026/20488164/b0337e3a-afcb-11e6-8994-c213c9852632.png)

Lors du clic sur un de ces boutons, une fenêtre s'ouvrira :
![image](https://cloud.githubusercontent.com/assets/2924026/20521597/8f7e8ec2-b071-11e6-99c2-590cb90c227f.png)

Quelques instants plus tard, si des informations ont été trouvées, les détails des contacts et sociétés seront téléchargé dans votre instance Mautic.
