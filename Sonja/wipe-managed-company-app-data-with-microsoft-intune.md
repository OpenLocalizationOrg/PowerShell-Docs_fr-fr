---
title: "Effacer les données d’application société gérées | Microsoft Intune"
description: "Découvrez comment vous pouvez sélectivement supprimer les données d’entreprise à partir d’appareils à distance."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 111cfe66e3ee6d9238bb885e3be4025a24811369
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Effacer les données d’application entreprise géré avec Microsoft Intune
Lorsqu’un appareil est perte ou de vol, ou si l’employé quitte votre entreprise, vous voulez définir comme que données d’application entreprise sont supprimées de l’appareil. Toutefois, il est possible que pas voulez-vous supprimer les données personnelles sur l’appareil, particulièrement s’il s’agit d’un employé appartenant appareil.

Pour supprimer sélectivement des données de l’application de société, créez une demande de réinitialisation en suivant les étapes décrites dans cette section **créer une demande de réinitialisation** dans cette rubrique.  Une fois terminée la demande, la prochaine fois que l’application s’exécute sur l’appareil, les données d’entreprise sont supprimées de l’application.
>[!NOTE]
> Contacts synchronisés directement à partir de l’application avec le carnet d’adresses natif sont supprimés. Tous les contacts synchronisés du carnet d’adresses native avec une autre source externe ne peut pas être nettoyés. Actuellement cela s’applique uniquement à l’application Microsoft Outlook.



## Créer une demande de réinitialisation

1.  Dans la carte de **Gestion des applications Intune Mobile** , sélectionnez la vignette **demandes à distance** .

    ![Capture d’écran de Intune carte de gestion des applications mobiles avec résumé vignette](../media/AppManagement/AzurePortal_MAM_WipeRequests.png)

2.  Cliquez sur **nouveau à distance demandes**.

    ![Capture d’écran de la nouvelle carte demande à distance](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

3.  Dans la carte de **nouveau à distance demande** , sélectionnez **utilisateur** pour ouvrir la carte **utilisateur** et sélectionnez l’utilisateur dont vous souhaitez effacer les données de l’application.

4.  Sélectionnez **l’appareil**.  Cette action ouvre la carte **appareil** qui répertorie tous les appareils associés à l’utilisateur sélectionné.  Sélectionnez le périphérique que vous voulez réinitialiser.

5.  Vous êtes maintenant dans la carte de **nouveau à distance demande** . Cliquez sur **Ok** pour effectuer une demande de réinitialisation. Le service crée et suit une demande de réinitialisation distincte pour chaque application protégée sur l’appareil.


![Capture d’écran de la réinitialisation demande vignette ](../media/AppManagement/AzurePortal_MAM_WipeRequestsSummary.png)

## Surveiller vos demandes de réinitialisation
La carte de **Gestion des applications mobiles Intune** dispose d’un rapport de synthèse sur la vignette **demande à distance** .  Il affiche le statut général et comporte le nombre de demandes en attente et échecs. Vous pouvez obtenir plus de détails en suivant les étapes décrites ci-dessous :

1.  Dans la carte de **Gestion des applications mobiles Intune** , sélectionnez la vignette **demande à distance** pour ouvrir la carte **demande à distance** .

2.  Dans la carte **demande à distance** , vous pouvez voir la liste de vos demandes regroupés par les utilisateurs.  Étant donné que le système crée une demande de réinitialisation pour chaque application protégée en cours d’exécution sur l’appareil, vous pouvez voir plusieurs requêtes d’un utilisateur.  L’état indique si une demande de réinitialisation est toujours **en attente**, **a échoué**ou **réussi**.

### Voir aussi
[Protéger les données d’application à l’aide de stratégies de gestion de l’application mobile ](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[À l’aide du portail Azure](azure-portal-for-microsoft-intune-mam-policies.md)
