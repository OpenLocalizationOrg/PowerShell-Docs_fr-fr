---
title: "Surveiller les stratégies MAM avec Microsoft Intune | Microsoft Intune"
description: "Voir combien d’utilisateurs ont la stratégie d’exploration pour en savoir plus de détails."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: e530960268e8ef7d9c7f5419e7221bec61c0e6ef
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Surveiller les stratégies de gestion de l’application mobile avec Microsoft Intune
Une fois que vous avez configuré une stratégie MAM et appliqués aux utilisateurs, vous pouvez surveiller l’état de conformité dans le [portail Azure](https://portal.azure.com). Le portail Azure inclut des informations sur les utilisateurs concernés par la stratégie, l’état de conformité et des problèmes qui peuvent être confronté à vos utilisateurs finaux.
## Affichage de synthèse
Sur la carte de **Gestion des applications mobiles Intune** vous pouvez consulter un résumé de l’état de conformité comme décrit ci-dessous :


![Vignette de résumé sur la carte de gestion des applications mobiles Intune](../media/mam-azure-portal-user-status-summary.png)

-   **Utilisateurs :** Le nombre total d’utilisateurs dans votre entreprise qui utilisent les applications qui sont associées à la stratégie.

-   **Gérées par la stratégie :**-le nombre d’utilisateurs qui ont utilisé au moins une des applications dans le contexte de travail.

-   **Aucune stratégie :** Le nombre d’utilisateurs qui utilisent les applications liées à la stratégie, mais ne sont pas ciblé par votre stratégie.  Vous pouvez envisager d’ajout de ces utilisateurs à votre stratégie.

- **Avec indicateur utilisateurs :** Le nombre d’utilisateurs rencontre des problèmes. Actuellement, seuls les utilisateurs d’appareils jailbroken sont signalés sous **utilisateurs avec indicateur**.


## Affichage détaillé
Vous pouvez accéder à la vue détaillée de la synthèse en cliquant sur la vignette de **l’état des utilisateurs** et la vignette **utilisateurs avec indicateur** .

### État de l’utilisateur
Vous pouvez rechercher un utilisateur unique et consulter l’état de conformité pour cet utilisateur. La carte de **Création de rapports application** affiche les informations suivantes pour un utilisateur sélectionné :
- Périphériques qui sont associés au compte d’utilisateur
- Applications qu’avec la stratégie MAM sur l’appareil
- État :

  **Archivé :** Cela signifie que la stratégie a été déployée à l’utilisateur, et l’application a été utilisée dans le contexte de travail au moins une fois.

  **Ne pas archivé :** Cela signifie que la stratégie a été déployée à l’utilisateur, mais l’application n’a pas été utilisée dans le contexte de travail depuis.

>[!NOTE]
> Si l’utilisateur que vous recherchez n’a pas la stratégie MAM déployée leur, vous verrez un message vous informant que l’utilisateur n’est pas ciblé pour toutes les stratégies de l’application.

Pour afficher la déclaration d’un utilisateur, procédez comme suit :

**Étape 1 :**  Pour sélectionner un utilisateur, cliquez sur la vignette résumée ou choisissez l’option **Application signalé par l’utilisateur** dans la carte de **paramètres** comme indiqué ci-dessous :

![Application de l’option sur la carte de paramètres de rapport](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

**Étape 2 :** Cette action ouvre la carte de **reporting de l’application** . Choisissez **Sélectionner utilisateur** pour rechercher un utilisateur Azure Active Directory.

![sélectionner l’option utilisateur sur la carte de création de rapports d’application](../media/mam-azure-portal-app-reporting-select-user.png)

**Étape 3 :** Après avoir sélectionné l’utilisateur dans la liste, vous verrez les détails de l’état de conformité pour cet utilisateur.

![Application détails du rapport](../media/mam-azure-portal-app-reporting-by-user.png)
### Utilisateurs avec indicateur
La vue détaillée affiche le message d’erreur, l’application qui a été accessible lorsque l’erreur s’est produite, la plateforme de l’appareil et un cachet d’heure.  

### Voir aussi
[Gérer le transfert de données entre les applications iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

[Expérience utilisateur final application MAM activé](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md)
