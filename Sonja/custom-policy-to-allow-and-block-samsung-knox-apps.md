---
title: "Autorisés et bloqués applications pour KNOX | Microsoft Intune"
description: "Profil personnalisé pour créer une liste d’autorisés et bloqués applications pour KNOX."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
ms.openlocfilehash: 937e291f193f61329598395baa63c24d7fefa25f
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Utiliser des stratégies personnalisées pour autoriser et bloquer des applications pour les appareils Samsung KNOX

Utiliser les procédures dans cette rubrique pour créer une stratégie personnalisée Microsoft Intune qui crée une des opérations suivantes :

- Liste des applications en cours d’exécution sur l’appareil sont bloqués. Aucune autre application ne pourra exécuter. Applications de cette liste sont bloquées en cours d’exécution, même s’ils ont été déjà installé lorsque la stratégie a été appliquée.
- Liste des applications que les utilisateurs de l’appareil sont autorisés à installer à partir de Google Play store. Les applications vous liste peut être installé. Aucune autre application ne peut être installée à partir du magasin.

Ces paramètres peuvent uniquement être utilisés par les périphériques qui s’exécutent KNOX Samsung.

## Pour créer une liste des applications bloqués ou autorisés

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **stratégie** &gt; **Stratégies de Configuration** &gt; **Ajouter**.
2. Dans la boîte de dialogue **créer une nouvelle stratégie de** développer **Android**, sélectionnez **Configuration personnalisée**, puis **Créer une stratégie**.
3. Fournir un nom et une description facultative de la stratégie, puis dans la section **Paramètres OMA URI** , sélectionnez **Ajouter**.
4. Dans la boîte de dialogue **Ajouter ou modifier le paramètre OMA URI** , spécifiez les options suivantes : pour obtenir la liste des applications en cours d’exécution sur l’appareil sont bloqués :
    
    - **Nom du paramètre.** Entrez **PreventStartPackages**.
    - **Description du paramètre.** Entrez une description facultative comme « Liste des applications qui sont bloqués exécution ».
    -   **Type de données.** Dans la liste déroulante, choisissez **chaîne**.
    -   **OMA-URI.** Entrez **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Valeur.** Entrez une liste des noms de package d’application que vous voulez autoriser les. Vous pouvez utiliser **; :,** ou **|** comme un délimiteur. (Exemple : package1 ; commande pour AIX2 ;)

    Pour obtenir une liste des applications que les utilisateurs sont autorisés à installer à partir de Google Play store tout en excluant tous les autres applications :

    - **Nom du paramètre.** Entrez **AllowInstallPackages**.
    - **Description du paramètre.** Entrez une description facultative comme « Liste des applications que les utilisateurs peuvent installer à partir de Google Play ».
    - **Type de données.** Dans la liste déroulante, choisissez **chaîne**.
    - **OMA-URI.** Entrez **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Valeur.** Entrez une liste des noms de package d’application que vous voulez autoriser les. Vous pouvez utiliser **; :,** ou **|** comme un délimiteur. (Exemple : package1 ; commande pour AIX2 ;)

4. Cliquez sur **OK**, puis cliquez sur **Enregistrer la stratégie**. 

>[CONSEIL] Vous pouvez trouver l’ID d’une application en accédant à l’application sur Google Play store. L’ID de package est contenue dans l’URL de la page de l’application. Par exemple, l’ID de package de l’application Microsoft Word est **com.microsoft.office.word**.

La prochaine fois destinée aux tests appareil dans l’application paramètres seront appliqués.


## Déploiement de la stratégie

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis cliquez sur **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** , sélectionnez un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis cliquez sur **Ajouter** &gt; **OK**.

 
Lorsque vous sélectionnez une stratégie déployée, vous pouvez afficher d’autres informations relatives au déploiement dans la partie inférieure de la liste des stratégies.

### Voir aussi
[Android et les paramètres de stratégie Samsung KNOX dans Microsoft Intune](android-policy-settings-in-microsoft-intune.md)
