---
title: Connecteur Exchange pour EAS local | Microsoft Intune
description: "Utiliser le connecteur outil pour activer la communication entre la console d’administration Intune et en local Exchange Server pour Exchange ActiveSync MDM."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41ff4212-a6f5-4374-8731-631f7560cff1
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: 18614cc272323b8031c94b8e582f80aa5c06d9d3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Installer le connecteur Intune local Exchange


Pour configurer une connexion qui permet à Microsoft Intune communiquer avec le serveur Exchange qui héberge les boîtes aux lettres de périphériques mobiles, vous devez télécharger et configurer l’outil Connecteur locale à partir de la console administrateur Intune. Intune prend uniquement en charge une connexion de connecteur Exchange de n’importe quel type par abonnement.

## Configuration requise pour le lien en local
Le tableau suivant répertorie la configuration requise pour l’ordinateur sur lequel vous installez le connecteur Exchange en local.

|Configuration requise|Plus d’informations|
|---------------|--------------------|
|Systèmes d’exploitation|Intune prend en charge le connecteur Exchange en local sur un ordinateur sur lequel s’exécute n’importe quelle édition de Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012 ou Windows Server 2012 R2.<br /><br />Le lien n’est pas pris en charge sur n’importe quelle installation Server Core.|
|Version de Microsoft Exchange|Un connecteur local nécessite Microsoft Exchange 2010 SP1 ou version ultérieure, ou héritées Exchange Online dédié. Pour déterminer si votre environnement Exchange Online dédié est dans la configuration du **Nouveau** ou **hérité** , contactez votre responsable de compte.|
|Autorité de gestion des appareils mobiles| [Définir l’autorité de gestion des périphériques mobiles pour Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority).|
|Matériel|L’ordinateur sur lequel vous installez le connecteur nécessite un 1,6 GHz processeur avec 2 Go de ram et les 10 Go de configuration matérielle minimale d’espace disque libre.|
|Synchronisation Active Directory|Avant de pouvoir utiliser un connecteur se pour connecter Intune à votre serveur Exchange, vous devez [configurer la synchronisation Active Directory](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) afin que vos utilisateurs locaux et les groupes de sécurité sont synchronisés avec votre instance d’Azure Active Directory.|
|Logiciel supplémentaire|Une installation complète de Microsoft .NET Framework 4 et Windows PowerShell 2.0 doit être installée sur l’ordinateur qui héberge le connecteur.|
|Réseau|L’ordinateur sur lequel vous installez le connecteur doit être placé dans un domaine ayant une relation de confiance au domaine qui héberge votre serveur Exchange.<br /><br />L’ordinateur doit des configurations pour lui permettre d’accéder au service Intune via le pare-feu et les serveurs proxy sur les Ports 80 et 443. Les domaines utilisés par Intune incluent manage.microsoft.com & #42;manage.microsoft.com, et & #42 ;. Manage.Microsoft.com.|
|Exchange hébergé configuré et en cours d’exécution|Pour plus d’informations, consultez [Exchange Server 2016](https://technet.microsoft.com/library/mt170645.aspx) . |

### Configuration requise pour Exchange applet de commande

Vous devez créer un compte d’utilisateur Active Directory utilisé par le connecteur Exchange Intune. Le compte doit avoir l’autorisation d’exécuter les applets de commande Windows PowerShell Exchange requis :


 -   Get-ActiveSyncOrganizationSettings, jeu ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, nouvelle-ActiveSyncMailboxPolicy, supprimer ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, nouvelle-ActiveSyncDeviceAccessRule, supprimer ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-Exchange Server
 -   Get-ActiveSyncDeviceClass
 -   Get-destinataire
 -   Effacer-ActiveSyncDevice, supprimer ActiveSyncDevice
 -   Set-ADServerSettings
 -   Commande Get

## Télécharger le package d’installation logiciel Connecteur Exchange en local

1. Sur le système d’exploitation Windows Server pris en charge pour le connecteur Exchange en local, ouvrez la [console d’administration Microsoft Intune](http://manage.microsoft.com) (http://manage.microsoft.com) avec un compte d’utilisateur qui est un administrateur dans le client Exchange avec une licence à utiliser Exchange Server.
![Ouvrir configurer connexion Exchange](../media/ExchangeConnector.gif)

2.  Dans le volet Raccourcis espace de travail, choisissez **administrateur**, sélectionnez **Gestion des appareils mobiles** > **Microsoft Exchange**, puis cliquez sur **Configurer une connexion Exchange**.

3.  Dans la page **Configurer une connexion Exchange** , sélectionnez **Télécharger le connecteur local**.

4.  Le connecteur Exchange locale est contenu dans un dossier compressé (.zip) qui peut être ouverts ou enregistré. Dans la boîte de dialogue **Téléchargement de fichier** , cliquez sur **Enregistrer** pour stocker le dossier compressé vers un emplacement sécurisé.

> [!IMPORTANT]
> Ne renommez ou déplacez les fichiers dans le dossier de connecteur Exchange en local. Déplacer ou renommer le contenu du dossier sauts de page de l’installation.

## Installer et configurer le connecteur Intune local Exchange
Procédez comme suit pour installer le connecteur Intune local Exchange. Le connecteur Exchange local peut uniquement être installé une fois par abonnement Intune et seulement sur un ordinateur. Si vous essayez de configurer un connecteur Exchange locaux supplémentaires, la nouvelle connexion remplacera celui d’origine.

1.  Sur un système d’exploitation pris en charge pour le connecteur locale, extraire les fichiers dans **Exchange_Connector_Setup.zip** dans un emplacement sécurisé.

2.  Une fois les fichiers extraits, ouvrez le dossier d’extraction et double-cliquez sur **Exchange_Connector_Setup.exe** pour installer le connecteur Exchange en local.

    > [!IMPORTANT]
    > Si le dossier de destination n’est pas un emplacement sécurisé, vous devez supprimer le fichier de certificat **WindowsIntune.accountcert** après avoir installé le connecteur locale.

3.  Dans le champ **serveur Exchange** , sélectionnez votre type d’environnement Exchange server, soit **En local Microsoft Exchange Server** , ou sélectionnez **Hébergés Microsoft Exchange Server**.

  ![Sélectionnez un type de serveur Exchange](../media/IntuneSA1dconfigureExchConnector.png)

  Pour un serveur Exchange local, indiquez le nom du serveur ou le nom de domaine complet du serveur Exchange qui héberge le rôle **Serveur d’accès Client** .

  Pour un serveur Exchange hébergé, fournissent l’adresse du serveur Exchange. Pour trouver l’URL du serveur Exchange hébergé :

      1.  Ouvrez Outlook Web App pour Office 365.

      2.  Choisissez le « ? » icône dans la partie supérieure gauche, puis sélectionnez **à propos**de.

      3.  Recherchez la valeur du **Serveur externe POP** .

      4.  Choisissez le **Serveur Proxy** pour spécifier proxy paramètres du serveur pour votre serveur Exchange hébergé.
        1.  Sélectionnez **utiliser un serveur proxy lors de la synchronisation de l’appareil mobile**.

        2.  Entrez le **nom du serveur proxy** et le **numéro de port** à utiliser pour accéder au serveur.

        3.  S’il est nécessaire de fournir des informations d’identification utilisateur pour accéder au serveur proxy, sélectionnez utiliser les références pour vous connecter au serveur proxy et entrez le **domaine\utilisateur** et le **mot de passe**.

        4.  Cliquez sur **OK**.

5.  Fournir les informations d’identification **utilisateur (domaine\utilisateur)** et **votre mot de passe** est nécessaire pour se connecter à votre serveur Exchange.

6.  Fournir des informations d’identification d’administration nécessaires pour envoyer des notifications aux lettres Exchange d’un utilisateur. Ces notifications sont configurables via les stratégies d’accès conditionnelle Intune.

    Assurez-vous que le service de découverte automatique et les Services Web Exchange sont configurés sur le serveur d’accès Client Exchange. Pour plus d’informations sur ce voir [serveur d’accès Client](https://technet.microsoft.com/library/dd298114.aspx).

7.  Dans le champ **mot de passe** , fournissent le mot de passe pour ce compte activer Intune accéder au serveur Exchange.

8. Cliquez sur **se connecter**.

    Il peut prendre quelques minutes alors que la connexion a été configurée.

Lors de la configuration, le connecteur Exchange enregistre vos paramètres de proxy pour activer l’accès à Internet. Si vos paramètres de proxy modifier, vous devrez reconfigurer le connecteur Exchange afin d’appliquer les paramètres de proxy mis à jour au connecteur Exchange.

Une fois que le connecteur Exchange configure la connexion, les appareils mobiles associés aux utilisateurs qui sont gérées dans le connecteur Exchange sont automatiquement synchronisés et ajoutés au connecteur Exchange. Cette synchronisation peut prendre un certain temps pour terminer.

> [!NOTE]
> Si vous avez installé le connecteur Exchange en local et si vous supprimez une connexion Exchange à un moment donné, vous devez désinstaller le connecteur Exchange en local à partir de l’ordinateur sur lequel il a été installé.

## Valider la connexion Exchange

Une fois que vous avez correctement configuré le connecteur Exchange, vous pouvez afficher l’état de la connexion et la dernière tentative de synchronisation. Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) choisir l’espace de travail **administrateur** , sous **Gestion des appareils mobiles**, sélectionnez **Microsoft Exchange**et valider que les détails que vous avez fourni s’affichent sous **Informations de connexion Exchange**.


Vous pouvez également vérifier l’heure et la date de la dernière tentative de synchronisation.
