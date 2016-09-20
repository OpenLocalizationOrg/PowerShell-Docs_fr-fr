---
title: "Effacement à distance utiliser afin de protéger vos données | Microsoft Intune"
description: "Intune offre des fonctionnalités de réinitialisation complète pour supprimer les données d’entreprise sensibles et supprimer l’accès à de nombreuses ressources d’entreprise et sélective."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ms.reviewer: lancecra
ms.suite: ems
ms.openlocfilehash: 309f0701426d6ea22c2c9bd1c3a64393b95c4859
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Protéger vos données avec la réinitialisation complète ou sélective à l’aide de Microsoft Intune
Si, car un appareil n’est plus nécessaire, est toute modification ou a disparu, vous pouvez réinitialiser applications et des données à partir d’appareils gérées avec Intune. Pour ce faire, Intune offre des fonctionnalités de réinitialisation complète et sélective. En outre, les utilisateurs peuvent émettre une commande d’effacement à distance appareil à partir du portail d’entreprise Intune sur appareils privées inscrits dans Intune.

  > [!NOTE]
  > Cette rubrique concerne uniquement à propos de nettoyage des périphériques gérés par la gestion des appareils mobiles Intune. Vous pouvez également utiliser [le portail Azure aperçu](https://portal.azure.com) pour [Effacer les données de la société à partir des applications](wipe-managed-company-app-data-with-microsoft-intune.md). Vous pouvez également [retirer ordinateurs pris en charge avec le logiciel client Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## Réinitialisation complète

**Réinitialisation complète** rétablit un appareil ses paramètres par défaut, suppression de toutes les données de société et les utilisateurs et des paramètres. Le périphérique est supprimé de Intune. Réinitialisation complète est utile pour la réinitialisation d’un périphérique avant de donner à un nouvel utilisateur ou instances où de perte ou de vol de l’appareil.  **En veillant à ne sur la sélection de réinitialisation complète. Données sur le périphérique ne peuvent pas être récupérées**.


> [!Warning]
> Windows 10 RTM périphériques (c'est-à-dire antérieures à la version 1511 Windows 10) avec moins de 4 Go de RAM peuvent être inaccessibles si est réinitialisation. Pour accéder à un appareil Windows 10 qui ne répond plu, vous pouvez démarrer l’appareil à partir d’un lecteur USB ou solution de contournement similaire.

### Effacer à distance un appareil à partir de la console administrateur Intune

1.  Sélectionner les unités de nettoyage. Vous pouvez les retrouver facilement par l’utilisateur ou par périphérique.

    -   **Par l’utilisateur :**

        1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les utilisateurs**.

        2.  Sélectionnez le nom de l’utilisateur dont le dispositif mobile que vous voulez réinitialiser. Sélectionnez **Afficher les propriétés**.

        3.  Sur la page de **Propriétés** de l’utilisateur, sélectionnez **périphériques**, puis le nom de l’appareil mobile que vous voulez réinitialiser. Utiliser la touche Ctrl enfoncée et cliquez pour sélections plusieurs appareils.

    -   **Par périphérique :**

        1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les appareils mobiles**.

      ![Démarrage d’un déclassement ou d’une opération à distance](../media/dev-sa-wipe.png)

        2.  Sélectionnez **périphériques**, puis le nom de l’appareil mobile que vous voulez réinitialiser. Utiliser la touche Ctrl enfoncée et cliquez pour sélections plusieurs appareils.

2.  Choisissez **Retirer/réinitialisation**.

3.  Un message s’affiche, vous invitant à confirmer si vous voulez retirer le périphérique.

    -   Pour effectuer une **réinitialisation sélective** qui supprime uniquement les données et applications d’entreprise, cliquez sur **Oui**.

    -   Pour effectuer une **réinitialisation complète** qui efface toutes les données et les applications et renvoie l’appareil paramètres par défaut, sélectionnez **le périphérique avant de retirer à distance**. Cette action s’applique à toutes les plates-formes sauf Windows 8.1. **Vous ne pouvez pas récupérer les données supprimées par une réinitialisation complète**.

Étant donné l’appareil est allumé et connecté, il prend moins de 15 minutes pour une commande d’effacement de se propager dans tous les types d’appareil.

## Réinitialisation sélective

**Réinitialisation sélective** supprime des données de la société, y compris les données de gestion (MAM) application mobile le cas échéant, les paramètres et les profils de messagerie à partir d’un appareil. Réinitialisation sélective et laisse les données personnelles de l’utilisateur sur le périphérique. Le périphérique est supprimé de Intune. Les tableaux suivants décrivent par plate-forme quelles données sont supprimées et l’effet sur les données qui reste sur l’appareil après une réinitialisation sélective.

**iOS**

|Type de données|iOS|
|-------------|-------|
|Applications d’entreprise et données associées installées par Intune.|Applications sont désinstallées. Données de l’application entreprise sont supprimées.<br /><br />Données d’application à partir des applications Microsoft qui utilise la gestion de l’application mobile sont supprimées. L’application n’est pas supprimée.|
|Paramètres|Configurations qui ont été définies par la stratégie Intune ne s’appliquent plus et les utilisateurs peuvent modifier les paramètres.|
|Paramètres de profil Wi-Fi et VPN|Supprimé|
|Paramètres de profil de certificat|Les certificats supprimés et révoqué.|
|Agent de gestion|Profil de gestion est supprimé.|
|Messagerie|Les profils de messagerie qui sont fournis par Intune sont supprimées et les messages mis en cache sur l’appareil sont supprimé.|
|Dissociez Azure Active Directory (DAS)|Enregistrement AAD supprimé|
|Contacts | Contacts synchronisés directement à partir de l’application avec le carnet d’adresses natif sont supprimés.  Tous les contacts synchronisés du carnet d’adresses native avec une autre source externe ne peut pas être nettoyés. <br /> <br />Pour l’instant, uniquement l’application Outlook est pris en charge.

**Android**

|Type de données|Android|Samsung Android KNOX|
|-------------|-----------|------------------------|
|Liens Web|Supprimé.|Supprimé|
|Applications non géré Google Play|Applications et les données sont toujours installées|Applications et les données sont toujours installées|
|Ligne non géré des applications d’entreprise|Applications et les données sont toujours installées|Désinstallation des applications et données locales de l’application sont supprimées en conséquence. Aucune donnée en dehors de l’application (carte SD, etc.) n’est supprimée.|
|Applications gérées Google Play|Données d’application sont supprimées. Application n’est pas supprimée. Données protégées par le chiffrement MAM en dehors de l’application (carte SD, etc.) sont chiffrées et inutilisable, mais ne sont pas supprimées.|Données d’application sont supprimées. Application n’est pas supprimée. Données protégées par un chiffrement MAM en dehors de l’application (carte SD, etc.) restent chiffrées, mais elles ne sont pas supprimées.|
|Ligne gérée des applications d’entreprise|Données d’application sont supprimées. Application n’est pas supprimée. Données protégées par le chiffrement MAM en dehors de l’application (carte SD, etc.) sont chiffrées et inutilisable, mais ne sont pas supprimées.|Données d’application sont supprimées. Application n’est pas supprimée. Données protégées par le chiffrement MAM en dehors de l’application (carte SD, etc.) sont chiffrées et inutilisable, mais ne sont pas supprimées.|
|Paramètres|Configurations qui ont été définies par la stratégie Intune ne s’appliquent plus et les utilisateurs peuvent modifier les paramètres.|Configurations qui ont été définies par la stratégie Intune ne s’appliquent plus et les utilisateurs peuvent modifier les paramètres.|
|Paramètres de profil Wi-Fi et VPN|Supprimé|Supprimé|
|Paramètres de profil de certificat|Certificats révoqué, mais pas supprimées.|Les certificats supprimés et révoqué.|
|Agent de gestion|Privilèges d’administrateur de l’appareil sont révoqué.|Privilèges d’administrateur de l’appareil sont révoqué.|
|Messagerie|Courrier électronique reçu par l’application Microsoft Outlook pour Android application est supprimé.|Les profils de messagerie qui sont fournis par Intune sont supprimées et les messages mis en cache sur l’appareil sont supprimé.|
|Dissociez Azure Active Directory (DAS)|Enregistrement AAD supprimé|Enregistrement AAD supprimé|
|Contacts | Contacts synchronisés directement à partir de l’application avec le carnet d’adresses natif sont supprimés.  Tous les contacts synchronisés du carnet d’adresses native avec une autre source externe ne peut pas être nettoyés. <br /> <br />Pour l’instant, uniquement l’application Outlook est pris en charge.|Contacts synchronisés directement à partir de l’application avec le carnet d’adresses natif sont supprimés.  Tous les contacts synchronisés du carnet d’adresses native avec une autre source externe ne peut pas être nettoyés. <br /> <br />Pour l’instant, uniquement l’application Outlook est pris en charge.

**Windows**

|Type de données|Windows 8.1 (MDM) et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Applications d’entreprise et données associées installées par Intune.|Fichiers protégés par EFS auront leur clé révoqué et l’utilisateur ne sera pas en mesure d’ouvrir les fichiers.|Ne supprime pas les applications d’entreprise.|Applications installées à l’origine via le portail d’entreprise sont désinstallées. Données de l’application entreprise sont supprimées.|Désinstallation des applications et chargement de version test clés sont supprimées.|
|Paramètres|Configurations qui ont été définies par la stratégie Intune ne s’appliquent plus et les utilisateurs peuvent modifier les paramètres.|Configurations qui ont été définies par la stratégie Intune ne s’appliquent plus et les utilisateurs peuvent modifier les paramètres.|Configurations qui ont été définies par la stratégie Intune ne s’appliquent plus et les utilisateurs peuvent modifier les paramètres.|Configurations qui ont été définies par la stratégie Intune ne s’appliquent plus et les utilisateurs peuvent modifier les paramètres.|
|Paramètres de profil Wi-Fi et VPN|Supprimé|Supprimé|Non pris en charge|Supprimé|
|Paramètres de profil de certificat|Les certificats supprimés et révoqué.|Les certificats supprimés et révoqué.|Non pris en charge|Les certificats supprimés et révoqué.|
|Messagerie|Supprime le message électronique qui est QU'EFS activé qui inclut l’application de messagerie pour la messagerie de Windows et les pièces jointes.|Non pris en charge|Les profils de messagerie qui sont fournis par Intune sont supprimées et les messages mis en cache sur l’appareil sont supprimé.|Supprime le message électronique qui est QU'EFS activé qui inclut l’application de messagerie pour la messagerie de Windows et les pièces jointes. Supprime les comptes de messagerie qui ont été mis en service par Intune.|
|Dissociez Azure Active Directory (DAS)|N°|N°|Enregistrement AAD supprimé|Non applicable. Windows 10 n'effectue pas prise en charge de réinitialisation sélective et Azure Active Directory rejoint appareils|

## Réinitialiser le chiffrement système de fichiers ()-activé du contenu
Réinitialisation sélective et de contenu chiffrés EFS est pris en charge par Windows 8.1 et Windows RT 8.1. Les éléments suivants s’appliquent à une réinitialisation sélective de contenu prenant en charge EFS :

-   Uniquement les applications et les données qui sont protégées par EFS en utilisant le même domaine Internet comme le compte Intune sont réinitialisé de manière sélective. Pour plus d’informations, voir [Windows à distance sélectif pour via la gestion des données](http://technet.microsoft.com/library/dn486874.aspx).

-   S’il existe que des modifications sont apportées au domaine associé avec EFS, les modifications peuvent prendre jusqu'à 48 heures avant d’applications et de données à l’aide du nouveau domaine peuvent être réinitialisé de manière sélective.

-   Chaque domaine est enregistré avec Intune efface.

Les données et les applications qui sont actuellement prises en charge par sélective EFS sont :

-   Application courrier pour Windows

-   Utiliser des dossiers

-   Fichiers et dossiers chiffrés EFS. Pour plus d’informations, voir [meilleures pratiques pour le système de fichiers le chiffrement](http://support.microsoft.com/kb/223316).

-   Si votre organisation gère son identité dans Active Directory, il doit utiliser l’outil de synchronisation d’annuaires (DirSync) vers des informations de synchronisation dans AAD pour sélective EFS fonctionne correctement.  Pour plus d’informations sur la synchronisation d’annuaire, consultez [Scénario de synchronisation d’annuaire](http://technet.microsoft.com/library/dn441212.aspx) dans la documentation Azure Active Directory.

## Moniteur retraite, réinitialiser et supprimer des actions
Pour obtenir un rapport de périphériques qui ont été déclassé, est réinitialisation ou supprimés et qui a effectué l’action :

1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), cliquez sur **rapports** &gt; **Appareil l’historique des rapports**.

2.  Taper une date de début et de fin pour le rapport, puis sélectionnez **Afficher le rapport**.


### Voir aussi
[Retirer des appareils mobiles](retire-devices-from-microsoft-intune-management.md)

[Windows sélectifs à distance pour la gestion des données appareil](http://technet.microsoft.com/library/dn486874.aspx)
