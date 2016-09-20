---
title: "Azure portail pour les stratégies MAM | Microsoft Intune"
description: "Créer des stratégies de gestion à l’aide du portail Azure application mobile. Les stratégies que vous créez ici peuvent être appliqués aux périphériques avec ou sans inscription dans Intune."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 1ddb7a30a6f23a3f3d754bd18975c50f32662578
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Azure portail pour les stratégies de Microsoft Intune MAM
## Accéder au portail Azure
Le **portail Azure** permet de créer et gérer les stratégies de gestion de l’application mobile.

Azure portail prend en charge la création de stratégies MAM pour :
- Applications en cours d’exécution sur les périphériques **inscrit et gérées par Intune**.
- Applications en cours d’exécution sur les périphériques qui sont **pas inscrit** dans n’importe quelle solution périphériques mobiles.
- Applications en cours d’exécution sur les périphériques qui sont **inscrits à une solution de la gestion des périphériques tiers**.

>[!IMPORTANT]

> Si vous utilisez actuellement la console d’administration Intune pour gérer vos périphériques, vous pouvez créer une stratégie MAM qui prend en charge des applications pour appareils inscrits dans Intune à l’aide de la [console d’administration Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Vous voyiez pas tous les paramètres de stratégie MAM dans la console d’administration Intune. Le portail Azure est la nouvelle console d’administration pour créer des stratégies MAM. Si vous créez des stratégies MAM sur console d’administration Intune et Azure portal, la stratégie dans le portail Azure est appliquée aux applications et déployée vers des utilisateurs.

## Connexion au portail Azure et personnaliser votre page de démarrage

1.  Accédez au [portail Azure](https://portal.azure.com) et vous connecter avec votre [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] informations d’identification.

    ![Capture d’écran du journal portail Azure dans la page](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Une fois que vous êtes connecté, vous verrez le **tableau de bord**. La page **tableau de bord** peut être personnalisée.

    ![Capture d’écran du tableau de bord du portail Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Dans le menu **Parcourir** , recherchez **Intune**. ![Capture d’écran du menu Parcourir avec Intune mis en surbrillance](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Choisissez **Intune > Gestion des applications mobiles Intune > Paramètres**.

    ![Capture d’écran de la cuillère de gestion des applications mobiles Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Pour épingler une carte à la page de **démarrage** , vous pouvez utiliser l’option **code confidentiel** de la carte.  Cliquez sur l’icône d’épingle sur la **carte de gestion des applications mobiles Intune**, pour épingler à la page de **démarrage** .

    ![Capture d’écran de la cuillère de gestion des applications mobiles Intune avec l’icône d’épingle mis en surbrillance](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Capture d’écran du tableau de bord avec la vignette Intune épinglée](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## Étapes suivantes
[Préparez-vous à configurer des stratégies de gestion de l’application mobile](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
