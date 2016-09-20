---
title: "Accéder à une messagerie d’entreprise avec les profils de messagerie | Microsoft Intune"
description: "Paramètres de profil de messagerie peuvent servir à configurer les paramètres d’accès de messagerie pour les clients de messagerie spécifiques sur les appareils mobiles."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 629836ef006e1c33c240f9daa373817a685c14bc
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configurer l’accès à la messagerie d’entreprise à l’aide des profils de messagerie avec Microsoft Intune
De nombreuses plates-formes mobiles incluent un client de messagerie native qui est fourni avec le système d’exploitation. Certaines de ces clients peuvent être configuré à l’aide des profils de courrier électronique, comme décrit dans cette rubrique.

Paramètres de profil de messagerie peuvent servir à configurer les paramètres d’accès de messagerie pour les clients de messagerie spécifiques sur les appareils mobiles. Sur les plateformes prises en charge, les clients de messagerie native peuvent être configurés par Microsoft Intune permettre aux utilisateurs d’accéder à leur messagerie d’entreprise sur leurs appareils personnels, sans tout le programme d’installation supplémentaire.

Si vous devez prendre des mesures supplémentaires pour la prévention des pertes de données, utilisez l' [accès conditionnel](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), qui contrôle l’accès aux boîtes aux lettres de l’utilisateur de n’importe quel client de messagerie, y compris les clients de messagerie native.

Les administrateurs informatiques ou les utilisateurs peuvent également choisir d’installer clients de messagerie alternative (par exemple, Microsoft Outlook pour Android ou iOS). Ces clients de messagerie peuvent ne pas gérer les profils de messagerie et ne peut pas être configurés à l’aide de Intune les profils de messagerie.  

Vous pouvez utiliser les profils de messagerie pour configurer le client de messagerie native sur les types d’appareil suivants :
-   Windows Phone 8 et versions ultérieur
-   Windows 10 (pour le bureau), Windows 10 Mobile et les versions ultérieures
-   iOS 8.0 et versions ultérieures
-   Samsung KNOX Standard (4.0 et versions ultérieures)

Outre la configuration d’un compte de messagerie sur l’appareil, vous pouvez définir la quantité messagerie électronique à synchroniser et selon le type d’appareil, laquelle synchroniser les types de contenu.
>[!NOTE]
>
>Si l’utilisateur a installé un profil de messagerie antérieures à configurer d’un profil par Intune, le résultat du déploiement de profil de messagerie Intune dépend de la plateforme de l’appareil :

[commentaire] : <> construction Passive dans trois paragraphes est nécessaire jusqu'à ce que le processus de détection des doublons est rendu Effacer en PM.

>**iOS**: un profil de messagerie existant, en double est détecté à l’adresse e-mail et le nom d’hôte. Le profil de messagerie en double créé par l’utilisateur bloque le déploiement d’un profil administrateur créé Intune. Il s’agit d’un problème courant, comme iOS utilisateurs généralement créer un profil de messagerie, puis inscrire. Le portail d’entreprise vous informe de l’utilisateur qu’ils ne sont pas compatibles en raison de leur profil de messagerie configurés manuellement et vous invite à l’utilisateur à supprimer ce profil. L’utilisateur doit supprimer son profil de messagerie, afin que le profil Intune peut être configuré. Pour éviter ce problème, demandez à vos utilisateurs pour inscrire avant d’installer un profil de messagerie et autoriser Intune Configurer le profil.

>**Windows**: un profil de messagerie existant, en double est détecté à l’adresse e-mail et le nom d’hôte. Intune remplace le profil de messagerie existant créé par l’utilisateur.

>**Samsung KNOX**: un profil de messagerie existant, en double est détecté à l’adresse de messagerie et remplace avec le profil Intune. Si l’utilisateur définit ce compte, il est à nouveau remplacé par le profil Intune. Notez que cela peut entraîner une certaine confusion à l’utilisateur.

>Dans la mesure où Samsung KNOX n’utilise pas le nom d’hôte pour identifier le profil, nous vous recommandons de créer plusieurs profils de messagerie à utiliser dans la même adresse de messagerie sur des hôtes différents, pas que ces remplacent les uns des autres.


## Sécuriser les profils de messagerie
Vous pouvez sécuriser les profils de messagerie à l’aide d’une des deux méthodes : via un certificat ou un mot de passe.

### Certificats
Lorsque vous créez le profil de messagerie, vous choisissez un profil de certificat que vous avez créé précédemment dans Intune. Ceci est connu sous le certificat d’identité et permet de s’authentifier un profil de certification approuvée (ou un certificat racine) pour établir qu’appareil de l’utilisateur est autorisé à se connecter. Le certificat de confiance est déployé sur l’ordinateur qui authentifie la connexion de messagerie, en règle générale, le serveur de messagerie native.

Pour plus d’informations sur la façon de créer et utiliser des profils de certificat dans Intune, voir [accès aux ressources sécurisé avec les profils de certificat](secure-resource-access-with-certificate-profiles.md).

### Nom d’utilisateur et mot de passe
L’utilisateur s’authentifie au serveur de messagerie native en fournissant leur nom d’utilisateur et mot de passe.

Le mot de passe ne figure pas dans le profil de messagerie, afin que l’utilisateur doit fournir ce lorsqu’ils se connectent à la messagerie.

### Créer un profil de messagerie

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **Ajouter une stratégie**.

2.  Configurer un des types de stratégie suivants :

    -   **Profil de messagerie pour les appareils Samsung KNOX Standard (4.0 et versions ultérieures)**

    -   **Profil de messagerie (iOS 8.0 et versions ultérieures)**

    -   **Profil de messagerie (Windows Phone 8 et versions ultérieur)**

    -   **Profil de messagerie (bureau 10 et Mobile et les versions ultérieures)**

    Vous pouvez seulement créer et déployer une stratégie de profil de messagerie électronique personnalisée. Paramètres recommandés ne sont pas disponibles.

3.  Utilisez le tableau suivant pour vous aider à configurer les paramètres de profil de messagerie :

|Nom du paramètre | Plus d’informations|
| ----------- | --------------- |
    |**Nom**|Nom unique pour le profil de messagerie.|
    |**Description**|Une description qui vous aident à identifier ce profil.|
    |**Hôte**|Le nom d’hôte du serveur de votre société qui héberge votre service de messagerie natif.|
    |**Nom du compte**|Le nom d’affichage pour le compte de messagerie tel qu’il apparaîtra aux utilisateurs sur leurs appareils.|
    |**Nom d’utilisateur**|Comment le nom d’utilisateur pour le compte de messagerie sera obtenu. Sélectionnez le **nom d’utilisateur** pour un serveur Exchange local, ou **Nom d’utilisateur Principal** pour Office 365.|
    |**Adresse de messagerie**|Comment l’adresse de messagerie de l’utilisateur sur chaque appareil est générée. Sélectionnez **L’adresse SMTP principale** à utiliser l’adresse SMTP principale pour vous connecter à Exchange ou utilisez le **Nom d’utilisateur Principal** pour utiliser le nom complet principal l’adresse de messagerie.|
    |**Méthode d’authentification** (Samsung KNOX et iOS)|Sélectionnez le **nom d’utilisateur et mot de passe** ou **certificats** en tant que la méthode d’authentification utilisée par le profil de messagerie.|
    |**Sélectionnez un certificat client pour l’authentification du client (identité certificat)** (Samsung KNOX et iOS)|Sélectionnez le certificat SCEP client que vous avez créé précédemment qui sera utilisé pour authentifier la connexion d’Exchange. Pour plus d’informations sur l’utilisation des profils de certificat dans Intune, voir [accès aux ressources sécurisé avec les profils de certificat](secure-resource-access-with-certificate-profiles.md). Cette option s’affiche uniquement lorsque la méthode d’authentification est **certificats**.|
    |**Utiliser S/MIME** (Samsung KNOX et iOS)|Envoyer du courrier sortant à l’aide du chiffrement S/MIME.|
    |**Certificat de signature** (Samsung KNOX et iOS)|Sélectionnez le certificat de signature qui sera utilisé pour signer le message électronique sortant. Cette option s’affiche uniquement lorsque vous sélectionnez **Utiliser S/MIME**.|
    |**Nombre de jours de la messagerie pour la synchronisation**|Le nombre de jours de messages électroniques que vous voulez synchroniser, ou sélectionnez **illimité** pour synchroniser tous les messages électroniques disponibles.|
    |**Planification de la synchronisation** (Samsung KNOX, Windows Phone 8 et versions ultérieur, Windows 10)|Sélectionnez le calendrier par lequel appareils synchroniseront des données à partir du serveur Exchange. Vous pouvez également sélectionner **en tant que Messages arrivent**, qui synchronise les données dès qu’il arrive, ou **manuel**, où l’utilisateur du périphérique doit lancer la synchronisation.|
    |**Utiliser le protocole SSL**|Utiliser la couche SSL (Secure Sockets) communication lors de l’envoi de messages électroniques, reçoit et la communication avec le serveur Exchange. Pour les appareils qui s’exécutent Samsung KNOX 4.0 ou version ultérieure, vous devez exporter votre certificat SSL de serveur Exchange et déployer comme un profil de certificat approuvés Android dans Intune. Intune ne prend pas en charge l’accès à ce certificat s’il est installé sur le serveur Exchange par d’autres moyens.|
    |**Type de contenu à synchroniser**|Sélectionnez les types de contenu que vous voulez synchroniser aux périphériques.|
    |**Messagerie autoriser soit envoyée à partir des applications tierces** (iOS uniquement)|Autoriser l’utilisateur à sélectionner ce profil comme compte par défaut pour l’envoi de messages électroniques et autoriser les applications tierces pour ouvrir messagerie dans l’application de messagerie native, par exemple, pour joindre des fichiers à des messages.|
    > [!IMPORTANT]
    > If you have deployed an email profile and then wish to change the values for **host** or **Email address**, you must delete the existing email profile and create a new one with the required values.

4.  Lorsque vous avez terminé, cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie s’affiche dans le nœud de **Stratégies de Configuration** de l’espace de travail de **stratégie** .

## Déploiement de la stratégie

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** :

    -   **Pour déployer la stratégie** - sélectionnez un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis **Ajouter** &gt; **OK**.

    -   **Pour fermer la boîte de dialogue sans le déployer** - cliquez sur **Annuler**.

Un résumé de l’état et les alertes dans la page **vue d’ensemble** de l’espace de travail de **stratégie** d’identifient les problèmes avec la stratégie qui nécessitent votre attention. En outre, un résumé de l’état apparaît dans l’espace de travail du tableau de bord.

> [!NOTE]
> Si vous voulez supprimer un profil de messagerie à partir d’un appareil, modifiez le déploiement et la suppression des groupes dont le périphérique est un membre.
