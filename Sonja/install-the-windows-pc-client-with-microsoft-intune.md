---
title: Installer le logiciel client PC | Microsoft Intune
description: "Utilisez ce guide pour vous aider à votre PC Windows gérés par le logiciel client Microsoft Intune."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: d59a0a08b6d72d2b2cb9462d99fc8e435fe0fba8
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Installer le logiciel client Intune sur PC Windows
PC Windows peut être inscrit en installant le logiciel client Intune. Le logiciel client Intune peut être installé des façons suivantes :

- Installation manuelle
- Installer à l’aide de la stratégie de groupe
- Inclure dans une image de disque
- Installés par les utilisateurs

## Télécharger le logiciel client Intune

Toutes les méthodes, à l’exception de l’endroit où les utilisateurs installer le logiciel client Intune eux-mêmes, nécessitent télécharger le logiciel afin qu’il peut être déployé.

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **administrateur** &gt; **Téléchargement du logiciel Client**

  ![Télécharger le client Intune PC](../media/pc-sa-client-download.png)

2.  Dans la page de **Téléchargement du logiciel Client** , cliquez sur **Télécharger le logiciel Client** et enregistrez le package **Microsoft_Intune_Setup.zip** contenant le logiciel dans un emplacement sécurisé sur votre réseau.

    > [!NOTE]
    > Le package d’installation de logiciel client Intune contient des informations concernant votre compte. Si les utilisateurs non autorisés à accéder au package d’installation, ils peuvent s’inscrire ordinateurs au compte qui est représenté par son certificat incorporé.

3.  Extraire le contenu du package d’installation à l’emplacement sécurisé sur votre réseau.

    > [!IMPORTANT]
    > Ne pas renommer ou supprimer le fichier **ACCOUNTCERT** qui est extrait ou sur l’installation du logiciel client échouera.

## Déployer manuellement

1.  Sur un ordinateur, accédez au dossier où se trouvent les fichiers d’installation du logiciel client et puis exécutez **Microsoft_Intune_Setup.exe** pour installer le logiciel client.

    > [!NOTE]
    > L’état de l’installation s’affiche lorsque vous pointez sur l’icône dans la barre des tâches sur l’ordinateur client.

## Déployer avec à l’aide de la stratégie de groupe

1.  Dans le dossier qui contient les fichiers **Microsoft_Intune_Setup.exe** et **MicrosoftIntune.accountcert**, exécutez la commande suivante pour extraire les programmes d’installation basé sur Windows Installer pour les ordinateurs 32 bits et 64 bits :

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Copiez le fichier **Microsoft_Intune_x86.msi** , le fichier **Microsoft_Intune_x64.msi** et le fichier **MicrosoftIntune.accountcert** vers un emplacement réseau accessible par tous les ordinateurs auquel le logiciel client doit être installé.

    > [!IMPORTANT]
    > Ne pas séparer ou renommer les fichiers ou le client de l’installation de logiciel échouera.

3.  Utiliser la stratégie de groupe pour déployer le logiciel sur les ordinateurs sur votre réseau.

    Pour plus d’informations sur l’utilisation de stratégie de groupe pour déployer automatiquement des logiciels, consultez la documentation de Windows Server.

## Installer dans le cadre d’une image
Vous pouvez déployer le logiciel client Intune sur ordinateurs dans le cadre d’une image de système d’exploitation à l’aide de cet exemple de procédure comme base :

1.  Copiez les fichiers d’installation client **Microsoft_Intune_Setup.exe** et **MicrosoftIntune.accountcert** dans le dossier **%Systemdrive%\Temp\Microsoft_Intune_Setup** sur l’ordinateur de référence.

2.  Créez l’entrée de Registre **WindowsIntuneEnrollPending** en ajoutant la commande suivante pour le script **SetupComplete.cmd** :

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  Ajouter la commande suivante à **setupcomplete.cmd** pour exécuter le package d’inscription avec l’argument de ligne de commande /PrepareEnroll :

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > Le script **SetupComplete.cmd** permet d’apporter des modifications au système avant qu’un utilisateur journaux sur l’installation de Windows. L’argument de ligne de commande **/PrepareEnroll** prépare un ordinateur cible afin de s’inscrire automatiquement Intune après l’installation de Windows.

4.  Placer **SetupComplete.cmd** dans le dossier **%Windir%\Setup\Scripts** sur l’ordinateur de référence.

5.  Capturer une image de l’ordinateur de référence, puis déployez ceci pour les ordinateurs cibles.

Au redémarrage de l’ordinateur cible à la fin de l’installation de Windows, la clé de Registre **WindowsIntuneEnrollPending** est créée. Le package d’inscription vérifie si l’inscription de l’ordinateur. Si l’ordinateur est inscrit, aucune autre action n’est considérée. Si l’ordinateur n’est pas inscrit, le package d’inscription crée une tâche de l’inscription automatique Microsoft Intune.

Lorsque la tâche de l’inscription automatique s’exécute à l’heure planifiée, il vérifie l’existence de la valeur de Registre **WindowsIntuneEnrollPending** , et il tente d’inscrire le PC ciblé dans Intune. Si l’inscription échoue pour une raison quelconque, l’inscription est retentée la prochaine fois que la tâche est exécutée. Les tentatives continuent pour une période d’un mois.

La tâche d’inscription automatique Intune et la valeur de Registre **WindowsIntuneEnrollPending** le certificat de compte sont supprimés à partir de l’ordinateur cible lors de l’inscription a réussi ou après un mois.

## Demandez à l’utilisateur s’inscrire eux-mêmes

Les utilisateurs peuvent installer le logiciel client Intune en accédant à [http://portal.manage.microsoft.com](http://portal..manage.microsoft.com). Si le portail web peut détecter le périphérique est un PC Windows, il est invité à s’inscrire PC en téléchargeant le logiciel client Intune. Une fois téléchargé, les utilisateurs peuvent installer le logiciel pour importer leurs PC dans gestion.

![Portail Intune vous invitant à télécharger le client de logiciel Intune](../media/software-client-download.png)

## Surveiller et valider le déploiement de client réussie
Utilisez une des procédures suivantes pour vous aider à contrôler et valider le déploiement client réussie.

### Pour vérifier l’installation du logiciel client à partir de la console Administrateur Microsoft Intune

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **groupes** &gt; **Tous les périphériques** &gt; **Tous les ordinateurs**.

2.  Faites défiler la liste des ordinateurs pour rechercher des ordinateurs gérés communiquent avec Intune ou pour rechercher un spécifique d’ordinateur géré en tapant le nom d’ordinateur ou une partie du nom, dans la zone **Rechercher des appareils mobiles** .

3.  Examiner l’état de l’ordinateur dans le volet inférieur de la console et résoudre les erreurs.

### Pour créer un rapport d’inventaire ordinateur pour afficher toutes les inscrit ordinateurs

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **rapports** &gt; **Ordinateur inventaire rapports**.

2.  Dans la page **Créer un nouveau rapport** , laissez tous les champs comme la valeur par défaut (sauf si vous souhaitez appliquer des filtres) des valeurs, cliquez sur **Afficher le rapport**.

3.  La page de **Rapport d’inventaire ordinateur** s’ouvre dans une nouvelle fenêtre qui s’affiche tous les ordinateurs qui sont correctement inscrits dans Intune.

    > [!TIP]
    > Cliquez sur un en-tête de colonne du rapport pour trier la liste en fonction du contenu de cette colonne.


### Voir aussi
[Gérer les PC Windows avec Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
[résoudre les problèmes d’installation du client](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune)
