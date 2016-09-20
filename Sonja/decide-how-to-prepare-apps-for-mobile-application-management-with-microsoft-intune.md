---
title: "Préparer des applications pour la gestion des applications mobiles | Microsoft Intune"
description: "Les informations contenues dans cette rubrique vous aide à décider quand vous devez utiliser l’application d’habillage outil et le Kit de développement de l’application pour activer votre trait personnalisé des applications d’entreprise à utiliser les stratégies de gestion de l’application mobile."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
ms.openlocfilehash: 0e5761859f4c0c30f1bd818c968bba3a3c6c60b6
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Déterminez comment préparer les applications pour la gestion des applications mobiles avec Microsoft Intune
Vous pouvez activer vos applications d’utiliser des stratégies de gestion (MAM) application mobile à l’aide de l’outil d’habillage de l’application Intune ou le SDK application Intune. Utiliser ces informations pour en savoir plus sur ces deux méthodes et quand les utiliser.

## Outil Intune application habillage
L’outil d’habillage application est utilisé principalement pour les applications interne de métier (métier). L’outil est une application de ligne de commande qui crée une enveloppe de l’application, ce qui permet à l’application d’être géré par une stratégie de gestion des applications mobiles Intune. Vous n’avez pas besoin le code source à utiliser l’outil, mais vous avez besoin d’informations d’identification de la signature.  Pour plus d’informations sur la signature des informations d’identification, consultez le [blog Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Pour la documentation de l’outil d’habillage application, voir [Android application habillage outil](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) et [outil d’habillage application iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

L’outil d’habillage application ne reconnaît pas les applications dans l’application ou Play Store ou des fonctionnalités qui requièrent l’intégration de temps de développement (voir le tableau de comparaison de fonctionnalité suivant).

Vous devez utiliser l’outil d’habillage application, plutôt que le Kit de développement, si l’application a déjà été écrit ou si le code source n’est pas disponible.

L’outil d’habillage application pour MAM **sur les périphériques qui ne sont pas inscrit dans Intune est pris en charge dans la version d’évaluation. Pour plus d’informations, voir [protéger métiers applications sur les appareils ne pas inscrits dans Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md) rubrique**.

### Plateformes prises en charge

|**Outil d’habillage application** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Oui|Oui|
|**Android**| N° |Oui|
## Kit de développement de l’application Intune
Le Kit de développement de l’application est conçu principalement pour les clients qui disposent d’applications dans le magasin application ou lecture et voulez être en mesure de gérer les applications avec Intune. Toutefois, n’importe quelle application peut tirer parti de l’intégration du Kit de développement, même s’il s’agit d’une application métier.

Pour en savoir plus sur le Kit de développement, consultez la [vue d’ensemble](/intune/develop/intune-app-sdk). Pour commencer à utiliser le Kit de développement, voir [Prise en main avec le Microsoft Intune application SDK](/intune/develop/intune-app-sdk-get-started).

### Plateformes prises en charge
|**Kit de développement de l’application Intune** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Oui, utiliser le composant Intune application SDK Xamarin|Oui – utiliser le plug-in Intune application SDK Cordova|
|**Android**| Oui – utiliser le composant Intune application SDK Xamarin|Oui – utiliser le plug-in Intune application SDK Cordova|

## Comparaison des fonctionnalités
Ce tableau répertorie les paramètres que vous pouvez utiliser pour l’outil d’habillage du application et le Kit de développement de l’application.

> [!NOTE]
> L’outil d’habillage application peut être utilisé avec Intune Standalone ou Intune avec le Gestionnaire de Configuration.

|Fonctionnalité|Kit de développement de l’application|Outil d’habillage application|
|-----------|---------------------|-----------|
|Restreindre le contenu web à afficher dans un navigateur géré d’entreprise|X|X|
|Empêcher les sauvegardes Android, iTunes ou iCloud|X|X|
|Autoriser l’application pour transférer des données vers d’autres applications|X|X|
|Autoriser l’application pour recevoir des données provenant d’autres applications|X|X|
|Limiter les commandes Couper, copier et coller avec d’autres applications|X|X|
|Simple code confidentiel est nécessaire pour l’accès|X|X|
|Remplacer une application intégrée code confidentiel par code confidentiel Intune|X||
|Spécifier le nombre de tentatives avant réinitialisation du code confidentiel|X|X|
|Exiger l’empreinte au lieu de code confidentiel (iOS uniquement)<br></br>**Remarque :** Disponible uniquement dans les environnements MAM uniquement.|X||
|Exiger des informations d’identification d’entreprise pour l’accès|X|X|
|Bloc gérées applications de s’exécuter sur des appareils racine ou jailbroken|X|X|
|Chiffrer les données d’application|X|X|
|Revérifier les conditions d’accès après un nombre spécifié de minutes|X|X|
|Spécifiez la période de grâce en mode hors connexion|X|X|
|Capture d’écran bloc (Android uniquement)|X|X|
|Réinitialisation complète|X|X|
|Réinitialisation sélective <br></br>**Remarque :** IOS, lorsque le profil de gestion est supprimé, l’application est également supprimée.|X||
|Empêcher les « Enregistrer sous » |X||
|Prise en charge de plusieurs identités|X||
### Voir aussi

[Outil d’habillage application Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[outil d’habillage application iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Utiliser le Kit de développement pour activer les applications pour la gestion des applications mobiles](use-the-sdk-to-enable-apps-for-mobile-application-management.md)
