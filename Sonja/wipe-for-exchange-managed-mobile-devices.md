---
title: "Réinitialisation pour les appareils mobiles Exchange géré | Microsoft Intune"
description: "Microsoft Intune vous permet de réinitialiser ou de réinitialiser des appareils mobiles qui sont gérés à l’aide d’Exchange ActiveSync (EAS) avec le connecteur Exchange Intune"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ms.reviewer: lancecra
ms.suite: ems
ms.openlocfilehash: 9d16bc6a4c68fbc06691538b4896676ae17ac7a2
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Réinitialisation pour des appareils mobiles géré par Exchange
Microsoft Intune vous permet de réinitialiser ou de réinitialiser des appareils mobiles qui sont gérés à l’aide d’Exchange ActiveSync (EAS) avec le connecteur Exchange Intune. Le tableau suivant décrit les fonctionnalités de déclassement/réinitialisation disponibles via Exchange ActiveSync :

|Type de transition|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|Réinitialisation complète|Supprime de messagerie compte et messagerie mis en cache|Supprime de messagerie compte et messagerie mis en cache|Usine par défaut|Usine par défaut|Usine par défaut|
|Réinitialisation sélective et de messagerie|Compte de messagerie supprime|Compte de messagerie supprime|Non pris en charge|Non pris en charge|Non pris en charge|
|Réinitialisation sélectives/stratégies|L’application des stratégies supprimé, mais pas ces paramètres sont modifiés|L’application des stratégies supprimé, mais pas ces paramètres sont modifiés|L’application des stratégies supprimé, mais pas ces paramètres sont modifiés|L’application des stratégies supprimé, mais pas ces paramètres sont modifiés|L’application des stratégies supprimé, mais pas ces paramètres sont modifiés|
