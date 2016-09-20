---
title: "Gérer les PC avec le logiciel client | Microsoft Intune"
description: "Gérer les PC Windows en installant le logiciel client Intune."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 1df2507df6bd3fc7748c10c1f398fbfdb8958a18
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer les PC Windows avec le logiciel client Intune PC
Au lieu de l' [inscription des PC Windows en tant que les appareils mobiles](set-up-windows-device-management-with-microsoft-intune.md), vous pouvez inscrire et gérer des PC Windows en installant le logiciel client Intune.

Intune gère PC Windows à l’aide de stratégies à la manière dont les objets de stratégie de groupe Windows Server Active Directory Domain Services (AD DS) (stratégie de groupe) effectuez. Si vous allez gérer les ordinateurs à un domaine Active Directory avec Intune, vous devez [vous assurer que les stratégies Intune ne sont pas en conflit avec les objets de stratégie](resolve-gpo-and-microsoft-intune-policy-conflicts.md) qui sont en place pour votre organisation.

Le client de logiciel Intune prend en charge les [fonctionnalités de gestion qui permettent de protéger le PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) en gérant des mises à jour logicielles, le pare-feu Windows et Endpoint Protection, PC gérés par le Intune logiciel client ne peut pas être ciblé avec d’autres stratégies Intune, y compris les paramètres de stratégie **Windows** spécifiques à la gestion des appareils mobiles.

> [!NOTE]
> Appareils exécutant Windows 8.1 ou version ultérieure peuvent être gérés par le client Intune ou les appareils mobiles. Cette rubrique s’applique aux ordinateurs qui exécutent le logiciel client Intune. Installer le client Intune et s’inscrire à la gestion des appareils mobiles ne sont pas pris en charge.

## Configuration requise pour la gestion des clients Intune PC

**Matériel**: Voici la configuration minimale requise pour l’installation du client Intune :

|Configuration requise|Plus d’informations|
|---------------|--------------------|
|Réseau|Le client nécessite le PC pour se connecter à Internet.|
|Processeur et la mémoire|Reportez-vous à la processeur et RAM requise pour le système d’exploitation du PC.|
|Espace disque|200 Mo d’espace disque disponible avant d’installer le logiciel client.|

**Logiciel**: configuration logicielle requise pour l’installation du client sont les suivantes :

|Configuration requise|Plus d’informations|
|---------------|--------------------|
|Système d'exploitation | Appareil Windows exécutant Windows Vista ou version ultérieure. Versions Édition familiale ne sont pas pris en charge.|
|Autorisations d’administration|Le compte qui installe le logiciel client doit disposer des autorisations d’administrateur local sur votre appareil.|
|Programme d’installation de Windows 3.1|Le PC doit avoir au minimum Windows Installer 3.1.<br /><br />Pour afficher la version de Windows Installer sur un PC :<br /><br />-Sur PC, avec le bouton droit **%windir%\System32\msiexec.exe**, puis cliquez sur **Propriétés**.<br /><br />Vous pouvez télécharger la dernière version de Windows Installer à partir de [Windows Installer redistribuables](http://go.microsoft.com/fwlink/?LinkID=234258) sur le site Web Microsoft Developer Network.|
|Supprimer le logiciel client incompatible|Avant d’installer le logiciel client Intune, vous devez désinstaller le logiciel n’importe quel client Gestionnaire de Configuration ou de système Management Server à partir de ce PC.|

## Gestion de l’ordinateur avec l’ordinateur client Intune
Une fois le logiciel client Intune est installé, les fonctionnalités de gestion des incluent : [Gestion des applications](deploy-apps-in-microsoft-intune.md), [surveillance en temps réel Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md), [Gestion des paramètres du pare-feu Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventaire matérielle et logicielle, contrôle à distance (à l’aide de requêtes d’assistance à distance), [paramètres de mise à jour logicielle](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)et des paramètres de création de rapports de conformité.

Certaines options de gestion disponibles sur les PC gérées comme les appareils mobiles ne sont pas disponibles pour les PC logiciels gérés par le client, y compris :

-   Réinitialisation complète (sélective est disponible)
-   Accès conditionnel
-   Stratégies de Windows différent de stratégies de **gestion de l’ordinateur**

![Modèle de stratégies pour les PC Windows](../media/pc_policy_template.png)

Outre les actions de l’agent de client Intune prises localement sur des ordinateurs individuels, vous pouvez également utiliser la console d’administration Intune à effectuer d’autres [tâches de gestion courantes ordinateur](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) sur PC Windows avec le client installé à :

-   Afficher des informations de stock matérielle et logicielle sur les ordinateurs gérés

-   Redémarrer l’ordinateur à distance

-   Retirer un ordinateur pour désinstaller le logiciel client et supprimer de la gestion avec Intune

-   Lier des utilisateurs pour les ordinateurs gérés spécifiques

-   Répondre à des demandes d’assistance à distance

L’agent du client Intune exécute généralement silencieusement en arrière-plan sans qu’il soit nécessaire pour quantité utilisateur interaction ou résolution des problèmes. Toutefois, devez vous avez besoin d’aide pour résoudre les problèmes de gestion ordinateur, il existe plusieurs [ressources disponibles pour vous aider à les résoudre](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).
