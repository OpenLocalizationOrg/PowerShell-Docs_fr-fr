---
title: "Limiter l’accès de messagerie vers Exchange Online | Microsoft Intune"
description: "Protéger et contrôler l’accès à la messagerie d’entreprise dans Exchange Online avec accès conditionnel."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 15aeddc7353c57e19fb43077b2e5dacb32808fc6
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès de messagerie Exchange Online et Exchange de nouveau en ligne-dédié avec Intune

Si vous disposez d’un environnement Exchange Online dédié et que vous devez déterminer si elle est dans la nouvelle ou de configuration héritées, contactez votre responsable de compte.

Pour contrôler l’accès de messagerie vers Exchange Online ou vers le nouvel environnement Exchange Online dédié, configurer l’accès conditionnel pour Exchange Online dans Intune.
Pour en savoir plus sur comment conditionnelle access, consultez l’article [restreindre l’accès aux messages électroniques, Office 365 et autres services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

>[!IMPORTANT]
>Accès conditionnel pour PC et Windows 10 Mobile appareils avec les applications en utilisant l’authentification moderne n’est pas disponible actuellement à tous les clients Intune. Si vous utilisez déjà ces fonctionnalités, vous n’avez pas besoin aucune action. Vous pouvez continuer à les utiliser.

>Si vous n’avez pas créé les stratégies d’accès conditionnel pour PC ou Windows 10 Mobile pour les applications en utilisant l’authentification moderne et que vous voulez faire, inscrivez-vous à la présentation publique Azure Active Directory qui inclut les périphériques en fonction accès conditionnel pour Intune gérée appareils ou un domaine rejoint PC Windows. Lisez [ce billet de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/) pour en savoir plus.  

**Avant de** pouvoir configurer l’accès conditionnelle, vous devez :

-   Posséder un **abonnement à Office 365 qui inclut Exchange Online (par exemple, E3)** et les utilisateurs doivent être une licence pour Exchange Online.

-  Envisagez de configurer le facultatif **Microsoft Intune service à service Connecteur**, qui se connecte [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] sur Microsoft Exchange Online et permet de gérer les informations relatives au périphérique via la [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] console. Vous n’avez pas besoin d’utiliser le connecteur à utiliser les stratégies de conformité ou accès conditionnel, mais il est nécessaire pour exécuter des rapports qui vous aident à évaluer l’impact d’accès conditionnelle.

   > [!NOTE]
   > Ne configurez pas le lien de service à service si vous envisagez d’utiliser access conditionnelle pour Exchange Online et Exchange en local

   Pour obtenir des instructions sur la configuration du connecteur, consultez la section [Intune service à service Connecteur](intune-service-to-service-exchange-connector.md)

Lorsque les stratégies d’accès conditionnelle sont configurées et destinées à un utilisateur, avant d’un utilisateur peut se connecter à leur messagerie, **périphérique** qu’ils utilisent doit être :

-   **Inscrit** avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou est un domaine rejoint PC.

-  **Enregistré dans Azure Active Directory**. Cela produit automatiquement lorsque l’appareil est inscrit auprès [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. En outre, le client Qu'exchange ActiveSync ID doit être enregistré avec Azure Active Directory.

  DRS AAD est activée automatiquement pour les clients Intune et Office 365. Clients qui ont déjà déployé le Service d’enregistrement de périphérique ADFS ne verront pas les appareils inscrits dans leurs locale d’Active Directory.

-   **Compatible** avec n’importe quel [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] des stratégies de conformité déployés sur votre appareil, ou un domaine à un domaine local.

Si une stratégie d’accès conditionnelle n’est pas remplie, l’utilisateur se voit avec l’un des messages suivants lors de la connexion :

- Si l’appareil n’est pas inscrit avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ou n’est pas enregistré dans Azure Active Directory, un message s’affiche avec des instructions sur la façon d’installer l’application portail d’entreprise, inscrire l’appareil et activer compte de messagerie. Ce processus associe également Exchange ActiveSync ID du périphérique avec l’enregistrement dans Azure Active Directory.

-   Si le périphérique est considéré comme pas compatible avec les règles de stratégie de conformité, l’utilisateur final est invité au [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] site Web du portail d’entreprise, ou l’application portail d’entreprise où ils peuvent trouver des informations sur le problème et comment plus.


L’illustration ci-dessous montre le flux utilisé par les stratégies d’accès conditionnel pour Exchange Online.

![Diagramme illustrant les points de décision qui déterminent si l’appareil est autorisé à accéder ou bloqué](../media/ConditionalAccess8-1.png)

## Prise en charge pour les appareils mobiles
Vous pouvez limiter l’accès à la messagerie Exchange Online à partir **d’Outlook** et d’autres **applications qui utilisent l’authentification moderne**:-

- Android 4.0 ou version ultérieure, Samsung Knox Standard 4.0 et versions ultérieur
- iOS 8.0 et versions ultérieures
- Windows Phone 8.1 et versions ultérieur

**Authentification moderne** apporte authentification basée sur le terme ADAL Active bibliothèque d’authentification de répertoire aux clients Microsoft Office.

-   Le terme ADAL en fonction de l’authentification permet aux clients Office de s’engager dans authentification basée sur le navigateur (également appelé authentification passive).  Pour l’authentification, l’utilisateur est dirigé vers une page web se connecter. Cette nouvelle méthode de connexion permet une meilleure sécurité tels que **l’authentification multifacteur**et **l’authentification basée sur le certificat**.
Cet [article](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) compte des informations plus détaillées sur le fonctionnement de l’authentification comment moderne.
Configurer des règles de revendications ADFS pour bloquer les protocoles d’authentification non-moderne. Obtenir des instructions détaillées sont fournies dans le scénario 3 - [bloquer tous les accès à Office 365 à l’exception des applications basé sur le navigateur](https://technet.microsoft.com/library/dn592182.aspx).

Vous pouvez limiter l’accès à **Outlook Web Access (OWA)** dans Exchange Online lors de l’accès à partir d’un navigateur sur **iOS** et **Android** appareils.  Access se voient d’uniquement les navigateurs pris en charge sur les appareils compatibles avec :

* Safari (iOS)
* Chrome (Android)
* Navigateur gérée (iOS et Android)

**Navigateurs non pris en charge seront bloquées**.

Les applications OWA pour iOS et Android ne sont pas pris en charge.  Ils doivent être bloqués en utilisant les règles de revendications ADFS.




Vous pouvez limiter l’accès à la messagerie Exchange à partir du **client de messagerie Exchange ActiveSync** intégrée sur les plateformes suivantes :

- Android 4.0 ou version ultérieure, Samsung Knox Standard 4.0 et versions ultérieur

- iOS 8.0 et versions ultérieures

- Windows Phone 8.1 et versions ultérieur

## Prise en charge pour les PC

Vous pouvez configurer access conditionnelle pour les ordinateurs qui exécutent les applications de bureau Office pour accéder à **Exchange Online** et **SharePoint Online** pour les PC qui remplissent les conditions suivantes :

-   L’ordinateur doit exécuter Windows 7.0 ou Windows 8.1.

-   L’ordinateur doit être domaine joint ou compatible avec les règles de stratégie de conformité.

    Pour être considéré comme conforme, l’ordinateur doit être inscrit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] respectez les stratégies.

    Pour domaine rejoint PC, vous devez le configurer pour [inscrire automatiquement l’appareil](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) avec Azure Active Directory.
    >[!NOTE]
    >Accès conditionnel n’est pas pris en charge sur les ordinateurs exécutant le client ordinateur Intune.

-   [Authentification moderne office 365 doit être activée](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), et toutes les mises à jour Office plus récente.

    Authentification moderne prend Active Directory authentification bibliothèque (terme ADAL) en fonction de se connecter aux clients Office 2013 Windows et permet une meilleure sécurité tels que **l’authentification multifacteur**et **l’authentification basée sur le certificat**.

-   Définir des règles pour bloquer les protocoles d’authentification moderne non revendications ADFS. Obtenir des instructions détaillées sont fournies dans le scénario 3 - [bloquer tous les accès à Office 365 à l’exception des applications basé sur le navigateur](https://technet.microsoft.com/library/dn592182.aspx).

## Configurer l’accès conditionnel
### Étape 1 : Configurer et déployer une stratégie de conformité
Vérifiez que vous [créez](create-a-device-compliance-policy-in-microsoft-intune.md) et [Déployez](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) une stratégie de conformité aux groupes d’utilisateurs qui recevront également la stratégie d’accès conditionnelle.


> [!IMPORTANT]
> Si vous n’avez pas déployé une stratégie de conformité, les périphériques sont considérés comme conformes et seront autorisés à accéder à Exchange.

### Étape 2 : Évaluer l’effet de la stratégie d’accès conditionnel
Vous pouvez utiliser les **Rapports d’inventaire appareil Mobile** afin d’identifier les appareils que l’accès à Exchange après avoir configuré la stratégie d’accès conditionnelle peuvent être bloqués.

Pour ce faire, configurez une connexion entre [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] et Exchange à l’aide du [connecteur de service au service Microsoft Intune](intune-service-to-service-exchange-connector.md).
1.  Accédez à **Rapports -> Rapports des stocks appareil Mobile**.
![Capture d’écran de la page de rapport d’inventaire appareil Mobile](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  Dans les paramètres du rapport, sélectionnez le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] groupe que vous voulez évaluer et, si nécessaire, les plateformes d’appareil sur lequel la stratégie s’appliquent.
3.  Une fois que vous avez sélectionné les critères qui répond aux besoins de votre organisation, sélectionnez **Afficher le rapport**.
La visionneuse de rapports s’ouvre dans une nouvelle fenêtre.
![Capture d’écran d’un rapport d’inventaire exemple appareil mobile](../media/IntuneSA2cViewReport.PNG)

Une fois que vous exécutez le rapport, examinez ces quatre colonnes pour déterminer si un utilisateur doit être bloqué :

-   **Gestion de canal** – indique si le périphérique est géré par Intune, Exchange ActiveSync ou les deux.

-   **AAD enregistré** – indique si l’appareil est inscrit avec Azure Active Directory (appelé joindre de l’espace de travail).

-   **Compatible** – indique si le périphérique est compatible avec les stratégies de conformité vous déployé.

-   **Exchange ActiveSync ID** – appareils iOS et Android doivent disposer de leur ID de ActiveSync Exchange associé à l’enregistrement de périphérique dans Azure Active Directory. Cela se produit lorsque l’utilisateur choisit le lien **Activer le courrier électronique** dans le message de mise en quarantaine.

    > [!NOTE]
    > Appareils Windows Phone toujours affichent une valeur dans cette colonne.

Appareils qui font partie d’un groupe ciblé ne pourront pas l’accès à Exchange, à moins que les valeurs de colonne correspondent à ceux indiqués dans le tableau suivant :

--------------------------
|Canal de gestion|AAD enregistré|Respecter les exigences|Exchange ActiveSync ID|Action résultante|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Gérés par Microsoft Intune et Exchange ActiveSync**|Oui|Oui|Une valeur est affichée|Accès à la messagerie autorisés|
|Toute autre valeur|N°|N°|Aucune valeur est affichée|Accès e-mail bloqué|
----------------------
Vous pouvez exporter le contenu du rapport et utilisez la colonne **Adresse de messagerie** pour informer les utilisateurs qu’ils seront bloquées.

### Étape 3 : Configurer les groupes d’utilisateurs pour la stratégie d’accès conditionnel
Les stratégies d’accès conditionnelle visent à différents groupes de sécurité Azure Active Directory des utilisateurs. Vous pouvez également exclure certains groupes d’utilisateurs à partir de cette stratégie.  Lorsqu’un utilisateur est ciblé par une stratégie, chaque périphérique qu’ils utilisent doit être conforme afin d’accéder à messagerie.

Vous pouvez configurer ces groupes dans le **Centre d’administration Office 365**, ou le **portail de compte Intune**.

Vous pouvez spécifier deux types de groupes dans chaque stratégie :

-   **Groupes cibles** – groupes d’utilisateurs à laquelle la stratégie est appliquée.

-   **Groupes Exempted** – groupes d’utilisateurs sont exempt de la stratégie (facultative)

Si un utilisateur se trouve dans deux groupes, il sera exemptés de la stratégie.

Seuls les groupes qui ciblés par la stratégie d’accès conditionnelle sont évaluées.

### Étape 4 : Configurer la stratégie d’accès conditionnel

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** > **Accès conditionnel** > **Exchange Online stratégie**.
![Capture d’écran de la page de stratégie d’accès conditionnel Exchange Online](../media/mdm-ca-exo-policy-configuration.png)

2.  Dans la page **Exchange Online stratégie** , sélectionnez **Activer la stratégie d’accès conditionnel pour Exchange Online**.

    > [!NOTE]
    > Si vous n’avez pas déployé une stratégie de conformité, appareils sont considérés comme conformes.
    >
    > Quelle que soit l’état de conformité, tous les utilisateurs qui visent à la stratégie seront invités à inscrire leur appareil avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

3.  Sous **accès aux applications**, pour les applications qui utilisent l’authentification moderne, il existe deux façons de choisir quelles plates-formes la stratégie doit être appliqué. Plateformes prises en charge incluent Android, iOS, Windows et Windows Phone.

    -   **Toutes les plateformes**

        Cela nécessite que n’importe quel appareil utilisé pour accéder à **Exchange Online**, à s’inscrire dans Intune et la conformité avec les stratégies.  N’importe quelle application client en utilisant **l’authentification moderne** est couvertes par la stratégie d’accès conditionnelle et si la plateforme n’est actuellement pas pris en charge par Intune, l’accès à **Exchange Online** est bloqué.

        Sélection de l’option **toutes les plateformes** signifie que Azure Active Directory appliquera cette stratégie à toutes les demandes d’authentification, quelle que soit la plateforme signalée par l’application cliente.  Toutes les plateformes devront inscrit et devenir compatibles, à l’exception de :
        *   Appareils Windows devront être inscrit et la conformité, domaine joint avec Active Directory local, ou les deux
        * Plateformes non prises en charge tels que Mac OS.  Toutefois, applications en utilisant l’authentification moderne en provenance de ces plateformes sera toujours être bloqué.

        >[!TIP]
           Vous ne pouvez pas voir cette option si vous n’utilisant pas déjà accès conditionnel pour PC.  Utilisez les **plateformes spécifiques** à la place. Accès conditionnel pour PC n’est pas disponible actuellement à tous les clients Intune.   Vous trouverez plus d’informations sur comment obtenir l’accès à cette fonctionnalité [dans ce billet de blog ](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/).

    -   **Plateformes spécifiques**

         Stratégie d’accès conditionnelle s’appliquent à n’importe quelle application client qui utilise **l’authentification moderne** sur les plateformes d’appareil que vous spécifiez.

4. Sous **accès web Outlook (OWA)**, vous pouvez choisir d’autoriser l’accès à Exchange Online uniquement via les navigateurs pris en charge : Safari (iOS) et Chrome (Android). Accès à partir d’autres navigateurs seront bloquées. Les mêmes restrictions de plateforme que vous avez sélectionné pour l’accès aux applications pour Outlook s’appliquent également ici.

  Sur les appareils **Android** , les utilisateurs doivent activer l’accès d’un navigateur.  Pour ce faire l’utilisateur final doit activer l’option « Activer l’accès navigateur » sur le périphérique inscrit comme suit :
  1.    Lancez l' **application portail d’entreprise**.
  2.    Accédez à la page **paramètres** dans les trois points (...) ou le bouton de menu matériel.
  3.    Appuyez sur le bouton **Activer l’accès navigateur** .
  4.    Dans le navigateur Chrome, se déconnecter de Office 365 et redémarrez Chrome.

  Sur les plateformes **iOS et Android** , pour identifier le périphérique utilisé pour accéder au service, Azure Active Directory émet un certificat Transport layer security (TLS) à l’appareil.  Le périphérique affiche le certificat invitant à l’utilisateur final pour sélectionner le certificat comme indiqué dans les captures d’écran ci-dessous. L’utilisateur final devez sélectionner ce certificat avant de pouvoir continuer à utiliser le navigateur.

  **iOS**

  ![capture d’écran de l’invite de certificat sur un ipad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![capture d’écran de l’invite de certificat sur un appareil Android](../media/mdm-browser-ca-android-cert-prompt.png)

5.  Sous **applications Exchange ActiveSync**, vous pouvez choisir de bloquer les périphériques non conformes d’accéder à Exchange Online. Vous pouvez également choisir autoriser ou bloquer l’accès à des messages lorsque l’appareil n’est pas exécuté une plateforme pris en charge. Plateformes prises en charge comprennent Android, iOS, Windows et Windows Phone.

6.  Sous **Destinée aux groupes**, sélectionnez les groupes de sécurité Active Directory des utilisateurs auxquels s’applique la stratégie. Vous pouvez choisir de cibler tous les utilisateurs ou une liste de groupes d’utilisateurs.
![Capture d’écran de la page de stratégie accès conditionnel Exchange Online, affichant les options de groupe ciblé et Exempted](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE]
    > Pour les utilisateurs qui se trouvent dans les **groupes cibles**, la Intune stratégies va remplacer Exchange et règles.
    >
    > Exchange appliquera uniquement l’échange autorise, les règles de bloc et de mise en quarantaine et d’échanger des stratégies si :
    >
    > -   L’utilisateur n’a pas de licence pour Intune.
    > -   L’utilisateur est sous licence pour Intune, mais l’utilisateur n’appartient pas à un groupe de sécurité ciblé dans la stratégie d’accès conditionnelle.

6.  Sous **Groupes exemptés**, sélectionnez les groupes de sécurité Active Directory des utilisateurs sont pas soumis à cette stratégie. Si un utilisateur se trouve dans les groupes ciblés et exemptés, il sera exemptés de la stratégie.

7.  Lorsque vous avez terminé, cliquez sur **Enregistrer**.

-   Vous n’êtes pas obligé de déployer la stratégie d’accès conditionnelle, il prend effet immédiatement.

-   Lorsqu’un utilisateur crée un compte de messagerie, le périphérique est bloqué immédiatement.

-   Si un utilisateur bloqué s’inscrit l’appareil avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] et correctifs de problèmes de conformité, accès à la messagerie est non bloqué dans les 2 minutes.

-   Si l’utilisateur désactiver-inscrit à leur appareil, les messages sont bloqués après environ 6 heures.

**Pour voir des exemples de scénarios de comment vous voulez configurer stratégie d’accès conditionnel pour restreindre l’accès des appareils, voir [limiter les scénarios d’exemple accès messagerie](restrict-email-access-example-scenarios.md).**

## Surveiller les stratégies d’accès conditionnelle et conformité

#### Pour afficher les périphériques sont bloqués depuis Exchange

Sur le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] tableau de bord, sélectionnez la vignette **Appareils bloqués à partir d’Exchange** pour afficher le nombre d’appareils bloqués et des liens vers des informations supplémentaires.
![Capture d’écran du tableau de bord Intune affichant le nombre d’unités qui sont bloqués d’accéder à Exchange](../media/IntuneSA6BlockedDevices.PNG)

## Étapes suivantes
[Limiter l’accès à SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Limiter l’accès à Skype entreprise Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
