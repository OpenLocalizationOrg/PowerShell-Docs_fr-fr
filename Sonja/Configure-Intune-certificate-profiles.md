---
title: Configurer les profils de certificat | Microsoft Intune
description: "Apprenez à créer un profil de certificat Intune."
keywords: 
author: nbigman
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
ms.openlocfilehash: e383b39493a7113d4e7c50b16df01d291b45036e
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configurer les profils de certificat Intune
Une fois que vous avez configuré votre infrastructure et les certificats comme décrit dans [l’infrastructure de certificats configurer pour SCEP](configure-certificate-infrastructure-for-scep.md) ou [infrastructure de certificats configurer pour PFX](configure-certificate-infrastructure-for-pfx.md), vous pouvez créer des profils de certificat. Voici la procédure :

- **Tâche 1**: exporter le certificat de certification racine de confiance
- **Tâche 2**: créer approuvés des profils de certificat
- **Tâche 3**: créer l’un des deux types de profil de certificats :
  - Profils de certificat SCEP
  - . Profils de certificat PFX

## **Tâche 1**: exporter le certificat de certification racine de confiance
Exportez le certificat autorités de Certification de racine de confiance (CA) sous forme de fichier **.cer** à partir de l’autorité de certification ou n’importe quel appareil qui approuve votre autorité de certification émission. Ne pas exporter la clé privée.

Vous allez importer ce certificat lorsque vous configurez un profil de certificat de confiance.

## **Tâche 2**: créer approuvés des profils de certificat
Vous devez créer un profil de certificat de confiance avant que vous puissiez créer un protocole d’inscription d’un certificat Simple (SCEP) ou un PKCS #12 (. Profil de certificat PFX). Vous avez besoin d’un profil de certificat de confiance et un SCEP ou. Profil PFX pour chaque plate-forme appareil mobile.

### Pour créer un profil de certificat de confiance

1.  Dans la [console d’administration Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **Ajouter une stratégie**.
2.  Ajoutez l’un de ces types de stratégie :
    - **Android &gt; profil de certificat approuvés (Android 4 et versions ultérieur)**
    - **iOS &gt; profil de certificat approuvés (iOS 8.0 et versions ultérieures)**
    - **Mac OS X &gt; profil de certificat approuvés (Mac OS X 10.9 et version ultérieure)**
    - **Windows &gt; profil de certificat approuvés (Windows 8.1 et versions ultérieures)**
    - **Windows &gt; profil de certificat approuvés (Windows Phone 8.1 et versions ultérieur)**

    En savoir plus : [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Entrez les informations requises pour configurer les paramètres de profil de certificats de confiance pour Android, iOS, Mac OS X, Windows 8.1 ou Windows Phone 8.1. 
4.  Dans le paramètre de **fichier de certificat** , importez le certificat d’autorité de certification racine de confiance (fichier .cer) que vous avez exporté à partir de votre autorité de certification émission. Le paramètre **Destination stocker** s’applique uniquement aux appareils exécutant Windows 8.1 et versions ultérieur et uniquement si le périphérique a plus d’un magasin de certificats.
    
4.  Cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie est présentée dans l’espace de travail de **stratégie** . À présent, vous pouvez déployer.

## **Tâche 3**: créer SCEP ou. Profils de certificat PFX
Après avoir créé un profil de certificat autorité de certification approuvée, créez SCEP ou. Profils de certificat PFX pour chaque plate-forme que vous souhaitez utiliser. Lorsque vous créez un profil de certificat SCEP, vous devez spécifier un profil de certificat de confiance pour cette plate-forme même. Cette opération lie les profils de deux certificat, mais vous devez toujours déployer chaque profil séparément.

### Pour créer un profil de certificat SCEP

1.  Dans la [console d’administration Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **Ajouter une stratégie**.
2.  Ajoutez l’un de ces types de stratégie :
    - **Android &gt; profil de certificat SCEP (Android 4 et versions ultérieur)**
    - **iOS &gt; profil de certificat SCEP (iOS 8.0 et versions ultérieures)**
    - **Mac OS X &gt; profil de certificat SCEP (Mac OS X 10.9 et version ultérieure)**
    - **Windows &gt; profil de certificat SCEP (Windows 8.1 et versions ultérieures)**
    - **Windows &gt; profil de certificat SCEP (Windows Phone 8.1 et versions ultérieur)**

    En savoir plus : [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Suivez les instructions dans la page de configuration de profil pour configurer les paramètres de profil de certificat SCEP.
    > [!NOTE]
    >
    > Sous **format du nom du sujet**, sélectionnez **personnalisée** pour entrer un format de nom de sujet personnalisé (dans iOS profils, uniquement).
    >
    > Les deux variables pris en charge pour le format personnalisé sont `Common Name (CN)` et `Email (E)`. En utilisant une combinaison de ces variables et de chaînes statiques, vous pouvez créer un format de nom de sujet personnalisé, comme celui-ci :

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > Dans cet exemple, l’administrateur créé un format de nom de sujet que, en plus de la `CN` et `E` variables, chaînes utilise pour les valeurs d’unité d’organisation, organisation, emplacement, état et pays. [Fonction CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) listes pris en charge des chaînes.

4.  Cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie est présentée dans l’espace de travail de **stratégie** . À présent, vous pouvez déployer.

### Pour créer un. Profil de certificat PFX

1.  Dans la [console d’administration Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **Ajouter une stratégie**.
2.  Ajoutez l’un de ces types de stratégie :
  - **Android &gt; . Profil de certificat PFX (Android 4 et versions ultérieur)**
  - **Windows &gt; PKCS #12 (. Profil de certificat PFX) (Windows 10 et versions ultérieures)**
  - **Windows &gt; PKCS #12 (. Profil de certificat PFX) (Windows Phone 10 et versions ultérieur)**
  - **iOS > PKCS #12 (. Profil de certificat PFX) (iOS 8.0 et versions ultérieures)**    
    En savoir plus : [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Entrez les informations demandées sur l’écran de stratégie.
4.  Cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie est présentée dans l’espace de travail de **stratégie** . À présent, vous pouvez déployer.

## Déployer des profils de certificat
Lorsque vous déployez des profils de certificat, le fichier de certificat à partir du profil de certificat autorité de certification approuvée est installé sur l’appareil. Le périphérique utilise la SCEP ou. Profil de certificat PFX pour créer une demande de certificat à l’appareil.

Profils de certificat installer uniquement sur les appareils exécutant la plateforme que vous utilisez lorsque vous créez le profil.

-   Vous pouvez déployer des profils de certificat aux collections de l’utilisateur ou aux collections de l’appareil.

    > [!TIP]
    > Pour publier un certificat à un appareil rapidement une fois que l’appareil s’inscrit, déployez le profil de certificat à un groupe d’utilisateurs plutôt qu’à un groupe de périphériques. Si vous déployez dans un groupe de périphériques, l’inscription d’une périphérique complet est nécessaire avant que le périphérique ne reçoive stratégies.

-   Même si vous déployez chaque profil séparément, vous devez également déployer l’autorité de certification racine de confiance et la SCEP ou. Profil PFX. Dans le cas contraire, la SCEP ou. Stratégie de certificat PFX échouera.

Déployer des profils de certificat la même façon que vous déployez d’autres stratégies pour Intune :

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis **Gérer le déploiement**.
2.  Dans la boîte de dialogue **Gérer le déploiement** :
    -   **Pour déployer la stratégie**, sélectionnez un ou plusieurs groupes pour déployer la stratégie, puis **Ajouter** &gt; **OK**.
    -   **Pour fermer la boîte de dialogue sans le déployer**, cliquez sur **Annuler**.

Lorsque vous sélectionnez une stratégie déployée, vous pouvez voir plus d’informations sur le déploiement dans la partie inférieure de la liste de stratégies.

### Étapes suivantes

Ensuite, découvrez comment utiliser des certificats afin de messagerie sécurisé, Wi-Fi et profils VPN.

-  [Configurer l’accès à la messagerie d’entreprise en utilisant les profils de courrier électronique](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Connexions Wi-Fi dans Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [Connexions VPN dans Microsoft Intune](vpn-connections-in-microsoft-intune.md)
