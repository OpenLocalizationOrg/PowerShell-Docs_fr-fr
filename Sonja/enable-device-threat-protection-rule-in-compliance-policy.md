---
title: "Activer la règle de protection d’appareil de stratégie de conformité | Microsoft Intune"
description: "Activer la règle de protection de menace mobile dans la stratégie de conformité d’appareil."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: 761372b2c8b81699bc2584ab1ef8d0f9d523abe9
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Activer la règle de protection de menace périphérique dans la stratégie de conformité
Intune avec protection contre les menaces mobiles affût vous donne la possibilité de détecter les menaces mobiles et effectuer une analyse de risque sur l’appareil.  
Règle de stratégie de conformité vous permet d’utiliser cette évaluation des risques pour déterminer si l’appareil est conforme à votre stratégie. Vous pouvez utiliser ensuite la stratégie d’accès conditionnel pour autoriser ou bloquer Exchange, SharePoint et d’autres services en fonction de la conformité appareil.

Pour que la menace de plan de référence affût détection influencer la stratégie de conformité pour l’appareil :

1.  La règle de **Protection contre les menaces appareil** doit être activée sur la stratégie de conformité.

2.  La page **État affût** dans la console d’administration Intune doit indiquer **Active**. Consultez la rubrique [connexion activer le plan de référence affût dans Intune](enable-lookout-mtp-connection-in-intune.md) pour obtenir plus d’informations et des instructions sur la façon d’activer l’intégration d’affût.


## Configurer la règle de protection de menace appareil

Avant de créer la règle de protection de menace périphérique dans la stratégie de conformité, il est recommandé que vous [Définissez votre abonnement avec plan de référence affût](set-up-your-subscription-with-lookout-mtp.md), [activer des connexions affût dans Intune](enable-lookout-mtp-connection-in-intune.md)et [configurer l’affût application de travail](configure-and-deploy-lookout-for-work-apps.md). La règle de conformité est appliquée uniquement une fois la configuration terminée.

Pour activer la règle de protection de menace appareil, vous pouvez utiliser une stratégie de conformité existant ou créez-en un.

Dans le cadre de la configuration du plan de référence affût, dans la [console affût le plan de référence](https://aad.lookout.com), vous avez créé une stratégie qui classe les différentes menaces en niveaux élevés, moyens et faibles. Dans la stratégie de conformité Intune, vous allez utiliser le niveau de menace pour définir le niveau de menace autorisés maximale.

Dans la console administrateur Intune, dans la page de la stratégie de conformité, accédez à **État des périphériques** et activez la règle de **Protection contre les menaces appareil** à l’aide de l’option Activer/désactiver. Sélectionnez le niveau de menace autorisés maximale, qui est une des opérations suivantes :
* **Aucune (sécurisé)**: il s’agit de la plus sûre.  Cela signifie que le périphérique ne peut pas contenir toutes les menaces.  Si l’appareil est détecté comme ayant n’importe quel niveau de menaces, il sera évaluée comme non conformes.  
* **Faible**: appareil est évalué comme conforme si une seule menaces niveau faibles sont présents. Toute valeur au-dessus place le périphérique dans un état irrégulière.
* **Support**: appareil est évalué comme conforme si les menaces qui sont présents sur l’appareil sont niveau faible ou moyen. Si le périphérique est détecté d’avoir menaces niveau élevés, il est déterminé comme irrégulière.
* **Haute**: il s’agit de la moins sûre. Pour l’essentiel, ainsi, tous les menaces niveaux et éventuellement uniquement utile si vous utilisez cette solution uniquement pour les rapports.

![capture d’écran montrant le paramètre de règle de protection de menace appareil dans ](../media/mtp/mtp-compliance-policy-rule.png)

![capture d’écran montrant la menace niveau option pour que le paramètre de règle de protection de menace appareil](../media/mtp/mtp-compliance-policy-setting.png)

Si vous créez des stratégies d’accès conditionnel pour Office 365 et d’autres services, l’évaluation de conformité ci-dessus est prise en considération et périphériques irrégulière sont bloqués accéder jusqu'à ce que le risque est résolu.

Vous pouvez consulter l’état de conformité d’un périphérique dans la page périphériques de la console administrateur Intune.

![capture d’écran de la page de périphériques dans la console d’administration Intune indiquant l’état de conformité d’un appareil](../media/mtp/mtp-device-status-intune-console.png)

## Étapes suivantes
* Créer la stratégie d’accès conditionnel
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype entreprise Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
