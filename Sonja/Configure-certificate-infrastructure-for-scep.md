---
title: "Configurer l’infrastructure de certificats pour SCEP | Microsoft Intune"
description: "Infrastructure pour créer et déployer des profils de certificat SCEP."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4ae137ae-34e5-4a45-950c-983de831270f
ms.reviewer: kmyrup
ms.suite: ems
ms.openlocfilehash: adef720c31eea978dc899f62e1eef60af2812a3d
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configurer l’infrastructure de certificats pour SCEP
Cette rubrique décrit quelle infrastructure que vous avez besoin pour créer et déployer des profils de certificat SCEP.

### Infrastructure en local

-    **Domaine Active Directory**: tous les serveurs répertoriés dans cette section (à l’exception du serveur Proxy d’applications Web) doivent être joints à votre domaine Active Directory.

-  **Autorité de certification** (CA) : une autorité de Certification Enterprise (CA) qui s’exécute sur une édition entreprise de Windows Server 2008 R2 ou version ultérieure. Une autorité de certification autonome n’est pas pris en charge. Pour obtenir des instructions sur la configuration d’une autorité de Certification, consultez [installer l’autorité de Certification](http://technet.microsoft.com/library/jj125375.aspx).
    Si votre autorité de certification s’exécute Windows Server 2008 R2, vous devez [installer le correctif de KB2483564](http://support.microsoft.com/kb/2483564/).
J’ai
-  **Serveur NDES**: sur un serveur qui exécute Windows Server 2012 R2 ou versions ultérieures, vous devez configurer la le réseau périphérique d’inscription Service NDES. Intune ne prend pas en charge à l’aide de NDES lorsqu’il s’exécute sur un serveur qui exécute également l’autorité de certification d’entreprise. Voir [Conseils de Service de réseau appareil d’inscription](http://technet.microsoft.com/library/hh831498.aspx) pour obtenir des instructions sur la configuration de Windows Server 2012 R2 héberger le Service d’inscription de périphériques réseau. Le serveur NDES doit être domaine joint au domaine qui héberge l’autorité de certification et ne pas être sur le même serveur que l’autorité de certification. Vous trouverez plus d’informations sur le déploiement du serveur NDES dans une forêt distincte, le réseau isolé ou le domaine interne à [l’aide d’un Module de stratégie avec le Service d’inscription de périphériques réseau](https://technet.microsoft.com/en-us/library/dn473016.aspx).

-  **Connecteur de certificat Intune Microsoft**: la console d’administration Intune vous permet de télécharger le programme d’installation de **Connecteur certificat** (**ndesconnectorssetup.exe**). Puis vous pouvez exécuter **ndesconnectorssetup.exe** sur l’ordinateur sur lequel vous voulez installer le connecteur certificat.
-  **Serveur Proxy d’Application Web** (facultatif) : vous pouvez utiliser un serveur qui exécute Windows Server 2012 R2 ou version ultérieure comme un serveur Proxy d’Application Web (WAP). Cette configuration :
    -  Permet aux périphériques pour recevoir les certificats à l’aide d’une connexion Internet.
    -  Est une recommandation de sécurité lorsque les périphériques se connectent via Internet pour recevoir et renouveler les certificats.

 > [!NOTE]           
> -    Le serveur qui héberge WAP [devez installer une mise à jour](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) qui permet de prise en charge pour les longues URL utilisées par le Service d’inscription de périphériques réseau. Cette mise à jour est inclus avec [mise à jour décembre 2014 cumulée](http://support.microsoft.com/kb/3013769), ou individuellement à partir de [KB3011135](http://support.microsoft.com/kb/3011135).
>-  En outre, le serveur que hôtes WAP doivent avoir un certificat SSL qui correspond au nom en cours de publication à des clients externes, ainsi que le certificat SSL qui est utilisée sur le serveur NDES approbation. Activer le serveur WAP pour mettre fin à la connexion SSL à partir de clients et ces certificats créer une nouvelle connexion SSL au serveur NDES.
    Pour plus d’informations sur les certificats pour WAP, consultez la section **planification des certificats** de [publier des Applications à l’aide de Web Proxy d’Application sur la planification](https://technet.microsoft.com/library/dn383650.aspx). Pour obtenir des informations générales sur les serveurs WAP, voir [utilisation des Proxy de l’Application Web](http://technet.microsoft.com/library/dn584113.aspx). |

### Configuration requise de réseau

À partir d’Internet au réseau de périmètre, autoriser le port 443 à partir de toutes les adresses de comprises hosts/IP sur internet vers le serveur NDES.

À partir du réseau de périmètre au réseau approuvé, autoriser tous les ports et protocoles requis pour l’accès au domaine sur le serveur NDES à un domaine. Le serveur NDES doit avoir accès aux serveurs de certificats, serveurs DNS, serveurs Gestionnaire de Configuration et domaine.

Nous vous recommandons de publication du serveur NDES via un proxy, tels que le [proxy d’application Azure AD](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-publish/), [Proxy d’accès Web](https://technet.microsoft.com/en-us/library/dn584107.aspx)ou un proxy tiers.


### <a name="BKMK_CertsAndTemplates"></a>Modèles et des certificats

|Objet|Plus d’informations|
|----------|-----------|
|**Modèle de certificat**|Vous configurez ce modèle sur votre autorité de certification émission.|
|**Certificat d’authentification client**|Demandé à partir de votre autorité de certification ou public émetteur autorité de certification, vous installez ce certificat sur le serveur NDES.|
|**Certificat d’authentification serveur**|Demande à partir de votre émission autorité de certification ou autorité de certification publique, vous installer et lier ce SSL de certificats dans IIS sur le serveur NDES.|
|**Certificat d’autorité de certification racine de confiance**|Vous exportez sous un fichier **.cer** à partir de l’autorité de certification racine ou n’importe quel appareil qui approuve l’autorité de certification racine et déployez aux périphériques en utilisant le profil de certificat autorité de certification approuvée.<br /><br />Vous utilisez un seul certificat d’autorité de certification racine de confiance par la plateforme de système d’exploitation et associez à chaque profil de certificat racine approuvé que vous créez.<br /><br />Vous pouvez utiliser les certificats d’autorité de certification racine de confiance supplémentaires lorsque cela est nécessaire. Par exemple, vous pouvez procéder pour fournir une approbation à une autorité de certification qui vous permet du serveur certificats d’authentification pour les points d’accès Wi-Fi.|

### <a name="BKMK_Accounts"></a>Comptes

|Nom|Plus d’informations|
|--------|-----------|
|**Compte de service NDES**|Vous spécifiez un compte d’utilisateur de domaine à utiliser comme compte de Service NDES.|

## <a name="BKMK_ConfigureInfrastructure"></a>Configurer votre infrastructure
Avant de configurer les profils de certificat que vous devez effectuer les tâches suivantes, qui requièrent des connaissances de Windows Server 2012 R2 et Active Directory certificat Services automatisée :

**Tâche 1**: créer un compte de service NDES

**Tâche 2**: configurer les modèles de certificats sur l’autorité de certification

**Tâche 3**: configurer les conditions préalables sur le serveur NDES

**Étape 4**: configurer les NDES pour une utilisation avec Intune

**Tâche 5**: activer, installer et configurer le connecteur de certificat Intune

### Tâche 1 : créer un compte de service NDES

Créer un compte d’utilisateur de domaine à utiliser comme compte de service NDES. Vous spécifierez ce compte lorsque vous configurez des modèles sur l’autorité de certification avant d’installer et configurer NDES. Vérifiez que l’utilisateur a les droits par défaut, les droits **D’ouverture de session en local**, **ouverture de session en tant que Service** et **accès par lots** . Certaines organisations ont renforcer les stratégies qui désactivent ces droits.




### Tâche 2 : configurer les modèles de certificats sur l’autorité de certification
Dans cette tâche, vous allez :

-   Configurer un modèle de certificat pour NDES

-   Publier le modèle de certificat pour NDES

##### Pour configurer l’autorité de certification

1.  Connectez-vous en tant qu’administrateur d’entreprise. 

2.  Sur l’autorité de certification, utilisez le composant logiciel enfichable modèles de certificats pour créer un modèle personnalisé ou copier un modèle existant, puis modifiez un modèle existant (par exemple, le modèle de l’utilisateur) pour une utilisation avec NDES.

    Le modèle doit avoir les configurations suivantes :

    -   Spécifiez un convivial **nom complet du modèle** pour le modèle.

    -   Sous l’onglet **Nom de sujet** , sélectionnez **fourni dans la demande**. (Sécurité est appliquée par le module de stratégie Intune NDES).

    -   Sous l’onglet **Extensions** , vérifiez que la **Description de stratégies d’Application** inclut **L’authentification du Client**.

        > [!IMPORTANT]
        > Pour iOS et modèles de certificats de Mac OS X, sous l’onglet **Extensions** , modifiez **L’utilisation de clé** et vérifiez **que la Signature est preuve d’origine** n’est pas sélectionnée.

    -   Sous l’onglet **sécurité** , ajoutez le compte de service NDES et lui donner des droits **d’inscription** au modèle. Les administrateurs Intune ayant créera profils SCEP requièrent **en lecture** afin que leur peuvent de rechercher le modèle lors de la création des profils SCEP.
    
    > [!NOTE]
    > Pour révoquer les certificats la NDES service compte des besoins droits *émettre et gérer des certificats* pour chaque modèle de certificat utilisé par un profil de certificat.

3.  Passez en revue la **période de validité** sous l’onglet **Général** du modèle. Par défaut, Intune utilise la valeur configurée dans le modèle. Toutefois, vous avez la possibilité pour configurer l’autorité de certification pour autoriser le demandeur spécifier une valeur différente, vous pouvez ensuite définir à partir de la console administrateur Intune. Si vous souhaitez toujours utiliser la valeur dans le modèle, ignorez le reste de cette étape.

    > [!IMPORTANT]
    > IOS les plateformes Mac OS X toujours utilise que la valeur définie dans le modèle indépendamment des autres configurations vous rendre.

Voici quelques captures d’écran d’un exemple de configuration du modèle.

![Modèle, onglet Gestion de demande](..\media\scep_ndes_request_handling.png) 

![Modèle, onglet Nom de l’objet](..\media\scep_ndes_subject_name.jpg) 

![Modèle, onglet sécurité](..\media\scep_ndes_security.jpg) 

![Modèle, onglet extensions](..\media\scep_ndes_extensions.jpg) 

![Modèle, onglet conditions d’émission](..\media\scep_ndes_issuance_reqs.jpg) 

>   [!IMPORTANT]
    > Pour les stratégies d’Application (dans la capture d’écran 4e), ajoutez une seule les stratégies d’application obligatoires. Confirmez vos choix avec vos administrateurs de sécurité.
   


Pour configurer l’autorité de certification pour autoriser le demandeur spécifier la période de validité, sur l’autorité de certification, exécutez les commandes suivantes :

   1.  **certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**
   2.  **net stop certsvc**

   3.  **démarrage NET certsvc**

4.  Sur l’autorité de certification, utilisez le composant logiciel enfichable Autorité de Certification pour publier le modèle de certificat.

    1.  Sélectionnez le nœud de **Modèles de certificats** , cliquez sur **Action** -&gt; **Nouveau** &gt; **Modèle de certificat**, puis sélectionnez le modèle créé à l’étape 2.

    2.  Valider que le modèle publié en l’affichant dans le dossier **Modèles de certificats** .


### Tâche 3 : configurer les conditions préalables sur le serveur NDES
Dans cette tâche, vous allez :

-   Ajouter NDES à Windows Server et configurer IIS pour prendre en charge NDES

-   Ajouter le compte de Service NDES au groupe IIS_IUSR

-   Définir le nom principal de service pour le compte de Service NDES




   1.  Sur le serveur qui sera hôtes NDES, vous devez ouvrir une session en tant qu’un un **Administrateur d’entreprise**et puis d’utiliser l' [Assistant de fonctionnalités et ajouter des rôles](https://technet.microsoft.com/library/hh831809.aspx) pour installer NDES :

    1.  Dans l’Assistant, sélectionnez **Les Services de certificat Active Directory** pour accéder aux Services de rôle AD SC. Sélectionnez le **Service d’inscription de périphérique réseau**, décochez la case **Autorité de Certification**et puis terminez l’Assistant.

        > [!TIP]
        > Dans la page de **progression de l’Installation** de l’Assistant, ne cliquez pas sur **Fermer**. Au lieu de cela, cliquez sur le lien pour **Configurer les Services Active Directory certificat sur le serveur de destination**. Cette action ouvre l’Assistant **Configuration de SC publicité** que vous utilisez pour la tâche suivante. Une fois la Configuration SC publicité s’ouvre, vous pouvez fermer l’Assistant Ajouter des rôles et fonctionnalités.

    2.  NDES est ajouté sur le serveur, l’Assistant installe également IIS. Garantir QU'IIS contient les configurations suivantes :

        -   **Serveur Web** &gt; **Sécurité** &gt; **filtrage des demandes**

        -   **Serveur Web** &gt; **Développement d’applications** &gt; **ASP.NET 3.5**. L’installation d’ASP.NET 3.5 va installer .NET Framework 3.5. Lorsque vous installez .NET Framework 3.5, installez la fonctionnalité de **.NET Framework 3.5** principale et **l’Activation HTTP**.

        -   **Serveur Web** &gt; **Développement d’applications** &gt; **ASP.NET 4.5**. Installer ASP.NET 4.5 installe .NET Framework 4.5. Lorsque vous installez .NET Framework 4.5, installez la fonctionnalité de **.NET Framework 4.5** core, **ASP.NET 4.5**et les **Services WCF** &gt; fonctionnalité **D’Activation HTTP** .

        -   **Outils de gestion** &gt; **Compatibilité avec la gestion 6 IIS** &gt; **compatibilité avec la métabase 6 IIS**

        -   **Outils de gestion** &gt; **Compatibilité avec la gestion 6 IIS** &gt; **IIS 6 WMI compatibilité**

  2.  Sur le serveur, ajoutez le compte de service NDES en tant que membre du groupe **IIS_IUSR** .

   3.  Dans une invite de commandes avec élévation de privilèges, exécutez la commande suivante pour définir le nom principal de service du compte de Service NDES :

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   Par exemple, si votre serveur NDES est appelé **SERVEUR01**, votre domaine est **Contoso.com**, et le compte de service est **NDESService**, utilisez :

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

### Tâche 4 - configurer NDES pour une utilisation avec Intune
Dans cette tâche, vous allez :

-   Configurer NDES pour une utilisation avec l’autorité de certification

-   Lier le certificat d’authentification (SSL) dans IIS

-   Configurer la demande filtrage dans IIS

##### Pour configurer NDES pour une utilisation avec Intune

1.  Sur le serveur NDES, ouvrez l’Assistant Configuration de SC AD, puis apportez les configurations suivantes.

    > [!TIP]
    > Si vous avez cliqué sur le lien à l’étape précédente, cet Assistant est déjà ouvert. Dans le cas contraire, ouvrez le Gestionnaire de serveur pour accéder à la configuration après le déploiement pour les Services de certificat Active Directory.

    -   Dans la Page **Des Services de rôle** , sélectionnez le **Service d’inscription de périphérique réseau**.

    -   Dans la page **Compte de Service pour NDES** , spécifiez le compte de Service NDES.

    -   Dans la page **autorité de certification pour NDES** , cliquez sur **Sélectionner**et sélectionnez l’autorité de certification dans lequel vous avez configuré le modèle de certificat.

    -   Dans la page de **chiffrement pour NDES** , définissez la longueur de la clé pour répondre aux besoins de votre entreprise.

    Dans la page de **Confirmation** , cliquez sur **configurer** pour terminer l’Assistant.

2.  Une fois l’Assistant terminé, modifier la clé de Registre suivante sur le serveur NDES :

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    Pour modifier cette clé, identifier **objectif**, tel qu’il figure sous l’onglet **Traitement de la demande** du modèle certificat et modifiez l’entrée correspondante dans le Registre en remplaçant les données existantes par le nom du modèle de certificat (pas le nom d’affichage du modèle de données) que vous avez spécifié dans la tâche 1. Le tableau suivant mappe le rôle du modèle certificat pour les valeurs dans le Registre :

    |Modèle de certificat objectif (onglet sur le traitement de la demande)|Valeur de Registre pour la modifier|Valeur affichée dans la console d’administration Intune pour le profil SCEP|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Signature|SignatureTemplate|Signature numérique|
    |Chiffrement|EncryptionTemplate|Chiffrement de la clé|
    |Signature et chiffrement|GeneralPurposeTemplate|Chiffrement de la clé<br /><br />Signature numérique|
    Par exemple, si l’objectif de votre modèle de certificat est **le chiffrement**, puis modifiez la valeur **EncryptionTemplate** est le nom de votre modèle de certificat.

3. Le serveur NDES recevra beaucoup d’URL (requêtes), qui requièrent que vous ajoutez deux entrées de Registre :

    |Emplacement|Valeur|Type|Données|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (décimal)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (décimal)|


4. Dans le Gestionnaire des services Internet, sélectionnez **Site Web par défaut** -> **Filtrage des requêtes** -> **Modifier le paramètre fonctionnalité**et modifiez la **longueur maximale d’une URL** et une **chaîne de requête Maximum** à *65534*, comme indiqué.

    ![Longueur maximale de URL et requête IIS](..\media\SCEP_IIS_max_URL.png) 

5.  Redémarrez le serveur. En cours d’exécution **iisreset** sur le serveur ne sera pas suffisant pour finaliser ces modifications.
6. Accédez à http://*nom de domaine complet*/certsrv/mscep/mscep.dll. Une page NDES semblable à ce qui doit s’afficher :

    ![Test NDES](..\media\SCEP_NDES_URL.png) 

    Si vous obtenez un **503 Service indisponible**, vérifiez l’eventviewer. Il est probable que le pool d’applications est arrêté en raison d’un manque vers la droite pour l’utilisateur NDES. Ces droits sont décrites dans la tâche 1.

##### Pour l’installation et lier des certificats sur le serveur NDES

1.  Sur votre serveur NDES, demander et installer un certificat **d’authentification serveur** de votre autorité de certification interne ou d’une autorité de certification publique. Vous allez puis lier ce certificat SSL dans IIS.

    > [!TIP]
    > Une fois que vous liez le certificat SSL dans IIS, vous allez également installer un certificat d’authentification client. Ce certificat peut être émis par une autorité de certification approuvée par le serveur NDES. Bien qu’il n’est pas une meilleure pratique, vous pouvez utiliser le même certificat d’authentification serveur et client dans la mesure où le certificat comporte les deux applications améliorer de la clé (EKU). Passez en revue les étapes suivantes pour plus d’informations sur ces certificats d’authentification.

    1.  Une fois que vous obtenez le certificat d’authentification serveur, ouvrez le **Gestionnaire IIS**, sélectionnez le **Site Web par défaut** dans le volet **connexions** , puis cliquez sur **liaisons** dans le volet **Actions** .

    2.  Cliquez sur **Ajouter**, la valeur **Type** **https**et vérifiez que le port est **443**. (Seulement le port 443 est prise en charge autonome Intune.

    3.  **Certificat SSL**, spécifiez le certificat d’authentification serveur.

        > [!NOTE]
        > Si le serveur NDES utilise à la fois un nom interne et externe pour une adresse réseau unique, le certificat d’authentification serveur doit avoir un **Nom de sujet** avec un nom de serveur public externe et un **Autre nom de l’objet** qui inclut le nom du serveur interne.

2.  Sur votre serveur NDES, demander et installer un certificat **d’authentification client** à partir de votre autorité de certification interne ou d’une autorité de certification public. Cela peut être le même certificat que le certificat d’authentification serveur si ce certificat comporte les deux fonctions.

    Le certificat d’authentification client doit avoir les propriétés suivantes :

    **Utilisation avancée de la clé** - cela doit inclure **L’authentification du Client**.

    **Nom de sujet** : elle doit être égale au nom du serveur dans lequel vous souhaitez installer le certificat (le serveur NDES) DNS.

##### Pour configurer le filtrage des demandes IIS

1.  Sur le serveur NDES ouvrir **Le Gestionnaire des services**, sélectionnez le **Site Web par défaut** dans le volet **connexions** et ouvrez **Filtrage des requêtes**.

2.  Cliquez sur **Modifier les paramètres de fonction**, puis définissez les éléments suivants :

    **chaîne (octets) de la requête** = **65534**

    **Taille maximale des URL (octets)** = **65534**

3.  Passez en revue la clé de Registre suivante :

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Vérifiez que les valeurs suivantes sont définies comme entrées DWORD :

    Nom : **MaxFieldLength**, avec une valeur décimale de **65534**

    Nom : **MaxRequestBytes**, avec une valeur décimale de **65534**

4.  Redémarrez le serveur NDES. Le serveur est maintenant prêt à prendre en charge le connecteur certificat.

### Tâche 5 - activer, installer et configurer le connecteur de certificat Intune
Dans cette tâche, vous allez :

Activer la prise en charge de NDES dans Intune.

Télécharger, installer et configurer le connecteur certificat sur le serveur NDES.

##### Pour activer la prise en charge pour le connecteur de certificat

1.  Ouvrez la [console d’administration Intune](https://manage.microsoft.com), cliquez sur **administrateur** &gt; **Connecteur certificat**.

2.  Cliquez sur **configurer le connecteur de certificat local**.

3.  Sélectionnez **Activer le lien certificat**, puis cliquez sur **OK**.

##### Pour télécharger, installer et configurer le connecteur de certificat

1.  Ouvrez la [console d’administration Intune](https://manage.microsoft.com), puis cliquez sur **administrateur** &gt; **Gestion des appareils mobiles** &gt; **Certificat connecteur** &gt; **Télécharger le connecteur certificat**.

2.  Une fois le téléchargement terminé, exécutez le programme d’installation téléchargé (**ndesconnectorssetup.exe**) sur un serveur Windows Server 2012 R2. Le programme d’installation installe également le module de stratégie pour NDES et le Service Web PRC. (Le Service Web PRC, CertificateRegistrationSvc, s’exécute en tant qu’application dans IIS).

    > [!NOTE]
    > Lorsque vous installez NDES pour Intune autonome, le service PRC installe automatiquement avec le lien certificat. Lorsque vous utilisez Intune avec le Gestionnaire de Configuration, vous installez le Point d’alignement de certificat en tant que site distinct système rôle.

3.  Lorsque vous êtes invité pour le certificat client pour le connecteur certificat, cliquez sur **Sélectionner**, puis sélectionnez le certificat **d’authentification de client** que vous avez installé sur votre serveur NDES dans la tâche 3.

    Après avoir sélectionné le certificat d’authentification client, vous revenez à la surface de **Certificat Client pour Microsoft Intune certificat Connector** . Bien que le certificat que vous avez sélectionné n’est pas visible, cliquez sur **suivant** pour afficher les propriétés de ce certificat. Puis cliquez sur **suivant**, puis cliquez sur **installer**.

4.  Une fois l’Assistant terminé, mais avant de fermer l’Assistant, cliquez sur **lancer l’interface utilisateur connecteur certificat**.

    > [!TIP]
    > Si vous fermez l’Assistant avant de lancer l’interface utilisateur connecteur certificat, vous pouvez le rouvrir en exécutant la commande suivante :
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Dans le **certificat connecteur** interface utilisateur :

    Cliquez sur **Se connecter** et entrez vos informations d’identification d’administrateur de service Intune ou les informations d’identification d’un administrateur client avec l’autorisation d’administration globale.

    Si votre organisation utilise un serveur proxy et le proxy est nécessaire pour le serveur NDES accéder à Internet, cliquez sur **utiliser un serveur proxy** , puis fournissez le nom du serveur proxy, port et informations d’identification de compte pour vous connecter.

    Sélectionnez l’onglet **Avancé** , puis indiquez les informations d’identification d’un compte qui a l’autorisation **émettre et gérer des certificats** sur votre autorité de certification et puis cliquez sur **Appliquer**.

    Vous pouvez à présent fermer l’interface utilisateur connecteur certificat.

6.  Ouvrez une invite et tapez **services.msc**, puis appuyez sur **entrée**, avec le bouton droit le **Service de connecteur Intune**et puis cliquez sur **redémarrer**.

Pour valider que le service est en cours d’exécution, ouvrez un navigateur et entrez l’URL suivante, qui doit renvoyer une erreur **403** :

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

## Étapes suivantes
Vous êtes maintenant prêt à configurer les profils de certificat, comme décrit dans [les profils de certificat configurer](Configure-Intune-certificate-profiles.md).
