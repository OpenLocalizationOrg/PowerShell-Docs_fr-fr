---
title: Connexions VPN | Microsoft Intune
description: "Utiliser les profils VPN pour déployer paramètres VPN à des utilisateurs et périphériques de votre organisation."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 738b7fbda92f24eaeae23638ea49c1c174901e7a
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Connexions VPN dans Microsoft Intune
 Vous pouvez utiliser les réseaux privés virtuels (VPN) pour donner accès à distance sécurisé à vos utilisateurs à votre réseau d’entreprise. Utilisateurs distants peuvent travailler comme si leurs appareils connectés physiquement au réseau. Périphériques utilisent un profil de connexion VPN pour établir une connexion avec le serveur VPN. Utiliser *les profils VPN* dans Microsoft Intune pour déployer des paramètres VPN à des utilisateurs et périphériques de votre organisation. En déployant ces paramètres, vous réduisez le piloté par l’utilisateur final requis pour vous connecter à des ressources sur le réseau d’entreprise.

Par exemple, supposons que vous voulez configurer tous les appareils iOS avec les paramètres requis pour vous connecter à un partage de fichiers sur le réseau d’entreprise. Vous créez un profil VPN qui contient les paramètres nécessaires pour se connecter au réseau d’entreprise, et vous déployez ce profil à tous les utilisateurs qui ont des appareils iOS. Les utilisateurs verront la connexion VPN dans la liste des réseaux disponibles et peuvent se connecter sans effort.

Vous pouvez configurer des types de périphériques suivants à l’aide de profils VPN :

* Appareils exécutant Android 4 et versions ultérieures
* Périphériques exécutant iOS 8.0 et versions ultérieures
* Périphériques exécutant Mac OS X 10.9 et version ultérieure
* Appareils inscrits qui exécutent Windows 8.1 et versions ultérieures
* Périphériques exécutant Windows Phone 8.1 et versions ultérieures
* Appareils exécutant mobile et bureau de Windows 10

Les options de configuration de profil VPN diffèrent selon le type d’appareil que vous sélectionnez.

## Types de connexions VPN

Intune prend en charge les profils VPN création qui utilisent les types de connexion suivants :




Type de connexion |iOS et Mac OS X  |Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Mobile et bureau de Windows 10 |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Oui |Oui   |N°    |     N°    |N°  |N°    | Oui (OMA URI, mobile uniquement)|     
Cisco (IPsec)|Oui |N°   |N°  |  N°|N°  |N° | N°|
Citrix|Oui |N°   |N°  |  N°|N°  |N° | N°|
Banque d’informations sécurisé Pulse|Oui  |Oui |Oui   |N°  |Oui  |Oui| Oui|        
F5 Côté Client|Oui |Oui |Oui |N°  |Oui  |   Oui |  Oui|   
Se connecter Dell SonicWALL Mobile|Oui |Oui |Oui |N°  |Oui |Oui |Oui|         
Point de contrôle Mobile VPN|Oui |Oui |Oui |Oui |Oui|Oui|Oui|
Microsoft SSL SSTP)|N° |N° |N° |N° |N°|N°|VPNv1 OMA-URI *|
Microsoft automatique|N° |N° |N° |N° |N°|Oui (OMA-URI)|Oui|
IKEv2|profil personnalisées iOS|N° |N° |N° |N°|Oui (OMA-URI)|Oui|
PPTP|profil personnalisées iOS|N° |N° |N° |N°|N°|Oui|
L2TP|profil personnalisées iOS|N° |N° |N° |N°|Oui (OMA-URI)|Oui|

\* Sans des paramètres supplémentaires qui sont disponibles pour Windows 10.

> [!IMPORTANT]
> Avant de pouvoir utiliser profils VPN déployés sur un appareil, vous devez installer l’application VPN applicable pour le profil. Vous pouvez utiliser les informations dans la rubrique [applications déployer dans Intune Microsoft](deploy-apps-in-microsoft-intune.md) pour vous aider à déployer l’application applicable à l’aide de Intune.  

 Découvrez comment créer des profils VPN personnalisés à l’aide des paramètres d’URI dans les [configurations personnalisées les profils VPN](custom-configurations-for-vpn-profiles.md).     

## Méthodes pour sécuriser les profils VPN

Profils VPN permet d’un nombre de plusieurs types de connexions et protocoles par différents fabricants. Ces connexions sont généralement sécurisées par une des deux méthodes.

### Certificats

Lorsque vous créez le profil VPN, vous choisissez un profil de certificat SCEP ou PFX que vous avez créée précédemment dans Intune.

Il s’agit le certificat d’identité. Il est utilisé pour l’authentification par rapport à un profil de certification approuvée (ou un certificat racine) que vous avez créé pour établir qu’appareil de l’utilisateur est autorisé à se connecter. Le certificat de confiance est déployé sur l’ordinateur qui authentifie la connexion VPN, en règle générale, le serveur VPN.

Pour plus d’informations sur la façon de créer et utiliser des profils de certificat dans Intune, voir [accéder ressource sécurisée avec les profils de certificat](secure-resource-access-with-certificate-profiles.md).

### Nom d’utilisateur et mot de passe

L’utilisateur s’authentifie sur le serveur VPN en fournissant un nom d’utilisateur et mot de passe.

## Créer un profil VPN

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** > **Ajouter une stratégie**.
2. Sélectionnez un modèle pour la nouvelle stratégie, développez le type de périphérique approprié, puis le profil VPN pour cet appareil :
    * **Profil VPN (Android 4 et versions ultérieur)**
    * **Profil VPN (iOS 8.0 et versions ultérieures)**
    * **Profil VPN (Mac OS X 10.9 et version ultérieure)**
    * **Profil VPN (Windows 8.1 et versions ultérieures)**
    * **Profil VPN (Windows Phone 8.1 et versions ultérieur)**
    * **Profil de VPN (Windows 10 Desktop et Mobile et les versions ultérieures)**

 Vous pouvez créer et déployer uniquement une stratégie de profil VPN personnalisée. Paramètres recommandés ne sont pas disponibles.

3. Utilisez le tableau suivant pour vous aider à configurer les paramètres de profil VPN :

Nom du paramètre  |Plus d’informations  
---------|---------
**Nom**     |Entrez un nom unique pour le profil VPN pour vous aider à identifier dans la console Intune.         
**Description**     |Fournir une description qui offre une vue d’ensemble du profil VPN et autres informations pertinentes qui vous aide à rechercher.         
**Nom de la connexion VPN (présenté aux utilisateurs)**     |Spécifiez un nom pour le profil VPN. Il s’agit du nom que les utilisateurs verront dans la liste des connexions VPN disponibles sur leurs appareils.         
**Type de connexion**     |  Sélectionnez un des types de connexion suivants à utiliser dans le profil VPN : **Cisco AnyConnect** (non disponible pour Windows 8.1 ou Windows Phone 8.1), **Pulse sécurisé**, **F5 bord Client**, **Dell SonicWALL Mobile se connecter**, **VPN Mobile de point de contrôle**.
**Description du serveur VPN**     | Entrez une description pour le serveur VPN qui appareils doit se connecter. Exemple : **serveur VPN Contoso**. Lorsque le type de connexion est **F5 bord Client**, utilisez le champ **liste de serveurs** pour spécifier une liste de description du serveur et les adresses IP.
**Adresse IP du serveur ou nom de domaine complet**    |Indiquez l’adresse IP ou le nom de domaine complet du serveur VPN appareils doit se connecter. D’exemples : **192.168.1.1**, **vpn.contoso.com**.  Lorsque le type de connexion est **F5 bord Client**, utilisez le champ **liste de serveurs** pour spécifier une liste de description du serveur et les adresses IP.         |         
**Liste de serveurs**     |Cliquez sur **Ajouter** pour ajouter un nouveau serveur VPN à utiliser pour la connexion VPN. Vous pouvez également spécifier le serveur qui sera le serveur par défaut pour la connexion. Cette option s’affiche uniquement lorsque le type de connexion est **F5 bord Client**.         
**Envoyer l’ensemble du trafic réseau via la connexion VPN**     |Si vous sélectionnez cette option, tout le trafic réseau est envoyé via la connexion VPN. Si vous ne sélectionnez pas cette option, le client sera négociation dynamiquement les itinéraires pour fractionner tunnel lors de la connexion au serveur VPN tiers. Seules les connexions au réseau d’entreprise sont envoyées via un tunnel VPN. Tunnel VPN n’est pas utilisé lorsque vous vous connectez à des ressources sur Internet.
**Méthode d’authentification**| Sélectionnez la méthode d’authentification qui utilise la connexion VPN : **certificats** ou **nom d’utilisateur et mot de passe**. (**Nom d’utilisateur et mot de passe** n’est pas disponible lorsque la connexion est de type Cisco AnyConnect.) L’option de **méthode d’authentification** n’est pas disponible pour Windows 8.1.
**N’oubliez pas les informations d’identification à chaque ouverture de session**|Sélectionnez cette option pour vous assurer que les informations d’identification utilisateur sont à retenir afin que l’utilisateur n’a pas à entrer les informations d’identification chaque fois qu’une connexion est établie.
**Sélectionnez un certificat client pour l’authentification du client (certificat d’identité)**|Sélectionnez le certificat client SCEP que vous avez créé précédemment et que vous utiliserez pour authentifier la connexion VPN. Pour plus d’informations sur l’utilisation des profils de certificat dans Intune, voir [accéder ressource sécurisée avec les profils de certificat](secure-resource-access-with-certificate-profiles.md). Cette option s’affiche uniquement lorsque la méthode d’authentification est **certificats**.
**Rôle**| Spécifiez le nom du rôle d’utilisateur qui a accès à cette connexion. Un rôle d’utilisateur définit les options et paramètres personnels, et il active ou désactive certaines fonctionnalités d’access. Cette option s’affiche uniquement lorsque le type de connexion est **Pulse banque d’informations sécurisé**.
**Domaine**|Indiquez le nom de domaine d’authentification que vous voulez utiliser. Un domaine d’authentification est un groupe de ressources d’authentification qui utilise le type de connexion Pulse banque d’informations sécurisé. Cette option s’affiche uniquement lorsque le type de connexion est **Pulse banque d’informations sécurisé**.
**Groupe de connexion ou un domaine**|Spécifiez le nom du groupe de connexion ou de domaine que vous voulez vous connecter. Cette option s’affiche uniquement lorsque le type de connexion est **Mobile SonicWALL DellConnect**.
**Empreinte**|Spécifier une chaîne (par exemple, « Contoso empreinte Code ») qui servira à vérifier que le serveur VPN peut être approuvé. Une empreinte peut être envoyée au client afin qu’il sache d’approuver tout serveur présentant l’empreinte même lorsque vous vous connectez. Si l’appareil n’a pas encore l’empreinte, il vous invite l’utilisateur à approuver le serveur VPN auxquels ils sont connectés pour tout en affichant l’empreinte numérique. (L’utilisateur manuellement vérifie l’empreinte et choisit une **gestion de la confidentialité** pour se connecter). Cette option s’affiche uniquement lorsque le type de connexion est **VPN Mobile de point de contrôle**.
**Par application VPN**|Sélectionnez cette option si vous voulez associer à cette connexion VPN avec un iOS ou application Mac OS X afin que la connexion s’ouvre lorsque l’application est exécutée. Vous pouvez associer le profil VPN à une application lorsque vous déployez le logiciel. Pour plus d’informations, voir [déployer des applications dans Microsoft Intune](deploy-apps-in-microsoft-intune.md).
**À la demande VPN**|Vous pouvez configurer VPN à la demande pour les appareils iOS 8.0 et versions ultérieures. Instructions pour la configuration de ces fonctionnalités sont fournies dans [VPN à la demande pour les appareils iOS](#on-demand-vpn-for-ios-devices).
**Détecter automatiquement les paramètres de proxy** (iOS, Mac OS X, Windows 8.1 et Windows Phone 8.1 uniquement)|Si votre serveur VPN nécessite un serveur proxy pour la connexion, indiquez si vous souhaitez appareils pour détecter automatiquement les paramètres de connexion. Pour plus d’informations, consultez la documentation de Windows Server.
**Utiliser un script de configuration automatique** (iOS, Mac OS X, Windows 8.1 et Windows Phone 8.1 uniquement)|Si votre serveur VPN nécessite un serveur proxy pour la connexion, spécifiez si vous souhaitez utiliser un script de configuration automatique pour définir les paramètres et spécifiez une URL vers le fichier qui contient les paramètres. Pour plus d’informations, consultez la documentation de Windows Server.
**Utiliser un serveur proxy** (iOS, Mac OS X, Windows 8.1 et Windows Phone 8.1 uniquement)|Si votre serveur VPN nécessite un serveur proxy pour la connexion, sélectionnez cette option, puis spécifiez l’adresse et numéro de port du serveur proxy. Pour plus d’informations, consultez la documentation de Windows Server.
**Paramètres de proxy de contournement pour les adresses locales** (iOS, Mac OS X, Windows 8.1 et Windows Phone 8.1 uniquement)|Si votre serveur VPN nécessite un serveur proxy pour la connexion, sélectionnez cette option si vous ne souhaitez pas utiliser le serveur proxy pour les adresses locales que vous spécifiez. Pour plus d’informations, consultez la documentation de Windows Server.
**XML personnalisé** (Windows 8.1 et versions ultérieures et Windows Phone 8.1 et versions ultérieur)|Spécifier des commandes XML personnalisées qui configurer la connexion VPN. Exemple de **Banque d’informations sécurisé Pulse**: &lt;pulse schéma&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Exemple de **Point de contrôle Mobile VPN**: &lt;CheckPointVPN port = nom « 443 » = « CheckPointSelfhost » sso = « true » déboguer = « 3 » /&gt;. Exemple pour **Mobile SonicWALL DellConnect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Exemple **F5 bord**client : &lt;f5-vpn-la rendez-vous&gt;&lt;d’identification unique se /&gt;&lt;/f5-vpn-conf&gt;. Reportez-vous à VPN documentation chaque fabricant pour plus d’informations sur l’écriture des commandes XML personnalisées.
**Liste de recherche de suffixe DNS** (Windows Phone 8.1 uniquement)|Spécifiez un suffixe DNS sur chaque ligne. Pour rechercher des chaque suffixe DNS que vous avez spécifié lors de la connexion à un site Web en utilisant un nom court. Par exemple, spécifier le DNS suffixes **domain1.contoso.com** et **domain2.contoso.com**, visitez l' URL **http://mywebsite**et l’URL **http://mywebsite.domain1.contoso.com** et **http://mywebsite.domain2.contoso.com** seront recherchées.
**Contournement VPN connecté au réseau Wi-Fi société** (Windows Phone 8.1 uniquement)|Sélectionnez cette option pour indiquer que la connexion VPN ne sera pas utilisée lorsque le périphérique est connecté au réseau Wi-Fi d’entreprise.
**Contournement VPN connecté au réseau Wi-Fi domestique** (Windows Phone 8.1 uniquement)|Sélectionnez cette option pour indiquer que la connexion VPN ne sera pas utilisée lorsque l’appareil est connecté à un réseau Wi-Fi domestique.

Les paramètres supplémentaires suivants sont disponibles pour Windows 10 appareils mobiles et de bureau.

Nom du paramètre  |Plus d’informations  
---------|---------
**Règles de trafic du réseau**|Sélectionner les protocoles et les ports locale et à distance et les plages d’adresses, seront activés pour la connexion VPN. Si vous ne créez pas une règle le trafic réseau, tous les protocoles, les ports et les plages d’adresses sont activées. Après avoir créé une règle, la connexion VPN utilise uniquement les protocoles, les ports et les plages d’adresses que vous spécifiez dans cette règle.
**Itinéraires**|Sélectionnez les itinéraires qui utilisera la connexion VPN.
**Serveurs DNS**| Sélectionnez les serveurs DNS qui utilise la connexion VPN une fois la connexion établie.         
**Applications associées**|Fournir une liste des applications qui utilise automatiquement la connexion VPN. Le type d’application détermine l’identificateur de l’application. Pour une application universelle, indiquez le nom de famille package. Pour une application de bureau, fournissent le chemin d’accès de l’application.          


> [!IMPORTANT]
> Nous vous recommandons de sécuriser toutes les listes des applications que vous compiler à utiliser dans la configuration de VPN per application. Si un utilisateur non autorisé modifie votre liste et que vous l’importer dans la liste des applications par application VPN, vous allez potentiellement autoriser l’accès VPN aux applications qui ne doivent pas y accéder. La première vous pouvez sécuriser les listes d’application consiste à l’aide d’une liste de contrôle d’accès (et).

Voici un exemple de lorsque vous pouvez utiliser les paramètres de limites d’entreprise. Si vous voulez activer VPN seulement pour le Bureau à distance, créez une règle de trafic réseau qui autorise le trafic de protocole 27 sur le port externe 3996. Aucune autre trafic n’utilisera le réseau privé virtuel.

Définir des itinéraires dans les limites d’entreprise est utile lorsque votre type de connexion VPN n’autorise pas vous permet de définir la façon dont le trafic est géré avec un fractionnement tunnel. Dans ce cas, utilisez **itinéraires** pour répertorier les itinéraires qui utiliseront le réseau privé virtuel.

Vous pouvez limiter l’utilisation VPN pour les appareils Windows 10 aux applications spécifiques en créant un paramètre OMA URI personnalisé.

La nouvelle stratégie apparaît dans le nœud de **Stratégies de Configuration** de l’espace de travail de **stratégie** .

### À la demande VPN pour les appareils iOS
Vous pouvez configurer à la demande VPN pour iOS 8.0 et des générations ultérieures.

> [!NOTE]
>  
> Vous ne pouvez pas utiliser par application VPN et VPN à la demande dans la même stratégie.
 
1. Dans la page configuration de la stratégie, rechercher des **règles à la demande pour cette connexion VPN**. Les colonnes sont étiquetés **correspondance**, la condition vérifient les règles et **Action**, l’action que la stratégie se déclenche lorsque la condition est associée. 
2. Cliquez sur **Ajouter** pour créer une règle. Il existe deux types de résultats que vous pouvez configurer dans la règle. Vous ne pouvez configurer un de ces types par règle.
  - **SSID**, qui font référence aux réseaux sans fil. 
  - **Domaines de recherche DNS**, qui sont en cours...  Vous pouvez utiliser des noms de domaine complet plein tel que *corp.contoso.com d’équipe.*ou utiliser des domaines tel que *contoso.com*, qui est l’équivalent de l’utilisation de * *. contoso.com*.
3. Facultatif : fournir une sonde de chaîne URL, ce qui correspond à une URL qui utilise la règle en guise de test. Si l’appareil sur lequel est installé ce profil ne peut accéder à cette URL sans la redirection, le réseau privé virtuel sera établi et le périphérique de connexion à l’URL cible. L’utilisateur ne verra pas le site de sonde de chaîne URL. Exemple d’une sonde de chaîne URL est l’adresse d’un serveur Web audit qui vérifie la conformité périphérique avant de vous connecter le réseau privé virtuel. Il est également possible que l’URL teste la possibilité du réseau privé virtuel pour vous connecter à un site, avant de vous connecter l’appareil à l’URL cible par le biais du réseau privé virtuel.
4. Choisissez une des actions suivantes :
  - **Se connecter**
  - **Connexion d’évaluation**, ce qui a trois paramètres un. **Action du domaine** - sélectionnez **se connecter si nécessaire** ou **ne vous connectez jamais** 
     b. **Liste séparées par des virgules de domaines** - vous configurer cette option uniquement si vous choisissez une **action du domaine** de **se connecter si nécessaire**  
     c. **Sonde de chaîne obligatoire URL** - une URL HTTP ou HTTPS (recommandé), par exemple *https://vpntestprobe.contoso.com*. La règle vérifie s’il existe une réponse à partir de cette adresse. Dans le cas contraire et que l' **action du domaine** est **se connecter si nécessaire**, le réseau privé virtuel sera déclenché.
     > [!TIP]
     >
     >Exemple de lorsque vous pouvez utiliser cette action est lorsque certains sites sur votre réseau d’entreprise nécessitent une connexion de réseau d’entreprise de VPN ou direct, mais que d’autres personnes n’est pas le cas. Si vous répertoriez dans la **liste séparées par des virgules du système DNS rechercher des domaines** *corp.contoso.com*, vous pouvez cliquez sur **se connecter si nécessaire** et puis Liste sites spécifiques de ce réseau qui peuvent nécessiter des VPN, tels que *sharepoint.corp.contoso.com*. La règle vérifie si *vpntestprobe.contoso.com* pouvez être contacté. Si ce n’est pas le cas, le réseau privé virtuel sera déclenché pour le site sharepoint.
  - **Ignorer** - cela modifie pas la connectivité VPN. Si le réseau privé virtuel est connecté, maladie connecté, s’il n’est pas connecté, ne le connecter. Par exemple, vous pouvez avoir une règle qui se connecte le réseau privé virtuel pour l’ensemble de vos sites web d’entreprise internes, mais voulez effectuer l’une de ces sites internes accessible uniquement lorsque l’appareil est en réalité connecté au réseau d’entreprise. Dans ce cas, vous devez créer une règle ignorer pour qu’un site.
  - **Se déconnecter** - déconnecter du VPN appareils lorsque les conditions sont remplies. Par exemple, faire vos réseaux sans fil d’entreprise dans le champ **SSID** de la liste et créer une règle qui déconnecte appareils VPN lorsqu’ils se connectent à un de ces réseaux.

Règles spécifiques au domaine sont évaluées avant les règles de tous les domaines. 


## Déploiement de la stratégie

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** :

    -   Pour déployer la stratégie, sélectionnez un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis sélectionnez **Ajouter** &gt; **OK**.

    -   Pour fermer la boîte de dialogue sans le déployer, cliquez sur **Annuler**.


Après le déploiement réussi, les utilisateurs verront le nom de la connexion VPN que vous avez spécifié dans la liste des connexions VPN sur leurs appareils.

Un résumé de l’état et les alertes dans la page **vue d’ensemble** de l’espace de travail de **stratégie** d’identifient les problèmes avec la stratégie qui nécessitent votre attention. En outre, un résumé de l’état apparaît dans l’espace de travail du tableau de bord.

### Voir aussi
[Configurations personnalisées les profils VPN](Custom-configurations-for-VPN-profiles.md)

[Banque d’informations sécurisé par application VPN pour Android Pulse](per-app-vpn-for-android-pulse-secure.md)
