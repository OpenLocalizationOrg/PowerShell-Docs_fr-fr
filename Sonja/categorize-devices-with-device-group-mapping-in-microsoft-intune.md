---
title: Classer les volumes de mappage de groupe appareil | Microsoft Intune
description: "Utiliser le mappage de groupe d’appareil Microsoft Intune pour regrouper les périphériques en catégories que vous définissez, afin de pouvoir modifier plus facile à gérer les appareils mobiles."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
ms.openlocfilehash: ad63978de4b9fdcacc0046fc05202ac7d7e5edd6
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Classer les volumes de mappage de groupe de périphériques dans Microsoft Intune
Utilisez Microsoft Intune **mappage de groupe appareil** pour regrouper les périphériques en catégories que vous définissez, afin de pouvoir modifier plus facile à gérer les appareils mobiles. 

Mappage de groupe appareil utilise le flux de travail suivant :
1. Vous créez Intune appareil groupes pour chaque catégorie que vous voulez utiliser.
2. Vous configurez appareil groupe mappage des règles qui établir une correspondance entre la catégorie que vous sélectionnez le groupe de l’appareil que vous avez créé.
3. Lorsque les utilisateurs finaux inscrire leur appareil, vous devez sélectionner une catégorie dans les catégories que vous avez configuré. Après leur choisissent, leur appareil est automatiquement ajoutée au groupe d’appareil correspondant que vous avez créé.
4. Vous pouvez alors utiliser ces groupes appareil lorsque vous déployez des applications et des stratégies.

Exemples de catégories peuvent être :
* Personnel
* Point d’appareil de vente
* Appareil de démonstration
* Ventes
* Comptabilité
* Gestionnaire

Toutefois, vous pouvez configurer les catégories que vous voulez.

## Comment faire pour configurer le mappage de groupe appareil
1. Pour chaque catégorie de périphérique que vous souhaitez utiliser, créez un groupe de périphériques Intune. Pour plus d’informations sur la création de groupes, voir [utiliser des groupes pour gérer les utilisateurs et dispositifs avec Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **administrateur**.
3. Dans l’espace de travail **Administration** , développez **Gestion des appareils mobiles**et puis cliquez sur **Le mappage de groupe appareil**.
4. Dans la page **Mappage de groupe appareil** , activer le mappage de groupe appareil.
5. Cliquez sur **Ajouter** pour créer une nouvelle règle de mise en correspondance.
6. Dans la boîte de dialogue **Ajouter une règle mappage groupe appareil** , entrez le nom de la catégorie que vous voulez créer, puis dans la liste déroulante, sélectionnez la collection de périphérique que vous voulez mapper cette catégorie à. Cliquez sur **Ajouter** lorsque vous avez terminé.
7. Lorsque vous avez terminé d’ajouter des catégories et groupes, cliquez sur **Enregistrer**.

À présent, lorsque les utilisateurs inscrire leur appareil, ils seront affiche avec une liste des catégories que vous avez configuré. Une fois qu’ils, choisissez une catégorie et de fin d’inscription, leur appareil est ajouté au groupe d’appareil qui correspond à la catégorie qu'ils ont choisi.

### Voir aussi
[Utiliser des groupes pour gérer les utilisateurs et dispositifs avec Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)