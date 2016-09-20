
---
# métadonnées requises

titre : application mise en service des profils | Microsoft Intune description : Intune vous offre les outils fait déployer une nouvelle stratégie de profil de mise en service qu’aux appareils dotés des applications qui sont arrive à expiration.
mots clés : auteur : Gestionnaire de robstackmsft : angrobe ms.date : ms.topic 19/07/2016 : article ms.prod : ms.service : microsoft intune ms.technology : ms.assetid : 86fbe736-7bdb-4f5e-ae21-13c91eb2462c

# métadonnées facultatives

#ROBOTS :
#public :
#MS.DevLang :
MS.Reviewer : mghadial ms.suite : ems
#MS.tgt_pltfrm :
#MS.Custom :

---

# Utiliser les stratégies de profil de mise en service mobile iOS pour empêcher l’expiration de vos applications


Ligne d’iOS Apple des applications métiers déployées pour iPhone et iPad sont générées avec un profil de mise à disponibilité inclus et le code est signé avec un certificat. Lorsque l’application est exécutée, iOS confirme l’intégrité de l’application iOS et applique les stratégies définies par le profil de mise en service. Contrôles suivants se produisent :

- **L’intégrité du fichier d’installation** - iOS compare les détails de l’application avec l’entreprise clé publique du certificat de signature. S’ils sont différents, le contenu de l’application peut-être avoir changé, et l’application ne pas être autorisée à exécuter.
- **Mise en œuvre des fonctionnalités** - iOS tente d’appliquer des fonctionnalités de l’application à partir de l’entreprise mise en service de profil (développeur individuel pas les profils de mise en service) qui se trouvent dans le fichier d’installation (.ipa) application.


L’entreprise qui vous permet de vous connecter applications généralement le certificat de signature dure trois ans. Toutefois, la mise en service profil expire après une année. Alors que le certificat est toujours valide, Intune vous offre les outils fait déployer une nouvelle stratégie mise en service de profil qu’aux appareils dotés des applications qui sont arrive à expiration.
Une fois que le certificat arrive à expiration, vous devez vous connecter à l’application d’un nouveau certificat et incorporer un nouveau profil de mise à disponibilité avec la touche du nouveau certificat.



## Comment savoir quand une ligne de l’application entreprise arrive à expiration

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **applications** > **applications**.
2. Dans la liste des applications, examinez la colonne **date d’Expiration** pour afficher la date d’expiration pour l’application. Vous pouvez également définir la liste déroulante **filtres** à **expiré/sur le point d’expirer** pour afficher uniquement les applications dont vous devez prendre des mesures.

## Comment créer un iOS mobile stratégie mise en service de profil


1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** > **vue d’ensemble** > **Ajouter une stratégie**.
2. Dans la boîte de dialogue **créer une nouvelle stratégie** , cliquez sur **iOS** > **Stratégie du profil de mise en service Mobile**, puis cliquez sur **Créer une stratégie**.
3. Dans la page **Général** , configurez les valeurs suivantes :
    - **Nom** : attribuez un nom à cette stratégie de profil de mise en service mobile.
    - **Description** - Entrez éventuellement une description pour la stratégie.
    - **Fichier de configuration de profil** - cliquez sur **Importer**, puis choisissez un fichier de profil de Configuration de Mobile Apple (avec l' extension **.mobileprovision**) que vous avez téléchargé depuis le site Web pour les développeurs Apple.
4. Lorsque vous avez terminé, cliquez sur **Enregistrer la stratégie**.
5. À présent, déployer la stratégie sur les appareils iOS requis. Pour plus d’informations, voir [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).
