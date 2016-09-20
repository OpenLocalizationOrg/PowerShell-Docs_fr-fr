---
title: "Préparez-vous à configurer des stratégies MAM | Microsoft Intune"
description: "Cette rubrique décrit les conditions préalables et le paramétrage des utilisateurs avant de créer l’application mobile stratégies de gestion des."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: aeaa64124384a71126eeca7339416b80d395d07d
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Préparez-vous à configurer des stratégies de gestion de l’application mobile avec Microsoft Intune
Cette rubrique décrit ce que vous devez faire avant de créer des stratégies de gestion des (MAM) de l’application mobile dans le portail Azure.

Le portail Azure est la nouvelle console d’administration pour créer des stratégies MAM. Nous vous recommandons d’utiliser ce portail pour créer des stratégies MAM. Le portail Azure prend en charge les scénarios MAM suivants :
- Appareils inscrit dans Intune
- Appareils qui sont gérés par une solution de la gestion des périphériques tiers
- Appareils mobiles qui ne sont pas gérés par n’importe quelle solution périphériques mobiles (BYOD)

Si vous débutez dans l’aide du portail Azure, consultez la rubrique [Azure portail pour les stratégies de Microsoft Intune MAM](azure-portal-for-microsoft-intune-mam-policies.md) pour obtenir un aperçu rapide.

>[!IMPORTANT]

> Si vous utilisez actuellement la console d’administration Intune pour gérer vos périphériques, vous pouvez créer des stratégies MAM qui prennent en charge des applications pour appareils mobiles inscrits dans Intune à l’aide de la console d’administration Intune. Mais nous vous recommandons d’utiliser le portail Azure, même pour les appareils que vous êtes inscrit à Intune. Pour obtenir des instructions sur la façon de créer une stratégie MAM à l’aide de la console d’administration Intune, voir [configurer et déployer des stratégies de gestion des applications mobiles dans la console Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Vous voyiez pas tous les paramètres de stratégie MAM dans la console d’administration Intune. Si vous créez des stratégies MAM dans la console d’administration Intune et le portail Azure, la stratégie dans le portail Azure est appliquée aux applications et déployée vers des utilisateurs.
> Stratégies MAM créés dans la console d’administration Intune ne peuvent pas être importées dans le portail Azure.  Les stratégies MAM doivent être recréées dans le portail Azure.


##  Plateformes prises en charge
- iOS 8.1 ou version ultérieure

- Android 4 ou version ultérieure

Appareils Windows ne sont actuellement pas pris en charge.
##  Applications pris en charge
* **Applications Microsoft :** Ces applications ont le Kit de développement logiciel intégré l’application Intune et n’exigent aucune un traitement approfondi avant d’appliquer des stratégies de MAM.
Pour afficher la liste complète des applications Microsoft pris en charge, accédez à la [Galerie des applications mobiles Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) sur la page partenaires d’application Intune Microsoft. Cliquez sur une application pour afficher les plateformes et les scénarios pris en charge et que l’application prend en charge plusieurs identités.
* **Applications du secteur d’activité de votre organisation :** Ces nécessitent préparer les applications pour inclure le SDK application Intune avant d’appliquer des stratégies MAM.

  * Pour les périphériques qui sont gérés par Intune, voir [déterminer comment préparer les applications pour MAM](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).
  * Pour les périphériques qui ne sont pas gérés (par exemple, périphériques appartenant à l’employé), ou pour ceux qui est gérés par une solution de gestion des périphériques mobiles tiers, voir [protéger métier des applications et des données sur les appareils ne pas inscrits dans Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

*Avant de* vous pouvez configurer des stratégies MAM, vous devez les éléments suivants :

-   Un abonnement à Microsoft Intune.    Les utilisateurs doivent [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] des licences pour obtenir des applications ayant des stratégies MAM.

-   Un abonnement Office 365, qui est requis pour les éléments suivants :
  - Pour appliquer des stratégies MAM aux applications avec prise en charge plusieurs identités.
  - Pour créer des comptes de travail SharePoint Online et Exchange Online. Exchange local et SharePoint localement ne sont pas pris en charge.
-   Skype pour le programme d’installation entreprise Online pour l’authentification moderne. Pour plus d’informations, voir [Activer l’authentification moderne](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (AD Azure) pour créer des utilisateurs. Azure AD authentifie les utilisateurs lorsqu’ils ouvrez l’application et entrez les informations d’identification de leurs travail.

    > [!NOTE]
    > Si vous configurez les utilisateurs à l’aide de la [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] console, n’oubliez pas que la configuration de la stratégie MAM se déplace vers le portail Azure. Pour utiliser ce portail, vous devez configurer les groupes d’utilisateurs Azure AD à l’aide du portail Office 365.


## Créer des utilisateurs et attribuer des licences Microsoft Intune

1. Vérifiez que vous avez un abonnement Intune. Vous disposez déjà d’un [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] abonnement si vous utilisez actuellement [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pour gérer vos périphériques.  Vous disposez également d’un [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] abonnement si vous avez acheté une licence entreprise mobilité Suite (EMS). Si vous essayez de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pour extraire les fonctionnalités MAM, vous pouvez obtenir un compte d’évaluation sur la [page Web Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/).

    Pour vérifier si vous disposez d’un [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] abonnement, dans le portail Office, accédez à la page **facturation** .  Vous devriez voir [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] comme **actif** dans les abonnements.

2.  Connectez-vous au [portail Office](http://portal.office.com) avec vos informations d’identification d’administration.

3.  Accédez à la page **Utilisateurs actifs** pour ajouter des utilisateurs et attribuer [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] des licences.

    ![Page utilisateurs actif dans le portail Office](../media/AppManagement/OfficePortal_AddUsers.png)

    ![Modifier la page de l’utilisateur dans le portail Office](../media/AppManagement/OfficePortal_AssignLicenses.png)

4.  Pour permettre à un utilisateur pour accéder au bureau portail, le portail Azure AD et le portail Azure, attribuer le rôle **d’administrateur Global** à l’utilisateur.

    ![Page de modification des rôles d’utilisateur dans le portail Office](../media/AppManagement/OfficePortal_AddRoletoUser.png)

5.  Stratégies MAM sont déployés sur les groupes d’utilisateurs dans Azure Active Directory. Pour créer des groupes d’utilisateurs pour vos stratégies MAM, accédez à la page **groupes** dans le portail Office et choisissez l' **option Ajouter un groupe** dans le menu supérieur pour créer un nouveau groupe de sécurité.  Tapez un nom et une description, puis cliquez sur **créer**. Lorsque le groupe est créé, vous pouvez ajouter des utilisateurs au groupe en cliquant sur **Modifier les membres**. Le groupe de sécurité est créé dans Azure Active Directory.

    ![Page groupes de sécurité sur le portail Office](../media/AppManagement/OfficePortal_CreateGroups.png)

Le tableau suivant répertorie les rôles et les autorisations que vous pouvez affecter aux utilisateurs d’administration.

|||
|--|----|
|**Rôle**|**Autorisations**|
|Administrateur global (portail Office 365)|Accès au portail Office 365 et le portail Azure AD.<br /><br />Accéder au portail Azure (peuvent effectuer la gestion des rôles et application mobile gestion des tâches).|
|Propriétaire (Azure portal)|Accéder au portail Azure (peuvent effectuer la gestion des rôles et application mobile gestion des tâches).|
|Collaboration (Azure portal)|Accéder au portail Azure (peuvent effectuer uniquement l’application mobile gestion des tâches).|

## Attribuer le rôle de collaborateur à un utilisateur

Les administrateurs globaux ont accès au [portail Azure](https://portal.azure.com).  Si vous souhaitez que d’autres utilisateurs d’administration pour pouvoir configurer des stratégies et effectuer d’autres tâches de gestion de l’application mobile, vous pouvez attribuer le rôle de collaborateur aux utilisateurs :


1.  Dans la carte de **paramètres** , dans la section **Gestion des ressources** , cliquez sur **utilisateurs**.

    ![Carte d’utilisateurs dans le portail Azure](../media/AppManagement/AzurePortal_MAM_AddUsers.png)

2.  Cliquez sur **Ajouter** pour ouvrir la carte **Ajouter access** .

3.  Cliquez sur **Sélectionner un rôle**, puis cliquez sur **collaborateur**.

    ![Sélectionnez un onglet de rôle dans le portail Azure](../media/AppManagement/AzurePortal_MAM_AddRole.png)

4.  Cliquez sur **Ajouter un utilisateur**et recherchez l’utilisateur par nom ou adresse de messagerie. Les utilisateurs que vous voyez dans cette liste sont les 1 000 premiers utilisateurs que vous avez créée précédemment dans Azure Active Directory à l’aide du portail Office. Cliquez sur **OK** dans la carte **Ajouter access** pour enregistrer et attribuer le rôle à l’utilisateur.

    ![Ajouter la carte d’utilisateurs dans le portail Azure](../media/AppManagement/AzurePortal_MAM_AddusertoRole.png)

    > [!IMPORTANT]
    > Si vous sélectionnez un utilisateur ne disposant pas un [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] licence, ils ne seront pas en mesure d’accéder au portail.

## Étapes suivantes
[Créer et déployer des stratégies de gestion de l’application mobile avec Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
