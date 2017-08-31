# Plugin Gmail pour Mautic
Ce plugin permet à [l'extension Chrome Mautic Helper](https://chrome.google.com/webstore/category/extensions) de tracer les emails envoyés directement depuis Gmail.

### Pré-requis

- Mautic installé sur une URL publiquement accessible.
- Un compte Gmail (pour tracer les emails).
- [L'extension Chrome "Mautic Helper"](https://chrome.google.com/webstore/category/extensions)

### Configuration du plugin
1. Installez le plugin Mautic. Il apparait dans la liste des plugins disponibles dans votre Mautic.
![image](https://cloud.githubusercontent.com/assets/2924026/18927139/dc426b0e-8577-11e6-934d-d428c2bf8cef.png)

2. Cliquez sur le bouton du plugin Gmail plugin et entrez une clé secrète pour valider l'extension Chrome "Mautic Helper"
![image](https://cloud.githubusercontent.com/assets/2924026/18927155/f336b23e-8577-11e6-99a7-9e1e5b493f5c.png)

3. Installez l'[extension Chrome "Mautic Helper"](https://chrome.google.com/webstore/category/extensions) disponible dans le Chrome Web Store
![image](https://cloud.githubusercontent.com/assets/2924026/18927690/2c995d2c-857a-11e6-9870-c5bf5b27e3be.png)

4. Configurez l'extension. (Utilisez la même clé secrète utilisée dans votre plugin Mautic)
![image](https://cloud.githubusercontent.com/assets/2924026/18927264/63b57608-8578-11e6-8721-07c0422ab9b8.png)

5. Dans le navigateur Chrome, un bouton apparaitra pour vous notifier lorsque de nouveaux événements se produirons pour vos contacts.
![image](https://cloud.githubusercontent.com/assets/2924026/18927593/cea645ea-8579-11e6-90e3-d760d0d0d682.png)

6. Pour ajouter le tracking à l'email envoyé à un contact, cliquez sur le bouton "Track Email“ dans la fenêtre d'écriture d'un nouvel email dans Gmail.
![image](https://cloud.githubusercontent.com/assets/2924026/18927624/e54bd2f6-8579-11e6-92f1-880fcc1c5839.png)

7. Cela ajoutera un pixel de tracking GIF à votre email avec la forme suivante :  [[MAUTIC_URL]]/index.php/gmail/tracking.gif?d=H4sIAAAAAAAEAIVRTW%2FCMAz9LRyCtgNVlFBpHHroWsRuk8ak7RpaUzqaGCUp0H8%2Fpy0TH4dJUZy892w921uLOvkCa8BGK2WLWi2dt6pUbM7PYPEcFainoFXdJKdBVvUy4quA9rxrNz9Q%2BCQ16HdgmeAenKewpfIU3lvfIO6nGyy75HNXO8LQAN3984R2X5tqMpkwnjOejrfg19%2FBJIHBJsskS3M1MOvOedChUA5HaPBAsp54a7UyBH%2BAw9YWECRrsMc6PHvFd2iR0NfW1QbcjUDwMjhctYqqq0YxkQU6SqMhNxi85GeoD8p0134zaBom%2By4ezlPMxTPFeCH5TLzI%2BdgizeEu5aIUQixmIubjSG5WAY8bC8kyC%2FvxSBX%2Flcvl3bT%2Fvr8k1oBgIQIAAA%3D%3D&sig=cf078d5b

8. Le plugin Mautic validera l'information en comparant les clés secrètes et ajoutera ensuite l'événement à l'historique du contact dans Mautic. Si le(s) contact(s) n'existe pas déjà, il sera créé automatiquement.
![image](https://cloud.githubusercontent.com/assets/2924026/18927644/f70f71fa-8579-11e6-91be-6acaba36e7e6.png)

## Problèmes de longueur de paramètre URL
Veuillez noter que les paramètres PHP avec le patch suhosin installé aura comme valeur par défaut une limite de 512 caractères pour les paramères GET. Cependant, la majorité des navigateurs (incluant IE) supportent les URLs jusqu'à 2000 caractères alors qu'Apache à une valeur par défaut de 8000.
Pour supporter des paramètres plus longs, ajouter le paramètre suivant dans php.ini
`suhosin.get.max_value_length = 5000`
