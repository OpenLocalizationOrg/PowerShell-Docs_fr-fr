---
title: "Termes et les paramètres de stratégie condition | Microsoft Intune"
description: "Vous pouvez déployer Intune termes et conditions aux groupes d’utilisateurs afin d’expliquer comment accéder à des ressources de travail et à l’aide de l’application portail d’entreprise, l’inscription affectent périphériques et des utilisateurs."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6edf0ac1-4f46-4543-a9e5-f484ac37e9a5
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 701f6c79b32a3968fd76b441b8f7fd4d9d810df6
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Termes et les paramètres de stratégie de condition dans Microsoft Intune
Vous pouvez déployer Intune termes et conditions aux groupes d’utilisateurs afin d’expliquer comment accéder à des ressources de travail et à l’aide de l’application portail d’entreprise, l’inscription affectent périphériques et des utilisateurs. Les utilisateurs doivent accepter les termes et conditions avant de pouvoir utiliser le portail d’entreprise pour vous inscrire et accéder à leur travail.

Vous pouvez créer et déployer des stratégies plusieurs contenant différents termes et conditions. Vous pouvez également produire des versions des termes et conditions dans d’autres langues, puis déployer ces à leurs groupes appropriés.

## Créer une stratégie de termes et conditions

1.  Cliquez sur **une stratégie** dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) &gt; **termes et Conditions**.

    ![Capture d’écran de stratégie termes et conditions](./media/pol-sa-terms-conditions.png)

2.  Cliquez sur **Ajouter** pour créer une nouvelle stratégie de termes et conditions.

    Vous pouvez également **Modifier** ou **Supprimer** une stratégie existante.

3.  Dans la page **créer des termes et Conditions** , spécifiez les informations suivantes :

    -   **Nom** : un nom de stratégie uniques affiché dans la console Intune

    -   **Description** - détails pour vous aider à identifier la stratégie dans la console Intune

    -   **Titre** - le titre affiché pour les utilisateurs dans le portail d’entreprise

    -   **Texte décrivant la signification si l’utilisateur accepte** -étiquette les utilisateurs voient en ce qui concerne l’acceptation. **Exemple**: « J’accepte les termes et conditions. »

4.  Lorsque vous avez terminé, cliquez sur **Enregistrer**. La nouvelle stratégie est affichée dans le nœud de **termes et Conditions** de l’espace de travail de **stratégie** .

## Déployer une stratégie de termes et conditions

1.  Cliquez sur **une stratégie** dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) &gt; **termes et Conditions**.

2.  Dans la liste des **termes et Conditions** , sélectionnez la stratégie que vous voulez déployer, puis cliquez sur **Gérer le déploiement**.

3.  Dans la boîte de dialogue **Gérer le déploiement** , sélectionnez les groupes d’utilisateurs que vous voulez déployer la stratégie, puis cliquez sur **OK**.

    Lorsque les utilisateurs accèdent le portail d’entreprise, Intune affiche les termes et conditions que vous avez déployé. Les utilisateurs doivent accepter ces termes avant qu’ils peuvent accéder aux ressources de l’entreprise.

## Surveiller une stratégie de termes et conditions

1.  Cliquez sur **une stratégie** dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) &gt; **termes et Conditions**.

2.  Dans la fenêtre de **Création de rapports** , cliquez sur **Afficher le rapport**. Le rapport s’ouvre détaillant les utilisateurs qui ont accepté les termes et conditions que vous avez déployé.

### Mises à jour et contrôle de version pour les termes et conditions
Lorsque vous modifiez une stratégie existante de termes et conditions, vous pouvez choisir le comportement lorsque vous déployez la stratégie. Utilisez la procédure suivante pour vous aider à mettre à jour les termes existants et stratégies de conditions.

## Comment travailler avec plusieurs versions des termes et conditions

1.  Cliquez sur **une stratégie** dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) &gt; **termes et Conditions**.

2.  Sélectionnez la stratégie de termes et conditions que vous voulez modifier, puis cliquez sur **Modifier**.

3.  Dans la page **Modifier les termes et Conditions** , vérifiez les modifications requises, puis puis spécifier si cette nouvelle version, tous les utilisateurs accepter les termes et conditions, ou uniquement les nouveaux utilisateurs verront la nouvelle version.

    Nous vous recommandons d’augmenter le numéro de version et exiger l’acceptation chaque fois que vous apportez significative les modifications à votre stratégie de termes et conditions. Conserver le numéro de version actuelle si vous résolution des fautes de frappe ou modifiez la mise en forme, par exemple.

### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
