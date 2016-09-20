---
title: "Limiter l’accès à SharePoint Online | Microsoft Intune"
description: "Protéger et contrôler l’accès aux données d’entreprise sur SharePoint Online avec accès conditionnel."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: fe1fae610e4d562b467e9778841fc1c547db3bfa
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès à SharePoint Online avec Microsoft Intune
Utiliser la [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] accès conditionnel pour contrôler l’accès aux fichiers situés sur SharePoint online.
Accès conditionnel comporte deux éléments :
- Stratégie de conformité d’appareil l’appareil doit respecter afin d’être considéré comme compatible.
- Stratégie d’accès conditionnelle dans laquelle vous spécifiez les conditions que l’appareil doit respecter afin d’accéder au service.
Pour en savoir plus sur comment conditionnelle access, consultez la rubrique [restreindre l’accès aux messages électroniques, Office 365 et autres services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

La conformité et les stratégies d’accès conditionnelle sont déployés à l’utilisateur. N’importe quel appareil qui utilise l’utilisateur à accéder aux services est activé pour la conformité avec les stratégies.

Lorsqu’un utilisateur tente de se connecter à un fichier en utilisant une application pris en charge tel que OneDrive sur leur appareil, l’évaluation suivante se produit :

![Diagramme pour afficher les points de décision qui déterminent si un appareil est autorisé à accéder à SharePoint est bloqué ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>Accès conditionnel pour PC et Windows 10 Mobile appareils avec les applications en utilisant l’authentification moderne n’est pas disponible actuellement à tous les clients Intune. Si vous utilisez déjà ces fonctionnalités, vous n’avez pas besoin aucune action. Vous pouvez continuer à les utiliser.

>Si vous n’avez pas créé les stratégies d’accès conditionnel pour PC ou Windows 10 Mobile pour les applications en utilisant l’authentification moderne et que vous voulez faire, inscrivez-vous à la présentation publique Azure Active Directory qui inclut les périphériques en fonction accès conditionnel pour Intune gérée appareils ou un domaine rejoint PC Windows. Lisez [ce billet de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/) pour en savoir plus.

**Avant de** configurer une stratégie d’accès conditionnel pour SharePoint Online, vous devez :
- Ayez un **abonnement SharePoint Online** et les utilisateurs doivent être une licence pour SharePoint Online.
- Posséder un abonnement pour **l’Entreprise mobilité Suite** ou **Azure Active Directory Premium**.

  Pour vous connecter aux fichiers requis, l’appareil doit :
-   Être **inscrit** auprès de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou un ordinateur à un domaine.

-   **Inscrire l’appareil** dans Azure Active Directory (cela produit automatiquement lorsque l’appareil est inscrit auprès [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).


-   Respecter les exigences en avec n’importe quel déployé [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] des stratégies de conformité

L’état de l’appareil est stocké dans Azure Active Directory qui accorde ou bloque l’accès aux fichiers, en fonction des conditions que vous spécifiez.

Si une condition n’est pas remplie, l’utilisateur se voit avec l’un des messages suivants lors de la connexion :

-   Si l’appareil n’est pas inscrit avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ou n’est pas enregistré dans Azure Active Directory, un message s’affiche avec des instructions sur la façon d’installer l’application portail d’entreprise et inscrire.

-   Si l’appareil n’est pas conforme, un message s’affiche et indique à l’utilisateur le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] site Web où ils peuvent trouver des informations sur le problème et comment mettre à jour le portail d’entreprise.

**Accès conditionnel est appliquée sur tous les sites SharePoint et le partage externe est bloqué**

>[!NOTE]
>Si vous activez l’accès conditionnel pour SharePoint Online, nous vous recommandons de désactiver le domaine dans la liste comme décrit dans la rubrique [Supprimer SPOTenantSyncClientRestriction](https://technet.microsoft.com/en-us/library/dn917451.aspx) .  
## Prise en charge pour les appareils mobiles
- iOS 8.0 et versions ultérieures
- Android 4.0 ou version ultérieure, Samsung Knox Standard 4.0 ou version ultérieure
- Windows Phone 8.1 et versions ultérieur

Vous pouvez limiter l’accès à SharePoint Online lors de l’accès à partir d’un navigateur à partir **d’iOS** et les appareils **Android** .  Access se voient d’uniquement les navigateurs pris en charge sur les appareils compatibles avec :
* Safari (iOS)
* Chrome (Android)
* Navigateur gérée (iOS et Android)

**Navigateurs non pris en charge seront bloquées**.

## Prise en charge pour les PC
- Windows 8.1 et versions ultérieures (lorsque inscrit avec Intune)
- Windows 7.0 ou Windows 8.1 (lorsqu’à un domaine)

  - PC à un domaine doit être configuré pour [Enregistrer automatiquement](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) avec Azure Active Directory.
DRS AAD est activée automatiquement pour les clients Intune et Office 365. Clients qui ont déjà déployé le Service d’enregistrement de périphérique ADFS ne verront pas les appareils inscrits dans leurs locale d’Active Directory.

  - Si la stratégie est définie pour exiger la jointure de domaines et le PC n’est pas à un domaine, un message s’affiche pour contacter l’administrateur informatique.

  - Si la stratégie est définie pour exiger jonction de domaine ou conforme et le PC ne répond pas à des exigences, un message s’affiche avec des instructions sur la façon d’installer l’application portail d’entreprise, inscrire.
  >[!NOTE]
  >Accès conditionnel n’est pas pris en charge sur les ordinateurs exécutant le client ordinateur Intune.

-    [Authentification moderne office 365 doit être activée](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), et toutes les mises à jour Office plus récente.

    Authentification moderne prend Active Directory authentification bibliothèque (terme ADAL) en fonction de se connecter aux clients Office 2013 Windows et permet une meilleure sécurité tels que **l’authentification multifacteur**et **l’authentification basée sur le certificat**.


## Configurer l’accès conditionnel pour SharePoint Online

### Étape 1 : Configurer les groupes de sécurité Active Directory
Avant de commencer, configurez des groupes de sécurité Azure Active Directory pour la stratégie d’accès conditionnelle. Vous pouvez configurer ces groupes dans le **Centre d’administration Office 365**, ou le **portail de compte Intune**. Ces groupes servira à cible, ou des agents utilisateurs à partir de la stratégie. Lorsqu’un utilisateur est ciblé par une stratégie, chaque périphérique qu’ils utilisent doit être conforme afin d’accéder à des ressources.

Vous pouvez spécifier deux types de groupes dans une stratégie de SharePoint Online :

-   **Groupes cibles** – contient des groupes d’utilisateurs pour lequel la stratégie est appliquée.

-   **Groupes Exempted** – contient des groupes d’utilisateurs qui sont exemptés de la stratégie.

Si un utilisateur se trouve dans deux groupes, il sera exemptés de la stratégie.

### Étape 2 : Configurer et déployer une stratégie de conformité
Si vous ne le n'avez pas déjà fait, créez et déployez une stratégie de conformité aux utilisateurs qui est ciblée sur la stratégie de SharePoint Online.

> [!NOTE]
> Tandis que les stratégies de conformité sont déployés sur [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] les groupes, accès conditionnel stratégies destinées à des groupes de sécurité Azure Active Directory.

Pour plus d’informations sur la configuration de la stratégie de conformité, voir [créer une stratégie de conformité](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT]
> Si vous n’avez pas déployé une stratégie de conformité, les appareils seront traités comme conformes.

Lorsque vous êtes prêt, passez à **l’étape 3**.

### Étape 3 : Configurer la stratégie de SharePoint Online
Ensuite, configurez la stratégie pour exiger qu’appareils uniquement gérées et la conformité peuvent accéder à SharePoint Online. Cette stratégie sera ne sera stocké dans Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** > **Accès conditionnel** > **SharePoint Online stratégie**.
![Capture d’écran de la page SharePoint Online stratégie](../media/mdm-ca-spo-policy-configuration.png)

2.  Sélectionnez **Activer la stratégie d’accès conditionnel pour SharePoint Online**.

3.  Sous **accès aux applications**, vous pouvez choisir appliquer la stratégie d’accès conditionnel pour :

    -   **Toutes les plateformes**

        Cela nécessite que n’importe quel appareil utilisé pour accéder à **SharePoint Online**, est inscrite dans Intune et la conformité avec les stratégies.  N’importe quelle application client en utilisant **l’authentification moderne** est couvertes par la stratégie d’accès conditionnelle. Si la plateforme n’est actuellement pas pris en charge par Intune, accès à **SharePoint Online** est bloqué.

        Sélection de **toutes les plateformes** option signifie que Azure Active Directory appliquera cette stratégie à toutes les demandes d’authentification, quelle que soit la plateforme signalée par l’application cliente.  Toutes les plateformes devront inscrit et devenir compatibles, à l’exception de :
        *   Appareils Windows devront être inscrit et la conformité, domaine joint avec Active Directory local, ou les deux
        * Plateformes non prises en charge comme Mac.  Toutefois, applications en utilisant l’authentification moderne en provenance de ces plateformes sera toujours être bloqué.
        >[!TIP]
        >Vous ne pouvez pas voir cette option si vous n’utilisant pas déjà accès conditionnel pour PC.  Utilisez les **plateformes spécifiques** à la place. Accès conditionnel pour PC n’est pas disponible actuellement à tous les clients Intune.   Vous trouverez plus d’informations sur comment obtenir l’accès à cette fonctionnalité [dans ce billet de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/).

    -   **Plateformes spécifiques**

         Stratégie d’accès conditionnelle s’appliquent à n’importe quelle application client qui utilise l’authentification moderne sur les plateformes que vous spécifiez.

     Pour windows PC, l’ordinateur doit être associés à un domaine ou inscrits avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] et la conformité. Vous pouvez définir les conditions suivantes :

     -   **Périphériques doivent être conformes ou à un domaine.** Choisissez cette option si vous souhaitez que les PC soit être associés à un domaine ou compatible avec les stratégies définies [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Si le PC ne répond pas à une de ces exigences, l’utilisateur est invité à inscrire l’appareil avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **Périphériques doivent être associés à un domaine.** Choisissez cette option pour exiger que les PC doivent être associés à un domaine pour accéder à Exchange Online. Si le PC n’est pas à un domaine l’accès à la messagerie est bloqué et l’utilisateur est invité à contacter l’administrateur informatique.

     -   **Appareils doivent être conformes.** Sélectionnez cette option pour exiger que les PC doivent être inscrits dans [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] et la conformité. Si le PC n’est pas inscrit, un message avec des instructions sur la procédure d’inscription s’affiche.

4.   Sous **accès d’un navigateur** sur SharePoint Online et OneDrive entreprise, vous pouvez choisir d’autoriser l’accès à Exchange Online uniquement via les navigateurs pris en charge : Safari (iOS) et Chrome (Android). Accès à partir d’autres navigateurs seront bloquées.  Les mêmes restrictions de plateforme que vous avez sélectionné pour l’accès aux applications pour OneDrive s’appliquent également ici.

  Sur les appareils **Android** , les utilisateurs doivent activer l’accès d’un navigateur.  Pour ce faire l’utilisateur final doit activer l’option « Activer l’accès navigateur » sur le périphérique inscrit comme suit :
  1.    Lancez l' **application portail d’entreprise**.
  2.    Accédez à la page **paramètres** dans les trois points (...) ou le bouton de menu matériel.
  3.    Appuyez sur le bouton **Activer l’accès navigateur** .
  4.  Dans le navigateur Chrome, se déconnecter de Office 365 et redémarrez Chrome.

  Sur les plateformes **iOS et Android** , pour identifier le périphérique utilisé pour accéder au service, Azure Active Directory émet un certificat Transport layer security (TLS) à l’appareil.  Le périphérique affiche le certificat invitant à l’utilisateur final pour sélectionner le certificat comme indiqué dans les captures d’écran ci-dessous. L’utilisateur final devez sélectionner ce certificat avant de pouvoir continuer à utiliser le navigateur.

  **iOS**

  ![capture d’écran de l’invite de certificat sur un ipad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![capture d’écran de l’invite de certificat sur un appareil Android](../media/mdm-browser-ca-android-cert-prompt.png)
5.  Sous **Destinée aux groupes**, cliquez sur **Modifier** pour sélectionner les groupes de sécurité Azure Active Directory à laquelle s’applique la stratégie. Vous pouvez choisir de cibler ce pour tous les utilisateurs ou simplement un sélectionner des groupes d’utilisateurs.

6.  Sous **Groupes exemptés**, si vous le souhaitez, cliquez sur **Modifier** pour sélectionner les groupes de sécurité Azure Active Directory qui sont pas soumis à cette stratégie.

6.  Lorsque vous avez terminé, cliquez sur **Enregistrer**.

Vous n’êtes pas obligé de déployer la stratégie d’accès conditionnelle, il prend effet immédiatement.

### Étape 4 : Surveiller la conformité et les stratégies d’accès conditionnelle
Dans l’espace de travail **groupes** , vous pouvez afficher l’état de vos appareils.

Sélectionnez n’importe quel groupe de l’appareil mobile et puis, sous l’onglet **périphériques** , sélectionnez une des **filtres**suivants :

-   **Appareils qui ne sont pas enregistrés avec AAD** – les appareils suivants sont bloqués depuis SharePoint Online.

-   **Appareils qui ne sont pas compatibles avec** les appareils suivants sont bloqués depuis SharePoint Online.

-   **Appareils qui sont enregistrés avec DAS et la conformité** – les appareils suivants peuvent accéder à SharePoint Online.

### Voir aussi
[Restreindre l’accès aux messages électroniques et les services Office 365 avec Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
