---
title: Comment vos utilisateurs Android obtenir leurs applications | Microsoft Intune
description: "Méthodes pour rendre les applications Android disponibles aux utilisateurs finaux"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: d34bdc9839ea7785a429bc70cba15cc85da56ee1
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Comment vos utilisateurs Android obtenir leurs applications
Utilisez ces informations pour comprendre où et comment vos utilisateurs finaux Android obtenir les applications que vous distribuez via Microsoft Intune. Les informations peuvent être différentes pour les appareils Android natifs par rapport aux appareils Samsung Knox.

## Appareils Android natif (non Samsung Knox)

| Type d’application | Applications de métier (professionnelle) | Applications du Store de lecture  |
| ------------- |-------------| -----|
| Applications disponibles      | Utilisateurs appuyez sur **installer** dans le portail d’entreprise. Une notification s’affiche, les utilisateurs puis appuyez sur pour démarrer l’installation. Une fois l’installation terminée, la notification disparaît. | Les utilisateurs appuyez sur l’application dans le portail d’entreprise et redirigés vers une page d’application dans le Play Store, où qu’ils puissent commencer l’installation.|
| Applications requises      | Les utilisateurs sont représentées une notification, ils ne peuvent pas faire disparaître, indiquant qu’ils doivent installer une application. Utilisateurs appuyez sur la notification pour démarrer l’installation. Une fois l’installation terminée, la notification disparaît.    | Les utilisateurs sont représentées une notification, ils ne peuvent pas faire disparaître, indiquant qu’ils doivent installer une application. Utilisateurs, appuyez sur la notification et redirigés vers une page d’application dans le Play Store, où qu’ils puissent commencer l’installation. Une fois l’installation terminée, la notification disparaît. |

## Appareils Samsung Knox Android

| Type d’application | Applications de métier (professionnelle) | Applications du Store de lecture  |
| ------------- |-------------| -----|
| Applications disponibles      | Utilisateurs appuyez sur **installer** dans le portail d’entreprise. L’application s’installe sans autre intervention de l’utilisateur. | Les utilisateurs appuyez sur l’application dans le portail d’entreprise et redirigés vers une page d’application dans le Play Store, où qu’ils puissent commencer l’installation.|
| Applications requises      | L’application est installée sans action de l’utilisateur.    | Les utilisateurs sont représentées une notification, ils ne peuvent pas faire disparaître, indiquant qu’ils doivent installer une application. Utilisateurs, appuyez sur la notification et redirigés vers une page d’application dans le Play Store, où qu’ils puissent commencer l’installation. Une fois l’installation terminée, la notification disparaît. |

Applications peuvent être gérées ou non gérées, comme décrit ci-dessous. Le processus de fabrication d’applications gérées est identique pour tous les types d’appareils Android.

**Applications Managed** - applications pouvant être gérés par le biais des stratégies et qui ont été « encapsulé » par Intune ou ont été créés avec le Kit de développement logiciel (SDK) Intune Mobile Application Management (MAM). Ces applications peuvent être gérées par Intune et les stratégies d’application puissent être appliqués.

**Applications non gérées** - applications qui peuvent être gérés par le biais des stratégies et qui n’ont pas été encapsulé par Intune ou qui n’intègrent pas le Kit de développement MAM Intune. Stratégies d’application ne peut pas être appliqués à ces applications.

### Voir aussi
[Ajouter des applications avec Microsoft Intune](/intune/deploy-use/add-apps)
[comment vos utilisateurs iOS obtenir leurs applications](how-your-ios-users-get-their-apps.md)
[comment vos utilisateurs Windows obtenir leurs applications](how-your-windows-users-get-their-apps.md)
