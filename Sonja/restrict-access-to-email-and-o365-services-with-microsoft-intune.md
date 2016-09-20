---
title: "Restreindre l’accès aux messages électroniques et services Office 365 | Microsoft Intune"
description: "Cette rubrique décrit comment conditionnelle peut être utilisée pour permettre périphériques uniquement compatibles pour accéder aux entreprise données de messagerie et société sur SharePoint Online et d’autres services."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 9e64ab7f9955f72e9d47a0282820ebdcba0db00b
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès à la messagerie Office 365 et d’autres services avec Microsoft Intune
Vous pouvez limiter l’accès à votre messagerie d’entreprise et les services Office 365 avec accès conditionnel de Intune. Accès conditionnel fonctionnalité de Intune vous permet de s’assurer que l’accès à votre messagerie d’entreprise et services Office 365 est limitée aux appareils compatibles avec les règles que vous avez défini.
## Fonctionnement de l’accès conditionnel
Paramètres de stratégie de conformité sont utilisées pour évaluer la conformité de l’appareil. Stratégie d’accès conditionnelle utilise l’évaluation pour restreindre ou autoriser l’accès à un service spécifique. Lorsqu’une stratégie d’accès conditionnelle est utilisée en combinaison avec une stratégie de conformité, seuls les périphériques conformes pourront pour accéder au service. La stratégie de conformité et la stratégie d’accès conditionnelle sont déployés à l’utilisateur. N’importe quel appareil qui utilise l’utilisateur à accéder aux services est activé pour la conformité avec les stratégies.

N’oubliez pas que l’utilisateur qui est à l’aide de l’appareil doit avoir une stratégie de conformité déployée leur afin que l’appareil doit être évaluée pour la conformité.
Si aucune stratégie de conformité n’est déployé à l’utilisateur le périphérique est considéré comme conformes et aucune restriction d’accès n’est appliquée.

Lorsque appareils ne remplissent pas les conditions définies dans les stratégies, l’utilisateur final est guidé bien que le processus d’inscription de l’appareil et de résoudre le problème qui empêche l’appareil compatible.

Un flux typique d’accès conditionnel :

![Le diagramme indique les points de décision utilisées pour déterminer si un appareil est autorisé à accéder à un service ou est bloqué](../media/ConditionalAccess4.png)

## Comment configurer l’accès conditionnelle ?
Accès conditionnel permet de gérer l’accès à Microsoft **Exchange en local**, **Exchange Online**, **Exchange Online dédié**, **SharePoint Online** et **Skype entreprise Online**.

Pour configurer l’accès conditionnelle, configurez une stratégie de conformité d’appareil et une stratégie d’accès conditionnelle.

La stratégie de conformité comprend des paramètres tels que le code secret, du chiffrement et ou non un périphérique est jailbroken. L’appareil doit respecter les règles suivantes pour être considéré comme compatible.

Vous pouvez définir une stratégie d’accès conditionnelle limiter l’accès basé sur :
- L’état de conformité appareil.
- La plateforme en cours d’exécution sur l’appareil.
- Le type d’applications utilisées pour accéder aux services.

Contrairement aux autres stratégies Intune, vous ne déployez pas les stratégies d’accès conditionnelle. Au lieu de cela, une fois que vous configurez la stratégie et sélectionnez les utilisateurs qui sont autorisés à la stratégie, la stratégie est appliquée à tous les utilisateurs cibles. Lorsqu’un utilisateur est ciblé par une stratégie, chaque périphérique qu’ils utilisent doit être conforme afin d’accéder à des ressources.


## Étapes suivantes
1. [En savoir plus sur la stratégie de conformité appareil et son fonctionnement ](introduction-to-device-compliance-policies-in-microsoft-intune.md)

2. [Créer une stratégie de conformité](create-a-device-compliance-policy-in-microsoft-intune.md)

2.  Créer une stratégie d’accès conditionnel pour une des opérations suivantes :
> [!div class="op_single_selector"]
  - [Créer une stratégie d’accès conditionnel pour Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Créer une stratégie d’accès conditionnel pour Exchange en local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Créer une stratégie d’accès conditionnel pour nouveau Exchange Online dédié](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Créer une stratégie d’accès conditionnel pour héritées Exchange Online dédié](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Créer la stratégie d’accès conditionnel pour SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Créer la stratégie d’accès conditionnel pour Skype entreprise Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Créer la stratégie d’accès conditionnel pour Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
