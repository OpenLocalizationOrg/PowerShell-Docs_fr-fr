---
title: "L’inscription directe pour les appareils iOS | Microsoft Intune"
description: "Utilisez l’outil de configuration du Apple pour inscrire directement des appareils iOS appartenant à l’entreprise avec une stratégie prédéfinie en vous connectant USB à un ordinateur Mac."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 17836bc826bc89e3f041f7b369be09c1cce9ea4f
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Inscrire directement à l’aide de la configuration du Apple les appareils iOS
Intune prend en charge l’inscription des appareils iOS appartenant à l’entreprise à l’aide de l’outil de [Configuration du Apple](http://go.microsoft.com/fwlink/?LinkId=518017) s’exécutant sur un ordinateur Mac. Ce processus ne pas usine-réinitialiser l’appareil et inscrit le périphérique avec une stratégie prédéfinie. Cette méthode est pour les appareils **sans** affinité utilisateur et vous oblige à se connecter USB l’appareil iOS sur un ordinateur Mac pour l’inscription d’entreprise le programme d’installation. Lors de l’inscription directement les appareils iOS, vous pouvez vous inscrire un appareil sans acquisition de numéro de série de l’appareil. Vous pouvez également nommer le périphérique pour l’identification avant Intune capture le nom du périphérique lors de l’inscription. L’application portail d’entreprise n’est pas prise en charge pour les périphériques inscrits direct. Ce guide suppose que vous utilisez Apple outil de configuration 2.0 sur un ordinateur Mac.

1.  **Créer un profil pour appareils mobiles** Un profil de l’inscription de périphérique définit les paramètres appliqués aux appareils. Si vous n’avez pas déjà le cas, créez un profil de l’inscription appareil pour les appareils iOS inscrit à l’aide de la configuration du Apple.

    1.  Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) accédez **stratégie** &gt; **Inscription d’un appareil d’entreprise**, puis cliquez sur **Ajouter**.

        ![Créer la page de profil d’inscription d’un appareil](../media/pol-sa-corp-enroll.png)

    2.  Entrez les détails pour les profils de périphériques :

        -   **Nom** – nom du profil d’inscription appareil. Non visibles par les utilisateurs.

        -   **Description** : Description du profil d’inscription appareil. Non visibles par les utilisateurs.

        -   **Affiliation utilisateur** – spécifie comment périphériques sont inscrits. Pour l’inscription directe, ne sélectionnez **aucune affinité utilisateur**.

        -   **Affectation de groupe de périphérique avant** – tous les périphériques déployés ce profil initialement appartiennent à ce groupe. Vous pouvez réaffecter appareils après l’inscription.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    3.  Sélectionnez **Enregistrer le profil** pour ajouter le profil.

5.  **Exporter un profil existant en tant que .mobileconfig à déployer les appareils iOS** Sélectionnez le profil de l’appareil que vous avez créé. Cliquez sur **Exporter.** dans la barre des tâches. Choisissez **profil à télécharger** et enregistrez le fichier téléchargé .mobileconfig.

6.  **Transfert de fichiers** Copiez le fichier téléchargé .mobileconfig sur un ordinateur Mac.
    > [!NOTE]
    > L’URL de profil d’inscription est valide pendant deux semaines à partir de lors de l’exportation. Deux semaines plus tard, vous devez exporter une nouvelle URL de profil d’inscription pour l’inscription des appareils iOS avec l’Assistant de configuration.
7.  **Préparer l’appareil avec l’outil de configuration Apple** iOS périphériques sont connectés à l’ordinateur Mac et inscrits pour la gestion des appareils mobiles.

    1.  Sur un ordinateur Mac, lancez **Apple configuration du 2.0**.

    2.  Se connecter à l’appareil iOS sur l’ordinateur Mac avec un câble USB. Fermez les **Photos**, **iTunes**et autres applications qui s’ouvre pour le périphérique lorsque le périphérique est détecté.

    3.  Dans le programme de configuration Apple, l’appareil iOS connecté d’un simple clic et puis cliquez sur le bouton **Ajouter** . Options peuvent être ajoutées à l’appareil s’affichent dans la liste déroulante. Choisissez **profils** .

    4.  Utilisez le sélecteur de fichier pour sélectionner le fichier .mobileconfig que vous avez exporté à partir de Intune et puis cliquez sur **Ajouter**. Le profil est ajouté à l’appareil.  Si le périphérique est **Unsupervised**, l’installation nécessite l’acceptation sur l’appareil.

8.  **Installer le profil** Vous êtes prêt à installer le profil sur l’appareil iOS. Le périphérique doit ont déjà terminé l’Assistant Installation et être prêt à utiliser.  Si l’inscription entraîne les déploiements d’application, le périphérique doit avoir un ID Apple configurer, car les déploiements d’application nécessite que vous avez un ID Apple connecté pour l’App Store.

    1.  Déverrouiller l’appareil iOS.

    2.  Boîte de dialogue **installer le profil** pour le **profil de gestion**, cliquez sur **installer**.

    3.  Indiquez **l’Appareil code secret** ou **ID Apple**, si nécessaire.

    4.  Acceptez l' **Avertissement**, puis appuyez sur **installer**.

    5.  Acceptez l' **Avertissement à distance**, puis appuyez sur la **gestion de la confidentialité**.

    6.  Lorsque la zone **Profil installés** confirme que le profil a **installé**, cliquez sur **terminé**.

9. **Vérifier le profil** 
    sur l’appareil iOS, lancer des **paramètres** et accédez **Général** &gt; **Gestion des appareils** &gt; **Profil Gestion** &gt; et confirmer l’installation du profil est répertoriée, vérifiez les restrictions de stratégie iOS et installé les applications. Applications et les restrictions de stratégie peuvent prendre jusqu'à 10 minutes apparaissent sur l’appareil.

10. **Répartir appareils** L’appareil iOS est maintenant inscrit avec Intune et gérée.
