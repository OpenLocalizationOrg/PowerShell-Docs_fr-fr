---
title: "Limiter l’accès aux scénarios d’exemple messagerie | Microsoft Intune"
description: "Quelques exemples de scénarios et comment ils peuvent être implémentés avec accès conditionnel."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 6b4751a67414a0b8a16886070b323a0296eeb829
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès à la messagerie avec Microsoft Intune : exemples de scénarios

## Empêcher les utilisateurs d’accéder à Exchange Online à l’aide de périphériques non conformes.
### Configuration requise de scénario
- Tous les utilisateurs dans le groupe de sécurité Active Directory **Accounting** doivent être bloqués l’accès à Exchange Online si leur appareil n’est pas compatible avec une stratégie de conformité que vous déployé.
- Si tous les utilisateurs existant dans ce groupe dont appareils ne sont pas pris en charge par [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ils doivent être bloqués d’accéder à Exchange Online sur votre appareil.
- Les utilisateurs du groupe de sécurité Active Directory **intérêts** doivent être exemptés de la stratégie, même s’ils sont également dans le groupe de sécurité **Accounting** .

Pour ce faire, configurez une stratégie d’accès conditionnel pour Exchange Online avec les paramètres suivants :

-   Sélectionnez **Activer la stratégie d’accès conditionnelle**.

- Sélectionnez les plateformes que vous voulez autoriser l’accès à partir des applications avec l’authentification moderne.
- Pour les applications Exchange ActiveSync, sélectionnez **bloquer les périphériques non conformes sur les plateformes prises en charge par Microsoft Intune** et **bloquer tous les autres périphériques sur les plateformes non pris en charge par Microsoft Intune.**
-   Dans la section **groupe cibles** , sous **groupes de sécurité sélectionnés** , choisissez le groupe d’utilisateurs **Accounting** .

-   Dans la section **groupe Exempted** , sous **groupes de sécurité sélectionnés** , sélectionnez le groupe d’utilisateurs **Finances** .


Le flux suivant est utilisé pour déterminer quels sont les appareils peuvent accéder à Exchange Online :

![Flux d’accès appareil](./media/ConditionalAccess8-5.png)

## Tous les appareils iOS qui accèdent à Exchange local doivent être gérés par Intune
### Configuration requise de scénario
- Uniquement les appareils exécutant iOS doivent accès autorisés à Exchange en local.
- Les périphériques doivent également être inscrits Intune et respectent les règles de stratégie de conformité avant de pouvoir être utilisés pour accéder à Exchange.

Pour ce faire, configurez la stratégie d’accès conditionnelle suivante pour Exchange en local avec les paramètres suivants :

-   Sélectionnez l’option **empêche les applications de messagerie à partir de l’accès à Exchange local si le périphérique dans non conformes ou non inscrit dans Microsoft Intune**. Lorsque vous sélectionnez cette option, la stratégie d’accès conditionnelle qui requiert que tous les périphériques doivent être inscrits dans Microsoft Intune et respectent les règles de stratégie de conformité avant de pouvoir accéder Exchange est activée.

-   Pour les paramètres avancés Exchange Active Sync, créez a :

  -   Une exception de plateforme qui permet aux périphériques exécutant iOS pour accéder à Exchange.   

  -   Une règle par défaut qui spécifie quand un appareil n’est pas couvert par l’exception de la plateforme de la règle, il doit être bloqué d’accéder à Exchange. Cette règle vérifie que les appareils n'exécutant pas iOS sont bloqués d’accéder à Exchange.

Le flux suivant est utilisé pour déterminer quels sont les appareils peuvent accéder à Exchange :

![Flux d’accès appareil](./media/ConditionalAccess8-3.png)

## Aucun appareils Android ne peuvent accéder à Exchange en local.
### Configuration requise de scénario
- Tous les appareils Android doit bloqué d’accéder à Exchange.
- Tous les autres appareils pris en charge peuvent accéder à Exchange dans la mesure où ils sont gérés par [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Pour ce faire, configurez une stratégie d’accès conditionnel pour Exchange en local avec les paramètres suivants :

-   Sélectionnez l’option **bloquer les applications de messagerie d’accéder à Exchange local si le périphérique est non conforme ou non inscrit dans Microsoft Intune**. Lorsque vous sélectionnez cette option, ils nécessitent de n’importe quel appareil doit être inscrit dans Intune et respecter les règles de stratégie de conformité.

- Pour les paramètres avancés Exchange Active Sync, créez a :
  -   Exceptions de plateforme qui bloque les appareils exécutant Android d’accéder à Exchange. Cette règle vérifie que les appareils Android ne peuvent pas être utilisés pour accéder à Exchange.

  -   Règle par défaut qui spécifie quand un appareil n’est pas traité par d’autres règles, il doit être autorisé à accéder à Exchange. Cette règle par défaut vérifie que les appareils exécutant plateformes différent Android, mais pris en charge par Microsoft Intune peuvent être utilisés pour accéder à Exchange. Ils doivent toutefois être inscrit à Intune et respecter les règles de stratégie de conformité.

Le flux suivant est utilisé pour déterminer quels sont les appareils peuvent accéder à Exchange :

![Flux d’accès appareil](./media/ConditionalAccess8-4.png)
