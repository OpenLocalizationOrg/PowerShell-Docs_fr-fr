---
title: "Par application VPN pour Android à l’aide de la banque d’informations sécurisé Pulse | Microsoft Intune"
description: "Vous pouvez créer un profil VPN par application pour les appareils Android gérés par Intune."
keywords: 
author: nbigman
manager: angrobe
ms.date: 08/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
ms.openlocfilehash: a2af91827f3a5ebc549e7f474943f1b0cc6208dd
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Utiliser une stratégie personnalisée pour créer un profil VPN par application pour les appareils Android

Vous pouvez créer un profil VPN par application pour Android 5.0 et des générations ultérieures qui sont gérées par Intune. Tout d’abord, créez un profil VPN qui utilise le type de connexion Pulse banque d’informations sécurisé. Ensuite, créez une stratégie de configuration personnalisé qui associe le profil VPN applications spécifiques. 

Une fois que vous déployez la stratégie à vos groupes utilisateur ou appareil Android, les utilisateurs doivent démarrer PulseSecure VPN. PulseSecure permettra puis le trafic uniquement à partir des applications à utiliser la connexion VPN ouverte spécifiées.

> [!NOTE]
>
> Seul le type de connexion Pulse Secure est pris en charge pour ce profil.


### Étape 1 : Créer un profil VPN

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** > **Ajouter une stratégie**.
2. Pour sélectionner un modèle pour la nouvelle stratégie, développez **Android**et puis sélectionnez **Profil VPN (Android 4 et versions ultérieur)**.
3. Dans le modèle pour le **type de connexion**, choisissez **Pulse banque d’informations sécurisé**.
4. Terminer et enregistrer le profil VPN. Pour plus d’informations sur les profils VPN, voir [connexions VPN](../deploy-use/vpn-connections-in-microsoft-intune.md).

> [!NOTE]
>
> Notez le nom du profil VPN à utiliser dans l’étape suivante. Par exemple, MyAppVpnProfile.

### Étape 2 : Créer une stratégie de configuration personnalisé

   1. Dans la console d’administration Intune, choisissez **stratégie** > **Ajouter une stratégie** > **Android** > **configuration personnalisée** > **Créer une stratégie**.
   2. Entrez un nom pour la stratégie.
   3. Sous **paramètres d’URI de OMA**, cliquez sur **Ajouter**.
   4. Entrez un nom de paramètre.
   5. Pour **type de données**, indiquez la **chaîne**.
   6. Pour **OMA URI**, spécifiez cette chaîne : * *./Vendor/MSFT/VPN/Profile/*nom*/PackageList**, où *nom* est le nom du profil VPN vous avez noté à l’étape 1. Dans notre exemple, la chaîne serait **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   Pour **valeur**, créer une liste délimitée par des points-virgules des packages à associer avec le profil. Par exemple, si vous voulez Excel et le navigateur Google Chrome à utiliser la connexion VPN, entrez **com.microsoft.office.excel;com.android.chrome**.

![Stratégie personnalisée exemple application Android VPN](./media/android_per_app_vpn_oma_uri.png)

#### Définir votre liste des applications à la liste de blocage ou d’autorisation (facultatif)
  Vous pouvez spécifier une liste des applications qui utilisent la connexion VPN *ne peut pas* à l’aide de la valeur de la **liste de blocage** . Toutes les autres applications vous connecterez via le réseau privé virtuel.
Par ailleurs, vous pouvez utiliser la valeur de la **liste d’autorisation** pour spécifier une liste des applications qui utilisent la connexion VPN *peut* . Applications qui ne figurent pas dans la liste ne se connecte pas via le réseau VPN.
  1.    Sous paramètres **OMA URI** , cliquez sur **Ajouter**.
  2.    Entrez un nom de paramètre.
  3.    Pour **type de données**, indiquez la **chaîne**.
  4.    Pour **OMA URI**, utilisez cette chaîne : * *./Vendor/MSFT/VPN/Profile/**nom/mode**, où *nom* est le nom du profil VPN vous avez noté à l’étape 1. Dans notre exemple, la chaîne serait **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    Pour **valeur**, entrez **blocage** ou **autorisation**.



### Étape 3 : Déployer les deux stratégies

Vous devez déployer des stratégies *à la fois* aux groupes Intune *même* .

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis **Gérer le déploiement**.
2.  Dans la boîte de dialogue **Gérer le déploiement** :
    -   **Pour déployer la stratégie**, sélectionnez un ou plusieurs groupes pour déployer la stratégie, puis cliquez sur **Ajouter** > **OK**.
    -   **Pour fermer la boîte de dialogue sans déploiement de la stratégie**, cliquez sur **Annuler**.

Un résumé de l’état et les alertes dans la page **vue d’ensemble** de l’espace de travail de **stratégie** d’identifient les problèmes avec la stratégie qui nécessitent votre attention. Un résumé de l’état apparaît également dans l’espace de travail de **tableau de bord** .
