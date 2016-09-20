---
title: Ajouter des applications pour les appareils inscrits | Microsoft Intune
description: "Avant de déployer une application, vous devez l’ajouter à Intune. Il est disponible dans la console Intune, où vous pouvez déployer et gérer."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: 0951a8c8ae635fed089e7bbf87018282a73daf74
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Ajouter des applications pour les appareils inscrits à Intune

Avant de déployer ou gérer une application, vous devez l’ajouter à Microsoft Intune. Cette rubrique vous montre comment ajouter des applications pour les appareils inscrits.


> [!IMPORTANT]
> Les informations contenues dans cette rubrique vous permettent d’ajouter des applications que vous voulez déployer sur inscrit appareils et inscrit PC Windows. Si vous voulez ajouter des applications pour les PC Windows que vous gérez à l’aide du logiciel client Intune, voir [Ajouter des applications pour les PC Windows dans Microsoft Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## Ajouter l’application
Vous utilisez l’Éditeur du logiciel Intune pour configurer les propriétés de l’application et, le cas échéant, téléchargez-le sur votre espace de stockage cloud. Procédez comme suit :

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **applications** &gt; **Ajouter des applications** pour démarrer l’Éditeur du logiciel Intune.

    > [!TIP]
    > Vous devrez peut-être entrer votre nom d’utilisateur Intune et mot de passe avant l’éditeur démarre.

2.  Dans la page **d’installation du logiciel** de l’éditeur, choisissez une des options suivantes pour **Sélectionner comment ce logiciel est accessibles aux appareils**:
    - **Programme d’installation logicielle**, pour les applications avec l’extension **.msi** ou **.exe**:
        - **Sélectionnez le type de fichier de programme d’installation de logiciel**. Indique le type du logiciel que vous voulez déployer. Par exemple, si vous voulez installer une application iOS, choisissez **Package d’application pour iOS (& #42 ;. fichier de loi)**.
        - **Indiquez l’emplacement des fichiers d’installation du logiciel**. Entrez l’emplacement des fichiers d’installation, ou cliquez sur **Parcourir** pour sélectionner l’emplacement à partir d’une liste.
        - **Inclure des fichiers supplémentaires et des sous-dossiers dans le même dossier**. Cette option est pour le type de fichier **Windows Installer** uniquement.<br>Certains logiciels qui utilise Windows Installer nécessite prenant en charge les fichiers qui se trouvent en général dans le même dossier que les fichiers d’installation. Sélectionnez cette option si vous souhaitez également déployer ces fichiers.<br>Ce type d’installation utilise certains de votre espace de stockage cloud.

  -   **Lien externe**, pour les applications que vous souhaitez créer en spécifiant une liaison à un app store :

        - **Spécifier l’URL**. Spécifiez l’URL d’une des opérations suivantes :
            - Application du store URL de l’application que vous voulez déployer. Par exemple, si vous voulez déployer l’application de bureau à distance Microsoft pour Android, spécifiez **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android**.<br>Pour rechercher l’URL de l’application, utilisez un moteur de recherche pour trouver la page magasin qui contient l’application. Par exemple, pour rechercher l’application de bureau à distance, vous pouvez rechercher pour **Microsoft Remote Desktop Android**.
            - Un site Web. Intune déployez une icône de raccourci du site sur le périphérique (également connu sous forme de clip web).
            - Une application sur le web. Intune déployez une icône de raccourci pour l’application sur l’appareil.
        - **Requièrent un navigateur géré pour ouvrir ce lien (Android et iOS uniquement)**. Lorsque vous déployez une application web ou site Web aux utilisateurs un lien, ils seront en mesure d’ouvrir uniquement dans le navigateur géré Intune. Ce navigateur doit être installé sur leur appareil.<br>Pour plus d’informations sur le navigateur géré, voir [accès Internet gérer à l’aide pour les stratégies de navigateur avec Microsoft Intune gérés](manage-internet-access-using-managed-browser-policies.md).<br>Ce type d’installation n’utilise pas un de l’espace de stockage cloud.

  -   **Application d’iOS gérés à partir de l’app store**, gratuitement applications du iTunes store que vous souhaitez gérer les stratégies de gestion (MAM) des applications mobiles :

        - **Spécifier l’URL**. Entrez l’URL de la banque d’application de l’application que vous voulez déployer. Par exemple, si vous voulez déployer l’application Microsoft travail dossiers pour iOS, spécifiez **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8**.<br>Ce type d’installation n’utilise pas un de l’espace de stockage cloud.

        Par exemple, si vous voulez déployer l’application Microsoft Word à partir du magasin iTunes pour appareils mobiles, la page présente comme ceci :

        ![Logiciel Intune Publisher](./media/publisher-for-mobile.png)

3.  Dans la page **description de logiciel** , vous devez configurer les éléments suivants :

    > [!TIP]
    > Selon le type d’installation que vous utilisez, certaines de ces valeurs aurait pu être automatiquement saisie.

    - **Publisher**. Entrez le nom de l’éditeur de l’application.
    - **Nom**. Entrez le nom de l’application tel qu’il s’affichera dans le portail d’entreprise.<br>Assurez-vous que tous les noms d’application que vous utilisez sont uniques. Si le même nom d’application existe à deux reprises, seul des applications s’affichera aux utilisateurs dans le portail d’entreprise.
    - **Description**. Entrez une description pour l’application. Cela sera affiché pour les utilisateurs dans le portail d’entreprise.
    - **Pour plus d’informations du logiciel**. Ceci est disponible uniquement si vous avez sélectionné le **programme d’installation du logiciel**. Si vous le souhaitez, entrez l’URL d’un site Web qui contient des informations sur cette application. L’URL sera affichée pour les utilisateurs dans le portail d’entreprise.
    - **URL de la confidentialité**. Ceci est disponible uniquement si vous avez sélectionné le **programme d’installation du logiciel**. Si vous le souhaitez, entrez l’URL d’un site Web qui contient des informations de confidentialité pour cette application. L’URL sera affichée pour les utilisateurs dans le portail d’entreprise.
    - **Catégorie** (facultatif). Sélectionnez une des catégories application intégrée. Cela facilitera aux utilisateurs de trouver l’application lorsqu’ils parcourent le portail d’entreprise.
    - **Ceci comme une application proposée afficher et mettre en surbrillance dans le portail d’entreprise**. Entraîne l’affichage l’application dans la page principale de l’application portail d’entreprise lorsque les utilisateurs rechercher les applications.
    - **Icône** (facultatif). Télécharger une icône qui sera associée à l’application. Il s’agit de l’icône qui s’affichera avec l’application lorsque les utilisateurs parcourir le portail d’entreprise.

        Dans cet exemple, vous avez configuré une description pour l’application Microsoft Word pour iOS :

        ![Exemple de description logiciel](./media/ios-software-description.png)

4.  Dans la page **Configuration requise** , sélectionnez la configuration requise doit être définie avant que l’application peut être installée sur un appareil. Par exemple, pour un package d’application pour iOS, vous pouvez sélectionner la version minimale d’iOS obligatoire. En outre, vous pouvez sélectionner le type d’appareil sur lequel il doit être, par exemple, un iPhone ou un iPad.

    > [!TIP]
    > La page **Configuration requise** s’affiche pas pour tous les types d’applications.

5.  Autres pages de l’Assistant sont affichent lorsque vous choisissez le type de fichier **Windows Installer** . Ce type de fichier est utilisé lorsque vous déployez le logiciel sur des PC qui exécutent Windows 10 ou version ultérieure qui sont inscrits avec Intune.

6.  Dans la page **Résumé** , passez en revue les informations que vous avez spécifié. Lorsque vous êtes prêt, cliquez sur **Télécharger**.

7.  Cliquez sur **Fermer** pour terminer.

L’application s’affiche sur le nœud **applications** de l’espace de travail **d’applications** .

## Exemple : déploiement d’applications .msi sur les appareils Windows 10
Dans cette vidéo quatre minutes, vous découvrirez comment déployer des applications Windows Installer (.msi) aux périphériques inscrits qui exécutent Windows 10.<br><br>

<iframe src="https://channel9.msdn.com/Series/How-to-Control-the-Uncontrolled/6--How-to-Deploy-MSI-Applications-to-Windows-10-Using-Intune-and-Mobile-Device-Management-MDM/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>

## Étapes suivantes

Une fois que vous avez créé une application, l’étape suivante consiste à déployer. Pour en savoir plus, voir [déployer des applications dans Microsoft Intune](deploy-apps.md).
