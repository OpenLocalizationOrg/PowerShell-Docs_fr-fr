---
title: "Paramètres de stratégie de mise à niveau de Windows edition | Microsoft Intune"
description: "Découvrez comment mettre automatiquement à jour les appareils Windows 10 vers la dernière version avec Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 45130e3e12968d9df579a7a9d0cade0343b7c165
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Windows Édition mettre à niveau les paramètres de stratégie dans Microsoft Intune
La **Stratégie de mise à niveau d’édition** de Microsoft Intune vous permet de mettre automatiquement à jour les appareils que vous exécutent une des versions suivantes de Windows 10 vers une version plus récente :
* Bureau Windows 10
* Windows 10 HOLOGRAPHIQUE
* Windows 10 Mobile

## Avant de commencer
Avant de commencer à mettre à niveau des périphériques vers la dernière version, vous devez une des opérations suivantes :
* Une clé de produit valide pour installer la nouvelle version de Windows sur tous les appareils que vous ciblez avec la stratégie de (pour les versions Windows 10 bureau). Vous pouvez utiliser les touches clés d’Activation Multiple (MAK) ou serveur de gestion de clés (KMS).
**or** Un fichier de licence de Microsoft contenant les informations de licence pour installer la nouvelle version de Windows sur tous les appareils que vous ciblez avec la stratégie de (pour les éditions Windows 10 Mobile et HOLOGRAPHIQUE Windows 10).
* Les appareils Windows 10 vous urbain doivent être inscrit à Microsoft Intune. Vous ne pouvez pas utiliser la stratégie de mise à niveau d’édition avec des PC qui exécutent le logiciel client Intune PC.

## Paramètres de stratégie de mise à niveau d’édition

|Nom du paramètre|Plus d’informations|
|-|-|
|**Nom**|Entrez un nom pour la stratégie de mise à niveau d’édition.|
|**Description**|Si vous le souhaitez, entrez une description pour la stratégie qui vous aidera à identifier dans la console Intune.
|**Édition mise à niveau vers**|Dans la liste déroulante, sélectionnez la version de Windows 10 bureau, HOLOGRAPHIQUE Windows 10 ou Windows 10 Mobile que vous souhaitez mettre à niveau les appareils pour.
|**Clé de produit**|Spécifiez la clé de produit que vous avez obtenu auprès de Microsoft, qui peut servir à mettre à niveau toutes destinée aux appareils de bureau de Windows 10.<br>Après avoir créé une stratégie qui contient une clé de produit, vous ne pouvez pas modifier la clé de produit ultérieurement. C’est parce que la clé est masquée pour des raisons de sécurité. Pour modifier la clé de produit, vous devez entrer à nouveau la totalité de la clé.
|**Fichier de licence**|Cliquez sur **Parcourir** pour sélectionner le fichier de licence que vous avez obtenu auprès de Microsoft contenant les informations de licence pour la HOLOGRAPHIQUE Windows ou Édition Windows 10 Mobile que vous souhaitez mettre à niveau les appareils pour.

### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
