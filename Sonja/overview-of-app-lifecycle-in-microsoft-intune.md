---
title: "Vue d’ensemble du cycle de vie application | Microsoft Intune"
description: "En savoir plus sur le cycle de vie des applications Intune géré, à partir de l’ajout, leur déclassement éventuelle."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: c93efd43a85c8046c7cfd6aa8341352b75ab0cfd
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Vue d’ensemble du cycle de vie application

Le cycle de vie de l’application Intune commence lorsqu’une application est ajoutée et progresse dans les phases supplémentaires jusqu'à ce que vous supprimer l’application.

![Le cycle de vie d’application](./media/app-lifecycle.png "the Intune app lifecycle")

## Ajouter

La première étape pour le déploiement des applications consiste à ajouter les applications que vous voulez gérer et déployer au Intune. Pendant que vous pouvez travailler avec de nombreux types différents d’application, les procédures de base sont identiques. Avec Intune, vous pouvez ajouter des applications pour à la fois [inscrit appareils](add-apps-for-mobile-devices-in-microsoft-intune.md) et [ordinateurs Windows que vous gérez avec le logiciel client Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## Déployer

Une fois que vous avez ajouté l’application à Intune, vous pouvez ensuite [déployer sur les appareils que vous gérez](deploy-apps.md). Intune facilite ce processus, et une fois l’application est déployée, vous pouvez [surveiller la réussite](monitor-apps-in-microsoft-intune.md) du déploiement à partir de la console d’administration Intune. En outre, dans certaines application banques, tels [Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md) et [Windows](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md) application, vous pouvez acheter des licences d’application en bloc pour votre société. Intune peut synchroniser des données avec ces banques de sorte que vous pouvez déployer et le suivi de l’utilisation des licences pour ces types d’applications vers la droite de la console d’administration Intune.

## Configurer

Dans le cadre du cycle de vie application, de nouvelles versions des applications sont régulièrement publiées. Intune fournit des outils à facilement [mettre à jour les applications](update-apps-using-microsoft-intune.md) que vous avez déployée vers une version plus récente. En outre, vous pouvez configurer des fonctionnalités supplémentaires pour certaines applications, par exemple :
- [stratégies de configuration d’application iOS](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md) approvisionnement paramètres pour les applications compatibles iOS qui sont utilisées lorsque l’application est exécutée. Par exemple, une application peut nécessiter des paramètres de personnalisation spécifiques ou le nom d’un serveur pour vous connecter à.
- [Gestion des stratégies de navigateur](manage-internet-access-using-managed-browser-policies.md) vous aider à configurer les paramètres pour le navigateur géré Intune, qui remplace le navigateur par défaut de l’appareil et vous permet de limiter les sites Web que vos utilisateurs peuvent visiter.

## Protéger

Intune offre de nombreuses façons de protéger les données dans vos applications. Les principales méthodes sont :
- [Accès conditionnel](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) contrôle l’accès à la messagerie et autres services en fonction de conditions que vous spécifiez. Conditions incluent les types d’appareils ou la conformité avec une [stratégie de conformité appareil](introduction-to-device-compliance-policies-in-microsoft-intune.md) que vous avez déployée.
- [Gestion des applications mobiles (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) fonctionne avec les applications individuelles à protéger les données d’entreprise qu’ils utilisent. Par exemple, vous pouvez limiter la copie des données entre les applications non gérées et applications que vous gérez, ou vous pouvez empêcher des applications de s’exécuter sur les périphériques qui ont été jailbroken ou associés à une racine.

## Retirer

Enfin, il est probable que les applications que vous avez déployée deviennent obsolètes et doivent être supprimés. Intune facilite le point de [Supprimer des applications de service](retire-apps-using-microsoft-intune.md).
