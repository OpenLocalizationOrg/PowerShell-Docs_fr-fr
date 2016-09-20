---
title: "Stratégies de pare-feu pour les PC Windows | Microsoft Intune"
description: "Intune peut vous aider à sécuriser PC vous gérez avec le client Intune sur de différentes manières, y compris pour vous aider à configurer les paramètres du pare-feu Windows."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 3fde6fb88bd929956d18e4dda502071901e4c4b4
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Protéger les PC Windows à l’aide de stratégies de pare-feu Windows Intune Microsoft
Microsoft Intune peut vous aider à sécuriser les PC Windows que vous gérez avec le client Intune dans de différentes manières. Première dans lequel cela consiste à fournir des stratégies qui vous permettent de configurer les paramètres du pare-feu Windows sur les PC.

Si vous n’avez pas encore installé le client PC Windows Intune sur vos ordinateurs, voir [installer le client PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Utilisez les informations dans les sections suivantes pour vous aider à configurer, déployer et contrôler les stratégies de pare-feu Windows sur PC Windows.

## Utiliser des stratégies Intune pour gérer le pare-feu Windows
La stratégie de pare-feu Windows vous permet de créer et déployer des paramètres qui contrôlent le pare-feu Windows sur PC gérés. Vous ne pouvez pas gérer les exceptions personnalisées pour le pare-feu Windows, et ces paramètres ne concernent pas les pare-feu tiers.

> [!NOTE]
> Si la stratégie Microsoft Intune et stratégie de groupe sont configurés pour gérer le même paramètre sur le PC, le paramètre de stratégie de groupe remplace la stratégie Microsoft Intune. Pour plus d’informations sur la façon d’éviter les conflits entre Intune stratégie et stratégie de groupe, voir [résoudre la stratégie de groupe et les conflits Intune Microsoft](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Si vous voulez déployer des paramètres du pare-feu Windows sur les ordinateurs exécutant Windows Vista, vous devez tout d’abord installer [KB971800 correctif](http://support2.microsoft.com/kb/971800) sur ces ordinateurs.

> [!IMPORTANT]
> Pour gérer le pare-feu Windows à l’aide de Intune, vérifiez que les deux services suivants sont activés sur les ordinateurs que vous gérez :
>
> -   Pare-feu Windows
> -   Agent de stratégie

## Configurer une stratégie de pare-feu Windows

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **stratégie** &gt; **Ajouter une stratégie**.

2.  Configurer et déployer une stratégie de **Paramètres du pare-feu Windows** . Vous pouvez utiliser les paramètres recommandés ou personnaliser les paramètres. Si vous avez besoin de plus d’informations sur la façon de créer et déployer des stratégies, voir [tâches de gestion courantes PC Windows avec le client ordinateur Intune Microsoft](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    La section suivante répertorie les valeurs que vous pouvez configurer dans la stratégie, ainsi que les valeurs par défaut qui seront utilisés si vous ne personnalisez la stratégie.

Une fois que vous déployez une stratégie de pare-feu Windows, vous pouvez afficher son statut dans la page de **Toutes les stratégies** de l’espace de travail de **stratégie** .

## Spécifier les paramètres de stratégie pour le pare-feu Windows

### Activer le pare-feu Windows

Ces paramètres de stratégie Activer le pare-feu Windows sur les ordinateurs gérés qui sont :
- Connecté à un domaine (par exemple, sur le lieu de travail)
- Connecté à un réseau privé (approuvé) (par exemple, un réseau domestique)
- Connecté à un réseau public non sécurisé (par exemple, un café)

La valeur par défaut pour chacun de ces paramètres est **Oui**, qui est la valeur la plus sécurisée.



### Bloquer toutes les connexions entrantes, y compris ceux présents dans la liste des programmes autorisés

Ces paramètres de stratégie configurent le pare-feu Windows pour bloquer le trafic réseau entrants sur les ordinateurs gérés qui sont :
- Connecté à un domaine (par exemple, sur le lieu de travail)
- Connecté à un réseau privé (approuvé) (par exemple, un réseau domestique)
- Connecté à un réseau public non sécurisé (par exemple, un café)

La valeur par défaut pour chacun de ces paramètres est **Oui**, qui est la valeur la plus sécurisée.

> [!IMPORTANT]
> Si votre environnement inclut des ordinateurs gérés qui exécutent Windows Vista sans service Pack installé, vous devez installer la mise à jour associée à [l’article 971800](http://go.microsoft.com/fwlink/?LinkId=188405) dans la Base de connaissances Microsoft ou désactiver les paramètres de stratégie **Bloquer toutes les connexions entrantes** dans stratégies déployées à ces ordinateurs.

### Avertir l’utilisateur lorsque le pare-feu Windows bloque un nouveau programme

Ces paramètres de stratégie déterminent si le pare-feu Windows vous avertit un utilisateur PC lorsqu’il bloque le trafic réseau entrant lors de l’ordinateur géré est :
- Connecté à un domaine (par exemple, sur le lieu de travail)
- Connecté à un réseau privé (approuvé) (par exemple, un réseau domestique)
- Connecté à un réseau public non sécurisé (par exemple, un café)

La valeur par défaut pour chacun de ces paramètres est **Oui**.


### Configurer des exceptions prédéfinies

Vous pouvez configurer des exceptions qui permettent aux types spécifiques de trafic réseau via le pare-feu indépendamment les valeurs que vous avez configuré précédemment. Aucune de ces paramètres sont configurés par défaut.

|Nom du paramètre|Plus d’informations|
|------------------|--------------------|
|**BranchCache - extraction du contenu**<br>(Windows 7 ou version ultérieure)|Permet aux clients BranchCache HTTP permet d’extraire le contenu à partir d’autres clients BranchCache lors en mode distribué et à partir du cache hébergé en mode de cache hébergé. Ce paramètre utilise le protocole HTTP.|
|**BranchCache - Cache hébergé Client**<br>(Windows 7 ou version ultérieure)|Permet aux clients BranchCache utiliser un cache hébergé. Ce paramètre utilise HTTPS.|
|**BranchCache - serveur de Cache hébergé**|Vous permet de BranchCache clients utilisent un cache hébergé pour communiquer avec d’autres clients. Ce paramètre utilise HTTPS.|
|**BranchCache - découverte d’homologues**<br>(Windows 7 ou version ultérieure)|Permet aux clients BranchCache utilisant le protocole Web Services découverte dynamique (Web-découverte) pour rechercher la disponibilité du contenu sur le sous-réseau local.|
|**Mise en cache BITS**|Permet aux clients utiliser le Service de transfert Intelligent en arrière-plan (BITS) pour rechercher et partager des fichiers qui sont stockés dans le cache BITS sur les clients dans le même sous-réseau. Ce paramètre utilise les Services Web sur des appareils mobiles (WSDAPI) et appel de procédure distante (RPC).|
|**Se connecter à un projecteur réseau**|Permet aux utilisateurs de se connecter à des projecteurs réseaux avec ou sans fil pour projeter vos présentations. Ce paramètre utilise WSDAPI.|
|**Réseau de base**|Permet aux clients permet de se connecter aux ressources réseau IPv4 et IPv6.|
|**Coordinateur de transactions distribuées**|Vous permettent de conserver des ordinateurs pour coordonner les transactions qui mettent à jour des ressources protégées par transaction, telles que des bases de données, les files d’attente et les systèmes de fichiers gérés.|
|**Partage de fichiers et imprimante**|Permet aux utilisateurs de partager des fichiers et imprimantes locaux avec d’autres utilisateurs sur le réseau. Ce paramètre utilise NetBIOS, lien Local résolution LLMNR (Multicast Name), protocole Server Message bloc (PME) et RPC.|
|**Groupe résidentiel**<br>(Windows 7 ou version ultérieure)|Vous permettent de conserver les ordinateurs gérés à participer à un réseau de groupe résidentiel.|
|**Service iSCSI**|Vous permettent de conserver les ordinateurs gérés pour vous connecter aux périphériques et serveurs iSCSI.|
|**Service de gestion de clés**|Vous permet d’ordinateurs à compter de conformité à la licence dans les environnements d’entreprise.|
|**Extensions Media Center**|Permet aux extensions Media Center de communiquer avec des ordinateurs qui exécutent Windows Media Center. Ce paramètre utilise qWave et Service de découverte SSDP (Simple Protocol).|
|**Service accès réseau**|Configure un canal de sécurité entre les clients de domaine et un contrôleur de domaine pour l’authentification des utilisateurs et des services. Ce paramètre utilise RPC.|
|**Découverte du réseau**|Permet aux ordinateurs découvrir les autres périphériques et être découvert par d’autres périphériques sur le réseau. Ce paramètre utilise les protocoles réseau fonction découverte hôte et Services de composition et SSDP, NetBIOS, LLMNR et UPnP.|
|**Alertes et des journaux des performances**|Active le service journaux de performances et les alertes de gestion à distance. Ce paramètre utilise RPC.|
|**Administration à distance**|Permet l’administration de l’ordinateur distante.|
|**Assistance à distance**|Permet aux utilisateurs d’ordinateurs gérés demande assistance à distance à partir d’autres utilisateurs sur le réseau. Ce paramètre utilise SSDP, homologue nom résolution PNRP (Protocol), Teredo et UPnP protocoles réseau.|
|**Bureau à distance**|Permet à l’ordinateur de bureau à distance permet d’accéder aux autres ordinateurs.|
|**Gestion à distance journal des événements**|Vous permet de consulter et gérer à distance les journaux d’événements client. Ce paramètre utilise des canaux nommés et RPC.|
|**Gestion des tâches planifiées distant**|Permet de gérer le service de planification des tâches à distance. Ce paramètre utilise RPC.|
|**Gestion du Service distant**|Permet de gestion à distance des services locaux sur les clients. Ce paramètre utilise des canaux nommés et RPC.|
|**Gestion des volumes à distance**|Permet de gestion à distance matérielle et logicielle disque volume. Ce paramètre utilise RPC.|
|**Routage et accès distant**|Permet de VPN entrant et les connexions d’accès à distance pour les ordinateurs.|
|**Secure Socket protocole**|Active les connexions VPN entrantes sur les ordinateurs gérés avec tunnel protocole SSTP (Secure Socket). Ce paramètre utilise HTTPS.|
|**Interruption SNMP**|Ordinateurs gérés vous permet de recevoir le trafic de service interruption SNMP Simple Network Management Protocol ().|
|**Cadre UPnP**|Configure le service UPnP Framework sur des ordinateurs pour lui permettre de découvrir et d’utiliser UPnP périphériques certifiés.|
|**Service d’enregistrement de nom d’ordinateur Collaboration de Windows**|Vous permet d’ordinateurs et de communiquer avec d’autres ordinateurs à l’aide de SSDP et PNRP.|
|**Lecteur Windows Media**|Permet aux utilisateurs reçoivent les supports de diffusion en continu sur UDP User Datagram Protocol ().|
|**Service de partage réseau du lecteur Windows Media**|Permet aux utilisateurs de partager des fichiers multimédias sur un réseau. Ce paramètre utilise les protocoles réseau SSDP qWave et UPnP.|
|**Service (Internet) de partage réseau du lecteur Windows Media**<br>(Windows 7 ou version ultérieure)|Permet aux utilisateurs de partager des médias personnels sur Internet.|
|**Espace de collaboration Windows**|Permet aux utilisateurs de collaborer sur un réseau pour partager des documents, des programmes et leur bureau. Ce paramètre utilise la réplication de système de fichiers distribués (DFSR) et P2P.|
|**Windows égal à égal Collaboration Foundation**|Configure les différents programmes d’égal à égal et technologies afin qu’ils puissent se connecter. Ce paramètre utilise SSDP et PNRP.|
|**Gestion à distance Windows (compatibilité)**|Permet de gestion à distance des ordinateurs gérés avec la gestion des services Web, un protocole Web services gestion à distance des systèmes d’exploitation et périphériques.|
|**Gestion à distance Windows**<br>(Windows 8 ou version ultérieure)|Permet de gestion à distance des ordinateurs gérés avec la gestion des services Web, un protocole Web services gestion à distance des systèmes d’exploitation et périphériques.|
|**PC virtuel Windows**<br>(Windows 7 ou version ultérieure)|Vous permet de machines virtuelles communiquer avec d’autres ordinateurs.|
|**Périphériques mobiles sans fil**|Permet de transférer des éléments multimédias d’un appareil caméra ou support réseau activé sur les ordinateurs gérés avec Media Transfer Protocol (plan de référence). Ce paramètre utilise SSDP et UPnP protocoles réseau.|

### Voir aussi
[Stratégies pour protéger des PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
