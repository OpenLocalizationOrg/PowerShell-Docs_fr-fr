---
title: "Déployer et surveiller une stratégie de conformité | Microsoft Intune"
description: "Suivez les instructions pas à pas dans cette rubrique à déployer et surveiller une stratégie de conformité d’appareil."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 8658df1fb9932fb2cab984a13557aad684569df5
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Déployer et surveiller une stratégie de conformité appareil dans Microsoft Intune
## Déployer une stratégie de conformité
Déployer la stratégie de conformité vous avez [créé](create-a-device-compliance-policy-in-microsoft-intune.md) à un ou plusieurs groupes d’utilisateurs de votre organisation. Lorsqu’une stratégie de conformité est déployée à un utilisateur, les périphériques de l’utilisateur vérifiés la conformité.

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis choisissez **Gérer le déploiement**.
![Capture d’écran de la page de la stratégie de conformité montrant l’option de menu gérer le déploiement en haut](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  Dans la boîte de dialogue **Gérer le déploiement** , sélectionnez un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis sélectionnez **Ajouter > OK**.
![Capture d’écran de la boîte de dialogue Gérer déploiement](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) vous pouvez déployer une stratégie de conformité aux utilisateurs. Utiliser des groupes Active Directory que vous avez déjà créé et synchronisé avec Intune ou créer manuellement ces groupes dans la console Intune. Pour plus d’informations sur la façon de déployer des stratégies, voir [déployer une stratégie de configuration](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Utilisez le résumé de l’état et les alertes dans la page **vue d’ensemble** de l’espace de travail **stratégie** pour identifier les problèmes avec la stratégie qui nécessitent votre attention. En outre, un résumé de l’état apparaît dans l’espace de travail de **tableau de bord** .

> [!IMPORTANT]
> Si vous n’avez pas déployé une stratégie de conformité, puis activez une stratégie d’accès conditionnel Exchange, tous les périphériques ciblées seront autorisés à accéder.

## Résolution des conflits de stratégie Intune
Conflits de stratégies peuvent se produire échéance lorsque plusieurs stratégies Intune sont appliquées à un appareil. Si les paramètres de stratégie se chevauchent, Intune résout les conflits en utilisant les règles suivantes :

-   Si les paramètres en conflit sont à partir d’une stratégie de configuration Intune et une stratégie de conformité, les paramètres de la stratégie de conformité ont priorité sur les paramètres de la stratégie de configuration, même si les paramètres de la stratégie de configuration sont plus sécurisées.

-   Si vous avez déployé plusieurs stratégies de conformité, la plus sûre de ces politiques sera utilisée.

## Contrôler la stratégie de conformité

#### Pour afficher les périphériques qui ne sont pas conformes à une stratégie de conformité

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **groupes > tous les périphériques**.

2.  Double-cliquez sur le nom d’un périphérique dans la liste des périphériques.

3.  Sélectionnez l’onglet **stratégie** pour afficher la liste des stratégies pour cet appareil.

4.  Dans la liste déroulante de **filtres** , sélectionnez **n’est pas conforme à la stratégie de conformité**.
![Capture d’écran montrant la liste des options dans la liste de filtres](./media/intune-sa-3e-view-device-noncompliance.png)

#### Pour afficher la certification d’intégrité des rapports

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **les rapports**.

2.  Dans la page de **Rapport d’intégrité Attestation - créer un rapport** , vous pouvez afficher un rapport avec toutes les données d’attestation d’au niveau de Windows 10 collectées par Intune. Vous pouvez également créer un rapport avec un sous-ensemble des données à l’aide de filtres. Les filtres peuvent être basés sur le type d’appareil, système d’exploitation ou uniquement un sous-ensemble de points de données.


## Étapes suivantes
Vous pouvez désormais utiliser la stratégie de conformité avec les stratégies d’accès conditionnel pour contrôler l’accès aux services de votre organisation.

[Restreindre l’accès aux messages électroniques et services Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


### Voir aussi
[Introduction à la conformité appareil stratégies dans Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)
