# Envoyer un message appelant une action via Microsoft Graph

Exemple de ligne de commande qui utilise la [Bibliothèque d’authentification Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) et la [Bibliothèque de client Microsoft Graph](https://www.nuget.org/packages/Microsoft.Graph/) pour envoyer un [message avec une carte de message actionnable](https://docs.microsoft.com/en-us/outlook/actionable-messages/) à l’utilisateur authentifié.

## Exécution de l’exemple

Pour exécuter l’exemple, vous devez inscrire une application dans le [portail d’inscription des applications](https://apps.dev.microsoft.com) pour obtenir un ID d’application, puis copier cet ID d’application dans le fichier [App. config](./App.config).

### Inscription de l’application

1. Accédez au [Portail d’inscription des applications](https://apps.dev.microsoft.com) et connectez-vous avec votre compte Microsoft ou un compte Office 365.
1. Cliquez sur le bouton **Ajouter une application**. Entrez un nom pour l’application, puis cliquer sur**Créer une application**.
1. Cliquez sur le bouton **Ajouter une plateforme** puis sélectionnez **Application mobile**.
1. Cliquez sur **Enregistrer**.

> **Remarque :** À ce moment-là, il existe un bogue dans le portail qui ajoute une entrée de plateforme **web** à votre inscription lorsque vous cliquez sur **Enregistrer**. Dans ce cas, il vous suffit de cliquer sur le bouton **Supprimer** sur la plateforme **web**, puis de cliquer sur **Enregistrer**.

Une fois que vous avez terminé, l’inscription doit ressembler à ceci :

![Capture d’écran de l’inscription d’application terminée dans le portail d’inscription d’application](readme-images/app-registration.PNG)

Copiez la valeur **ID de l’application**

### Ajoutez l’ID de l’application au projet

1. Ouvrez le fichier [App.config](App.config) dans l’explorateur de solutions.
1. Recherchez la ligne suivante : 

    ```xml
    <add key="applicationId" value="" />
    ```
1. Collez l’ID d’application que vous avez copié à partir du portail dans la `valeur` puis enregistrez le fichier. Par exemple, si vous utilisez l’ID d’application de la capture d’écran ci-dessus, la ligne sera mise à jour vers :

    ```xml
    <add key="applicationId" value="b9831d46-3f6b-4c77-82d3-220a9ea4e5ba" />
    ```

### Création et exécution de l’application

Appuyez sur **F5** dans Visual Studio pour générer et exécuter l’application. Une fenêtre d’invite de commandes s’affiche, puis une fenêtre contextuelle d’authentification s’affiche.

![Capture d’écran de la fenêtre contextuelle d’authentification](readme-images/auth-popup.PNG)

Connectez-vous avec un compte Microsoft (avec une boîte aux lettres Outlook.com) ou un compte Office 365 (avec Exchange Online). Consultez la liste des autorisations demandées, puis cliquez sur **Accepter** ou **Annuler**. (**Remarque :** en choisissant **Annuler** l'application renvoie une erreur et à ne pas envoyer de message.)

La fenêtre d’invite de commandes doit afficher `Message envoyé` pour indiquer que la réussite. Consultez votre boîte de réception à l’aide d’Outlook sur le web pour le message.

### Modification de la carte ou du corps du message

Vous pouvez essayer différents formats pour la carte et le corps du message en modifiant respectivement [Card.json](Card.json) et [MessageBody.html](MessageBody.html). Pour créer rapidement des charges utiles de carte de test, visitez [https://messagecardplayground.azurewebsites.net/](https://messagecardplayground.azurewebsites.net/).