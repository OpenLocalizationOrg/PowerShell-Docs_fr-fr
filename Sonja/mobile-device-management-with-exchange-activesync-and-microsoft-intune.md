---
title: Exchange ActiveSync via la gestion | Microsoft Intune
description: "Gestion des appareils mobiles avec la gestion d’Exchange ActiveSync (EAS) à l’aide du connecteur Exchange"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 3e8ca71a8a7011eb4d2e34c61ef869dbf0abe3b7
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gestion des appareils mobiles Exchange ActiveSync avec Microsoft Intune
Pour Microsoft Intune directement gérer les appareils mobiles, périphériques doivent être [inscrit à Intune](get-ready-to-enroll-devices-in-microsoft-intune.md). Comme alternative, les administrateurs peuvent activer une solution plus limitée qui utilise la gestion d’Exchange ActiveSync (EAS) avec un connecteur Exchange. Appareils peuvent être gérés avec les serveurs Exchange en local et Exchange Online à l’aide d’Office 365. Intune prend uniquement en charge une connexion de connecteur Exchange de n’importe quel type par abonnement.

## Règles d’accès Exchange pour les appareils mobiles ##

Exchange a besoin d’un ensemble de règles qui définit que se passe-t-il lorsque vous essaient d’appareils mobiles pour vous connecter à EAS. Les règles suivantes sont gérées dans la console d’administration Intune.

[Règles d’accès Exchange pour les appareils mobiles](exchange-access-rules-for-mobile-devices.md)

## Installer le connecteur Exchange
Le connecteur Exchange vous permet de gérer votre déploiement Exchange dans la console Intune. Vous devez tout d’abord installer et configurer le connecteur Intune vers Exchange approprié. Choisissez l’option appropriée selon si votre serveur Exchange est locale ou hébergée en tant que service dans le cloud :

-   [Configurer la Intune pour Exchange Online ou des environnements Exchange Online dédié](intune-service-to-service-exchange-connector.md)
-   [Installer le connecteur Intune pour les serveurs Exchange en local et les environnements Exchange Online dédié hérités](intune-on-premises-exchange-connector.md)


## Appliquer une stratégie pour des appareils mobiles géré par Exchange
La console Intune peut être utilisée pour gérer les [paramètres de stratégie EAS](exchange-activesync-policy-settings-in-microsoft-intune.md) et limiter [l’accès aux ressources d’entreprise](restrict-access-to-email-and-o365-services-with-microsoft-intune.md). Pour une liste des paramètres de stratégie d’Exchange ActiveSync et fonctionnalités pris en charge par des périphériques mobiles spécifiques, voir le [Tableau de comparaison des clients Exchange ActiveSync](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Une fois connecté Intune à un environnement Microsoft Exchange, la stratégie EAS pour tous les utilisateurs géré tout au long Intune est ramenée à la stratégie par défaut en cours sur le serveur Microsoft Exchange, sauf si vous définissez une stratégie plus spécifique dans Intune.

## Effacer les données d’entreprise à partir d’appareils mobiles
Enfin, vous pouvez [Effacer les données de société à partir d’appareils mobiles gérées EAS](wipe-for-exchange-managed-mobile-devices.md) lorsqu’ils ne sont plus en cours d’utilisation, ou si appareils perte ou de vol.
