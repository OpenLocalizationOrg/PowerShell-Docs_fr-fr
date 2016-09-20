---
title: "Expérience utilisateur final MAM activé applications | Microsoft Intune"
description: "Cette rubrique décrit à quoi s’attendre lorsque votre application est gérée par des stratégies de gestion de l’application mobile."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.openlocfilehash: 48783b21c64c9031b0fbbd58afb8aa0eb911ed6b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Expérience utilisateur final MAM activé applications avec Microsoft Intune
Stratégies de gestion des applications mobiles (MAM) sont appliqués uniquement lorsque des applications sont utilisées dans le contexte de travail.  Lire les scénarios suivants pour mieux comprendre comment gérées applications fonctionnent.
##  Accéder à OneDrive sur un appareil iOS

1.  Lancez l’application **OneDrive** pour ouvrir le signe dans la page.

    ![Page de connexion du une lecteur capture d’écran](../media/AppManagement/iOS_OneDriveLaunch.png)

    > [!NOTE]
    > Sur un appareil personnel, généralement l’utilisateur final serait télécharger l’application.  Si l’appareil est géré par une solution périphériques mobiles, vous pouvez déployer l’application sur le périphérique.

2.  Tapez votre nom d’utilisateur compte professionnel. Vous êtes redirigé vers la page **Office 365 authentification** à entrer vos informations d’identification de travail.

    ![Capture d’écran de la page d’accès O365](../media/AppManagement/iOS_O365SignInPage.png)

3.  Une fois vos informations d’identification sont correctement authentifiées par Azure AD, le MAM stratégies sont appliqués, et vous être invité à redémarrer l’application **OneDrive** .
  >[NOTE] ! Le redémarrage obligatoire boîte de dialogue s’affiche uniquement sur les appareils que vous n’êtes pas inscrit à Intune.

    ![Capture d’écran de la boîte de dialogue requise redémarrer](../media/AppManagement/iOS_AppRestartforMAM.png)

4.  Lorsque vous exécutez de nouveau l’application **OneDrive** , l’application lance avec les stratégies MAM activés. Vous êtes désormais invité à définir un **code confidentiel** pour l’application. (si vous avez configuré la stratégie pendant ce).

    ![Capture d’écran de OneDrive application demandant un code confidentiel](../media/AppManagement/iOS_AppPINPrompt.png)

5.  Une fois que vous définissez le code confidentiel et confirmez, vous êtes en mesure d’accéder aux fichiers sur votre **SkyDrive Pro**.

    ![Capture d’écran montrant l’emplacement du fichier à ouvrir avec la liste des fichiers existants](../media/AppManagement/iOS_OneDriveSuccess.png)

    > [!NOTE]
    > Lorsque vous modifiez une stratégie déployée, les modifications seront appliquées prochaine qu'ouverture de l’application.

##  Accéder à OneDrive sur un appareil Android

1.  Lancez l’application OneDrive pour ouvrir le signe dans la page.

    > [!NOTE]
    > Sur un appareil personnel, généralement l’utilisateur final serait télécharger l’application.  Si l’appareil est géré par une solution périphériques mobiles, vous pouvez déployer l’application à l’appareil.

2.  Tapez votre nom d’utilisateur compte professionnel. Vous êtes redirigé vers la page **Office 365 authentification** à entrer vos informations d’identification de travail.

    ![Capture d’écran de O365 dans page de connexion sur un appareil Android](../media/AppManagement/Android_O365SignInPage.png)

3.  Une fois que vos informations d’identification sont correctement authentifiées par **Azure Active Directory**, vous devez voir un message qui s’affiche avec les instructions pour installer l’application portail d’entreprise, s’il n’est pas déjà installé sur l’appareil.  Appuyez sur **Télécharger l’application** pour continuer.

>[!NOTE]
>L’application portail d’entreprise est requise pour toutes les applications associées aux stratégies MAM sur les appareils Android. Pour les appareils ne pas inscrits dans Intune, l’application doit être installée sur l’appareil, mais ne nécessite pas de lancement ou la connexion à l’application.  


  ![Capture d’écran de la boîte de dialogue avec l’application portail d’entreprise installer message configuration requise](../media/AppManagement/Android_CompanyPortalMessage.png)

4.  Vous êtes maintenant dans **Google Play** store où vous pouvez télécharger et installer l’application **Portail d’entreprise** .

    L’application portail d’entreprise vous permet de conserver les données sécurisées et protégées.

    ![Capture d’écran de l’application portail d’entreprise](../media/AppManagement/Android_CompanyPortalInstall.png)

5.  Une fois que vous avez terminé l’installation, cliquez sur **Accepter** pour accepter les termes.

6.  L’application **OneDrive** se lance automatiquement.

7.  La prochaine fois que vous ouvrirez OneDrive, vous verrez l’invite pour définir un **code confidentiel**, la stratégie de paramètres sont définis pour exiger un code confidentiel accéder à l’application **OneDrive** .

    ![Capture d’écran de l’application OneDrive avec l’invite de code confidentiel](../media/AppManagement/Android_OneDriveSetPIN.png)

8.  Une fois que le code confidentiel est et confirmé, vous pouvez continuer à l’aide **OneDrive**, qui est maintenant géré par les stratégies d’application.


##  Utilisation des applications avec prise en charge plusieurs identité
Microsoft Word est utilisé comme exemple dans ce scénario.

1.  Ouvrez l’application **Word** sur votre appareil. Nous utilisons un appareil iOS pour afficher les étapes.

2.  Appuyez sur **Nouveau** pour créer un nouveau document word.

    ![Capture d’écran d’un appareil iOS avec la nouvelle option de menu affichée dans la partie inférieure de l’écran](../media/AppManagement/iOS_WordCreateNewDoc.png)

3.  Tapez une phrase de votre choix.  Lorsque vous essayez d’enregistrer ce document, personnels et Professionnel emplacements apparaissent sous forme d’options pour enregistrer le document que vous venez de créer.  À ce stade, les stratégies d’application sont appliquées pas encore étant donné que ce contexte de travail/personnel n’est pas encore établi.

4.  Enregistrez le document à votre emplacement OneDrive entreprise. Ceci est maintenant marqué comme les données d’entreprise et les restrictions de stratégie appliquent.

    ![Capture d’écran d’une phrase tapée dans un document Word](../media/AppManagement/iOS_WordCreateCompanyDoc.PNG)

5.  Ouvrez le document que vous avez enregistré sur votre lieu de travail.  Copier le texte, ouvrez votre compte **Facebook** personnel et essayez de coller le texte copié.  Vous ne devez pas être en mesure de coller le contenu dans le nouveau billet Facebook. L’option Coller n’est pas grisée, mais rien ne se passe lorsque vous appuyez sur **Coller**.

    ![Capture d’écran montrant le couper, copier et coller des sélections](../media/AppManagement/iOS_WordCopyCompany.png)

    ![Capture d’écran ne montrant aucune donnée collée dans le billet de Facebook](../media/AppManagement/iOS_FacebookPasteCompany.png)

6.  Répétez les étapes 2 et 3 pour créer un autre document, tapez une phrase de votre choix et au lieu d’enregistrer votre travail, enregistrez-la dans votre emplacement personnel, tel que **OneDrive - personnel**maintenant.

    ![Capture d’écran de la couper, copier et coller la sélection avec la phrase à copier](../media/AppManagement/iOS_WordCopyPersonal.png)

7.  Ouvrez le document enregistré personnel.  Copier le texte, ouvrez l’application **Facebook** et essayez de coller le texte copié. Vous voyez que vous ne pouvez coller le contenu dans un billet de Facebook.

    ![Contenu indiquant que collé dans le billet de Facebook](../media/AppManagement/iOS_FacebookPastePersonal.png)

##  Gestion des comptes d’utilisateur

Intune prend uniquement en charge le déploiement des stratégies MAM compte qu’un seul utilisateur par périphérique. Si un périphérique possède plusieurs comptes de travail, travail qu’un seul compte est géré par les stratégies MAM.

En fonction de l’application que vous utilisez, le second utilisateur peut ou ne peut pas être bloqué sur l’appareil. Toutefois, dans tous les cas, seul le premier utilisateur qui obtient les stratégies MAM est affecté par la stratégie.

Si un périphérique a existantes plusieurs comptes d’utilisateur avant de déploiement les stratégies MAM, le compte que les stratégies MAM est déployé sur tout d’abord est géré par des stratégies de Intune MAM.

**Microsoft Word**, **Excel**et **PowerPoint** ne bloquent un deuxième compte d’utilisateur, mais le deuxième compte d’utilisateur n’est pas affecté par les stratégies MAM.  

Pour les **applications OneDrive et Outlook**, vous ne pouvez utiliser un compte professionnel.  Ajout de plusieurs comptes de travail sont bloqués sur ces applications.  Cependant, vous pouvez supprimer un utilisateur et ajouter un autre utilisateur sur le périphérique.

Lisez le scénario d’exemple ci-dessous pour obtenir de mieux comprendre comment plusieurs comptes d’utilisateurs sont traités.

L’utilisateur A fonctionne de deux sociétés - **Société X**et **Y de société**. L’utilisateur A dispose d’un compte de travail pour chaque société et utilisent Intune pour déployer des stratégies MAM. **Société X** déploie MAM stratégies **avant** **d’Y société**. Le compte associé **Société X** peuvent accéder à la stratégie MAM, mais pas le compte associé à Y société. Si vous souhaitez que le compte d’utilisateur associé à Y entreprise devant être gérés par les stratégies MAM, vous devez supprimer le compte d’utilisateur associé à X de la société.
### Ajout d’un deuxième compte
#### IOS
Si vous utilisez un appareil iOS, lorsque vous tentez d’ajouter un deuxième compte sur le même appareil, vous pouvez voir Bloquer les messages.  Vous verrez également une option pour supprimer le compte existant et ajoutez-en une nouvelle. Vous pouvez le faire en choisissant **Oui**.

![Capture d’écran de la boîte de dialogue avec le message blocage et Oui et aucune option](../media/AppManagement/iOS_SwitchUser.PNG)
####  Android
Si vous utilisez un appareil Android, un message de blocage des instructions pour supprimer le compte existant et ajoutez-en une nouvelle peut s’afficher.  Sur les appareils Android, pour supprimer le compte existant, accédez à **paramètres &gt;général &gt; Gestionnaire d’Application &gt;portail d’entreprise et sélectionnez « Effacer les données »**.

![Capture d’écran du message d’erreur et des instructions pour supprimer le compte](../media/AppManagement/Android_SwitchUser.png)

##  Affichage de fichiers multimédias avec la gestion des droits le partage d’application
Pour afficher les AV de société, PDF et les fichiers image sur les appareils Android, utilisent le [Partage d’application Microsoft Rights Management (RMS)](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Téléchargez cette application à partir de Google Play store.  Une fois que l’application est installée sur votre appareil, lancez l’application et vous authentifier avec vos informations d’identification de la société. Vous devriez maintenant pouvoir afficher les fichiers protégés et s’affiche-t-il provenant d’autres applications géré par une stratégie.

Les types de fichiers suivants sont pris en charge :

* **Audio :** AAC LC, HE-AACv1 (AAC +), HE-AACv2 (amélioré AAC +), AAC ELD (amélioré faible retard AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Vorbis, PCM/vague.
* **Vidéo :** H.263, AVC H.264, MPEG-4 SP, VP8.
* **Image :** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* FORMAT PDF, PPDF

------------
|**fichier pfile**|**texte**|
|----|----|
|Fichier pfile est un format générique « emballage » pour les fichiers protégés qui contient le contenu chiffré et les licences RMS et peut être utilisé pour protéger n’importe quel type de fichier.|Fichiers de texte, y compris XML, CSV, etc. peuvent être ouvert pour l’affichage dans l’application même lorsqu’ils sont protégés. Types de fichiers : txt, ptxt, csv, pcsv, journal, plog, xml, pxml.|
---------------
**Appareils Android ne sont pas inscrit dans Intune**

Avant de pouvoir utiliser le partage d’application de RMS pour afficher les fichiers à partir d’autres applications gérées par Intune, lancez l’application RMS et vous authentifier avec votre compte professionnel.  Lorsque vous connectez, vous verrez suivant message **uniquement si vous n’avez pas une licence RMS**:

**Authentification réussie – vous pouvez à présent afficher des fichiers d’entreprise, mais votre organisation n’est pas configuré pour vous permettre de protéger les fichiers. Pour plus d’informations, contactez votre administrateur informatique.**

Cela ne vous empêche pas d’utiliser le partage d’application de RMS pour afficher les fichiers de la société. Vous pouvez toujours ouvrir et afficher des fichiers de la société à partir d’autres applications gérées par Intune et les stratégies MAM seront appliquent toujours.  Témoignages ce message est que vous ne serez pas en mesure d’ajouter les fonctionnalités de protection supplémentaire qui fournit la RMS le partage d’application.  Vous devez disposer d’une licence de RMS pour ajouter une protection à vos fichiers. Pour en savoir plus sur les fonctionnalités de protection de fichier RMS, voir [protéger un fichier sur un appareil](https://docs.microsoft.com/en-us/rights-management/rms-client/sharing-app-protect-in-place) et [protéger un fichier que vous partagez par courrier électronique](https://docs.microsoft.com/en-us/rights-management/rms-client/sharing-app-protect-by-email).


### Voir aussi
[Créer et déployer des stratégies de gestion de l’application mobile avec Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
