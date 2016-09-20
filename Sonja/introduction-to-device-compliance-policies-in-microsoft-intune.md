---
title: "Stratégies de conformité appareil | Microsoft Intune"
description: "Cette rubrique explique les concepts que vous devez comprendre la conformité appareil sont des stratégies et leur fonctionnement."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 476f44df54fbea5c0fcfe8cf0e3ce4a61bd7c0a0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Stratégies de conformité appareil dans Microsoft Intune
## Qu’est une stratégie de conformité ?
Pour protéger les données d’entreprise, vous devez vous assurer que les appareils permettant d’accéder aux applications d’entreprise et les données, répondre à certaines règles comme à l’aide d’un code confidentiel pour accéder à l’appareil et le chiffrement des données stockées sur le périphérique. Un ensemble de ces règles est appelé une stratégie de conformité.

## Comment dois-je utiliser des stratégies de conformité ?
Vous pouvez utiliser des stratégies de conformité avec les stratégies d’accès conditionnel pour autoriser uniquement les appareils conformes aux règles de stratégie de conformité pour accéder aux messages électroniques et autres services. Consultez l’article [restreindre l’accès aux messages électroniques et services Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) pour mieux comprendre comment les deux stratégies peuvent être utilisées ensemble.

Vous pouvez également utiliser des stratégies de conformité indépendamment de celles accès conditionnel. Lorsqu’il est utilisé indépendamment, les appareils ciblées sont évaluées et signalés avec leur état de conformité. Par exemple, vous souhaiterez peut-être état sur le nombre d’unités n’est pas chiffré, ou les périphériques sont jailbroken ou associés à une racine. Cependant, lorsqu’il est utilisé indépendamment, aucune restriction d’accès aux ressources d’entreprise n’est en place.

Déployer des stratégies de conformité aux utilisateurs. Lorsqu’une stratégie de conformité est déployée à un utilisateur, les périphériques de l’utilisateur vérifiés la conformité.

Le tableau suivant répertorie l’appareil types pris en charge par les stratégies de conformité et paramètres comment non conformes sont gérés lorsque la stratégie est utilisée avec une stratégie d’accès conditionnelle.

-----------------------------

|Paramètre de stratégie| Windows 8.1 et versions ultérieures| Windows Phone 8.1 et versions ultérieur| iOS 8.0 et versions ultérieures|Android 4.0 ou version ultérieure<br/>Samsung KNOX Standard 4.0 et versions ultérieur|
|-----|----|----|----|----|
|**Configuration de mot de passe ou code confidentiel** |Convertis|Convertis|Convertis|Mis en quarantaine|
|**Chiffrement de périphériques**|N/A|Convertis|Résolues (en définissant le code confidentiel)|Mis en quarantaine|
|**Jailbroken ou appareil racine**|N/A|N/A|Mis en quarantaine (pas un paramètre)|Mis en quarantaine (pas un paramètre)|
|**Profil de messagerie**|N/A|N/A|Mis en quarantaine|N/A|
|**Version du système d’exploitation minimale**|Mis en quarantaine|Mis en quarantaine|Mis en quarantaine|Mis en quarantaine|
|**Version du système d’exploitation maximale**|Mis en quarantaine| Mis en quarantaine| Mis en quarantaine| Mis en quarantaine|
|**Attestation d’intégrité de Windows**|Windows 10 et Windows 10 Mobile sont mis en quarantaine.<br /><br />Paramètre n’est pas applicable à Windows 8.1|N/A|N/A|N/A|

------------------------------

**Remediated** = conformité est appliquée par le système d’exploitation du périphérique (par exemple, l’utilisateur est obligé de définir un code confidentiel).  Il n’est jamais un cas lorsque le paramètre est non conforme.

**Mis en quarantaine** = le périphérique de système d’exploitation n’applique pas de conformité (par exemple, les appareils Android ne forcez pas l’utilisateur pour chiffrer l’appareil). Lorsque les appareils n’est pas conforme, les actions suivantes se produisent :

-   Le périphérique est bloqué si l’utilisateur est destinée par une stratégie d’accès conditionnelle.

-   Le portail d’entreprise vous avertit de l’utilisateur sur les problèmes de conformité.

## Étapes suivantes
[Créer une stratégie de conformité appareil](create-a-device-compliance-policy-in-microsoft-intune.md)

[Déployer et surveiller une stratégie de conformité appareil](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Voir aussi
[Restreindre l’accès aux messages électroniques et services Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
