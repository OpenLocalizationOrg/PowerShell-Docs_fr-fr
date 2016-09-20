---
title: Comment vos utilisateurs iOS obtenir leurs applications | Microsoft Intune
description: "Méthodes pour rendre iOS applications disponibles aux utilisateurs finaux"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: e53a94a9da3162908b9bbb3714d64db917c8174b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Comment vos utilisateurs iOS obtenir leurs applications

Utilisez ces informations pour comprendre où et comment vos utilisateurs finaux obtenir les applications que vous distribuez via Microsoft Intune.

**Applications requises** - applications qui sont requises par l’administrateur et qui sont installés sur l’appareil avec une intervention minimale de l’utilisateur, en fonction de la plateforme.

**Applications disponibles** - applications qui sont fournies dans la liste des applications portail d’entreprise et que l’utilisateur peut vous pouvez également choisir d’installer.

**Applications Managed** - applications pouvant être gérés par le biais des stratégies et qui ont été « encapsulé » par Intune ou ont été créés avec le Kit de développement logiciel (SDK) Intune Mobile Application Management (MAM). Ces applications peuvent être gérées par Intune et les stratégies d’application puissent être appliqués.

**Applications non gérées** - applications qui peuvent être gérés par le biais des stratégies et qui n’ont pas été encapsulé par Intune ou qui n’intègrent pas le Kit de développement MAM Intune. Stratégies d’application ne peut pas être appliqués à ces applications.

Restrictions de Apple interdisent applications du store app-professionnelles et gérées d’être répertoriés dans l’application portail d’entreprise. Pour contourner ce problème, les mosaïques d’applications dans l’application portail d’entreprise pour iOS dirige les utilisateurs vers différents affichages dans un emplacement unique (le site Web portail d’entreprise) pour l’ensemble de leurs applications, comme suit :

- La vignette **d’Applications d’entreprise** précédemment redirigé vers une liste de toutes les applications sous l’onglet tout du [site Web du portail d’entreprise](http://portal.manage.microsoft.com)., et il continue de fonctionner de la même manière. Le nom de la mosaïque a changé à **Toutes les applications**.

- La vignette **d’Autres applications** précédemment vers laquelle pointe un affichage, à l’intérieur de l’application portail d’entreprise, qui répertorie toutes les applications Apple permet à l’application portail d’entreprise à afficher. Le nom de la mosaïque a changé pour **Applications proposées**, puis en cliquant sur la vignette vous permettront d’utilisateurs à l’onglet proposées du site Web portail d’entreprise.

-  La vignette **catégories** précédemment vers laquelle pointe un affichage, à l’intérieur de l’application portail d’entreprise, qui répertorie les catégories d’applications. Le nom de la mosaïque n’a pas changé, mais elle pointe désormais sur l’onglet catégories du site Web portail d’entreprise.
Vous pouvez trouver les mises à jour de captures d’écran [ici](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).



###Voir aussi
[Comment vos utilisateurs Android obtenir leurs applications](how-your-android-users-get-their-apps.md)</br>
[Comment vos utilisateurs Windows obtenir leurs applications](how-your-windows-users-get-their-apps.md)
