# Notifications mobiles

Les notifications mobiles sont activable sur vos applications iOS et Android avec [One Signal](https://onesignal.com/). En utilisant votre compte OneSignal, vous pouvez maintenant envoyer des push notifications sur les smartphones de vos contacts (avec leur permission). Activez la fonctionnalité dans la configuration Mautic pour le voir apparaitre dans les Cannaux de votre menu principal.

Pour plus d'information, consultez [la documentation One Signal iOS](https://documentation.onesignal.com/docs/ios-native-sdk) et [One Signal Android](https://documentation.onesignal.com/docs/android-native-sdk)

### Configuration

### Code iOS pour l'intégration OneSignal

Pour activer les push notifications dans votre application iOS, ajoutez le code suivant (ou une variante) dans votre `application` func du `AppDelegate`. Les exemples de code suivant utilisent Swift 3.1. Modifiez les selon votre besoin si vous utilisez C#.

```
// Somehow determine the user email. If you have user accounts, it may be better to move
// this outside of the `application` func of `AppDelegate` in order to determine the user email.
// In this example, the address is hardcoded for ease of use.
let userEmail = "you@domain.com"

OneSignal.initWithLaunchOptions(launchOptions, appId: "YOUR-ONE-SIGNAL-APP-ID")
OneSignal.syncHashedEmail(userEmail);

OneSignal.idsAvailable({(_ userId, _ pushToken) in
    let pushId      = userId != nil ? userId : ""
    let pushEnabled = pushToken != nil ? true : false
    let userData    = UserData(email: userEmail, push_id: pushId!, enabled: pushEnabled)

    self.pushUserDataToMautic(userData, "https://dev.mautic.com/notification/appcallback")
});
```

Pour des questions de praticité, nous avons créé les `struct` et `func` suivantes pour envoyer les données d'utilisateur à Mautic.
Créez cette `struct` dans votre app, et importez là où c'st nécessaire.

#### UserData struct
```
struct UserData {
    var email   = String()
    var push_id = String()
    var enabled = Bool()

    static func toJSON(_ userData: UserData) -> String {
        let email   = userData.email
        let pushId  = userData.push_id
        let enabled = userData.enabled

        return "{\"email\":\"\(email)\",\"push_id\":\"\(pushId)\",\"enabled\":\(enabled)}"
    }
}
```

#### pushUserDataToMautic func

Ceci est une fontion basique pour envoyer la `UserData struct` à votre instance Mautic.
Cela enverra la `user data`, et affichera la réponse de Mautic comme une alerte.
Modifiez pour atteindre vos objectifs.

```
func pushUserDataToMautic(_ userData: UserData, _ url: String) {
    var request = URLRequest(url: URL(string: url)!)
    request.httpMethod = "POST"

    let postString = UserData.toJSON(userData)
    request.httpBody = postString.data(using: .utf8)

    let task = URLSession.shared.dataTask(with: request) { data, response, error in
        guard let data = data, error == nil else {
            // check for fundamental networking error
            return
        }

        if let httpStatus = response as? HTTPURLResponse, httpStatus.statusCode != 200 {
            // check for http errors
            return
        }

        // Comment the next 4 lines to remove the alert
        let responseString = String(data: data, encoding: .utf8)
        let alert = UIAlertController(title: "Response Data", message: responseString, preferredStyle: UIAlertControllerStyle.alert)
        alert.addAction(UIAlertAction(title: "OK", style: UIAlertActionStyle.default, handler: nil))
        self.window?.rootViewController?.present(alert, animated: true, completion: nil);
    }
    task.resume()
}
```

### Code Android pour intégration OneSignal

Coming soon...

### Statistiques de notification

En plus des `UserData` qui sont envoyées à Mautic, vous pouvez pousser les statistiques d'ouvertures et d'interactions à Mautic en envoyant la `UserData struct`, avec un l'ajout des `stat` JSON key.
