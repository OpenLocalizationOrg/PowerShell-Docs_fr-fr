---
title: Ce qui se passe | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
ms.openlocfilehash: 0949172a7b8517b12fb46e8fd1f8a3cd70d93099
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Nouveautés de Microsoft Intune - août
Ces informations sont fournies sous réserve de confidentialité de manière extrêmement limitée et peuvent être modifiées. Certaines fonctionnalités répertoriées ici risquent de ne pas avoir effectué les dates de démarcation et peuvent être retardées jusqu'à une version ultérieure. Autres fonctionnalités sont testées dans un pilote (flighting) pour vous assurer qu’elles soient prêtes à l’emploi. Veuillez contacter votre ami Intune/PM Si vous avez des questions ou des problèmes.

Cette page est mis à jour régulièrement. Cochez retour pour les nouveaux ce qui se passe mises à jour.

Les modifications suivantes sont en cours de développement pour Intune. Toutes ces fonctionnalités seront finalement prise en charge pour les déploiements clients hybride (Gestionnaire de Configuration avec Intune). Pour plus d’informations sur les nouvelles fonctionnalités hybride, consultez notre [hybride page Nouveautés](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Gestion de l’application
### Applications masquées et affichées pour iOS 9.3
Pour les périphériques contrôlés exécutant iOS 9,3 ou version ultérieure, vous pourrez utiliser la liste des applications masqués et affichés dans la stratégie de configuration générale iOS pour :
- Spécifiez une liste des applications qui sont masqués pour les utilisateurs. Les utilisateurs ne peuvent pas afficher ou lancer ces applications.
- Spécifiez une liste des applications que les utilisateurs peuvent afficher et barre de lancement. Aucune autres applications peuvent être affichées ou lancées.

Les applications que vous pouvez spécifier incluent les deux applications que vous avez déployé, et les applications iOS intégrée comme des Messages et des Notes.
<!---TFS 1279009--->

### Stratégie d’applications autorisés et bloqués pour les appareils Samsung KNOX

Vous pouvez configurer une stratégie personnalisée pour les appareils Samsung KNOX qui vous permet de créer une des opérations suivantes :
- Liste des applications en cours d’exécution sur l’appareil sont bloqués. Même si installé, une application définie dans la liste d’expéditeurs bloqués ne peut pas être activée sur le périphérique.
- Liste des applications que les utilisateurs de l’appareil sont autorisés à installer à partir de Google Play store. Aucune autre application ne peut être installée à partir du magasin.

Ces paramètres peuvent uniquement être utilisés par les périphériques qui s’exécutent KNOX Samsung.
<!--- For details, see [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md)--->
<!---TFS 1311629 --->

### Nouvelles applications compatibles avec les stratégies de gestion des (MAM) application mobile
L’application Yammer pour [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) et [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) seront compatible avec les [stratégies de gestion (MAM) Intune application mobile](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), que l’appareil est inscrit ou non.

Pour une liste complète des applications compatibles MAM, voir le site [Microsoft Intune application partenaires](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) .
<!--- TFS 1252335 & 1252336--->

## Gestion des appareils
### Prise en charge 7.0 Android
En août, Intune fournit un support « jour 0 » pour le système d’exploitation Android 7.0 à venir pour les appareils mobiles.
<!---TFS 1262053--->
### Fonction sur les appareils Android 7.0 de réinitialisation Google suppression du code secret à distance
Google consiste à supprimer la possibilité des administrateurs informatiques et les utilisateurs finaux à distance réinitialiser le code secret des appareils Android 7.0. Auparavant, les administrateurs informatiques peuvent réinitialiser à distance code secret d’un utilisateur et les utilisateurs finaux pu réinitialiser leurs codes secrets à partir du site portail d’entreprise.

## Gestion de groupe
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

## Amortissement de service
### Applications de portail d’entreprise pour Windows 8 et Windows Phone 8 sont en cours déconseillées démarrage dans septembre 2016
À partir d’octobre 2016, Microsoft Intune sera déconseiller prise en charge pour les applications Windows 8 et Windows Phone 8 application portail d’entreprise. Microsoft Intune seront déconseiller également de prise en charge de la plateforme Windows Phone 8. Par conséquent, vous ne serez pas en mesure de s’inscrire ou mettre à jour les appareils Windows Phone 8. Vous pouvez continuer à gérer les appareils Windows Phone 8 et Windows 8 qui sont déjà inscrit. Mettre à jour les appareils Windows Phone 8 et Windows 8 pour Windows 8.1 et Windows Phone 8.1 et utiliser les applications Windows 8.1 et Windows Phone 8.1 application portail d’entreprise correspondantes pour continuer à distribuer des applications pour les appareils suivants sans interruptions.
<!---TFS 1255391--->

### Groupe personnalisé ciblage de suppression de règles de Notification
Les règles de notification Intune définissent qui sera envoyé à un message d’alerte de Intune. Pour l’instant, vous pouvez configurer des règles de notification pour envoyer des messages électroniques à tous les utilisateurs de périphériques dans un groupe de périphériques Intune que vous avez créé. À partir de juin 2016, ciblage groupes créés par l’utilisateur est n’est plus pris en charge.

La barre de planning préliminaire pour que cette modification est la suivante :
- Dans septembre 2016, les nouveaux clients ne voient pas étape 2 de l’Assistant Création de règle de Notification. Clients existants ne sont pas affectés.
- Autour d’octobre 2016, certains clients existants ne verront pas les groupes « sélectionnez le périphérique » dans l’Assistant.
- Avec une date ultérieure, nous prévoyons que toutes les installations ne verra pas les groupes « sélectionnez le périphérique » dans l’Assistant.

<!---   TFS 1278864--->
### Modifications apportées à la prise en charge pour l’application portail d’entreprise iOS
En septembre, tous les utilisateurs de l’application portail d’entreprise Intune Microsoft pour iOS doivent utiliser la version la plus récente. Nouveaux utilisateurs ne seront en mesure de télécharger la version la plus récente et utilisateurs actuels doivent mettre à jour vers celui-ci. La dernière version nécessite iOS 8.0 ou version ultérieure, afin que les appareils exécutant d’anciennes versions d’iOS ne puissent pas utiliser le portail d’entreprise ou s’inscrire jusqu'à ce qu’ils mettre à jour leur appareil iOS 8.0 ou version ultérieure et puis mettez à jour l’application portail d’entreprise vers la dernière version. Inscrits appareils exécutant versions inférieures à iOS 8.0 continuent à être gérés et répertoriés dans la Console d’administration Intune.

<!---TFS 1283165--->


### Visionneuse Intune applications
Dans la version de la nouvelle RMS le partage d’application, nous supprime les applications Intune visionneuse suivantes dans août 2016 :
- Visionneuse de AV Intune
- Visionneuse PDF Intune
- Visionneuse Intune Image pour Android à partir de Google Play

Au lieu d’utiliser les applications Intune visionneuse, nous recommandons d’utiliser la nouvelle application de gestion des droits (RMS partage) pour Android, qui permet de déployer une application au lieu de trois applications distinctes pour afficher les fichiers d’entreprise sur les appareils Android en toute sécurité. En savoir plus sur les [services RMS le partage d’application](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app).
<!--- goes in 1608 What's New--->


### Voir aussi
Pour plus d’informations sur les développements récents, voir [Nouveautés de Microsoft Intune](whats-new-in-microsoft-intune.md) .
