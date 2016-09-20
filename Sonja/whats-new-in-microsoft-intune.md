---
title: "Quelles sont les nouveautés | Microsoft Intune"
description: "Découvrez les possibilités nouveauté de ce mois, et passé versions de Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
ms.openlocfilehash: 1d09e5a0adb3ecfa8f2d64f668ea7ff16bdf31fa
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Quelles sont les nouveautés dans Microsoft Intune--septembre
Découvrez quelles sont les nouveautés de cette version de Microsoft Intune. Vous pouvez également Découvrez les prochains changements que vous devez être prévue pour, ainsi que des informations sur les versions précédentes.

Toutes ces fonctionnalités seront finalement prise en charge pour les déploiements clients hybride (Gestionnaire de Configuration avec Intune). Pour plus d’informations sur les nouvelles fonctionnalités hybride, consultez notre [hybride page Nouveautés](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT]
>Billet de blog - s’assurer que les appareils mobiles sont à jour à l’aide de Microsoft Intune<br>
>Lumière les attaques de programmes malveillants « Trident » récentes sur les appareils iOS, nous avons publié un nouveau billet de blog, [garantir les appareils mobiles sont à jour à l’aide de Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) pour vous aider à en savoir plus sur les différentes façons Intune peut vous aider à protéger vos périphériques et à jour.

## prise en charge iOS 10
Scénarios existantes Intune MDM et MAM sont compatibles avec iOS 10. Pour obtenir des conseils, consultez le [Blog de l’équipe Intune prise en charge](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

## Outil d’habillage application prend en charge MAM sans inscription d’un appareil pour Android et iOS
L’outil d’habillage de l’application Intune est un outil de ligne de commande permet d’activer Intune MAM dans des applications de ligne-de-métier pour iOS et Android. Il est plus simple d’incorporer le Kit de développement MAM Intune dans votre application, afin que votre application peut appliquer des stratégies MAM déployées via Intune. À l’aide de stratégies MAM, vous pouvez :

1. Chiffrer les données de l’application.
2. Demander l’information à entrer un code confidentiel lors de l’exécution de l’application.
3. Autoriser l’application transférer des données uniquement aux autres applications gérées.
4. Empêcher l’application de sauvegarde des données sur Android, iTunes et iCloud.
5. Autoriser uniquement les commandes Couper, copier et coller dans et se déconnecter d’autres applications gérées.

La version d’évaluation de l’outil mis à jour Intune application habillage prend désormais en charge MAM sans inscription d’un appareil dans des applications métier internes sur iOS et Android. Cela signifie que vos utilisateurs finaux n’êtes pas obligé d’inscrire leur appareil avec Intune d’utiliser des applications métier activé MAM.

Tout le monde peut tester le logiciel de version d’évaluation et lisez la documentation utile, située dans GitHub de msintuneappsdk :

http://www.github.com/msintuneappsdk/Intune-App-wrapper-IOS-Preview

http://www.github.com/msintuneappsdk/Intune-App-wrapper-Android-Preview

Avant d’installer et utiliser Microsoft Intune application Wrapper pour Android et iOS préliminaires vous devez :

* Passez en revue termes du contrat de licence Microsoft pour Microsoft Intune application habillage outil pour Android et iOS en version précommerciale
* Imprimer et conserver une copie des termes de licence pour vos enregistrements. En téléchargeant et en utilisant l’outil d’habillage Microsoft Intune application pour Android précommercial vous acceptez ces termes du contrat de licence. Si vous n’acceptez pas les, n’utilisez pas le logiciel.
<!---TFS 1235607--->

## Groupes Intune commencent à effectuer la migration vers Azure Active Directory de septembre
Quelques nouveaux comptes Intune utilisera les groupes de sécurité Azure Active Directory plutôt que des groupes d’utilisateurs Intune. Vous savez que vous travaillez avec des groupes de sécurité, comme la page groupes de portails Intune aura un lien vous diriger vers le portail de gestion Azure.

## Intégration affût pour protéger les appareils Android
Microsoft est intégration avec la solution de protection d’affût menace mobile pour protéger des appareils mobiles Android par la détection des logiciels malveillants, applications risquées et plus d’informations, sur les appareils. Solution d’affût vous permet de déterminer le niveau de menace, qui peut être configuré. Vous pouvez créer une règle de stratégie de conformité dans Intune pour déterminer la conformité appareil en fonction de l’évaluation des risques à l’affût. À l’aide de stratégies d’accès conditionnelle, vous pouvez autoriser ou bloquer l’accès aux ressources de l’entreprise en fonction de l’état de conformité appareil.

Les utilisateurs finaux de périphériques non conformes est invités à s’inscrire et doivent installer l’affût de travail de votre application sur les appareils Android, activer l’application, puis convertir menaces signalées dans l’affût de travail de votre application accéder. Pour plus d’informations, voir [restreindre l’accès basé sur appareil, réseau et risque d’application](restrict-access-based-on-device-network-app-risk.md).


## Met à jour de l’application portail d’entreprise

### Android

**Ajout de « Notifications » pour le portail d’entreprise pour Android**<br/>
Une nouvelle icône Notifications a été ajoutée à l’application portail d’entreprise pour Android sur la page d’accueil. En cliquant sur cette icône accède à la page Notifications, qui affiche vos utilisateurs finaux tous les éléments qui requièrent votre attention dans l’application portail d’entreprise, tels que l’activation d’inscription non-conformité appareil et mise à jour d’inscription. L’application portail d’entreprise iOS a déjà cette expérience des notifications. La nouvelle page signifie Notifications cet utilisateur ne reportez-vous à la page Configuration de l’accès société chaque fois qu’ils lancement ou reprendre le portail d’entreprise dans la mesure où l’appareil est déjà inscrit. Si vous créez vos propres recommandations pour l’utilisateur final, vous souhaiterez peut-être mettre à jour votre documentation afin de refléter ce changement. Rechercher les mises à jour de captures d’écran [ici](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->


### iOS
**Modifications apportées à la prise en charge pour l’application portail d’entreprise iOS**<br/>
Tous les utilisateurs de l’application portail d’entreprise Intune Microsoft pour iOS doivent désormais utiliser la version la plus récente. Nouveaux utilisateurs sont peut télécharger uniquement la dernière version, et les utilisateurs actuels sont requises pour mettre à jour vers celui-ci. La dernière version nécessite iOS 8.0 ou version ultérieure, appareils exécutant d’anciennes versions d’iOS ne pouvez pas utiliser le portail d’entreprise ou s’inscrire jusqu'à ce qu’ils mettre à jour leur appareil iOS 8.0 ou version ultérieure et puis mettez à jour l’application portail d’entreprise vers la dernière version. Appareils inscrits exécutant versions inférieures à iOS 8.0 continuent à être gérés et répertoriés dans la Console d’administration Intune.
<!---TFS 1283165--->

**Améliorations apportées à la manière dont les utilisateurs finaux iOS leurs applications**<br/>
Les modifications suivantes ont été apportées aux mosaïques des applications dans l’application portail d’entreprise pour iOS renvoyer les utilisateurs vers différents affichages dans un emplacement unique, le site Web portail d’entreprise, pour l’ensemble de leurs applications. Restrictions Apple interdisent secteur d’activité et application gérée stocker des applications d’être répertoriés dans l’application portail d’entreprise et obliger les utilisateurs à visiter différents affichages pour trouver toutes leurs applications.

- La vignette **d’Applications d’entreprise** précédemment redirigé vers une liste de toutes les applications sous l’onglet tout du site Web portail d’entreprise, et il continue de fonctionner de la même manière. Le nom de la mosaïque a changé à **Toutes les applications**.
- La vignette **d’Autres applications** précédemment vers laquelle pointe un affichage, à l’intérieur de l’application portail d’entreprise, qui répertorie toutes les applications Apple permet à l’application portail d’entreprise à afficher. Le nom de la mosaïque a changé pour **Applications proposées**, puis en cliquant sur la vignette vous permettront d’utilisateurs à l’onglet proposées du site Web portail d’entreprise.
-  La vignette **catégories** précédemment vers laquelle pointe un affichage, à l’intérieur de l’application portail d’entreprise, qui répertorie les catégories d’applications. Le nom de la mosaïque n’a pas changé, mais elle pointe désormais sur l’onglet catégories du site Web portail d’entreprise.
Vous pouvez trouver les mises à jour de captures d’écran [ici](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

**Inviter à installer l’application de navigateur gérées iOS si professionnels de l’informatique définit cette configuration minimale requise pour une application**<br/>
Si vous avez configuré un clip web à ouvrir uniquement dans le navigateur géré, et le navigateur géré n’est pas installé sur un appareil, l’application portail d’entreprise sur l’appareil invitera l’utilisateur pour installer le navigateur géré avant de pouvoir installer le clip du web. 
<!---TFS 1228570--->

### Windows
**Bouton Commentaires ajouté à l’application portail d’entreprise Windows Phone 8.1**<br/>
L’application portail d’entreprise Windows Phone 8.1 permet aux utilisateurs finaux envoyer des commentaires sur l’application à l’aide d’un nouveau bouton « Envoyer des commentaires ». Pour trouver le bouton, les utilisateurs appuyez sur le menu « points de suspension » en bas à droite de l’écran de l’application portail d’entreprise, puis sur **Envoyer des commentaires**. Les commentaires collectées et rendues aider Microsoft à améliorer l’expérience de l’application portail d’entreprise pour les utilisateurs.
<!---TFS 1317806--->


## Ce qui se passe

### Groupes Intune transition vers groupes Azure Active Directory
Intune consiste à créer une nouvelle expérience de gestion de groupe qui utilise des groupes de sécurité Azure Active Directory (DAS) sous forme de groupes d’utilisateurs et des périphériques dans Intune. Ces groupes seront utilisées pour tous les gestion de groupe, déploiement de stratégie et profil déploiement **lorsque nous introduisez le portail d’administration Intune basée sur Azure nouveau**.

Cette nouvelle expérience sera vous empêcher de devoir dupliquer des groupes entre les services, **vous permettent de qu'accéder à certaines des nouvelles fonctionnalités groupe Azure Active Directory Premium (AADP)**et fournissez extensibilité à l’aide de PowerShell et le graphique. Cela va également unifier l’expérience de gestion de groupe au sein de gestion de mobilité d’entreprise.

Pour activer le déplacement aux groupes de sécurité, l’expérience de la **console d’administration actuelle** est soumises à certaines modifications. **Ces modifications et l’utilisation des groupes de sécurité AAD, seront enregistrés dans la documentation de Intune**.

Clients qui débutent avec Intune verront **certains les modifications du groupe de sécurité avant de clients en cours**.

En plus des modifications dans Gestion du groupe, **les fonctionnalités suivantes seront être déconseillée**:
- À l’exception des membres ou groupes lors de la création d’un nouveau groupe
- Groupes **Dissociée utilisateurs** et **Dispositifs dissociée**
- **Gérer les groupes** dans le rôle d’administrateur de Service
- Alertes basées sur le groupe personnalisés pour les règles de Notification
- Faire pivoter des groupes dans les rapports
<!--- TFS 1295329--->

### Nouvelles stratégies d’application Access conditionnelle pour Exchange Online et SharePoint Online
Vous ne pourrez pas limiter l’accès à Exchange Online et SharePoint Online afin qu’access peuvent provenir uniquement à partir des applications Office mobile tels que Outlook, Word, Excel et OneDrive. Cette nouvelle fonctionnalité paires parfaitement avec les stratégies de gestion (MAM) Intune application mobile que vous pouvez bloquer l’accès aux clients de messagerie intégrée ou d’autres applications qui n’ont pas été configurées avec les stratégies Intune MAM. Ainsi, que vos utilisateurs sont l’accès aux données de votre organisation avec les applications qui peuvent être protégées à l’aide de Intune MAM. Vous pouvez commencer dans la gestion de l’application mobile Intune via le portail Azure. Recherchez la section accès conditionnelle nouvelle dans la carte de « Paramètres ».



### Amortissement de service

- **Déconseillées des applications de portail d’entreprise pour Windows 8 et Windows Phone 8** <br/>
À partir d’octobre 2016, Microsoft Intune sera déconseiller prise en charge pour les applications Windows 8 et Windows Phone 8 application portail d’entreprise. Microsoft Intune sera déconseiller également de prise en charge de la plateforme Windows Phone 8. Par conséquent, vous ne serez pas en mesure de s’inscrire ou mettre à jour les appareils Windows Phone 8. Vous pouvez continuer à gérer les appareils Windows Phone 8 et Windows 8 qui sont déjà inscrit. Mettre à jour les appareils Windows Phone 8 et Windows 8 pour Windows 8.1 et Windows Phone 8.1 et utiliser les applications Windows 8.1 et Windows Phone 8.1 application portail d’entreprise correspondantes pour continuer à distribuer des applications pour les appareils suivants sans interruptions.



### Feuille de route de cloud
Rester informé des progrès à venir pour Intune avec [feuille de route de plateforme en nuage](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).


## Versions précédentes de Intune
Si vous voulez voir qu’est publié dans Intune pendant les six mois derniers, elles sont répertoriées dans l’article [précédent Intune libère](previous-intune-releases.md) .

### Voir aussi
* [Microsoft Intune Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Feuille de route de plateforme cloud](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
