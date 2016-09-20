---
title: "Les versions précédentes | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
ms.openlocfilehash: 8d8ef81d5051af5ef8f81e2a8b0c784282a8ade4
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Versions précédentes de Intune
## Août 2016
## Août 2016
## Gestion de l’application
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### Applications masquées et affichées pour iOS 9.3
Pour les périphériques contrôlés exécutant iOS 9,3 ou version ultérieure, vous pouvez utiliser la liste d’applications masqués et affichés dans la stratégie de configuration générale iOS pour :
- Spécifiez une liste des applications qui sont masqués pour les utilisateurs. Les utilisateurs ne peuvent pas afficher ou lancer ces applications.
- Spécifiez une liste des applications que les utilisateurs peuvent afficher et barre de lancement. Aucune autres applications peuvent être affichées ou lancées.

Les applications que vous pouvez spécifier incluent les deux applications que vous avez déployé, et les applications iOS intégrée comme des Messages et des Notes. Pour plus d’informations, voir [paramètres de stratégie iOS dans Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
### Stratégie d’applications autorisés et bloqués pour les appareils Samsung KNOX
Vous pouvez configurer une stratégie personnalisée pour les appareils Samsung KNOX qui vous permet de créer une des opérations suivantes :
- Liste des applications en cours d’exécution sur l’appareil sont bloqués. Même si installé, une application définie dans la liste d’expéditeurs bloqués ne peut pas être activée sur le périphérique.
- Liste des applications que les utilisateurs de l’appareil sont autorisés à installer à partir de Google Play store. Aucune autre application ne peut être installée à partir du magasin.

Ces paramètres peuvent uniquement être utilisés par les périphériques qui s’exécutent KNOX Samsung.
Pour plus d’informations, voir [utiliser des stratégies personnalisées pour autoriser et bloquer des applications pour les appareils Samsung KNOX]( custom-policy-to-allow-and-block-samsung-knox-apps.md).
<!---TFS 1311629 checked --->
### Nouvelles applications compatibles avec les stratégies de gestion des (MAM) application mobile
L’application Yammer pour [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) et [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) est désormais compatible avec les [stratégies de gestion (MAM) Intune application mobile](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), que l’appareil est inscrit ou non.

Pour une liste complète des applications compatibles MAM, voir le site [Microsoft Intune application partenaires](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) .
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Visionneuse Intune applications
Avec la version de la nouvelle RMS le partage d’application, nous sommes suppression les applications Intune visionneuse suivantes, août 2016 à partir de :
- Visionneuse de AV Intune
- Visionneuse PDF Intune
- Visionneuse Intune Image pour Android à partir de Google Play

Au lieu d’utiliser les applications Intune visionneuse, nous recommandons d’utiliser la nouvelle [application Rights Management (RMS partage) pour Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), qui permet de déployer une application au lieu de trois applications distinctes pour afficher les fichiers d’entreprise sur les appareils Android en toute sécurité. Lorsque l’application visionneuse Intune n’est plus pris en charge, il a été supprimé de la banque de Google et ne sera pas disponible pour une utilisation ultérieure.

## Gestion des appareils
### Prise en charge 7.0 Android
Intune prend en charge « jour 0 » pour le système d’exploitation Android 7.0 à venir pour les appareils mobiles.
<!---TFS 1262053--->
### Fonction sur les appareils Android 7.0 de réinitialisation Google suppression du code secret à distance
Google consiste à supprimer la possibilité des administrateurs informatiques et les utilisateurs finaux à distance réinitialiser le code secret des appareils Android 7.0. Auparavant, les administrateurs informatiques peuvent réinitialiser à distance code secret d’un utilisateur et les utilisateurs finaux pu réinitialiser leurs codes secrets à partir du site portail d’entreprise.



## Met à jour de l’application portail d’entreprise
### Site Web du portail d’entreprise
- **Lien de commentaires à partir du portail d’entreprise à Microsoft** <br/>
Le site Web portail d’entreprise permet aux utilisateurs finaux appuyez sur un nouveau lien « Commentaires », en bas de la page, pour envoyer des commentaires à Microsoft sur leur expérience avec le site. Les commentaires collectées et rendues aider Microsoft à améliorer l’expérience de site Web portail d’entreprise pour les utilisateurs.
<!--- TFS 1313657 checked--->

### iOS
- **Version de navigateur gérées iOS minimale mises à jour en 8.0**<br/>
L’application Microsoft Intune gérées navigateur pour iOS a été mis à jour pour prendre en charge des appareils exécutant iOS 8.0 ou version ultérieure. Tandis que les appareils iOS 7.1 peuvent toujours utiliser l’application de navigateur géré existante, encourager vos utilisateurs à mettre à jour sur iOS 8.0 ou version ultérieure pour l’accès et tirer pleinement parti des nouvelles fonctionnalités du navigateur gérées.  
<!---TFS 1313253 checked--->

## Ce qui se passe

### prise en charge iOS 10
Intune gèrera entièrement iOS 10. Plus d’informations suivent la publication iOS 10.

### Groupes Intune transition vers le début de groupes Azure Active Directory dans septembre 2016
Intune consiste à créer une nouvelle expérience de gestion de groupe qui utilise des groupes de sécurité Azure Active Directory (DAS) sous forme de groupes d’utilisateurs et des périphériques dans Intune. Ces groupes seront utilisées pour tous les gestion de groupe, déploiement de stratégie et profil déploiement **lorsque nous introduisez le portail d’administration Intune basée sur Azure nouveau**.

Cette nouvelle expérience sera vous empêcher de devoir dupliquer des groupes entre les services, **vous permettent de qu'accéder à certaines des nouvelles fonctionnalités groupe Azure Active Directory Premium (AADP)**et fournissez extensibilité à l’aide de PowerShell et le graphique. Cela va également unifier l’expérience de gestion de groupe au sein de gestion de mobilité d’entreprise.

Pour activer le déplacement aux groupes de sécurité, l’expérience de la **console d’administration en cours** est soumises à certaines modifications. **Ces modifications et l’utilisation des groupes de sécurité AAD, seront enregistrés dans la documentation Intune**.

Clients qui débutent avec Intune verront **certains les modifications du groupe de sécurité avant de clients en cours**.

En plus des modifications dans Gestion du groupe, **les fonctionnalités suivantes seront être déconseillée**:
- À l’exception des membres ou groupes lors de la création d’un nouveau groupe
- Groupes **Dissociée utilisateurs** et **Dispositifs dissociée**
- **Gérer les groupes** dans le rôle d’administrateur de Service
- Alertes basées sur le groupe personnalisés pour les règles de Notification
- Faire pivoter des groupes dans les rapports
<!--- TFS 1295329--->

### Ajout de « Notifications » pour le portail d’entreprise pour Android
Nous allons libération d’une mise à jour le portail d’entreprise pour Android en septembre qui lancera une nouvelle icône **Notifications** sur la page d’accueil. Pour accéder à la page **Notifications** qui s’affichent à l’utilisateur final tous les éléments qui requièrent votre attention dans l’application portail d’entreprise, tels que l’activation d’inscription appareil non-conformité et mise à jour d’inscription, en cliquant sur cette icône. Si vous utilisez également l’application portail d’entreprise iOS, vous verrez déjà les notifications de rencontrer. Avec l’introduction de la page **Notifications** , vous verrez pas la page **Configuration de l’accès société** chaque fois que vous lancez ou reprenez le portail d’entreprise pour Android dans la mesure où l’appareil est déjà inscrit. Nous entendre bon nombre d'entre vous avez créé des conseils pour l’utilisateur final et vous remercions préavis vos captures d’écran/conseils peut s’avérer nécessaire de mise à jour. Mettez à jour votre documentation pour refléter les changements à venir dans expérience. Rechercher les mises à jour captures d’écran ici : https://aka.ms/androidcpupdate.  

### Améliorations apportées à la manière dont les utilisateurs finaux iOS leurs applications
Les modifications suivantes sont effectuées dans septembre pour les mosaïques des applications dans l’application portail d’entreprise pour iOS renvoyer les utilisateurs vers différents affichages dans un emplacement unique, le site Web portail d’entreprise, pour l’ensemble de leurs applications. Pour l’instant, restrictions Apple interdisent secteur d’activité et application gérée stocker des applications d’être répertoriés dans l’application portail d’entreprise et obliger les utilisateurs à visiter différents affichages pour trouver toutes leurs applications.

- Les **Applications d’entreprise** en mosaïque actuellement pointe vers une liste de toutes les applications sous l’onglet tout du site Web portail d’entreprise, et il continue de fonctionner de la même manière. Le nom de la mosaïque remplacera par **Toutes les applications**.
- Les **Autres applications** vignette actuellement pointe vers un affichage, à l’intérieur de l’application portail d’entreprise, qui répertorie toutes les applications Apple permet à l’application portail d’entreprise à afficher. Le nom de la mosaïque remplacera par **Applications proposées**, puis en cliquant sur la vignette vous permettront d’utilisateurs à l’onglet proposées du site Web portail d’entreprise.
-  La vignette **catégories** actuellement pointe vers une vue, à l’intérieur de l’application portail d’entreprise, qui répertorie les catégories d’applications. Le nom de la mosaïque ne change pas, mais elle pointe maintenant sur l’onglet catégories du site Web portail d’entreprise. Vous pouvez trouver les mises à jour de captures d’écran [ici](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Feuille de route de cloud
Rester informé des progrès à venir pour Intune avec [feuille de route de plateforme en nuage](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Amortissement de service
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Modifications apportées à la prise en charge pour l’application portail d’entreprise iOS**<br/>
En septembre, tous les utilisateurs de l’application portail d’entreprise Intune Microsoft pour iOS doivent utiliser la version la plus récente. Nouveaux utilisateurs ne seront en mesure de télécharger la version la plus récente et utilisateurs actuels doivent mettre à jour vers celui-ci. La dernière version nécessite iOS 8.0 ou version ultérieure, afin que les appareils exécutant d’anciennes versions d’iOS ne puissent pas utiliser le portail d’entreprise ou s’inscrire jusqu'à ce qu’ils mettre à jour leur appareil iOS 8.0 ou version ultérieure et puis mettez à jour l’application portail d’entreprise vers la dernière version. Inscrits appareils exécutant versions inférieures à iOS 8.0 continuent à être gérés et répertoriés dans la Console d’administration Intune.  

- **Version de navigateur gérées iOS minimale mises à jour en 8.0**<br/>
En août, Intune sera lancé une application Microsoft Intune gérées navigateur mis à jour pour iOS qui prend uniquement en charge les appareils exécutant iOS 8.0 ou version ultérieure. Tandis que les appareils iOS 7.1 seront toujours en mesure d’utiliser l’application de navigateur géré existante, veuillez encourager vos utilisateurs pour mettre à jour sur iOS 8.0 ou une version ultérieure pour accéder et tirer pleinement parti des nouvelles fonctionnalités du navigateur gérées.  
<!---TFS 1313253--->

- **Déconseillées des applications de portail d’entreprise pour Windows 8 et Windows Phone 8** <br/>
À partir d’octobre 2016, Microsoft Intune sera déconseiller prise en charge pour les applications Windows 8 et Windows Phone 8 application portail d’entreprise. Microsoft Intune seront déconseiller également de prise en charge de la plateforme Windows Phone 8. Par conséquent, vous ne serez pas en mesure de s’inscrire ou mettre à jour les appareils Windows Phone 8. Vous pouvez continuer à gérer les appareils Windows Phone 8 et Windows 8 qui sont déjà inscrit. Mettre à jour les appareils Windows Phone 8 et Windows 8 pour Windows 8.1 et Windows Phone 8.1 et utiliser les applications Windows 8.1 et Windows Phone 8.1 application portail d’entreprise correspondantes pour continuer à distribuer des applications pour les appareils suivants sans interruptions.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## Juillet 2016
### Gestion de l’application
#### Améliorer l’application mise en service expérience de mise à jour de profil
Apple iOS ligne d’entreprise applications mobiles sont créées avec un profil de mise à disponibilité inclus et code signée avec un certificat. Lorsque l’application s’exécute sur un appareil iOS, iOS confirme l’intégrité de l’application iOS et applique les stratégies définies par le profil de mise en service.

L’entreprise vous permet de vous connecter applications généralement le certificat de signature dure 3 ans. Toutefois, la mise en service profil expire après un an. Cette mise à jour, Intune vous offre les outils fait déployer une nouvelle stratégie mise en service de profil qu’aux appareils dotés des applications qui sont point d’expirer alors que le certificat est toujours valide. Pour plus d’informations, voir [utiliser iOS mobile mise à disponibilité les stratégies de profil à conserver votre ligne d’applications d’entreprise à jour](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
#### Xamarin SDK pour les applications Intune est disponible
Le composant Intune application SDK Xamarin permet d’activer les fonctionnalités de gestion de l’application mobile Intune dans vos mobile iOS et Android applications créées avec Xamarin. Vous pouvez trouver le composant dans le [Xamarin stocker](https://components.xamarin.com/view/Microsoft.Intune.MAM) ou sur la [page Microsoft Intune Github](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### Gestion des appareils
#### Limites de l’inscription appareil accrue
Intune est augmenté la limite d’inscription DISPOSITIF configurable maximale de 5 à 15 périphériques par utilisateur.
<!---TFS 1289896 --->

#### TeamViewer intégration pour Windows PC qui exécutent le logiciel client Intune
L’intégration de [TeamViewer](https://www.teamviewer.com) pour PC Windows qui s’exécutent le client Intune vous permet d’établir des sessions d’assistance à distance avec Windows PC pour effectuer le support des services de support technique pour l’utilisateur final. Cela inclut Windows 7, 8, 8.1 et Windows 10. Pour plus d’informations, voir [tâches de gestion courantes PC Windows avec le client ordinateur Intune Microsoft](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).
<!---TFS 1284856--->

### Met à jour de l’application portail d’entreprise
#### Site Web du portail d’entreprise
- **Expérience utilisateur améliorée lors de l’inscription des appareils Windows**<br/>
Lorsque vous utilisez l’accès conditionnel, les étapes d’inscription pour Windows 8.1 et Windows 10 Mobile Windows 10 bureau ont été clarifier le site Web de portail d’entreprise. Les utilisateurs maintenant verront distincte « inscription d’un appareil » et « Jointure poste de travail » étapes, ce qui facilite leur pour afficher l’état de leur appareil et terminer le processus s’ils rencontrent une défaillance de jointure poste de travail (WPJ). Les différentes étapes sont également présumés pour simplifier le processus de dépannage pour les administrateurs informatiques. Précédemment, lorsque les utilisateurs finaux essayé d’inscription et toutes les étapes de l’inscription a réussi à l’exception des WPJ, le périphérique inscrit n'aurait pas s’affichent dans la liste des périphériques pour les utilisateurs à identifier, entraînant une certaine confusion pour les utilisateurs.

#### Android
- **Application du portail d’entreprise Android**<br/>
Si les utilisateurs finaux Android voir un message d’erreur indiquant que leur appareil il manque un certificat requis, ils peuvent appuyez sur un bouton « Comment résoudre ce problème » pour connaître la [procédure](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) de l’installation du certificat manquant. Si les étapes, mais les utilisateurs voir un « certificat manquant » supplémentaire message d’erreur, ils sont invités à contacter son administrateur informatique et fournir ce [lien](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), qui contient des étapes qui permettent aux administrateurs informatiques à résoudre le problème de certificat.

- **Limiter les installations d’application chargée côté aux périphériques inscrits**<br/>
Les appareils Android peuvent n’est plus installer des applications via le site Web portail d’entreprise, à moins que les périphériques ont été inscrits Intune à l’aide de l’application portail d’entreprise Intune pour Android.
<!---TFS 1299082--->

#### iOS
- **Modifications apportées aux responsables d’inscription d’un appareil comptes dans l’application portail d’entreprise iOS**<br/>
Pour améliorer les performances et échelle, Intune n’affiche plus tous les périphériques responsables d’inscription d’un appareil (DEM) dans le volet **Mes périphériques** de l’application portail d’entreprise iOS. Seul le périphérique local exécute l’application est affiché et uniquement si elle est inscrite via l’application portail d’entreprise.

L’utilisateur DEM peut effectuer des actions sur le périphérique local, mais gestion à distance d’autres appareils inscrits ne peut être effectuée à partir de la console d’administration Intune. En outre, Intune est déconseiller utilisation des comptes DEM avec le programme de l’inscription d’appareil Apple ou l’outil de configuration du Apple. Ces deux méthodes d’inscription support déjà utilisateur moins d’inscription pour les appareils iOS partagé.

Utilisez uniquement des comptes DEM lors de l’inscription d’un utilisateur moins pour les périphériques partagés n’est pas disponible. Pour plus d’informations, voir [périphériques appartenant à l’entreprise inscrire avec le Gestionnaire d’inscription de périphériques dans Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### Modification des noms des fonctionnalités de Windows
- [Microsoft Passport pour Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) est désormais appelé **Windows Hello pour les entreprises**.
- [Protection des données d’entreprise](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) est désormais appelée **Protection des informations Windows**.

## Juin 2016
### Fonctionnement du service Intune
Informations d’état du service pour Intune a été déplacées vers un emplacement central avec d’autres services Microsoft. Désormais, vous trouverez ces informations dans le portail de gestion d’Office 365 sous état du Service. Pour plus d’informations, voir [ce billet de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### Gestion de l’application
- **Configuration de la stratégie améliorée Windows 10 entreprise données rencontrer.** Nous avons apporté améliorations apportées à la configuration de stratégie de protection de données Windows 10 entreprise expérience autour de création de règles d’application, spécifiant la définition des limites de réseau et d’autres paramètres de protection des données enterprise. Pour plus d’informations, voir [créer une stratégie de protection (EDP) de données entreprise à l’aide de Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### Gestion des appareils
- **Windows Defender paramètre de stratégie pour protéger des applications potentiellement indésirables.** Un nouveau paramètre de Windows Defender nommé **Potentiellement indésirables détection des applications** a été ajouté à la stratégie de configuration générale pour Windows 10 Desktop et Mobile. Vous pouvez utiliser ce paramètre pour protéger inscrit Windows ordinateurs de bureau par rapport à l’exécution d’un logiciel classé par Windows Defender comme potentiellement indésirables. Vous pouvez protéger contre ces applications en cours d’exécution, ou utiliser le mode d’audit pour rapport après avoir installé une application potentiellement indésirable. Pour plus d’informations, voir [paramètres de stratégie Windows 10 dans Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune) .
<!---TFS 1244478--->

### Accès conditionnel
- **Stratégie de contrôle access Cisco ISE réseau pour Intune.**  Les clients qui utilisent le 2.1 Cisco identité Service moteur (ISE) et également utilisent Microsoft Intune peuvent définir une stratégie de contrôle d’accès réseau dans ISE.

    À l’aide de cette stratégie, appareils que vous devez vous connecter au réseau à l’aide de Wi-Fi ou VPN doivent respecter la suite de conditions avant qu’ils sont autorisés à accéder :

    * Doit être géré par Intune
    * Doit être compatible avec les stratégies de conformité Intune déployés

 Les utilisateurs finaux de périphériques non conformes est invités à s’inscrire et corriger les éventuels problèmes de conformité pour y accéder.
- **Accès conditionnel navigateur.** Vous pouvez définir une stratégie d’accès conditionnel pour [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) et [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) afin qu’ils n’est accessible à partir de navigateurs web pris en charge sur gérées et la conformité appareils iOS et Android. Les utilisateurs finaux qui tentez de vous connecter à Outlook Web Access (OWA) et SharePoint sites avec des appareils iOS et Android devra inscrire leur appareil avec Intune également sous pour résoudre les problèmes de conformité non avant qu’ils sont habilités à effectuer de se connecter.
<!---TFS 1175844--->

- **Dynamics CRM Online prend en charge accès conditionnel.** Vous pouvez définir une stratégie d’accès conditionnel pour [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) afin qu’il n’est accessible par gérées et la conformité appareils iOS et Android. Les utilisateurs finaux qui tentez de vous connecter à l’application mobile de Dynamics CRM sur iOS et Android devra inscrire avec Intune ainsi que de corriger les éventuels problèmes de conformité non avant de connexion sont habilités à effectuer.
<!---TFS1295358--->

##Mises à jour de l’application portail d’entreprise E

#### Application du portail d’entreprise Android

- Lorsque les administrateurs informatiques appliquent la nouvelle stratégie « Exiger que les périphériques interdire l’installation des applications d’origine inconnue (Android 4.0 +) », les utilisateurs finaux avec Android 4.0 ou générations ultérieures verra s’afficher le message « L’Installation d’origine inconnue doit être désactivée ». Les utilisateurs devront accédez à **paramètres** > **sécurité**et désactivez **inconnue**. Un lien dans le message de conformité permet aux utilisateurs d’obtenir plus d' [informations](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sur le message et pourquoi elles sont requises pour désactiver le paramètre.

- Lorsque les administrateurs informatiques appliquent la nouvelle stratégie « Exiger que les périphériques ont activé l’analyse des applications pour menaces (Android 4.0 +) », les utilisateurs finaux avec Android 4.0 ou générations ultérieures verra s’afficher le message « Analyse périphérique menaces pour la sécurité ». Les utilisateurs devront accédez à **paramètres** > **Google** > **sécurité**et activer **l’Analyse périphérique menaces pour la sécurité**. Un lien dans le message de conformité permet aux utilisateurs d’obtenir plus d' [informations](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sur le message et pourquoi elles sont requises pour activer le paramètre.

- Lorsque les administrateurs informatiques appliquent la nouvelle « exiger que débogage USB est désactivé (Android 4.2 +) « stratégie, les utilisateurs finaux avec 4.2 Android ou générations ultérieures verra s’afficher le message, « débogage USB doit être désactivé. » Les utilisateurs devront accédez à **paramètres** > **options pour les développeurs**et désactivez **débogage USB**. » Un lien dans le message de conformité permet aux utilisateurs d’obtenir plus d' [informations](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sur le message et pourquoi elles sont requises pour désactiver le paramètre.

- Lorsque les administrateurs informatiques appliquent la nouvelle stratégie « sécurité Android Minimum correctif niveau (Android 6.0 +) », les utilisateurs finaux avec 6.0 Android ou générations ultérieures verra s’afficher le message « cet appareil ne respecte pas le niveau de correctifs de sécurité Android minimale. » Les utilisateurs devront installer le correctif de sécurité nécessaires. Un lien dans le message de conformité permet aux utilisateurs d’obtenir des [informations](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sur la façon d’installer le correctif de sécurité requises et pour afficher le correctif de sécurité pour qu’ils ont installé actuellement.

#### application portail d’entreprise iOS

- Lorsque les utilisateurs finaux sont installées métier, ils verront maintenant une installation d’application amélioré rencontrer. Si l’installation de l’application est met beaucoup de temps, les utilisateurs peuvent synchroniser manuellement leur appareil pour forcer le processus de synchronisation à reprendre. Pour consulter les instructions de l’utilisateur final, voir [synchroniser manuellement votre appareil iOS](/Intune/EndUser/sync-your-device-manually-ios).

- L’application portail d’entreprise Intune Microsoft pour iOS a été mis à jour pour prendre en charge iOS 8.0 et versions ultérieures. Cette mise à jour signifie que les utilisateurs finaux peuvent installer l’application portail d’entreprise et inscrire de nouveaux appareils dans Intune uniquement si l’appareil exécute une version iOS 8.0 ou version ultérieure. Les utilisateurs qui ont déjà inscrit appareils qui sont exécutent sur une version non prises en charge d’iOS peuvent continuer à utiliser l’application portail d’entreprise qui se trouve sur leur appareil.


## Mai 2016

Toutes ces fonctionnalités sont également pris en charge pour les déploiements hybrides (Gestionnaire de Configuration avec Intune). Pour plus d’informations sur les nouvelles fonctionnalités hybride, consultez la page [hybride What's New](https://technet.microsoft.com/en-us/library/mt718155.aspx) .

### Documentation
Bienvenue dans la version de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Il s’agit d’une plateforme de contenu entièrement nouvelle, moderne conçue pour le rendre plus facile pour vous, nos clients à comprendre et utiliser Intune.
Pour en savoir plus sur toutes les nouvelles fonctionnalités, voir [Introduction docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Fonctionnement du service Intune
Informations d’état du service pour Intune a été déplacées vers un emplacement central avec d’autres services Microsoft. Désormais, vous trouverez ces informations dans le [portail de gestion d’Office 365](https://portal.office.com/Admin/Default.aspx) , sous **État du Service**.
Pour plus d’informations, voir [ce billet de blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Gestion de l’application
- **MAM SDK : Prise en charge configuration longueur du code confidentiel.** Vous ne pourrez pas spécifier la longueur du code confidentiel pour les applications MAM semblables à un code confidentiel du périphérique. Cette opération requiert aux utilisateurs finaux d’être conformes aux nouvelles restrictions que vous définissez. Ils verront un écran de code confidentiel légèrement modifié pour prendre en compte les plus d’entrée. Pour plus d’informations, voir [paramètres de stratégie MAM pour Android](android-mam-policy-settings.md)et les [paramètres de stratégie MAM pour iOS](ios-mam-policy-settings.md).

- **Skype entreprise pour iOS et Android.** Vous pouvez maintenant cibler Skype entreprise avec [MAM sans les stratégies d’inscription](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md). Une fois que les utilisateurs se connecter, les stratégies MAM seront appliquées.

- **Nouvelles applications disponibles pour la gestion des stratégies de MAM.** Les applications Microsoft Word, Excel et PowerPoint pour Android peuvent désormais être associées à des stratégies MAM sur les périphériques qui ne sont pas inscrits avec Intune. Pour une liste complète des applications pris en charge, accédez à la galerie des applications mobiles Microsoft Intune sur la page [Microsoft Intune application partenaires](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) .


### Met à jour de l’application portail d’entreprise

#### Application du portail d’entreprise Android
- **Les notifications de l’utilisateur final toast**: les utilisateurs voient maintenant toast des notifications de l’application portail d’entreprise Android lorsqu’ils sont s’inscrire leur appareil ou suppression de leurs périphériques à partir du portail d’entreprise.

- **Modifications apportées aux comptes d’appareil d’inscription responsables dans l’application portail d’entreprise Android.** Pour améliorer les performances et échelle, Intune disparaît tous les périphériques responsables d’inscription d’un appareil (DEM) dans le volet mes périphériques de l’application portail d’entreprise Android. Seul le périphérique local exécute l’application est affiché et uniquement si elle est inscrite via l’application portail d’entreprise. L’utilisateur DEM peut effectuer des actions sur le périphérique local, mais gestion à distance d’autres appareils inscrits ne peut être effectuée à partir de la console d’administration Intune.

#### Site Web du portail d’entreprise
- **Site Web du portail société : bannière d’identification appareil fournit davantage d’informations pour les utilisateurs finaux.** Les utilisateurs finaux peuvent à présent plus facilement identifier le périphérique ils sélectionnée lorsqu’ils utilisent le site Web portail d’entreprise. Si le périphérique incorrect est sélectionné, ils seront en mesure de sélectionner le périphérique correct en appuyant sur le lien **Cliquez ici** dans la bannière de page d’accueil.

## Ce qui se passe
- **Intégration de l’interface utilisateur du centre de messages**. Dans le cadre de la migration de Intune au [portail Office 365 gestion](https://portal.office.com/), nous se lance en tirant parti de son centre de messages pour communiquer les nouvelles fonctionnalités et les autres notifications. En outre, en installant l’application mobile du Guide d’administration Office 365, vous pouvez recevoir des notifications sur votre téléphone mobile et facilement transférer des messages à des utilisateurs ou un alias de distribution.
Nous allons commencer à l’aide du centre de messages avec notre mai release afin de vous avertir lorsque des mises à jour sont effectuées et incluent des informations sur les nouvelles fonctionnalités améliorées Intune. Consultez le centre de messages aujourd'hui en vous connectant au [portail Office 365 gestion](https://portal.office.com/) et choix de l’option Centre de messages dans le volet de navigation gauche.

- **Modifications apportées aux comptes responsables d’inscription d’un appareil**. Pour améliorer les performances et échelle, Intune n’est plus affichant **tous les** périphériques responsables d’inscription d’un appareil (DEM) dans le volet **Mes périphériques** de l’application portail d’entreprise iOS. Seul le périphérique local exécute l’application est affiché et uniquement si elle est inscrite via l’application portail d’entreprise. L’utilisateur DEM peut effectuer des actions sur le périphérique local, mais gestion à distance d’autres appareils inscrits ne peut être effectuée à partir de la console d’administration Intune. En outre, Intune est déconseiller utilisation des comptes DEM avec le programme de l’inscription d’appareil Apple ou l’outil de configuration du Apple. Ces deux méthodes d’inscription support déjà utilisateur moins d’inscription pour les appareils iOS partagé. Utilisez uniquement des comptes DEM lors de l’inscription d’un utilisateur moins pour les périphériques partagés n’est pas disponible.

### Feuille de route de cloud
Rester informé des progrès à venir pour Intune avec [feuille de route de plateforme en nuage](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Amortissement de service
- **Visionneuse Intune applications.** Dans la version de la nouvelle RMS le partage d’application, nous sommes suppression les applications Intune visionneuse suivantes, début août 2016 :
    - Visionneuse de AV Intune
    - Visionneuse PDF Intune
    - Visionneuse Intune Image pour Android à partir de Google Play

  Au lieu d’utiliser les applications Intune visionneuse, nous recommandons d’utiliser la nouvelle application de gestion des droits (RMS partage) pour Android, qui permet de déployer une application au lieu de trois applications distinctes pour afficher les fichiers d’entreprise sur les appareils Android en toute sécurité. En savoir plus sur le services RMS le partage d’application (avec lien vers la documentation).

- **Groupe personnalisé ciblage de suppression de règles de Notification.**
Les règles de notification Intune définissent qui sera envoyé à un message d’alerte de Intune. Pour l’instant, vous pouvez configurer des règles de notification pour envoyer des messages électroniques à tous les utilisateurs de périphériques dans un groupe de périphériques Intune que vous avez créé. À partir d’autour 2016 1er juin aller plus loin, ciblage groupes créés par l’utilisateur est n’est plus pris en charge.

    Aujourd'hui, pour cibler une règle de notification à un groupe que vous avez créé à partir de la console d’administration Microsoft Intune, vous devez procéder comme suit :

    Dans l’espace de travail **d’administrateur** , cliquez sur **Règles de Notification** > **Créer une nouvelle règle**

    À l’étape 2 de l’Assistant Création de règle de Notification, sélectionnez les groupes de périphériques dont la règle est cibles. Cette étape, « sélectionnez le périphérique groupes », est supprimé de la Intune Console.

    La barre de planning préliminaire pour que cette modification est la suivante :
    - Dans juin 2016, les nouveaux clients ne voient pas étape 2 de l’Assistant Création de règle de Notification. Clients existant ne sont pas affectés.
    - Autour août 2016, certains clients existantes ne verront pas les groupes » sélectionnez le périphérique » dans l’Assistant.
    - Autour d’octobre 2016, nous espérons que toutes les installations ne verra pas les groupes « sélectionnez le périphérique » dans l’Assistant.


- **Modifications apportées à prendre en charge pour iOS application portail d’entreprise**. Dans les mois à venir, il sera une mise à jour pour l’application portail d’entreprise Intune Microsoft pour iOS qui prend uniquement en charge les appareils exécutant iOS 8.0 ou version ultérieure. Les utilisateurs ne pourront pas s’inscrire nouveaux appareils exécutant versions inférieures à iOS 8.0. Inscrits appareils exécutant versions inférieures à iOS 8.0 continuent à être gérés et, pour une période limitée, seront en mesure de continuer à utiliser l’application portail d’entreprise. Toutefois, les périphériques doivent être sur iOS 8.0 ou version ultérieure pour accéder à la dernière version de l’application portail d’entreprise. Nous vous invitons à informer les utilisateurs à mettre à jour sur iOS 8.0 ou version ultérieure pour tirer pleinement parti des nouvelles fonctionnalités Intune.  


## 2016 d’avril
Toutes ces fonctionnalités sont également pris en charge pour les clients hybride (Gestionnaire de Configuration intégré à Intune).
### Gestion de l’application
- **Mise en conformité MAM utilisateur.**
Vous pouvez à présent afficher l' [état](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) de vos stratégies de gestion des applications pour tous les utilisateurs de votre client Azure Active Directory (DAS). Cela inclut :
   - Appareils mobiles
   - Applications sur l’appareil

   Valeurs d’état :

   **Checked dans**: indique la stratégie a été déployée à l’utilisateur, et application a été utilisée dans le contexte de travail et bien reçu la stratégie.

    **Pas archivé**: indique la stratégie a été déployée à l’utilisateur, mais l’application n’a pas été utilisée dans le contexte de travail depuis.


- **Contrôles MAM pour empêcher la synchronisation des contacts d’Outlook (Android).**
Un nouveau paramètre n’est disponible pour la [Gestion des applications mobiles](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sans inscription d’un appareil. Ce paramètre vous permet d’empêcher une application à partir de la synchronisation des contacts au carnet d’adresses natif sur les appareils Android. Lorsque ce paramètre est activé, applications ciblées sera n’est plus en mesure d’enregistrer des contacts dans le carnet d’adresses natif. Lorsque ce paramètre est désactivé, applications ciblées seront en mesure d’enregistrer des contacts dans le carnet d’adresses natif. Lorsque vous [Effacer à distance un appareil ou une application](wipe-managed-company-app-data-with-Microsoft-Intune.md), les contacts qui ont déjà été enregistrées dans le carnet d’adresses natif seront supprimés. Ce nouveau paramètre est prise en charge initiale par l’application Outlook sur les appareils Android.

### Gestion des appareils
- **Identification de numéros de téléphone pour les périphériques appartenant à l’entreprise.** Téléphones classés comme « Entreprise » sont maintenant identifiés avec son numéro de téléphone complet lorsque, par exemple, vous exécutez un rapport de stock appareil mobile. Numéros de téléphone BYOD continuer à être masquée avec ***, avec les 4 derniers chiffres affichés.


### Mises à jour du portail d’entreprise
**Application du portail d’entreprise Android** Les utilisateurs qui n’ont pas inscrit leur appareil dans Intune et qui n’ont pas le certificat correct installé ne seront pas en mesure de se connecter à l’application portail d’entreprise Android et le message s’affiche, « Vous ne peut pas se connecter, car votre périphérique est manquant un certificat requis. » Le message inclut un lien « Comment résoudre ce problème » qui les utilisateurs peuvent appuyer dessus pour voir les instructions pour installer le certificat. Pour voir les étapes qui suivent les utilisateurs finaux pour résoudre le problème, consultez [votre périphérique est manquant un certificat requis](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**application portail d’entreprise iOS** Prise en charge a été ajouté pour l’action extraire pour actualiser actualiser le contenu de l’écran d’accueil, qui inclut les applications répertoriées, périphériques répertoriés et contact informatique informations. L’action extraire pour actualiser ne vérifie pas la conformité ou les informations de stratégie, qui peuvent être effectuées en sélectionnant la vignette pour votre périphérique actuel et en appuyant sur le bouton **synchroniser** .

**Application Mobile Windows 10 et Windows Phone 8.1 Entreprise Portal** Lorsque les utilisateurs finaux sont installées métier, ils verront maintenant une installation d’application amélioré rencontrer. Si l’installation de l’application est met beaucoup de temps, les utilisateurs peuvent synchroniser manuellement leur appareil pour forcer le processus de synchronisation à reprendre. Pour consulter les instructions de l’utilisateur final, voir [synchroniser votre appareil manuellement pour accélérer les installations d’application](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Site Web du portail d’entreprise** Lorsque les utilisateurs de Windows 10 Mobile et Windows Phone 8.1 sont installées métier, ils seront affiche les nouvelle statuts suivants, qui lui fournissent plus de détails sur l’état de son installation :

* **En attente de synchroniser sur un appareil** – l’utilisateur a cliqué « Installer » et le périphérique maintenant essaie de synchroniser avec l’infrastructure Intune. La synchronisation est requise avant l’installation sont habilités à effectuer. Le message « En attente de synchroniser sur un appareil » est également un lien utilisateurs peuvent appuyer dessus pour voir les [instructions](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sur la façon de synchroniser manuellement leur appareil avec Intune si le processus de synchronisation est met beaucoup de temps ou obtient bloqué.
* **Téléchargement** – demande de téléchargement de l’utilisateur est en cours de traitement et l’appareil est téléchargé et installé l’application.

Avant de ces deux États ont été ajoutées, les utilisateurs avez confondus si une installation d’application a eu beaucoup de temps, car ils unes uniquement un statut de « Installation », qui peut rester dans l’écran pour les heures. Ajout de nouveaux moyens statuts que, au lieu d’appeler le support, les utilisateurs peuvent maintenant appuyez sur « D’attente d’appareil pour synchroniser » créer un lien et suivez les instructions pour forcer le processus de synchronisation à reprendre.


## Mars 2016
### Quelles sont les nouveautés à partir du 29 mars 2016
À l’exception de la mise à jour à la stratégie de configuration générale Windows 10, toutes les fonctionnalités relâché sur 29 mars 2016, sont également pris en charge pour les clients hybride (Gestionnaire de Configuration intégré à Intune). Prise en charge hybride pour la mise à jour de la stratégie de la configuration générale Windows 10 sera bientôt disponible. Veuillez noter que certaines de ces fonctionnalités peuvent nécessiter la dernière version du Gestionnaire de Configuration.

### Gestion de l’application
- **Contrôles MAM pour empêcher la synchronisation des contacts d’Outlook (iOS).** Un nouveau paramètre n’est disponible pour la gestion des applications mobiles sans inscription d’un appareil. Ce paramètre vous permet d’empêcher une application à partir de la synchronisation des contacts au carnet d’adresses natif sur les appareils iOS. Lorsque ce paramètre est activé, l’application ne seront plus en mesure d’enregistrer des contacts dans le carnet d’adresses natif. Lorsque ce paramètre est désactivé, l’application sera en mesure d’enregistrer des contacts dans le carnet d’adresses natif. Réinitialisation sélective d’un appareil, tous les contacts qui ont déjà été enregistrées dans le carnet d’adresses native sont été supprimés. Ce nouveau paramètre est pris en charge par l’application Outlook sur les appareils iOS. Pour plus d’informations sur cette modification et d’autres paramètres, voir [créer et déployer des stratégies MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Contrôle d’accès
- **Skype entreprise Online prend en charge l’accès conditionnel.** Vous pouvez définir une stratégie d’accès conditionnel pour Skype entreprise Online afin qu’il n’est accessible par gérées et la conformité appareils iOS et Android. Les utilisateurs finaux qui tentez de vous connecter à la Skype entreprise App mobile sur iOS et Android devra inscrire avec Intune ainsi que pour résoudre les problèmes de conformité non avant de connexion sont habilités à effectuer. Pour plus d’informations, voir [gérer l’accès à Skype entreprise Online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Gestion des appareils
- **Prise en charge Intune pour iOS 9.3.** Lundi mars 21, Apple annoncé la disponibilité d’iOS 9.3. Nous avons utilisation pour vous assurer que Microsoft Intune est compatible avec la version la plus récente d’Apple mobile système d’exploitation, [nous sommes heureux d’annoncer que Intune prend en charge la gestion des appareils iOS 9.3](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)occupé (e).

  Toutes les fonctionnalités Intune existantes actuellement disponibles pour la gestion des appareils iOS continueront à fonctionner en toute transparence comme utilisateurs migrer leurs appareils iOS 9.3. En outre, iOS 9.3 est également prise en charge aujourd'hui pour les clients hybride (Gestionnaire de Configuration intégré à Intune).

- **La stratégie de configuration générale Windows 10 contient maintenant des paramètres pour gérer Windows Defender sur inscrits Windows 10 PC.** Pour plus d’informations, voir [paramètres de stratégie de configuration de Windows 10 dans Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Portail d’entreprise

- **Packages d’application Windows disponibles directement depuis le site du portail d’entreprise.** Utilisateurs de Windows 8, Windows 8.1 et Windows RT PC peuvent désormais installer des packages d’application Windows (avec l’extension .aspx) directement depuis le site du portail d’entreprise. Auparavant, vous deviez déployer, ou les utilisateurs devaient installer l’application portail d’entreprise sur les périphériques d’installation des applications.

- **Les utilisateurs peuvent verrouiller à distance leur appareil à partir du site portail d’entreprise.** Une nouvelle option à distance verrouillage a été ajoutée au site Web portail d’entreprise pour permettre aux utilisateurs de verrouiller à distance leur appareil à partir du portail si leur appareil perte ou de vol. Consultez les [instructions de l’utilisateur final](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). Le tableau suivant répertorie la plateforme prise en charge pour verrouiller à distance Intune Standalone et Intune avec le Gestionnaire de Configuration.

|Plateforme | Détails de la prise en charge|
|---------|----------------|
|Android |Prise en charge|
|iOS |Prise en charge|
|Windows 10 Mobile |Prise en charge uniquement si le téléphone est défini pour un code secret|
|Bureau Windows 10 |Non pris en charge|
|Windows Phone 8.1 |Prise en charge uniquement si le téléphone est défini pour un code secret|
|Windows Phone 8.0 |Non pris en charge|
|PC (Windows 8.0 et versions ultérieures) |Non pris en charge|
|PC (Windows 8.1) |Non pris en charge|

### Quelles sont les nouveautés à compter du 10 mars 2016

### Gestion de l’application

- **Tirer parti des iOS « ouvrir dans » gestion pour appareils mobiles qui sont inscrits dans une solution de la gestion des périphériques tiers** Vous pouvez utiliser votre fournisseur de gestion des (périphériques mobiles) appareil mobile tiers pour tirer parti des iOS « Ouvrir dans » gestion. Vous pouvez définir les restrictions de la configuration des paramètres de profil et déployer l’application à l’aide de [gérer le transfert de données entre les applications iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

     Cette approche présente deux principaux avantages :

     1. Les utilisateurs doivent se connecter avec leur propre compte travail avant qu’ils accéder à toutes les données d’entreprise à partir de Services en nuage ou d’autres applications. Cela garantit que les stratégies de gestion des (MAM) de l’application mobile sont en place lorsque les données sont accessibles.

     2. Les profils de messagerie gérées et d’autres applications gérées déployées au moyen d’une solution de la gestion des périphériques tiers peuvent partager des fichiers et des données à partir des applications ayant des stratégies Intune MAM.

- **Gérer l’application Microsoft Outlook avec des stratégies de MAM pour appareils ne pas inscrits dans Intune** Vous pouvez désormais gérer l’application Microsoft Outlook sur les périphériques qui ne sont pas inscrits dans Intune avec la stratégie de gestion des applications mobiles Intune. L’application Microsoft Outlook mis à jour avec les fonctionnalités MAM est disponible pour [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) et les appareils [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook) . Utilisez les instructions dans la [créer et déployer des stratégies de gestion de l’application mobile](https://technet.microsoft.com/library/mt627829.aspx) rubrique pour créer une stratégie MAM.  


- **Stratégies de configuration de l’application mobile vous offrent davantage de flexibilité pour spécifier les détails de l’utilisateur pour les applications iOS** Vous pouvez fournir des paramètres utilisateur une application iOS devrez lorsqu’il est ouvert. Par exemple, vous pouvez fournir un port réseau ou un nom d’utilisateur. Pour plus d’informations, voir [Configuration des applications iOS avec les stratégies de configuration de l’application mobile dans Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Déploiement d’Adobe Reader pour Microsoft Intune sur les appareils iOS gérées Intune de votre entreprise** L’application Adobe Reader pour iOS peut désormais être gérée sur les appareils inscrits avec la stratégie de gestion des applications mobiles Intune.

- **Vérifiez que déployée web clips sont ouverts dans le navigateur géré** Vous pouvez déployer les clips web ciblées qui peuvent uniquement être ouvert à l’aide du navigateur géré sur les appareils iOS et Android. Par exemple, vous déployez des liens vers des ressources d’entreprise via le portail d’entreprise, et lorsque les utilisateurs accèdent aux liens, qu’ils s’ouvrent directement dans le navigateur géré où ils peuvent être protégées par la stratégie MAM. Pour plus d’informations, voir [déployer des applications ](deploy-apps.md).


- **Rechercher, gérer et distribuer du Windows Store pour les applications d’entreprise pour les appareils Windows 10 à partir de la console administrateur Intune** Prise en charge pour Windows Store pour les entreprises est disponible dans Intune pour vous aider à rechercher, gérer et distribuer des applications pour les appareils Windows 10 que vous gérez. Windows Store pour les entreprises vous permet de gérer le processus de déploiement et de surveillance ces applications à partir de la console administrateur Intune — la même console vous permet de gérer vos autres applications. Plus précisément, du Windows Store pour les entreprises gère le contenu et de licence de « applications sous licence en ligne ». Pour plus d’informations, voir [Gérer les applications que vous avez acheté auprès du Windows Store pour les entreprises](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Gestion des appareils
- **Distribution de certificats PFX pour les appareils iOS** Administrateurs Intune peuvent créer et déployer des certificats PFX iOS pour Wi-Fi, du courrier et l’authentification VPN sur les appareils iOS. Cette fonctionnalité est déjà disponible pour les appareils Android et Windows 10. Pour plus d’informations, voir [Activer l’accès aux ressources d’entreprise à l’aide des profils de certificat ](secure-resource-access-with-certificate-profiles.md).


- **Applications appliquer et les stratégies à des groupes de périphérique différent en fonction de la sélection d’une catégorie utilisateur** Les administrateurs Intune peuvent maintenant définir des catégories de périphériques personnalisés pour les utilisateurs sélectionnent dans lors de l’inscription. Par exemple, les administrateurs peuvent souhaitent que leurs utilisateurs spécifier si ils vous inscrire un périphérique utilisé pour la « Caisse » ou « Remise chariot » ou de « Stock salle ». La catégorie sélectionnée entraînera le périphérique pour devenir membre d’un groupe d’appareil Intune, qui peut être utilisé pour le déploiement des applications différentes et les stratégies à l’appareil inscrit. Pour plus d’informations, voir [appareils classer avec le mappage de groupe appareil](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Modifications et mises à jour de Microsoft application portail d’entreprise
Les modifications suivantes ont été apportées à l’application portail d’entreprise dans cette version.

**Application du portail d’entreprise Android**

* Lorsque vos utilisateurs lancement une application qui est gérée par la gestion des applications mobiles (MAM), ils verront un message pour les informer que l’application est gérée par leur société. Les utilisateurs peuvent maintenant appuyez sur un lien « En savoir plus » pour obtenir [plus d’informations](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) ici sur ce que signifie « gérées applications ». Ils peuvent également appuyez sur « Ne plus afficher » afin que le message n’apparaît plus au lancement de l’application.
* Nouveaux écrans ont été ajoutés pour les utilisateurs à travers le processus d’inscription et fournissent plus d’informations sur la raison pour laquelle les utilisateurs doivent s’inscrire et ce que les administrateurs informatiques peuvent et ne peuvent pas voir sur leurs appareils inscrits. Consultez les [instructions d’inscription](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) pour plus d’informations.
* Messages d’erreur d’inscription sont désormais affichés dans l’application portail d’entreprise. Ces messages apparaissaient précédemment, le site Web de portail d’entreprise. Faire cela signifie modifier que tous les messages d’erreur apparaissent désormais dans un seul endroit au lieu de deux emplacements différents.


**application portail d’entreprise iOS**
* Lorsque vos utilisateurs lancement une application qui est gérée par la gestion des applications mobiles (MAM), ils verront un message pour les informer que l’application est gérée par leur société. Les utilisateurs peuvent maintenant appuyez sur un lien « En savoir plus » pour obtenir [plus d’informations](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) ici sur ce que signifie « gérées applications ». Ils peuvent également appuyez sur « Ne plus afficher » afin que le message n’apparaît plus au lancement de l’application.
* Nouveaux écrans ont été ajoutés pour les utilisateurs à travers le processus d’inscription et fournissent plus d’informations sur la raison pour laquelle les utilisateurs doivent s’inscrire et ce que les administrateurs informatiques peuvent et ne peuvent pas voir sur leurs appareils inscrits. Consultez les [instructions d’inscription](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) pour plus d’informations.
* Messages d’erreur d’inscription sont désormais affichés dans l’application portail d’entreprise. Ces messages apparaissaient précédemment, le site Web de portail d’entreprise. Faire cela signifie modifier que tous les messages d’erreur apparaissent désormais dans un seul endroit au lieu de deux emplacements différents.




## Février 2016
### Modifications et mises à jour de Microsoft application portail d’entreprise

Les modifications suivantes ont été apportées à l’application portail d’entreprise dans cette version.

#### Application du portail d’entreprise Android
- Nouveaux écrans ont été ajoutés pour les utilisateurs à travers le processus d’inscription et fournissent plus d’informations sur la raison pour laquelle les utilisateurs doivent s’inscrire et ce que les administrateurs informatiques peuvent et ne peuvent pas voir sur leurs appareils inscrits. Consultez les [instructions d’inscription](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) pour plus d’informations.
- Messages d’erreur d’inscription sont désormais affichés dans l’application portail d’entreprise. Ces messages apparaissaient précédemment, le site Web de portail d’entreprise. Faire cela signifie modifier que tous les messages d’erreur apparaissent désormais dans un seul endroit au lieu de deux emplacements différents.

#### application portail d’entreprise iOS
 - Nouveaux écrans ont été ajoutés pour les utilisateurs à travers le processus d’inscription et fournissent plus d’informations sur la raison pour laquelle les utilisateurs doivent s’inscrire et ce que les administrateurs informatiques peuvent et ne peuvent pas voir sur leurs appareils inscrits. Consultez les [instructions d’inscription](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) pour plus d’informations.

 - Messages d’erreur d’inscription sont désormais affichés dans l’application portail d’entreprise. Ces messages apparaissaient précédemment, le site Web de portail d’entreprise. Faire cela signifie modifier que tous les messages d’erreur apparaissent désormais dans un seul endroit au lieu de deux emplacements différents.


## Janvier 2016

### Tirer parti des fonctionnalités de Windows 10
* **Conditionnel accéder avec le Service de Attestation d’intégrité** Les administrateurs Intune peuvent à présent afficher l’état de Windows 10 appareil santé Attestation dans la console Intune Admin. Attestation d’intégrité de périphérique permet à l’administrateur de vous assurer que le client ordinateurs disposez BIOS digne de confiance, module et démarrer des configurations logicielles. Pour prendre en charge attestation d’intégrité du périphérique, les périphériques client doivent exécuter Windows 10 avec 2 plateforme sécurisée activé. Attestation de santé appareil affiche le nombre d’unités activées pour chacune des opérations suivantes :
    * Menu de lancement au plus tôt contre les logiciels malveillants
    * BitLocker
    * Démarrage sécurisé
    * Intégrité du code

    Lecture [Introduction aux stratégies de conformité appareil pour Intune Microsoft](introduction-to-device-compliance-policies-in-microsoft-intune.md) pour plus d’informations sur le paramètre d’intégrité d’appareil, collectées points de données et le rapport d’intégrité des attestation. Les [Détails du service HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) explique le service en détail.

* **Windows 10 Passport pour consigne de travail et la gestion des certificats** Avec Intune, vous pouvez [intégrer Microsoft Passport pour le travail](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), ce qui correspond à une autre méthode de connexion pour Windows 10 qui utilise un compte Azure Active Directory ou Active Directory pour remplacer un mot de passe, une carte à puce ou une carte à puce virtuelle. Passport vous permet d’utiliser un mouvement utilisateur pour se connecter à la place d’un mot de passe. Un mouvement utilisateur peut être un simple code confidentiel, une authentification biométrique tels que Windows Hello ou un appareil externe tel qu’un lecteur d’empreinte.

* **VPN pour les applications spécifiques** Vous pouvez sélectionner les applications qui se connectent automatiquement à votre réseau d’entreprise sur réseau privé virtuel. Créer la liste des applications lorsque vous configurez le profil VPN, comme décrit dans l’aide les utilisateurs se connectent à leurs tâches à l’aide des profils VPN avec Microsoft Intune.

* **Prise en charge de réinitialisation complète Windows 10** Vous pouvez maintenant émettre une réinitialisation à distance complète de Windows 10 équipements de bureau inscrit dans Intune via la console d’administration Intune. Réinitialisation complète Windows 10 effectue une réinitialisation usine du périphérique.


### Mise à jour Apple Volume achat programme (VPP)
Intune peut maintenant aider à [Gérer les applications que vous avez acheté via Apple Volume achat programme (VPP) pour les entreprises](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Cela inclut la synchronisation des informations de licence entre Apple et Intune et le suivi du nombre de copies de chaque application que vous avez déployé.

### Utiliser des numéros IMEI pour identifier les périphériques appartenant à l’entreprise
Vous pouvez désormais [Importer les numéros d’identité (IMEI) international équipement mobile](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) pour les plateformes d’appareil mobile qui ont un numéro IMEI pour aider à identifier les appareils mobiles appartenant à l’entreprise. Une fois inscrit à Intune, appareils avec numéros IMEI importées sont marqués comme société, qui peut être utilisée pour appliquer des stratégies sont différentes de celles qui sont appliquées aux périphériques personnellement propriétaire.

### Plus d’applications sont désormais compatibles avec les stratégies Intune MAM
Autres applications à partir de partenaires Microsoft sont désormais compatibles avec les stratégies de gestion (MAM) Intune application mobile (pour les périphériques gérés par Intune) :
* Zone EMM (à partir de zone Inc) – iOS uniquement
* Adobe Reader (à partir d’Adobe) – Android uniquement
* Foxit PDF Reader (de Foxit Corporation) – iOS et Android


### Prise en charge IE9 se terminant par janvier
Février 2016, à partir d’Internet Explorer 9 est n’est plus pris en charge comme un navigateur pour accéder à le site Web du portail Microsoft Intune société, le portail de compte Intune et la console d’administration Intune officiel. Vous devrez migrer vers Internet Explorer 10 ou version ultérieure.


>[!div class="step-by-step"]

>[&larr; **Quelles sont les nouveautés dans Intune**](whats-new-in-microsoft-intune.md)    
