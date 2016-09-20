---
title: "Personnaliser les vues console de rôles d’administrateur | Microsoft Intune"
description: "Utilisez cette rubrique pour vous aider à filtrer l’affichage de la console d’administration Intune pour autoriser vos administrateurs afficher uniquement les éléments que dont elles ont besoin pour leur rôle."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 1059aae1c90e3623201281d4cf14d9db442e3f20
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Personnaliser les affichages de la console Intune en fonction des rôles d’administrateur
Vous pouvez filtrer la Microsoft Intune administration de la vue de la console pour autoriser vos administrateurs afficher uniquement les éléments que dont elles ont besoin pour leur rôle. Par exemple, vous pouvez autoriser uniquement les opérateurs de console d’administration mettre à jour des définitions de programme malveillant ou mot de passe sur les appareils. Pour cela, à l’aide des **dénomination** prédéfinis que vous attribuez à des utilisateurs spécifiques. Lorsque ces utilisateurs accèdent à la console d’administration, ils peuvent uniquement afficher les éléments qui sont spécifiques à leur désignation.

## Pour créer un affichage personnalisé

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **administrateur** &gt; **Les administrateurs de Service**.

2.  Dans la liste des administrateurs de service, sélectionnez l’utilisateur dont la désignation que vous voulez modifier et cliquez sur **Gérer l’accès**.

3.  Dans la boîte de dialogue **Gérer l’accès** , choisissez le niveau d’accès que vous souhaitez donner à l’utilisateur sélectionné. Vous pouvez choisir :

    -   **Accès complet**
    -   **Accès en lecture seule**
    -   **Support technique - nœud de groupes**

    Un accès total et accès en lecture seule sont explicites. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    **Support technique - nœud groupes** restreint que l’administrateur peut voir et procédez comme suit :

    -   Afficher des listes des utilisateurs et des appareils mobiles. L’administrateur ne peut pas utiliser des filtres pour modifier l’affichage. Toutefois, vous pouvez utiliser le filtrage des groupes pour modifier ce que l’administrateur peut afficher. Pour plus d’informations, voir [utiliser des groupes pour gérer les utilisateurs et dispositifs avec Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Imprimer la liste des utilisateurs et des appareils mobiles

    -   Exporter la liste des utilisateurs et dispositifs

    -   Afficher les propriétés d’un utilisateur ou un appareil

    -   Effectuer les tâches à distance suivantes :

        -   Exécuter une analyse complète contre les logiciels malveillants

        -   Exécuter une analyse des programmes malveillants rapide

        -   Redémarrer l’ordinateur

        -   Mettre à jour les définitions de programmes malveillants

        -   Actualiser les stratégies

        -   Actualiser le stock

        -   Verrouiller un appareil à distance

        -   Réinitialiser un code secret

Lorsque l’administrateur que vous avez configuré suivant ouvre la console d’administration Intune, il seront attribué le niveau d’accès que vous avez désigné.
