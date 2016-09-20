---
title: Inscription des appareils iOS avec Assistant | Microsoft Intune
description: "S’inscrire iOS appartenant à l’entreprise appareils à l’aide de l’outil de configuration Apple outil pour usine-réinitialiser l’appareil et prépare à exécuter l’Assistant de configuration."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 1260001be3e5479ff0758178dc161260d31dcc3e
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Inscription des appareils iOS avec Apple le programme de configuration à l’aide de l’Assistant de configuration
Intune prend en charge l’inscription des appareils iOS appartenant à l’entreprise à l’aide de l’outil de [Configuration du Apple](http://go.microsoft.com/fwlink/?LinkId=518017) s’exécutant sur un ordinateur Mac. Ce processus usine une réinitialisation du périphérique et prépare à exécuter l’Assistant de configuration par utilisateur de l’appareil avec les stratégies de la société préinstallés.


## Configurer l’inscription de l’Assistant pour les appareils iOS avec Microsoft Intune
À l’aide de la configuration du Apple vous pouvez usine réinitialiser des appareils iOS et les prépare pour le programme d’installation par utilisateur de l’appareil.  Cette méthode nécessite l’appareil iOS sur un ordinateur Mac pour l’inscription d’entreprise le programme d’installation pour vous connecter USB et suppose que vous utilisez Apple configuration du 2.0. La plupart des scénarios requièrent que la stratégie est appliquée à l’appareil iOS inclure **affinité utilisateur** pour activer l’application portail d’entreprise Intune.

**Conditions préalables**
* [inscription iOS activée](set-up-ios-and-mac-management-with-microsoft-intune.md) par l’installation d’un certificat APNs
* Accès physique pour les appareils iOS - périphériques doivent être non configurée (usine Rétablir) sans protection par mot de passe
* Numéros de série appareil - [comment obtenir un numéro de série iOS](https://support.apple.com/en-us/HT204308)
* Câble de connexion USB
* Ordinateur Mac avec [Apple configuration du 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


1.  **Créer un groupe appareil mobile** (Facultatif) Si votre entreprise requiert des groupes d’appareil mobile faciliter la gestion des appareils mobiles, créer des groupes. [Utilisez des groupes pour gérer les utilisateurs et dispositifs avec Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

2.  **Créer un profil pour appareils mobiles** Un profil de l’inscription de périphérique définit les paramètres appliqués à un groupe de périphériques. Si vous n’avez pas déjà le cas, créez un profil de l’inscription appareil pour les appareils iOS inscrit à l’aide de la configuration du Apple.

    1.  Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) accédez **stratégie** &gt; **Inscription d’un appareil d’entreprise**, puis cliquez sur **Ajouter**.
    ![Créer le profil d’inscription d’un appareil](../media/pol-sa-corp-enroll.png)

    2.  Entrez les détails pour les profils de périphériques :

        -   **Nom** – nom du profil d’inscription appareil. (Non visibles des utilisateurs)

        -   **Description** : Description du profil d’inscription appareil. (Non visibles des utilisateurs)

        -   **Détails de l’inscription** – spécifie comment périphériques sont inscrits.

            -   **Choisir l’affinité utilisateur** – le périphérique doit être affilié à un utilisateur lors de l’installation initiale et pourrait puis être autorisé à accéder aux données de la société et la messagerie électronique en tant que cet utilisateur. **Affinité utilisateur** doit être configuré pour les périphériques gérés DEP qui appartiennent aux utilisateurs et que vous devez utiliser le portail d’entreprise (c'est-à-dire pour installer des applications).

            -   **Aucune affinité utilisateur** – l’appareil n’est pas affilié à un utilisateur. Utilisez cette affiliation pour appareils mobiles qui effectuent des tâches sans accès aux données utilisateur local. Applications nécessitant une affiliation utilisateur, y compris l’application portail d’entreprise utilisée pour les applications professionnelles de l’installation, ne fonctionnent pas.

        -   **Affectation de groupe de périphérique avant** – tous les périphériques déployés ce profil initialement appartiennent à ce groupe. Vous pouvez réaffecter appareils après l’inscription.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

          -  **Programme d’inscription d’un appareil** - l’Apple appareil inscription d’un programme (PED) ne peut pas être utilisé avec Assistant de configuration d’inscription. Vérifiez que le bouton bascule est défini sur **désactiver**.

    3.  Sélectionnez **Enregistrer le profil** pour ajouter le profil.

3.  **Ajouter les appareils iOS s’inscrire à l’Assistant de configuration** Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) accédez **groupes** &gt; **Tous les périphériques** &gt; **appartenant à l’entreprise tous les appareils** &gt; **Tous les périphériques**, puis cliquez sur **Ajouter les unités**. Vous pouvez ajouter des périphériques de deux façons :

    ![Ajouter la boîte de dialogue périphériques](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **Télécharger un fichier CSV contenant les numéros de série** – créer séparées par des virgules (.csv) valeur liste de deux colonnes sans en-tête, limité à 5 000 unités ou 5 Mo par fichier csv.

        |||
        |-|-|
        |&lt;1 # en série&gt;|&lt;Détails de l’appareil #1&gt;|
        |&lt;Série #2&gt;|&lt;Détails de l’appareil #2&gt;|
        Ce fichier .csv lorsqu’ils sont affichés dans un éditeur de texte apparaît sous la forme :

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Ajouter manuellement des détails de l’appareil** - Entrez le numéro de série et les détails de l’appareil de cinq appareils

    > [!NOTE]
    > Si vous devez supprimer ultérieurement périphériques appartenant à l’entreprise de la gestion des Intune, vous devrez peut-être supprimer le numéro de série appareil Intune dans le groupe **par numéro de série iOS** appareil sous **périphériques de l’entreprise pré-inscrit** pour désactiver l’inscription d’un appareil.  Si Intune effectue une procédure de reprise sur ou autour de l’heure à laquelle les numéros de série ont été supprimées, vous avez besoin vérifier que seuls les numéros de série dispositifs actifs sont présents dans ce groupe.

    Cliquez sur **suivant**.

4.  **Sélectionnez périphériques d’inscription** Vérifiez les périphériques d’inscription. Numéros de série déjà inscrit ou inscrits par d’autres moyens ne peuvent pas être importés. Cliquez sur **suivant** pour continuer.

5.  **Affecter le profil** Spécifier le profil pour attribuer aux périphériques ajoutés dans la liste des profils disponibles, vérifiez les **Détails de profil d’inscription**, puis sélectionnez **Terminer**. Appareils ajoutés manuellement peuvent être affectées à n’importe quel profil d’inscription.

6.  **Exporter un profil à déployer les appareils iOS** Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) accédez **stratégie** &gt; **Inscription d’un appareil d’entreprise**et sélectionnez le profil de l’appareil à déployer les appareils mobiles. Cliquez sur **Exporter.** dans la barre des tâches. Copiez et enregistrez l' **URL du profil**. Vous allez le télécharger dans le programme de configuration Apple une version ultérieure pour définir le profil Intune utilisé par les appareils iOS.
    Prise en charge Apple configuration du 2, l’URL de profil 2.0 doit être modifiée. Remplacer
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    avec

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   Vous allez télécharger cette URL de profil du service DEP Apple à l’aide de configuration du Apple dans la procédure suivante pour définir le profil Intune utilisé par les appareils iOS.



7.  **Préparer l’appareil avec l’outil de configuration Apple** iOS périphériques sont connectés à l’ordinateur Mac et inscrits pour la gestion des appareils mobiles.

    1.  Sur un ordinateur Mac, ouvrez **Apple configuration du 2**. Dans la barre de menus, sélectionnez **Apple configuration du 2**, puis **Préférences**.

         > [!WARNING]
         > Les appareils seront ramenés à des configurations usine pendant le processus d’inscription. Pour obtenir les meilleurs résultats, réinitialisez l’appareil et mettez-le sous tension. Pour obtenir les meilleurs résultats, les périphériques doivent être à l’écran **Hello** lorsque vous vous connectez le périphérique.

    2. Dans le volet Préférences, sélectionnez **serveurs** et choisissez le symbole « + » situé sous le volet gauche pour lancer l’Assistant serveur MDM. Cliquez sur **suivant**.

    3. Entrez le **nom** et **l’URL d’inscription** pour le serveur de la gestion des périphériques à partir de l’étape 6 ci-dessus. Pour l’URL d’inscription Entrez l’URL de profil d’inscription exporté à partir de Intune. Cliquez sur **suivant**.  

       Si vous recevez un message d’avertissement indiquant « URL du serveur n’est pas vérifiée », « vous pouvez ignorer en toute sécurité l’avertissement. Pour continuer, choisissez **suivant** jusqu'à ce que l’Assistant est terminé.

    4.  Connecter les appareils mobiles iOS à l’ordinateur Apple avec une carte USB.

        > [!WARNING]
        > Les appareils seront ramenés à des configurations usine pendant le processus d’inscription. Pour obtenir les meilleurs résultats, réinitialisez l’appareil et mettez-le sous tension. Pour obtenir les meilleurs résultats, les périphériques doivent être à l’écran **Hello** lorsque vous démarrez l’Assistant de configuration.

    5.  Cliquez sur **préparer**. Dans le volet **préparer iOS Device** , sélectionnez **manuel** , puis choisissez **suivant**.

    6. Dans le volet **inscrire dans Server périphériques mobiles** , sélectionnez le nom du serveur vous avez créé, puis sélectionnez **suivant**.

    7. Dans le volet **Appareils superviser** , sélectionnez le niveau de la surveillance et puis cliquez sur **suivant**.

    8. Dans le volet **créer une organisation** , sélectionnez l' **organisation** ou créer une organisation, puis **suivant**.

    9. Dans le volet **configurer iOS Assistant de configuration** , sélectionnez les étapes présentées à l’utilisateur, puis **préparer**. Si vous y êtes invité, authentifier pour mettre à jour les paramètres de gestion de la confidentialité.  

    10. Une fois le périphérique iOS préparation, vous pouvez déconnecter le câble USB.  

8.  **Répartir appareils** Les périphériques sont maintenant prêts pour l’inscription d’entreprise. Tension les appareils et les distribuer aux utilisateurs. Lorsque l’appareil est activé, l’Assistant Installation démarre.



### Voir aussi
[Préparer d’inscription des appareils mobiles](get-ready-to-enroll-devices-in-microsoft-intune.md)
