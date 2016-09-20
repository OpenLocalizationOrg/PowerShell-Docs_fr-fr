---
title: "Configurer l’infrastructure de certificats pour PFX | Microsoft Intune"
description: "Créez et déployez. Profils de certificat PFX."
keywords: 
author: nbigman
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ms.reviewer: vinaybha
ms.suite: ems
ms.openlocfilehash: da988778ab1156597fe19ac40bab155be6046d75
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configuration de l’infrastructure de certificat
Cette rubrique décrit ce que vous avez besoin pour créer et déployer. Profils de certificat PFX.

Pour effectuer un certificat d’authentification de votre organisation, vous avez besoin d’une autorité de Certification d’entreprise.

Pour utiliser. Profils de certificat PFX, en plus de l’autorité de Certification d’entreprise, vous devez également :

-   Un ordinateur sur lequel vous pouvez communiquer avec l’autorité de Certification, ou vous pouvez utiliser l’ordinateur autorité de Certification proprement dit.

-  Le connecteur certificat Intune, qui s’exécute sur l’ordinateur qui peut communiquer avec l’autorité de Certification.

## Description d’infrastructure en local


-    **Domaine Active Directory**: tous les serveurs répertoriés dans cette section (à l’exception du serveur Proxy d’applications Web) doivent être joints à votre domaine Active Directory.

-  **Autorité de certification**: une autorité de Certification Enterprise (CA) qui s’exécute sur une édition entreprise de Windows Server 2008 R2 ou version ultérieure. Une autorité de certification autonome n’est pas pris en charge. Pour obtenir des instructions sur la configuration d’une autorité de Certification, consultez [installer l’autorité de Certification](http://technet.microsoft.com/library/jj125375.aspx).
    Si votre autorité de certification s’exécute Windows Server 2008 R2, vous devez [installer le correctif de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Ordinateur qui peut communiquer avec une autorité de Certification**: vous pouvez également utiliser l’ordinateur autorité de Certification proprement dit.
-  **Connecteur de certificat Intune Microsoft**: la console d’administration Intune vous permet de télécharger le programme d’installation de **Connecteur certificat** (**ndesconnectorssetup.exe**). Puis vous pouvez exécuter **ndesconnectorssetup.exe** sur l’ordinateur sur lequel vous voulez installer le connecteur certificat. Pour. Profils de certificat PFX, installez le connecteur certificat sur l’ordinateur qui communique avec l’autorité de Certification.
-  **Serveur Proxy de l’Application Web** (facultatif) : vous pouvez utiliser un serveur qui exécute Windows Server 2012 R2 ou version ultérieure comme un serveur Proxy d’Application Web (WAP). Cette configuration :
    -  Permet aux périphériques pour recevoir les certificats à l’aide d’une connexion Internet.
    -  Est une recommandation de sécurité lorsque les périphériques se connectent via Internet pour recevoir et renouveler les certificats.

 > [!NOTE]           
> -    Le serveur qui héberge WAP [devez installer une mise à jour](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) qui permet de prise en charge pour les longues URL utilisées par le réseau périphérique d’inscription Service NDES. Cette mise à jour est inclus avec [mise à jour décembre 2014 cumulée](http://support.microsoft.com/kb/3013769), ou individuellement à partir de [KB3011135](http://support.microsoft.com/kb/3011135).
>-  En outre, le serveur que hôtes WAP doivent avoir un certificat SSL qui correspond au nom en cours de publication à des clients externes, ainsi que le certificat SSL qui est utilisée sur le serveur NDES approbation. Activer le serveur WAP pour mettre fin à la connexion SSL à partir de clients et ces certificats créer une nouvelle connexion SSL au serveur NDES.
    Pour plus d’informations sur les certificats pour WAP, consultez la section **planification des certificats** de [publier des Applications à l’aide de Web Proxy d’Application sur la planification](https://technet.microsoft.com/library/dn383650.aspx). Pour obtenir des informations générales sur les serveurs WAP, voir [utilisation des Proxy de l’Application Web](http://technet.microsoft.com/library/dn584113.aspx). |


### Modèles et des certificats

|Objet|Plus d’informations|
|----------|-----------|
|**Modèle de certificat**|Vous configurez ce modèle sur votre autorité de certification émission.|
|**Certificat d’autorité de certification racine de confiance**|Vous exportez sous un fichier **.cer** à partir d’autorité de certification ou n’importe quel appareil qui approuve l’autorité de certification l'émission et déployez aux périphériques en utilisant le profil de certificat autorité de certification approuvée.<br /><br />Vous utilisez un seul certificat d’autorité de certification racine de confiance par la plateforme de système d’exploitation et associez à chaque profil de certificat racine approuvé que vous créez.<br /><br />Vous pouvez utiliser les certificats d’autorité de certification racine de confiance supplémentaires lorsque cela est nécessaire. Par exemple, vous pouvez procéder pour fournir une approbation à une autorité de certification qui vous permet du serveur certificats d’authentification pour les points d’accès Wi-Fi.|


## Configurer votre infrastructure
Avant de configurer les profils de certificat, vous devez effectuer les tâches suivantes. Ces tâches nécessitent une connaissance de Windows Server 2012 R2 et Active Directory certificat Services automatisée :

- **Tâche 1** : configurer des modèles de certificats sur l’autorité de certification.
- **Tâche 2** : activer, installer et configurer le connecteur de certificat Intune.

### Tâche 1 : configurer des modèles de certificats sur l’autorité de certification
Dans cette tâche, vous allez publier le modèle de certificat.

##### Pour configurer l’autorité de certification

1.  Sur l’autorité de certification, utilisez le composant logiciel enfichable modèles de certificats pour créer un modèle personnalisé, ou copier et modifier un modèle existant (par exemple, le modèle de l’utilisateur) pour une utilisation avec. PFX.

    Le modèle doit inclure les éléments suivants :

    -   Spécifiez un convivial **nom complet du modèle** pour le modèle.

    -   Sous l’onglet **Nom de sujet** , sélectionnez **fourni dans la demande**. (Sécurité est appliquée par le module de stratégie Intune NDES).

    -   Sous l’onglet **Extensions** , vérifiez que la **Description de stratégies d’Application** inclut **L’authentification du Client**.

        > [!IMPORTANT]
        > Pour iOS et modèles de certificats de Mac OS X, sous l’onglet **Extensions** , modifiez **L’utilisation de clé** et vérifiez que la **que signature est la preuve d’origine** n’est pas activée.

2.  Passez en revue la **période de validité** sous l’onglet **Général** du modèle. Par défaut, Intune utilise la valeur configurée dans le modèle. Toutefois, vous avez la possibilité pour configurer l’autorité de certification pour autoriser le demandeur spécifier une valeur différente, vous pouvez ensuite définir à partir de la console administrateur Intune. Si vous souhaitez toujours utiliser la valeur dans le modèle, ignorez le reste de cette étape.

    > [!IMPORTANT]
    > IOS les plateformes Mac OS X toujours utilise que la valeur définie dans le modèle, indépendamment des autres configurations vous rendre.

    Pour configurer l’autorité de certification pour autoriser le demandeur spécifier la période de validité, exécutez les commandes suivantes sur l’autorité de certification :

    un.  **certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **démarrage NET certsvc**

3.  Sur l’autorité de certification, utilisez le composant logiciel enfichable Autorité de Certification pour publier le modèle de certificat.

    un.  Sélectionnez le nœud de **Modèles de certificats** , cliquez sur **Action** -&gt; **Nouveau** &gt; **Modèle de certificat**, puis sélectionnez le modèle créé à l’étape 2.

    b.  Valider que le modèle publié en l’affichant dans le dossier **Modèles de certificats** .

4.  Sur l’ordinateur autorité de certification, assurez-vous que l’ordinateur qui héberge le connecteur de certificat Intune a l’autorisation, d’inscription afin qu’il peut accéder au modèle utilisé pour créer la. Profil PFX. Définir cette autorisation sur l’onglet **sécurité** de propriétés de l’ordinateur autorité de certification.

### Tâche 2 : activer, installer et configurer le connecteur de certificat Intune
Dans cette tâche, vous allez :

Télécharger, installer et configurer le connecteur certificat.

##### Pour activer la prise en charge pour le connecteur de certificat

1.  Ouvrez la [console d’administration Intune](https://manage.microsoft.com)et choisissez **administrateur** &gt; **Connecteur certificat**.

2.  Cliquez sur **configurer le connecteur de certificat local**.

3.  Sélectionnez **Activer le lien certificat**et cliquez sur **OK**.

##### Pour télécharger, installer et configurer le connecteur de certificat

1.  Ouvrez la [console d’administration Intune](https://manage.microsoft.com)et choisissez **administrateur** &gt; **Gestion des appareils mobiles** &gt; **Certificat connecteur** &gt; **Télécharger le connecteur certificat**.

2.  Une fois le téléchargement terminé, exécutez le programme d’installation téléchargé (**ndesconnectorssetup.exe**).

  Exécutez le programme d’installation sur l’ordinateur qui peut se connecter avec l’autorité de Certification. Choisissez la. Distribution PFX option et cliquez sur **installer**. Une fois l’installation terminée, passez en créant un profil de certificat comme décrit dans [les profils de certificat configurer](configure-intune-certificate-profiles.md).

   <!-- Not sure about step 3 below -->

3.  Lorsque vous êtes invité pour le certificat client pour le connecteur certificat, choisissez **Sélectionner**, puis sélectionnez le certificat **d’authentification du client** que vous avez installé dans la tâche 3.

    Après avoir sélectionné le certificat d’authentification client, vous revenez à la surface de **Certificat Client pour Microsoft Intune certificat Connector** . Bien que le certificat que vous avez sélectionné n’est pas visible, cliquez sur **suivant** pour afficher les propriétés de ce certificat. Puis cliquez sur **suivant**, puis **installer**.

4.  Une fois l’Assistant terminé, mais avant de fermer l’Assistant, cliquez sur **lancer l’interface utilisateur connecteur certificat**.

    > [!TIP]
    > Si vous fermez l’Assistant avant de lancer l’interface utilisateur connecteur certificat, vous pouvez le rouvrir en exécutant la commande suivante :
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Dans le **certificat connecteur** interface utilisateur :

    un. Sélectionnez **Se connecter** et entrez vos informations d’identification d’administrateur de service Intune ou les informations d’identification d’un administrateur client avec l’autorisation d’administration générale.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b. Sélectionnez l’onglet **Avancé** , puis puis fournissez les informations d’identification d’un compte qui a l’autorisation **émettre et gérer des certificats** sur votre autorité de certification.

    c. Cliquez sur **Appliquer**.

    Vous pouvez à présent fermer l’interface utilisateur connecteur certificat.

6.  Ouvrez une invite et tapez **services.msc**. Appuyez sur **entrée**, avec le bouton droit le **Service de connecteur Intune**, puis sélectionnez **redémarrer**.

Pour valider que le service est en cours d’exécution, ouvrez un navigateur et entrez l’URL suivante, qui doit renvoyer une erreur **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Étapes suivantes
Vous êtes maintenant prêt à configurer les profils de certificat, comme décrit dans [les profils de certificat configurer](Configure-Intune-certificate-profiles.md).
