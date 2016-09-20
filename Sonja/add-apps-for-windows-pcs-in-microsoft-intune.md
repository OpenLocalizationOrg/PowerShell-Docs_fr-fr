---
title: "Ajouter des applications pour les PC Windows qui s’exécutent le logiciel client Intune | Microsoft Intune"
description: "Utilisez les informations dans cette rubrique pour savoir comment ajouter des applications pour les PC Windows à Intune avant de les déployer."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 33ef6a417c38ab04095afc8fb7573ea92253f229
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Ajouter des applications pour les PC Windows qui s’exécutent le logiciel client Intune

Utilisez les informations dans cette rubrique pour savoir comment ajouter des applications à Intune avant de les déployer.

> [!IMPORTANT]
> Les informations contenues dans cette rubrique vous permettent d’ajouter des applications pour les PC Windows que vous gérez à l’aide du logiciel client Intune. Si vous voulez ajouter des applications pour inscrits PC Windows et d’autres appareils mobiles, voir [Ajouter des applications pour les appareils mobiles dans Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).


## Ajouter l’application
Vous utilisez l’Éditeur du logiciel Intune pour configurer les propriétés de l’application et téléchargez-le sur votre espace de stockage cloud à l’aide de la procédure suivante :

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **applications** &gt; **Ajouter des applications** pour démarrer l’Éditeur du logiciel Intune.

    > [!TIP]
    > Vous devrez peut-être entrer votre nom d’utilisateur Intune et mot de passe avant l’éditeur démarre.

2.  Dans la page **d’installation du logiciel** de l’éditeur, sous **Sélectionnez comment ce logiciel est accessibles aux périphériques**, choisissez le **programme d’installation logicielle**, puis spécifiez :

    - **Sélectionnez le type de fichier de programme d’installation de logiciel**. Indique le type du logiciel que vous voulez déployer. Pour un PC Windows, cliquez sur **Windows Installer**.
    - **Indiquez l’emplacement des fichiers d’installation du logiciel**. Entrez l’emplacement des fichiers d’installation, ou cliquez sur **Parcourir** pour sélectionner l’emplacement à partir d’une liste.
    - **Inclure des fichiers supplémentaires et des sous-dossiers dans le même dossier**. Certains logiciels qui utilise Windows Installer nécessite de fichiers pris en charge. Ces sont généralement stockées dans le même dossier que les fichiers d’installation. Sélectionnez cette option si vous souhaitez également déployer ces fichiers pris en charge.

    Par exemple, si vous souhaitez publier une application nommée Application.msi au Intune, la page se présente comme suit : ![page de configuration de logiciel de l’éditeur](./media/publisher-for-pc.png)

   Ce type d’installation utilise certains de votre espace de stockage cloud.

3.  Dans la page **description de logiciel** , vous devez configurer les éléments suivants.

    > [!NOTE]
    > En fonction du fichier d’installation que vous utilisez, certaines de ces valeurs éventuellement automatiquement saisies ou qu’ils peuvent ne pas apparaître.

    - **Publisher**. Entrez le nom de l’éditeur de l’application.
    - **Nom**. Entrez le nom de l’application tel qu’il s’affichera dans le portail d’entreprise.<br />Assurez-vous que tous les noms d’application que vous utilisez sont uniques. Si le même nom d’application existe à deux reprises, seul des applications s’affichera aux utilisateurs dans le portail d’entreprise.
    - **Description**. Entrez une description pour l’application. Cela sera affiché pour les utilisateurs dans le portail d’entreprise.
    - **URL plus d’informations sur** (facultatif). Entrez l’URL d’un site Web qui contient des informations sur cette application. L’URL sera affichée pour les utilisateurs dans le portail d’entreprise.
    - **URL de la confidentialité** (facultatif). Entrez l’URL d’un site Web qui contient des informations de confidentialité pour cette application. L’URL sera affichée pour les utilisateurs dans le portail d’entreprise.
    - **Catégorie** (facultatif). Sélectionnez une des catégories application intégrée. Cela facilitera aux utilisateurs de trouver l’application lorsqu’ils parcourent le portail d’entreprise.
    - **Icône** (facultatif). Télécharger une icône qui sera associée à l’application. Il s’agit de l’icône qui s’affichera avec l’application lorsque les utilisateurs parcourir le portail d’entreprise.

4.  Dans la page **Configuration requise** , sélectionnez la configuration requise qui doit être remplie avant de pouvoir installer l’application. Choisir :

    - **Architecture**. Indiquez si cette application peut être installée sur les deux systèmes d’exploitation, 32 bits ou 64 bits.
    - **Système d’exploitation**. Sélectionnez le système d’exploitation minimal sur laquelle cette application peut être installée.

5.  Dans la page **règles de détection** , vous pouvez configurer des règles pour détecter si l’application que vous configurez est déjà installée sur un PC. Ou bien, vous pouvez utiliser les règles de détection par défaut pour remplacer automatiquement les versions antérieures de l’application. Cette option est pour Windows Installer (fichiers .exe uniquement).

    Les règles que vous pouvez configurer sont :
    - **Fichier existe**. Spécifiez le chemin d’accès au fichier que vous souhaitez détecter. Vous pouvez effectuer des recherches sous **% ProgramFiles%** (qui recherche **Program Files**\&lt ; chemin d’accès&gt; et **Program Files (x86)**\&lt ; chemin d’accès&gt;) sur le PC ou **%systemdrive%** (les recherches à partir du lecteur racine du PC, généralement le lecteur C).
    - **Code de produit MSI existe**. Cliquez sur **Parcourir** pour choisir le fichier Windows Installer (.msi) que vous souhaitez détecter.
    - **Clé de Registre existe**. Spécifier une clé de Registre qui commence par **HKEY_LOCAL_MACHINE\**. Les chemins d’accès du Registre 32 bits et 64 bits sont recherchés. Si la clé que vous avez spécifié existe dans les deux emplacements, la règle de détection est remplie.

    Si l’application satisfait à une des règles que vous avez configurée, elle ne sera pas installé.

6.  Pour **Windows Installer** type uniquement (.msi et fichiers .exe) : dans la page **des arguments de ligne de commande** , choisissez si vous souhaitez fournir des arguments de ligne de commande facultatifs pour le programme d’installation. Par exemple, certains programmes d’installation peuvent prendre en charge l' **argument/q** pour installer en mode silencieux sans intervention de l’utilisateur.

7.  Pour **Windows Installer** fichier type (.exe uniquement) : dans la page de **codes de retour** , vous pouvez ajouter de nouveaux codes d’erreur Intune interprète lorsque l’application est installée sur un PC Windows géré.

    Par défaut, Intune utilise des codes de retour normalisé pour signaler l’échec ou la réussite d’une installation de package d’application : **0** (succès) ou **3010** (succès avec redémarrage). Vous pouvez également ajouter vos propres codes de retour à cette liste. Si vous spécifiez une liste des codes de retour et l’installation de l’application renvoie un code qui ne figure pas dans la liste, il est interprété comme une défaillance.

8.  Dans la page **Résumé** , passez en revue les informations que vous avez spécifié. Lorsque vous êtes prêt, cliquez sur **Télécharger**.

9. Cliquez sur **Fermer** pour terminer.

L’application s’affiche sur le nœud **applications** de l’espace de travail **d’applications** .

## Étapes suivantes

Une fois que vous avez créé une application, l’étape suivante consiste à déployer. Pour en savoir plus, voir [déployer des applications dans Microsoft Intune](deploy-apps.md).
