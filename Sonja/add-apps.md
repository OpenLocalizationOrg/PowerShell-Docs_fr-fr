---
title: Ajouter des applications | Microsoft Intune
description: "Avant de commencer le déploiement des applications avec Intune, prenez quelques instants pour vous familiariser avec les concepts présentés dans cette rubrique."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: 93c05ecd0154bb637f421dcc5d7ee56ff8d3ab2d
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Ajouter des applications avec Microsoft Intune
Avant de commencer le déploiement des applications avec Microsoft Intune, prenez quelques instants pour vous familiariser avec les concepts présentés dans cette rubrique. Ces concepts vous aidera à comprendre quelles applications vous pouvez déployer sur les plateformes sur lesquelles. Ils permettent également vous comprendre les conditions préalables qui doivent être en place avant de déployer les applications.

## Types d’application que vous pouvez déployer

### Programme d’installation logicielle

|Type d’application|Plus d’informations|
|----------------|-------|
|**Windows Installer (& #42 ;. exe, & #42 ;. MSI)**|Ce type de l’application doit prendre en charge l’installation en mode silencieux sans entrée utilisateur. Documentation de votre application doit inclure les options de ligne de commande appropriées pour installer silencieusement l’application (par exemple, **/q/q**). Vous trouverez une liste des options de ligne de commande courantes dans [Les commutateurs de ligne de commande pour l’outil Microsoft Windows Installer](https://support.microsoft.com/en-us/kb/227091).<br><br>Les autres fichiers ou dossiers qui nécessite le programme d’installation de l’application doivent être disponibles à partir de l’emplacement que vous spécifiez pour les fichiers d’installation de l’application.<br><br>Dans la plupart des cas, Windows Installer (.msi) et les fichiers de correctif Windows Installer (.msp) ne nécessitent pas Intune installer des arguments de ligne de commande. Vérifiez la documentation de votre application.<br><br>Si les arguments de ligne de commande sont nécessaires, ils doivent être entrées en tant que nom paires = valeur (par exemple, TRANSFORMS=custom_transform.mst).|
|**Package d’application pour Android (& #42 ;. Apk)**|Pour déployer des applications Android, vous devez disposer d’un package .apk valide.|
|**Package d’application pour iOS (& #42 ;. loi)**|Pour déployer des applications iOS, vous devez disposer d’un package .ipa valide.<br><br>Le package .ipa doit être signé par Apple, et la date d’expiration dans le profil de mise en service doit être valide. Intune pouvez distribuer des applications d’entreprise certificat iOS.<br><br>Pas toutes les applications de certificat de développeur Apple sont prises en charge.<br><br>Votre société doit être enregistrée pour le programme Enterprise développeur iOS.<br><br>Assurez-vous que pare-feu de votre organisation autorise l’accès au fichier iOS certification et mise en service des sites Web.<br><br>Vous n’avez pas besoin déployer un fichier manifeste (.plist) avec l’application.|
|**Package d’application Windows Phone (& #42 ;. XAP, .aspx, .appxbundle)**|Pour déployer des applications, vous avez besoin d’un certificat de signature de code mobile enterprise. Pour plus d’informations, voir [configurer la gestion de Windows Phone avec Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md).|
|**Package d’application Windows (.aspx, .appxbundle)**|Pour déployer des applications, vous avez besoin d’un certificat de signature de code mobile enterprise. Pour plus d’informations, voir [configurer la gestion des appareils Windows avec Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).|
|**Programme d’installation de Windows via la gestion des périphériques (& #42 ;. MSI)**|Cette application vous permet de créer et déployer des applications basées sur Windows Installer sur les PC inscrits qui s’exécutent Windows 10. Ces PC est gérées via la gestion des appareils mobiles (périphériques mobiles).<br /><br />Vous pouvez télécharger qu’un seul fichier avec l’extension .msi.<br><br>Le fichier code du produit et version du produit sont utilisés pour la détection de l’application.<br><br>Le comportement de redémarrage par défaut de l’application sera utilisé. Intune ne contrôle pas cela.<br><br>Packages MSI par utilisateur seront installés pour un seul utilisateur.<br><br>Packages MSI par ordinateur seront installés pour tous les utilisateurs sur l’appareil.<br><br>Packages MSI double mode sont installés uniquement pour tous les utilisateurs sur l’appareil.<br><br>Mises à jour de l’application sont prises en charge lorsque le code du produit de chaque version MSI est la même.<br>
Tous les types d’application installer logiciel sont téléchargés vers votre espace de stockage cloud.

### **Lien externe**
Utilisez un lien externe lorsque vous avez a :
- URL qui permet aux utilisateurs de télécharger une application à partir d’un magasin d’application.
- Créer un lien vers une application basée sur le web qui s’exécute à partir du navigateur web.

Applications basées sur des liens externes ne sont pas stockées dans votre espace de stockage cloud Intune.
### **Gèrent application iOS à partir de l’app store**
Vous pouvez utiliser des applications iOS gérées pour gérer et déployer des applications iOS gratuites à partir de l’app store. Vous pouvez également utiliser des applications iOS gérées à associer [stratégies de gestion des applications mobiles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) [compatibles applications](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) et consulter leur statut dans la console administrateur.<br /><br />Gèrent iOS applications ne sont pas stockées dans votre espace de stockage cloud Intune.

> [!TIP]
> Options pour les appareils mobiles ne sont pas disponibles jusqu'à ce que vous [Définissez l’autorité MDM](get-ready-to-enroll-devices-in-microsoft-intune.md) Intune.

## Éditeur du logiciel Intune
L’Éditeur du logiciel Microsoft Intune démarre lorsque vous ajoutez ou modifiez des applications à partir de la console administrateur Intune. Dans l’éditeur, sélectionner et configurer un type de programme d’installation de logiciel peut :

- Télécharger des applications (programmes pour les ordinateurs ou applications pour les appareils mobiles) pour être stockées dans le stockage cloud Intune.
- Créer un lien vers un magasin en ligne ou une application web.

Avant de commencer à utiliser l’Éditeur du logiciel, vous devez installer la version complète de [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Après l’installation, vous devrez peut-être redémarrer votre ordinateur avant de l’Éditeur du logiciel s’ouvrira correctement.

## Espace de stockage cloud
Toutes les applications que vous créez en utilisant le type d’installation installer logiciel (par exemple, une application métier) sont regroupées et télécharger sur le stockage de cloud Microsoft Intune. Un abonnement d’évaluation de Intune inclut 2 gigaoctets (Go) de stockage sur le nuage qui est utilisé pour stocker des applications gérées et mises à jour. Votre abonnement complet inclut 20 Go d’espace de stockage.

Vous pouvez voir la quantité d’espace que vous utilisez dans le nœud de **l’Utilisation du stockage** de l’espace de travail **d’administrateur** .

Configuration requise pour l’espace de stockage cloud est les suivantes :

-   Tous les fichiers d’installation de l’application doivent être placé dans le même dossier.
-   La taille de fichier maximale pour tous les fichiers que vous téléchargez est supérieure à 2 Go.


## Prise en charge pour Windows universel applications plateforme (UWP)
Windows 10 PC ne nécessitent pas une clé de chargement de version test pour installer des applications métier. Toutefois, la clé de Registre **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** doit comporter une valeur de **1** pour activer le chargement de version test.

Si cette clé de Registre n’est pas configurée, Intune définira automatiquement cette valeur à **1** la première fois que vous déployez une application sur le périphérique. Si vous définissez cette valeur sur **0**, Intune ne peut pas modifier automatiquement la valeur et le déploiement des applications métier échouera.

Universel plateforme Windows-métier applications doivent être connectées avec un certificat de signature de code approuvé sur chaque appareil sur lequel l’application est déployée. Vous pouvez utiliser un certificat à partir d’une infrastructure à clé publique interne (infrastructure de clés publiques), ou un certificat d’un certificat racine publique tiers installé sur l’appareil.

Sur les appareils Windows 10 Mobile, vous pouvez utiliser un certificat de signature de code non Symantec se universel **.aspx** applications. Pour les applications **.xap** et également **.aspx** packages créés pour Windows Phone 8.1 que vous voulez installer sur les appareils Windows 10 Mobile, vous devez utiliser un certificat de signature de code Symantec.

## Étapes suivantes

Vous devez ajouter des applications dans la console Intune avant de les déployer. Vous pouvez ajouter des applications pour [inscrit appareils](add-apps-for-mobile-devices-in-microsoft-intune.md) ou pour les [PC Windows que vous gérez avec le logiciel client Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).
