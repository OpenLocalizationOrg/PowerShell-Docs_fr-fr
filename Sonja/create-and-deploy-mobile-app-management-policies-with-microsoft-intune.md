---
title: "Créer et déployer des stratégies MAM | Microsoft Intune"
description: "Suivez les instructions pas à pas dans cette rubrique pour créer et déployer des stratégies de gestion de l’application mobile."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 686610249b35f81e9ad7a87fe20d736a32eafb43
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Créer et déployer des stratégies de gestion de l’application mobile avec Microsoft Intune
Stratégies de gestion des (MAM) de l’application mobile peuvent être appliqués aux applications en cours d’exécution sur les périphériques qui ne peuvent pas être gérés par Intune. Pour une description plus détaillée de la façon travail de stratégies MAM et les scénarios pris en charge par les stratégies Intune MAM, consultez la rubrique [protéger des données d’application à l’aide de stratégies de gestion de l’application mobile](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) .

Cette rubrique décrit le processus de création d’une stratégie MAM dans le **portail Azure**. Le portail Azure est la nouvelle console d’administration pour créer des stratégies MAM et nous vous recommandons d’utiliser ce portail pour créer des stratégies MAM. Portail Azure prend en charge les scénarios MAM suivants :
- Appareils inscrits dans Intune
- Périphériques gérés par une solution de la gestion des périphériques tiers
- Appareils mobiles qui ne sont pas gérés par n’importe quelle solution périphériques mobiles (BYOD).

>[!IMPORTANT]
Si vous utilisez actuellement la **console d’administration Intune** pour gérer vos périphériques, tenez compte les éléments suivants :

> * Vous pouvez créer une stratégie MAM qui prend en charge des applications pour appareils inscrits dans Intune à l’aide de la [console d’administration Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).
> * Les stratégies MAM créées dans la console d’administration Intune ne peuvent pas être importées dans le portail Azure.  Les stratégies MAM doivent être recréés dans le portail Azure.

> * Vous voyiez pas tous les paramètres de stratégie MAM dans la console d’administration Intune. Le portail Azure est la nouvelle console d’administration pour créer des stratégies MAM.

> * Déploiement de gérer les applications, vous devez créer une stratégie MAM dans la console d’administration Intune. Dans ce cas, vous souhaiterez peut-être créer des stratégies de MAM dans la console d’administration Intune et le portail Azure : Intune console d’administration pour vous assurer que vous avez la possibilité de déployer des applications gérées, portail Azure car il s’agit de la nouvelle console d’administration qui comporte tous les paramètres de stratégie MAM.

> * Si vous créez des stratégies MAM sur console d’administration Intune et Azure portal, la stratégie est créée dans le portail Azure est appliquée aux applications.

Pour afficher la liste des paramètres de stratégie pris en charge pour les plateformes Android et iOS, sélectionnez une des opérations suivantes :

> [!div class="op_single_selector"]
- [stratégies d’iOS](ios-mam-policy-settings.md)
- [Stratégies Android](android-mam-policy-settings.md)

##  Créer une stratégie MAM
Avant de créer une stratégie MAM, passez en revue les informations [préalables et prise en charge](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) .
1.  Choisissez **Gestion des applications mobiles Intune &gt; paramètres** pour ouvrir la carte de **paramètres** .

    ![Capture d’écran de la cuillère de gestion des applications mobiles Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Si c’est la première fois que vous utilisez le portail Azure, lisez tout d’abord [Azure portail pour les stratégies de Microsoft Intune MAM](azure-portal-for-microsoft-intune-mam-policies.md) pour vous familiariser avec le portail.

2.  Dans la carte de **paramètres** , choisissez la **stratégie d’application**.  Cette action ouvre la carte de **stratégie d’application** dans laquelle vous allez créer des stratégies et modifier des stratégies existantes. Cliquez sur **Ajouter une stratégie**.

    ![Capture d’écran de la carte de stratégie d’application avec l’ajouter une option de menu stratégie mise en évidence ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  Tapez un nom pour la stratégie, ajoutez une brève description, puis sélectionnez le type de plateforme à créer une stratégie pour iOS ou Android.  Vous pouvez créer plusieurs stratégies pour chaque plate-forme.

    ![Capture d’écran de l’ajouter une carte de stratégie](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  Cliquez sur **applications** pour ouvrir la **carte applications** où une liste des applications disponibles s’affiche. Vous pouvez sélectionner une ou plusieurs applications dans la liste que vous souhaitez associer à la stratégie que vous créez. Celui que vous avez sélectionné les applications, cliquez sur le bouton **Sélectionner** en bas de la cuillère **applications** pour enregistrer votre sélection.

    > [!IMPORTANT]
    > Vous devez sélectionner au moins une application pour créer une stratégie.

5.  Dans la zone **Ajouter une carte de stratégie**, sélectionnez **configurer les paramètres requis** pour ouvrir la carte de paramètres de stratégie.

    Il existe deux catégories de paramètres de la stratégie,**déplacement de données** et **Access**.  Règles de déplacement des données sont applicables aux mouvements de données et les applications, tandis que le niveau d’accès des stratégies déterminer comment l’utilisateur final accède aux applications dans un contexte de travail.
    Pour vous aider aux paramètres de stratégie ont des valeurs par défaut.  Vous n’avez pas à apporter des modifications si les valeurs par défaut selon vos besoins.

    > [!TIP]
    > Ces paramètres de stratégie sont appliquées uniquement lorsque vous utilisez des applications dans le contexte de travail.  Lorsque l’utilisateur final utilise l’application pour effectuer une tâche personnelle, ils ne pas être affectés par ces politiques.

    ![Capture d’écran de la cuillère paramètres ainsi que de l’ajouter une carte de stratégie](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  Cliquez sur **OK** pour enregistrer cette configuration.  Vous êtes maintenant dans la carte de **Ajouter une stratégie** . Cliquez sur **créer** pour créer la stratégie et enregistrer vos paramètres.

    ![Capture d’écran de l’ajouter un affichage de carte stratégie que les applications et les paramètres ont été configurés](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)



Lorsque vous avez terminé la création d’une stratégie comme décrit dans la procédure précédente, il n’est pas déployée à tous les utilisateurs.  Suivez les étapes décrites ci-dessous pour déployer la stratégie.

> [!IMPORTANT]
> Si vous créez une stratégie MAM pour une application à l’aide de la console d’administration Intune et une stratégie MAM à l’aide du portail Azure, la stratégie que vous avez créé à l’aide du portail Azure est prioritaire. Toutefois, la création de rapports dans la console Intune ou Gestionnaire de Configuration signalera les paramètres de stratégie créés à partir du portail Azure. Par exemple :
>
> -   Vous avez créé une stratégie de gestion des applications mobiles dans la console d’administration Intune blocs de la copie d’une application.
> -   Vous avez créé une stratégie de gestion de l’application mobile dans la console Azure qui permet de copier d’une application
> -   Vous associez ces deux stratégies à l’application même.
> -   Le résultat est que la stratégie que vous avez créé à partir de la console Azure est prioritaire et copier est autorisé.
> -   Toutefois, état et rapports dans la console Intune incorrectement indiquera que copie est bloquée.

## Déployer une stratégie auprès des utilisateurs

1.  Dans la carte de **stratégie** , cliquez sur **groupes d’utilisateurs**, qui permet d’ouvrir la carte de **groupes d’utilisateurs** . Cliquez sur **Ajouter un groupe utilisateur** dans la carte de **groupes d’utilisateurs** pour ouvrir la carte **Ajouter un groupe utilisateur** .

    ![Capture d’écran de la cuillère groupes utilisateur avec l’option de menu Ajouter utilisateur groupe mis en surbrillance](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  Une liste de groupes d’utilisateurs s’affiche dans la carte **d’Ajouter un groupe utilisateur** . Il s’agit d’une liste de tous les groupes de sécurité dans votre **Azure Active Directory**.  Vous pouvez sélectionner les groupes d’utilisateurs que vous souhaitez que cette stratégie à appliquer et choisissez **Sélectionner**. Vous choisissez **Sélectionner**, déploie la stratégie aux utilisateurs.

    ![Capture d’écran de la cuillère de groupe utilisateur Ajouter montrant la liste des utilisateurs Azure Active Directory](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    Vous venez de créer une stratégie et déployée vers des utilisateurs.

Seuls les utilisateurs dotés [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] des licences qui leur sont affectées sont sera-t-il affectés par la stratégie.  Les utilisateurs qui se trouvent dans le groupe de sécurité que vous avez sélectionné qui n’ont pas un [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] licence qui leur sont affectée ne sont pas affectés.

>[!IMPORTANT]
> Si vous utilisez Intune avec le Gestionnaire de Configuration pour gérer vos appareils iOS et Android, la stratégie est appliquée uniquement aux utilisateurs directement dans le groupe que vous avez sélectionné.  Membres de groupes enfants imbriqués dans le groupe que vous avez sélectionné ne seront pas affectés.

Les utilisateurs finaux peut télécharger les applications à partir du magasin des applications ou Google Play. Pour une description détaillée des comment MAM protège les données d’entreprise sur l’appareil voir rubrique [expérience utilisateur final avec MAM activé applications](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md) .

##  Modifier les stratégies existants
Vous pouvez modifier une stratégie existante et l’appliquer aux utilisateurs ciblées. Toutefois, lorsque vous modifiez les stratégies existantes, les utilisateurs qui sont déjà connectés aux applications ne verrez pas les modifications pour une période de 8 heures.

Pour visualiser les modifications immédiatement l’utilisateur final devra se déconnecter de l’application, puis vous reconnecter à.

### Pour modifier la liste des applications liées à la stratégie

1.  Dans la carte de **stratégie d’application** , sélectionnez la stratégie que vous voulez modifier. Cette action ouvre une carte spécifique à la stratégie que vous venez de sélectionner.

    ![Capture d’écran d’une stratégie existante ouverte dans une carte distincte](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Dans la carte de stratégie, cliquez sur **applications cibles** pour ouvrir la liste des applications.

3.  Supprimer ou ajouter des applications à partir de la liste et cliquez sur l' **icône d’enregistrement** pour enregistrer vos modifications.

### Pour modifier la liste des groupes d’utilisateurs

1.  Dans la carte de **stratégie d’application** , sélectionnez la stratégie que vous voulez modifier. Cette action ouvre la carte spécifique à la stratégie que vous avez sélectionné.

2.  Dans la carte de stratégie, cliquez sur **groupes d’utilisateurs** pour ouvrir la carte de **groupe d’utilisateurs** qui affiche la liste actuelle des groupes d’utilisateurs qui ont cette stratégie.

3.  Pour **Ajouter un nouveau groupe d’utilisateurs** à la stratégie, cliquez sur **Ajouter un groupe utilisateur**, puis sélectionnez le groupe d’utilisateurs. Choisissez **Sélectionner** pour déployer la stratégie sur le groupe que vous avez sélectionné.

    ![Capture d’écran de la cuillère Ajouter utilisateur groupe avec deux utilisateurs sélectionnés](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  Pour **Supprimer un groupe d’utilisateurs**, mettez en surbrillance le groupe d’utilisateurs que vous voulez supprimer, cliquez sur les points de suspension (...), puis cliquez sur **Supprimer** pour supprimer le groupe d’utilisateurs.

    ![Capture d’écran montrant une option de suppression ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### Pour modifier les paramètres de stratégie

1.  Dans la carte de **stratégie d’application** , sélectionnez la stratégie que vous voulez modifier. Cette action ouvre une carte spécifique à la stratégie que vous venez de sélectionner.

    ![Capture d’écran d’une stratégie existante ouverte dans une carte distincte ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Sélectionnez **paramètres de stratégie** pour ouvrir la carte de **paramètres de la stratégie** .

3.  Modifier les paramètres, puis cliquez sur l' **icône d’enregistrement** pour enregistrer vos modifications.

    ![Capture d’écran de la cuillère de paramètres de stratégie montrant l’enregistrer option de menu en haut](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## Paramètres de stratégie
Pour obtenir la liste complète du paramètre de stratégie pour iOS et Android, sélectionnez une des opérations suivantes :

> [!div class="op_single_selector"]
- [stratégies d’iOS](ios-mam-policy-settings.md)
- [Stratégies Android](android-mam-policy-settings.md)

## Étapes suivantes
[Surveiller l’état de l’utilisateur et conformité](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### Voir aussi
[Expérience utilisateur final MAM activé applications](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md)
