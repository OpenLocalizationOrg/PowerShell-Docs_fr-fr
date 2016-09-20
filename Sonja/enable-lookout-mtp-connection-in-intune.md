---
title: "Activer le plan de référence dans Intune affût | Microsoft Intune"
description: "Activer la protection de menace mobile affût dans la console d’administration Intune."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: 4ae7d6c571f69c0cc51dc15355e50325afb88694
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Activer le plan de référence affût de connexion dans la console d’administration Intune
Cette rubrique vous montre comment activer la connexion au plan de référence affût dans Intune. Vous devez avoir configuré le connecteur Intune dans la console de plan de référence affût avant d’effectuer cette étape.  Si vous ne le n'avez pas déjà fait, effectuez les étapes décrites dans le [jeu de votre abonnement avec protection contre les menaces mobiles affût](set-up-your-subscription-with-lookout-mtp.md).

Pour activer le plan de référence affût connexion dans Intune, dans la page **Administration** de la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **L’intégration de Service tiers**. Choisissez **le statut affût** et activer **la synchronisation avec le plan de référence** à l’aide du bouton bascule.

![capture d’écran de la page de synchronisation affût avec le bouton bascule Activer mis en surbrillance](../media/mtp/lookout-intune-synchronization.png)

Le programme d’installation de l’intégration affût et Intune dans la console administrateur Intune est terminée.  Les étapes suivantes pour mettre en œuvre cette solution impliquent le déploiement l' [affût pour les applications de travail](configure-and-deploy-lookout-for-work-apps.md) et la configuration de la stratégie de [conformité](enable-device-threat-protection-rule-in-compliance-policy.md) .

>[!IMPORTANT]
> Vous **devez** configurer l’affût application travail avant de créer des règles de stratégie de conformité et la configuration d’accès conditionnel. Ainsi que l’application est prêt et disponible pour les utilisateurs finaux d’installer avant qu’elles puissent accéder accès à la messagerie électronique ou d’autres ressources d’entreprise.
## Étapes suivantes
[Configurer affût application de travail ](configure-and-deploy-lookout-for-work-apps.md)
