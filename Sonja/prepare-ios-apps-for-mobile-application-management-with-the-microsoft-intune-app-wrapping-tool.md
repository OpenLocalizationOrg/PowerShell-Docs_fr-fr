---
title: "Renvoyer à la ligne applications iOS avec l’outil d’habillage application | Microsoft Intune"
description: "Utilisez les informations dans cette rubrique pour apprendre à renvoyer à la ligne de vos applications iOS sans modifier le code de l’application elle-même. Préparer les applications afin que vous pouvez appliquer des stratégies de gestion de l’application mobile."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
ms.openlocfilehash: a07958d58d037545630fcfda749ee0e58b84c69d
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Préparer des applications iOS pour la gestion des applications mobiles avec l’outil d’habillage de l’application Intune
Utilisez l' **Outil Microsoft Intune d’habillage du application pour iOS** pour modifier le comportement des applications iOS internes en limitant les fonctionnalités de l’application sans modifier le code de l’application elle-même.

L’outil est une application de ligne de commande du système d’exploitation Mac qui crée un emballage autour d’une application. Une fois qu’une application est traitée, vous pouvez ensuite modifier les fonctionnalités de l’application à l’aide de [stratégies de gestion des applications mobiles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) que vous configurez.

Pour télécharger l’outil, voir [Microsoft Intune application habillage outil pour iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

>[!IMPORTANT]
>La version de l’application, un outil qui prend en charge des appareils ne pas inscrits dans Intune, d’habillage est disponible pour la version d’évaluation. Si vous souhaitez participer à la version d’évaluation, vous pouvez télécharger l’outil à partir de [cette page github](https://github.com/msintuneappsdk/intune-app-wrapper-ios-preview) pour iOS.

>Le scénario est décrite dans la rubrique [applications métiers protéger sur appareils ne pas inscrits dans Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md) .

## Étape 1 remplissent les conditions préalables à l’aide de l’application outil d’habillage
Lisez [ce billet de blog](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) pour en savoir plus sur les conditions préalables et comment les définir.

|Configuration requise|Plus d’informations|
|---------------|--------------------------------|
|Jeu d’outils et de système d’exploitation pris en charge|Vous devez exécuter l’application sur un ordinateur Mac qui s’exécute OS X 10.8.5 d’habillage outil ou une version ultérieure, qui dispose de la version de jeu d’outils XCode 5 ou version ultérieure.|
|Certificat de signature et mise en service de profil|Vous devez avoir un Apple certificat de signature et mise en service de profil. Consultez la [documentation du développeur Apple](https://developer.apple.com/).|
|Traitement d’une application avec l’application outil d’habillage|Applications doivent être développées et signées par votre entreprise ou un éditeur de logiciels (fil). Vous ne pouvez pas utiliser cet outil pour traiter les applications dans le Store d’Apple. Applications doivent être écrits pour iOS 8.0 ou version ultérieure. Applications doivent également être au format Position indépendante exécutable (secteur). Pour plus d’informations sur le format de graphique en secteurs, voir la documentation développeur Apple. Enfin, l’application doit avoir l’extension **.app**, ou format **.ipa** .|
|L’outil d’habillage ne peut plus traiter des applications|Applications chiffrées, les applications non signées et les applications avec les attributs de fichier étendu.|
|Définition de droits d’accès pour votre application|Vous devez définir les droits d’accès, qui fournissent les autorisations des applications supplémentaires et les capacités au-delà de celles généralement accordées, avant de vous renvoyer à la ligne de l’application. Pour obtenir des instructions, voir [droits au paramètre application](#setting-app-entitlements) .|

## Étape 2 installer l’application outil d’habillage

1.  Dans la page **Microsoft Intune application habillage outil pour iOS** dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=45218), téléchargez le fichier d’installation de l’outil d’habillage application sur un ordinateur Mac.

2.  Sur l’ordinateur Mac, double-cliquez sur le fichier d’installation **Microsoft Intune application habillage outil pour iOS.dmg**.

3.  Cliquez sur **Accepter** pour accepter le contrat de licence utilisateur final (CLUF). Le programme d’installation est chargé et affiché sur l’ordinateur Mac.

4.  Le programme d’installation et copiez les fichiers affichés dans un dossier sur l’ordinateur Mac. Vous pouvez maintenant déconnecter le lecteur monté installer.

    Vous êtes maintenant prêt à être exécuté l’application outil d’habillage.

## Étape 3, puis exécutez l’application outil d’habillage
* Sur l’ordinateur Mac, ouvrez une fenêtre de Terminal et accédez au dossier où vous avez enregistré les fichiers. Étant donné que le fichier exécutable réside à l’intérieur du package, vous devez exécuter la commande comme suit :
```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|Propriété|Plus d’informations|
  |------------|--------------------|
  |**-h**|Affiche les propriétés de ligne de commande pour l’application outil d’habillage.|
  |**-i**|Spécifie le chemin d’accès et le nom de l’application d’entrée.|
  |**+ o**|Spécifie le chemin d’accès dans lequel vous souhaitez enregistrer l’application traitée.|
  |**-p**|Spécifie le chemin d’accès à votre profil de mise en service pour les applications iOS.|
  |**-c**|Spécifie le hachage SHA1 du certificat de signature.|
  |**-v**|Messages détaillées de sortie à la console (facultatif).|
  |-f |Facultatif) <Path to a plist file specifying arguments>  |
  |-b|(Facultatif) Ne spécifiez pas un argument pour cet indicateur si vous voulez que l’application renvoyé à la ligne d’avoir la même version offre que l’application d’entrée (non recommandée). Utilisez «-b <custom bundle version>» si vous souhaitez que l’application renvoyé à la ligne pour avoir une CFBundleVersion personnalisée. Nous vous recommandons d’incrémentation CFBundleVersion de l’application native par le composant moins important, par exemple. 1.0.0 -> 1.0.1 |

>[!IMPORTANT]
>Les indicateurs -f et -b sont uniquement pris en charge dans la version de la version d’évaluation de l’outil d’habillage application prenant en charge MAM sur les périphériques qui ne sont pas inscrit dans Intune.


Une des façons d’exécuter l’outil d’habillage application consiste à placer tous les arguments de commande dans un fichier [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) . Plist est un format de fichier similaire à XML qui nous permettent d’entrée notre arguments de ligne de commande dans une interface clé-valeur.

Ouvrez Parameters.plist, un modèle vierge plist, avec un éditeur de texte ou Xcode.
Entrez votre arguments de chemin d’accès d’entrée, chemin de sortie, mise en service de chemin d’accès de profil, hachage SHA1 du certificat, et activé détaillée.
Pour finir, exécutez la IntuneMAMPackager avec la plist comme argument unique :
```
./IntuneMAMPackager –f Parameters.plist
```

* Après le traitement, le message **a été correctement de sport avec l’application** s’affiche.

    Si une erreur se produit, voir [messages d’erreur](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) de l’aide.

*   L’application encapsulée est enregistrée dans le dossier de sortie que vous avez spécifiée précédemment. Vous pouvez maintenant télécharger l’application dans [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] et l’associer à une stratégie de gestion des applications mobiles.

    > [!IMPORTANT]
    > Vous devez télécharger l’application en tant que nouvelle application. Vous ne pouvez pas mettre à jour une version plus ancienne, non de l’application.

    Vous pouvez désormais déployer l’application à votre [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] groupes et l’application fonctionnent désormais sur le périphérique utilisé par les restrictions d’application que vous spécifiez.

## Messages d’erreur et les fichiers journaux
Utilisez les informations suivantes pour résoudre les problèmes que vous avez avec l’application outil d’habillage.

### Messages d’erreur
Si l’outil d’habillage application ne parvient pas à terminer correctement, un des messages d’erreur suivant s’affiche :

|Message d’erreur|Plus d’informations|
|-----------------|--------------------|
|Vous devez spécifier un iOS valide mise en service de profil.|Votre profil de mise en service ne peut-être pas être valide. Vérifier pour vous assurer que vous disposez des autorisations appropriées pour les appareils et que votre profil est correctement le ciblage du développement ou distribution. Votre profil mise en service peut également être expiré.|
|Spécifiez un nom d’application d’entrée valide.|Vérifiez que le nom de l’application d’entrée spécifié est correct.|
|Spécifier un chemin d’accès valide à l’application de sortie.|Vérifiez que le chemin d’accès à l’application de sortie que vous avez spécifié existe et est correct.|
|Entrer une valeur valide mise en service de profil.|Vérifiez que vous fournissez un nom de profil de mise en service valide et une extension. Votre profil mise à disponibilité peut-être être manquantes droits ou vous n’avez ne peut-être pas inclus l’option de ligne de commande **– p** .|
|L’application d’entrée que vous avez spécifié est introuvable. Spécifiez un nom de l’application d’entrée valide et le chemin d’accès.|Vérifiez que le chemin d’accès de l’application d’entrée existe et est correct. Vérifiez que l’application d’entrée existe à cet emplacement.|
|Impossible de trouver le fichier profil mise en service d’entrée que vous avez spécifié. Spécifiez un fichier de profil de mise en service d’entrée valide.|Assurez-vous que le chemin d’accès au fichier de configuration d’entrée est valide et que le fichier que vous avez spécifié existe.|
|Le dossier d’application de sortie que vous avez spécifié est introuvable. Spécifier un chemin d’accès valide à l’application de sortie.|Vérifiez que le chemin d’accès de sortie que vous avez spécifié existe et est correct.|
|Application de sortie n’a pas d’extension .ipa.|Uniquement les applications avec les extensions **.app** et **.ipa** sont acceptées par l’application outil d’habillage. Vérifiez que votre fichier de sortie a une extension valide.|
|Un certificat de signature non valide a été spécifié. Spécifiez un certificat de signature Apple valide.|Vérifiez que vous avez téléchargé le certificat de signature approprié à partir du portail développeur Apple. Votre certificat peut également être expiré. Si votre profil Apple certificat et mise en service peut être utilisé pour signer correctement une application dans Xcode, ils sont valides pour l’application outil d’habillage.|
|L’application d’entrée que vous avez spécifié n’est pas valide. Spécifier une application valide.|Vérifiez que vous disposez d’une application iOS valide qui a été compilée en tant que fichier .app ou .ipa.|
|L’application d’entrée que vous avez spécifié est chiffrée. Spécifier une application non chiffrée valide.|L’outil d’habillage application ne reconnaît pas les applications chiffrées. Spécifiez une application non chiffrée.|
|L’application d’entrée que vous avez spécifié n’est pas dans un format Position indépendante exécutable (secteur). Spécifiez une application valide au format de graphique en secteurs.|Position exécutable indépendant (secteur) applications peuvent être chargées à une adresse de mémoire vive lorsque exécutez qui peut avoir des avantages de sécurité. Pour plus d’informations, consultez la documentation développeur Apple.|
|L’application d’entrée que vous avez spécifié a déjà été encapsulée. Spécifier une application non valide.|Vous ne pouvez pas traiter une application qui a déjà été traitée par l’outil. Si vous souhaitez traiter à nouveau une application, exécutez l’outil à l’aide de la version d’origine de l’application.|
|L’application d’entrée que vous avez spécifié n’est pas connectée. Spécifiez une application signée valide.|L’outil d’habillage application nécessite des applications à être connecté. Consultez la documentation de développeur pour apprendre à vous connecter à une application renvoyé à la ligne.|
|L’application d’entrée que vous avez spécifié doit être au format .ipa ou .app.|Uniquement les extensions .app et .ipa sont acceptées par l’application outil d’habillage. Vérifiez que votre fichier d’entrée avec une extension valide et a été compilé sous forme de fichier .app ou .ipa.|
|L’application d’entrée que vous avez spécifié a déjà été encapsulée et se trouve sur la dernière version de modèle de stratégie.|L’outil d’habillage application n'est pas renvoyer à la ligne une application existante encapsulée avec la dernière version de modèle de stratégie.|
|Avertissement : Vous n’avez pas spécifié un hachage SHA1 du certificat. Vérifiez que votre application encapsulée est connectée avant de déployer.|Assurez-vous que vous spécifiez un hachage ça valide (à l’aide de la propriété de ligne de commande **– c** ).|

### Fichiers journaux pour l’application outil d’habillage
Applications retours ont été ajoutées à l’aide de l’outil d’habillage application génèrent des journaux qui sont écrits à la console appareil iOS du client. Ces informations sont utiles dans les situations dans lesquelles vous rencontrez des problèmes avec l’application et devez diagnostiquer si le problème est associé à l’application outil d’habillage. Pour récupérer ces informations, procédez comme suit :

1.  Reproduire le problème en exécutant l’application.

2.  Collecter la console de sortie en suivant les instructions d’Apple pour [iOS débogage déployé applications](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3.  Filtrer les journaux enregistrés pour la sortie de Restrictions d’application en entrant le script suivant dans la console :

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Vous pouvez envoyer les journaux filtrées à Microsoft.

    > [!NOTE]
    > Dans le fichier journal, l’élément « build version » représente le numéro de version de Xcode.

    Applications renvoyé à la ligne automatiquement présenter aux utilisateurs également la possibilité d’envoyer les journaux directement à partir de l’appareil par courrier électronique après que l’application se bloque. Les utilisateurs peuvent envoyer le journal d’examiner et transférer à Microsoft si nécessaire.


### Certificat, mise en service de profil et configuration requise pour l’authentification

|Configuration requise|Plus d’informations|
|---------------|-----------|
|Mise en service de profil|**Vérifiez que le profil de mise en service est valide avant de l’inclure** - l’application habillage outil ne vérifie pas si le profil de mise en service a expiré lors du traitement d’une application iOS. Si un profil de mise en service qui a expiré n’est spécifié, l’outil d’habillage application inclura le profil de mise en service qui a expiré, et vous ne connaissez pas qu'un problème est survenu jusqu'à ce que l’application ne parvient pas à installer sur un appareil iOS.|
|Certificat|**Vérifiez que le certificat est valide avant que vous indiquez** - l’outil ne vérifie pas si un certificat a expiré lors du traitement des applications iOS. Si le hachage pour un certificat expiré est fourni, l’outil traitera et vous connecter à l’application, mais elle ne pourra pas installer sur appareils mobiles.<br /><br />**Assurez-vous qu’une correspondance dans le profil de mise à disponibilité du certificat prévu pour la signature de l’application empaquetée** - l’outil ne vérifie pas si le profil de mise en service a une correspondance pour le certificat fourni pour l’application renvoyé à la ligne de signature.|
|Authentification|Un périphérique doit avoir un code confidentiel défini pour le chiffrement pour l’utiliser. Sur les périphériques à laquelle vous avez déployé une application encapsulée, toucher la barre d’état sur le périphérique nécessite que l’utilisateur s’authentifie auprès [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. La stratégie par défaut dans une application encapsulée est *l’authentification sur relancer*. iOS gère toute notification externes (par exemple un appel téléphonique) en tant que quitter l’application et lancer nouveau.<br /><br />Pour les applications renvoyé à la ligne, le premier utilisateur qui se connecte dans n’importe quelle application renvoyé à la ligne de l’éditeur même est mis en cache. Après ce point, seul cet utilisateur est autorisé à accéder à l’application. Pour réinitialiser l’utilisateur, l’appareil doit être unenrolled et puis réinscrits.|


## Définition de droits d’application
Avant d’habillage votre application, vous pouvez accorder des **droits d’accès** pour donner les autorisations des applications supplémentaires et des fonctions qui dépassent une application généralement offertes.  Un **fichier droit** est utilisé lors de code de signature pour spécifier des autorisations spéciales au sein de votre application (par exemple, l’accès à une trousse partagée). Services d’application spécifique, appelés **capacités**, sont activés dans Xcode pendant le développement de l’application. Une fois activée, les fonctionnalités sont répercutées dans votre fichier de droits d’accès. Pour plus d’informations sur les droits d’accès et des fonctions, voir [Ajouter des fonctionnalités](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) dans la bibliothèque de développeur iOS. Pour obtenir une liste complète des fonctionnalités prises en charge, voir [fonctionnalités prises en charge](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### Fonctionnalités prises en charge pour l’outil d’habillage d’application pour iOS

|Fonction|Description|Conseils recommandés|
|--------------|---------------|------------------------|
|Groupes d’application|Groupes d’application permet d’autoriser plusieurs applications à accéder aux conteneurs partagés et autoriser la communication entre les processus supplémentaire entre les applications.<br /><br />Pour activer les groupes de l’application, ouvrez le volet de **fonctionnalités** , puis cliquez sur le commutateur **sur** dans la section **Groupes d’application** . Vous pouvez ajouter des groupes d’application ou sélectionner existants.|Lorsque vous utilisez des groupes d’application, utilisez la notation DNS inverse :<br /><br />*group.com.companyName.AppGroup*|
|Modes d’arrière-plan|Activer les modes d’arrière-plan permet de votre application iOS continuer à exécuter en arrière-plan.||
|Protection des données|Protection des données ajoute un niveau de sécurité aux fichiers stockés sur disque à votre application iOS. Protection des données utilise le matériel de chiffrement intégrés présent sur des appareils spécifiques pour stocker des fichiers dans un format chiffré sur le disque. Votre application doit être configuré pour utiliser la protection des données.||
|Dans l’application achat|Dans l’application achat incorpore un magasin directement dans votre application par qui vous permet de vous connecter à la banque et en toute sécurité traiter les paiements de l’utilisateur. Vous pouvez utiliser dans l’application achat pour collecter le paiement pour les fonctionnalités améliorées ou du contenu supplémentaire utilisable par votre application.||
|Partage de trousse|Activer le partage de trousseau permet à votre application partager les mots de passe dans le trousseau avec d’autres applications de développé par votre équipe.|Lorsque vous utilisez le partage de trousse, utilisez la notation DNS inverse :<br /><br />*com.companyName.KeychainGroup*|
|VPN personnel|Activez VPN personnel permettre à votre application créer et contrôler une configuration VPN système personnalisé à l’aide de l’infrastructure d’Extension de réseau.||
|Notifications de transmission|Service de Notification Push Apple (APNs) permet à une application qui n’est pas exécuté en avant-plan pour avertir l’utilisateur qu’il comporte des informations pour l’utilisateur.|Pour les notifications push pour l’utiliser, vous devez utiliser un profil de mise en service spécifique à l’application.<br /><br />Suivez les étapes décrites dans la [documentation du développeur Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Configuration LAP sans fil|L’activation de la configuration LAP sans fil ajoute l’infrastructure LAP externes à votre projet et permet à votre application configurer accessoires MFi Wi-Fi.||

### Étapes pour activer les droits d’accès

1.  Activer les fonctionnalités dans votre application :

    1.  Dans Xcode, naviguez jusqu'à cible votre application, puis cliquez sur le volet de **fonctionnalités** .

    2.  Activer les fonctionnalités appropriées. Pour obtenir des informations détaillées sur chaque fonctionnalité et comment déterminer les valeurs correctes, voir [Ajouter des fonctionnalités](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) dans la bibliothèque de développeur iOS.

    3.  Notez les ID que vous avez créé au cours du processus.

    4.  Créer et vous connecter votre application à être encapsulé.

2.  Activer les droits d’accès dans votre profil de mise en service :

    1.  Connectez-vous au centre de membre de développement Apple.

    2.  Créer un profil de mise en service pour votre application. Pour obtenir des instructions, voir [comment obtenir les conditions préalables pour l’outil d’habillage d’application Intune pour iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/).

    3.  Dans votre profil mise à disponibilité, activer les mêmes droits que vous avez dans votre application. Vous devrez fournir les mêmes ID que vous avez spécifié lors du développement de votre application.

    4.  Exécuter l’Assistant Mise en service de profil et téléchargez votre fichier.

3.  Assurez-vous que vous avez satisfait à toutes les conditions préalables et puis renvoyer à la ligne l’application.

### Résolution des erreurs courantes avec des droits d’accès
Si l’outil d’habillage application pour iOS affiche une erreur droit, essayez les étapes de dépannage ci-dessous.

|Problème|Cause|Résolution|
|---------|---------|--------------|
|Impossible d’analyser les droits générés à partir de l’application d’entrée.|L’outil d’habillage d’application ne peut pas lire le fichier de droits d’accès qui a été extrait de l’application. Le fichier de droits d’accès peut-être être incorrect.|Vérifiez que le fichier de droits d’accès pour votre application. Pour ce faire, suivez les instructions détaillées ci-dessous. Lors de l’inspection le fichier de droits d’accès, recherchez une syntaxe incorrecte. Le fichier doit être au format XML.|
|Il manque des droits d’accès dans le profil de mise en service (les droits manquantes sont répertoriés). Réorganiser l’application à un profil de mise en service qui comporte ces droits.|Il existe une incompatibilité entre les droits activés dans le profil de mise en service et les fonctionnalités activées dans l’application. Cette incompatibilité s’applique également aux ID associés aux fonctionnalités particuliers (par exemple, groupes d’application, trousseau Access etc.).|En règle générale, vous pouvez créer un nouveau profil de mise en service qui permet des mêmes fonctionnalités que l’application. Lors de l’ID entre le profil et l’application ne correspondre pas, l’outil d’habillage application remplacera les ID s’il s’agit pas. Si vous rencontrez toujours cette erreur après la création d’un nouveau profil de mise en service, vous pouvez essayer de suppression des droits d’accès de l’application en utilisant le paramètre **– e** (voir « utilise le paramètre – e pour supprimer les droits d’une section application ci-dessous).|

### Recherche les droits d’une application signée existants
Passer en revue les droits d’une application signée et la mise en service de profil existants :

1.  Recherchez le fichier .ipa et la modification il s’agit de l’extension par .zip.

2.  Développez le fichier .zip. Vous obtiendrez un dossier de charge utile contenant votre offre .app.

3.  Utilisez l’outil codesign pour vérifier les droits sur le paquet .app comme suit :

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    où `YourApp.app` est le nom de votre offre .app réel.

4.  Utilisez l’outil de sécurité pour vérifier que les droits de l’application incorporé de mise en service de profil :

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    où `YourApp.app` est le nom de votre offre .app réel.

### En utilisant le paramètre – e pour supprimer les droits d’une application
Cette commande supprime les fonctionnalités activées dans l’application qui ne sont pas dans le fichier de droits d’accès. Si vous supprimez des fonctionnalités qui sont utilisées par l’application, il peut interrompre votre application. Est un exemple d’où que vous souhaitiez supprimer fonctionnalités manquantes si vous avez une application produite par un fournisseur qui comporte toutes les fonctionnalités par défaut.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Sécurité et confidentialité pour l’application outil d’habillage
Utilisez les sécurité et confidentialité meilleures pratiques suivantes lorsque vous utilisez l’application outil d’habillage.

-   Le certificat de signature, mise en service de profil et l’application de professionnelles que vous spécifiez doit se trouver sur le même ordinateur Mac que vous utilisez pour exécuter l’application outil d’habillage. Si les fichiers se trouvent sur un chemin UNC, assurez-vous que celles-ci sont accessibles à partir de l’ordinateur Mac. Le chemin d’accès doit être sécurisé via IPsec ou PME de signature.

    L’application encapsulée importées dans le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] console doit se trouver sur le même ordinateur que vous exécutez l’outil sur. Si le fichier se trouve sur un chemin UNC, assurez-vous qu’il est accessible sur l’ordinateur qui exécute la [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] console. Le chemin d’accès doit être sécurisé via IPsec ou PME de signature.

-   L’environnement dans lequel l’outil de retour à la ligne de l’application est téléchargé à partir du site Microsoft Download Center doit être sécurisés via IPsec ou PME de signature.

-   L’application que vous traitez doit provenir d’une source trust-worthy pour garantir la protection contre les attaques.

-   Vérifiez que le dossier de sortie que vous spécifiez dans l’outil d’habillage application est sécurisé, notamment s’il s’agit d’un dossier distant.

-   applications iOS incluant une boîte de dialogue de téléchargement de fichier peuvent aux utilisateurs de contourner couper, copier et coller des restrictions appliquées à l’application. Par exemple, un utilisateur peut utiliser la boîte de dialogue de téléchargement de fichier pour télécharger une capture d’écran des données d’application.

-   Lorsque les utilisateurs surveiller le dossier documents sur leur appareil à partir d’une application encapsulée, ils peuvent voir un dossier nommé **.msftintuneapplauncher**. Si ce dossier est modifié ou supprimé, cela peut affecter le bon fonctionnement des applications à accès restreint.

### Voir aussi
- [Déterminez comment préparer les applications pour la gestion des applications mobiles avec Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Utiliser le Kit de développement pour activer les applications pour la gestion des applications mobiles](use-the-sdk-to-enable-apps-for-mobile-application-management.md)
