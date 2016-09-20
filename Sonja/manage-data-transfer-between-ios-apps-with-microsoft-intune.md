---
title: "Gérer le transfert de données entre les applications iOS | Microsoft Intune"
description: "Utilisez cette rubrique pour comprendre comment vous pouvez utiliser l’iOS ouvrir dans fonctionnalité et stratégies de gestion de l’application mobile pour gérer les transferts de données entre les applications."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 1d212dddc1d5665b7badf6cc27b41e012f74d96c
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer le transfert de données entre les applications iOS avec Microsoft Intune
## Gérer les applications iOS
Protection des données de votre société inclut s’assurer que les transferts de fichiers sont limités aux applications qui sont gérées par vous.  Vous pouvez gérer les applications d’iOS des façons suivantes :

-   Éviter la perte de données d’entreprise en configurant une stratégie MAM pour les applications, nous fera référence à comme applications **géré par une stratégie** .

-   Vous pouvez également déployer et gérer les applications via le **canal des périphériques mobiles**.  Cette fonctionnalité nécessite que les périphériques sont inscrits dans la solution périphériques mobiles. Il peut s’agir d’applications **géré par une stratégie** ou autres applications gérées.

La fonctionnalité **Ouvrir Gestion** pour les appareils iOS peut limiter les transferts de fichiers entre les applications déployées via le **canal des périphériques mobiles**. Ouvrir dans les restrictions de gestion des sont définis dans les paramètres de configuration et déployées à l’aide de votre solution de périphériques mobiles.  Lorsque l’utilisateur installe l’application déployée, les restrictions définies sont appliquées.
##  À l’aide de MAM avec applications iOS
Stratégies de gestion des (MAM) de l’application mobile peuvent servir avec la fonctionnalité **Ouvrir Gestion des** iOS pour protéger des données de plusieurs façons :

-   **Employé appartenant périphériques ne pas gérés par n’importe quelle solution MDM :** Vous pouvez définir les paramètres de stratégie MAM **Autoriser l’application pour transférer des données vers**gérés uniquement des applications. Lorsque l’utilisateur final ouvre un fichier protégé dans une application qui n’est pas géré par une stratégie, le fichier est illisible.

-   **Périphériques gérés par Intune :** Pour les appareils inscrits dans Intune, de transfert de données entre les applications avec les stratégies MAM et autres applications iOS gérées déployées via Intune est automatiquement autorisés. Pour autoriser le transfert de données entre les applications avec les stratégies MAM, activez le paramètre **Autoriser l’application pour transférer des données vers gérés uniquement des applications** . Vous pouvez utiliser la fonctionnalité **Ouvrir Gestion** pour contrôler le transfert de données entre les applications qui sont déployés via Intune.   

-   **Périphériques gérés par une solution de la gestion des périphériques tiers :** Vous pouvez limiter le transfert de données pour que les applications gérées en utilisant la fonctionnalité **Ouvrir Gestion des** iOS.
Pour vous assurer que les applications que vous déployez à l’aide de votre solution de la gestion des périphériques tiers sont également associées avec les stratégies MAM que vous avez configuré dans Intune, vous devez configurer le paramètre de UPN utilisateur comme décrit dans la procédure pas à pas [configurer le paramètre UPN utilisateur](#configure-user-upn-setting) .  Lorsque des applications sont déployées avec le paramètre UPN utilisateur, les stratégies MAM sont appliquées à l’application lorsque l’utilisateur final signes à l’aide de leur compte professionnel.

> [!IMPORTANT]
> Le paramètre UPN utilisateur n’est requis pour les applications déployées sur périphériques gérés par un MDM tiers.  Pour les appareils Intune géré, ce paramètre n’est pas nécessaire.

## Configurer le paramètre UPN utilisateur
Cette configuration est requise pour les périphériques qui sont gérés par une solution de la gestion des périphériques tiers. La procédure décrite ci-dessous est un flux général sur la façon de mettre en œuvre le paramètre UPN et l’expérience utilisateur qui en résulte :


1.  Dans le portail Azure, [configurer une stratégie de gestion de l’application mobile](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) pour la plateforme iOS. Configurer les paramètres de stratégie par les exigences de votre société, puis sélectionnez les applications qui sont autorisés à cette stratégie.

2.  Déployer les applications et le profil de messagerie souhaitée gérées **via votre solution de la gestion des périphériques tiers** en utilisant le paramètre décrit dans les étapes 3 et 4.

3.  Déploiement de l’application avec les paramètres de configuration d’application suivants : clé = IntuneMAMUPN, valeur =<username@company.com> [exemple : 'IntuneMAMUPN', 'jondoe@microsoft.com']

4.  Déployez l’ouvrir dans la stratégie de gestion des appareils inscrits.

### Expérience utilisateur final exemple

1.  L’utilisateur final installe Microsoft Word application sur l’appareil.

2.  L’utilisateur final ouvre l’application de messagerie native gérées pour accéder à sa messagerie électronique.

3.  L’utilisateur final tente d’ouvrir le document à partir de mail native dans Microsoft Word.

4.  Au démarrage de l’application Word, l’utilisateur final est invité à se connecter à l’aide de leur compte professionnel.  Ce compte de travail de l’utilisateur final entre lorsque vous y êtes invité doit correspondre compte que vous avez spécifié dans configuré dans les paramètres de configuration d’application pour l’application Microsoft Word.

    > [!NOTE]
    > L’utilisateur final peut ajouter d’autres comptes personnels dans Word à suivre leur tâches personnelles et ne pas affectées par les stratégies MAM lors de l’utilisation de l’application Word dans un contexte personnel.

5.  Lorsque la connexion a réussi, les paramètres de stratégie d’application sont appliquées à l’application Word.

6.  Maintenant le transfert de données a réussi et le document est marqué comme identité de l’entreprise dans l’application. En outre, les données sont traitées dans un contexte de travail et les paramètres de stratégie sont appliquées en conséquence.

### Voir aussi
[Protéger les données d’application à l’aide de stratégies de gestion de l’application mobile avec Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
