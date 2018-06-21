# Plugin bi-directionnel - Mautic et Microsoft Dynamics CRM

Ce plugin permet de pousser et récupérer les contacts vers et depuis Microsoft Dynamics CRM quand un contact fait des actions ou lorsque vous exécutez une action de synchronisation de contacts.

Si nous n'avez pas de compte Microsoft Dynamics CRM, suivez les instructions créez vous un compte free trial.

## Configuration du plugin Dynamics CRM

1. Insérez l'URL de votre compte Microsoft Dynamics CRM, l'ID de l'application et le Secret ID dans le plugin Mautic et autorisez la connexion. Publiez la connexion et sauvegardez.
![Dynamics CRM Plugin configuration](media/dynamics/858c5a2a7134.png "Dynamics CRM Plugin configuration")
2. Sélectionnez en suite les fonctionnalités que vous souhaitez intégrer dans l'onglet Fonctionnalités. *Envoyer les contacts vers l'intégration* est déjà activé par défaut.
3. Configurez la [correspondance des champs](./../plugins/field_mapping.html).
4. Sauvegardez la configuration du plugin.

## Testez le plugin

Suivez [ces étapes](./../plugins/integration_test.html) pour tester l'intégration.

#### Créer un compte de test gratuit Microsoft Dynamics 365
#### Paramétrer Microsoft Dynamics 365
1. Allez sur [le site de test Dynamics 365](https://www.microsoft.com/en-us/dynamics/free-crm-trial.aspx)

![image](media/dynamics/bbdb46ab545f.png)
![image](media/dynamics/8106fe116d63.png)
![image](media/dynamics/d08c1298aa54.png)
![image](media/dynamics/7084b5f865d5.png)
![image](media/dynamics/fd5952a2005f.png)

#### Configurez Azure
1. Allez sur le [portail Azure](https://portal.azure.com)
2. Connectez vous avec votre compte onmicrosoft.com

![image](media/dynamics/4e7c9a85014f.png)

3. Allez dans 'Azure Active Directory'

![image](media/dynamics/1ecee71fe408.png)

4. Ajoutez l'enregistrement d'une nouvelle application

![image](media/dynamics/72e65de87640.png)

5. Remplissez les informations de l'application CRM

![image](media/dynamics/402a6170bc22.png)

6. Cliquez sur créer
7. Cliquez sur l'application que vous venez de créer

![image](media/dynamics/3570e550894a.png)

8. Récupérer l'ID d'application que vous utilisez dans le plugin dans Mautic

![image](media/dynamics/1f320e76452e.png)

9. Ajoutez une nouvelle clé. Donnez lui le nom de votre choix et copiez la valeur. Vous aurez à l'utiliser dans le plugin dans Mautic

![image](media/dynamics/a53a371dd0fb.png)
![image](media/dynamics/5b254970ed35.png)

10. Configurez l'URLs de réponse en utilisant les callbacks dans les paramètres du plugin dans Mautic. Cliquez sur sauvegardez.

![image](media/dynamics/e2a837fe2fc7.png)

11. Configurez les permissions requises. Cliquez sur ajouter

![image](media/dynamics/a2482b3511de.png)

12. Ajoutez l'accès API pour Microsoft Dynamics CRM Online. Cliquez sur sélectionner.

![image](media/dynamics/b6977cfd4de7.png)

13. Autoriser l'accès à Dynamics CRM pour les utilisateurs. Cliquez sur sélectionner puis valider.

![image](media/dynamics/7de74e72ae3d.png)

15. Activez les permissions en cliquant sur "Obtenir Permissions". Puis Oui.

![image](media/dynamics/abc667cdd178.png)

16. Retournez dans Mautic
17. Autorisez le plugin

![image](media/dynamics/858c5a2a7134.png)

18. Utilisez votre compte onmicrosoft.com pour vous identifier

![image](media/dynamics/3a66e53a9265.png)

19. Le plugin est prêt. Vous pouvez tester en utilisant l'action "Envoyer les contacts vers l'intégration" dans les formulaires, campagnes et points.
20. Vous pouvez également tester en utilisant : `php app/console mautic:integration:fetchleads -i Dynamics`
