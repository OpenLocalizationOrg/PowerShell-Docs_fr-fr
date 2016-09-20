---
title: Connexions Wi-Fi | Microsoft Intune
description: "Utiliser les profils Wi-Fi pour aider les utilisateurs de se connecter à vos réseaux Wi-Fi."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 5bad6dce377bcec66154ecbb4febe5316894402f
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Configurer des périphériques pour vous connecter à vos réseaux Wi-Fi d’entreprise

Utiliser Microsoft Intune Wi-Fi profils pour déployer des paramètres réseau sans fil à des utilisateurs et périphériques de votre organisation. Lorsque vous déployez un profil Wi-Fi, vos utilisateurs ont accès à votre réseau Wi-Fi d’entreprise sans avoir à configurer eux-mêmes.

Par exemple, vous installez un réseau Wi-Fi nommé **Contoso Wi-Fi** et voulez configurer tous les appareils iOS pour vous connecter à ce réseau. Voici la procédure :

![Résumé du processus de profil Wi-Fi](..\media\wi-fi-process-diagram.png) 

1.   Créer un profil Wi-Fi contenant les paramètres nécessaires pour se connecter au réseau sans fil **Contoso Wi-Fi** .

2. Déployer le profil sur le groupe d’utilisateurs avec des appareils iOS.

3.   Les utilisateurs rechercher le réseau **Wi-Fi Contoso** dans la liste des réseaux sans fil et peuvent se connecter facilement à ce réseau.


## Comment créer un profil Wi-Fi

Vous pouvez déployer profils Wi-Fi sur les plateformes suivantes :

-   Android 4.0 ou version ultérieure

-   iOS 8.0 et versions ultérieures

-   Mac OS X 10.9 et version ultérieure

Pour les appareils exécutant Windows 8.1 ou Windows 10 bureau ou portable, vous pouvez importer un profil de configuration Wi-Fi qui ont été précédemment exporté vers un fichier. Pour plus d’informations, voir [exporter ou importer un profil de configuration Wi-Fi pour les appareils Windows](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **stratégie** &gt; **Ajouter une stratégie**.

2.  Choisissez parmi les types suivants de la stratégie, puis cliquez sur **Créer une stratégie**:

    -   Profil de Wi-Fi (Android 4 et versions ultérieur)

    -   Profil de Wi-Fi (iOS 8.0 et versions ultérieures)

    -   Profil de Wi-Fi (Mac OS X 10.9 et version ultérieure)

    Il n’existe aucun paramètres recommandés pour ce type de stratégie. Vous devez créer une stratégie personnalisée.

3.  Indiquez le nom et une description pour le profil.

4. Spécifier les valeurs de **Connexions réseau** .
 - **SSID (Service Set Identifier)**: les utilisateurs voient le nom du réseau, pas le SSID.
 - **Se connecter lorsque le réseau n’est pas diffusé son nom (SSID)**: sélectionnez cette option pour autoriser les périphériques pour vous connecter au réseau lorsqu’elle n’est pas visible dans la liste de réseaux (parce qu’il est masqué et non la diffusion son nom).
 
5. Configurer les **Paramètres de sécurité** pour la plateforme sélectionnée. Les paramètres disponibles dépendent des types de sécurité que vous sélectionnez, puis sont décrites dans [les paramètres de sécurité](#security-settings).

6. (iOS et MAC OS X uniquement) Configurer **les paramètres Proxy**

    |Nom du paramètre|Plus d’informations|Contexte d’utilisation :|
    |----------------|-------------------|-------------|
    |**Paramètres de proxy pour cette connexion Wi-Fi**|Choisissez que les paramètres de proxy tapez :<br /><br />-   **Aucun** (par défaut)<br />-   **Manuel** : spécifiez l’URL et le numéro de port du serveur proxy manuellement.<br />-   **Automatique** – utilisation d’un fichier de configuration pour configurer le serveur proxy.|Toujours|
    |**Adresse du serveur proxy** et **numéro de Port**|Spécifiez l’URL et le numéro de port du serveur proxy.|**Paramètres de proxy pour cette connexion Wi-Fi** est définie sur **manuel**|
    |**URL du serveur proxy**|Spécifiez l’URL du fichier contenant les paramètres du serveur proxy.|**Paramètres de proxy pour cette connexion Wi-Fi** est définie sur **automatique**|

7.  Enregistrer le profil Wi-Fi

La nouvelle stratégie s’affiche dans le nœud de **Stratégies de Configuration** de l’espace de travail de **stratégie** . Consultez les **étapes suivantes** pour plus d’informations sur le déploiement du profil.

## Exporter ou importer un profil de configuration Wi-Fi pour les appareils Windows
 
Pour les appareils exécutant Windows 8.1 ou Windows 10 bureau ou portable, vous pouvez importer un profil de configuration Wi-Fi qui ont été précédemment exporté vers un fichier. 

### Exporter un profil Wi-Fi
Dans Windows, vous pouvez utiliser l’utilitaire **netsh wlan** pour exporter un profil Wi-Fi existant vers un fichier XML lisible par Intune. Sur un ordinateur Windows qui a déjà le profil Wi-Fi requis installé, suivez la procédure suivante.

1.  Créer un dossier local pour W-Fi-profils exportés, par exemple c:\WiFi

2.  Ouvrez une invite de commandes en tant qu’administrateur.

3.  Exécutez la commande `netsh wlan show profiles`et notez le nom du profil que vous voulez exporter.  Dans cet exemple, le nom du profil est *WiFiName*.

4.  Exécutez la commande suivante : `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Cela créera un fichier de profil Wi-Fi nommé « Wi-Fi-WiFiName.xml dans votre dossier cible ».

### Importer un profil Wi-Fi
Utiliser le **Wi-Fi Windows importer une stratégie** pour importer un ensemble de paramètres Wi-Fi que vous pouvez déployer puis aux groupes utilisateur ou périphérique requis.


1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **stratégie** &gt; **Ajouter une stratégie**.

2.  Configurer une stratégie de type **Windows** &gt; **Importation Wi-Fi (Windows 8.1 et versions ultérieures)**.

    Cette stratégie peut être appliquée au bureau Windows 8.1 et Windows 10 et mobile appareils.

    Vous pouvez seulement créer et déployer un *personnalisé* Windows Wi-Fi importer une stratégie. Paramètres recommandés ne sont pas disponibles.

3.  Spécifiez les valeurs générales suivantes pour la stratégie d’importation Wi-Fi Windows :

    |Nom du paramètre|Plus d’informations|
    |----------------|--------------------|
    |**Nom**|Entrez un nom unique pour le profil Wi-Fi identifier dans la console Intune.|
    |**Description**|Fournir une description w du profil Wi-Fi et d’autres informations pertinentes qui vous aide à rechercher.|

4.  Spécifiez les valeurs suivantes sous l’en-tête **Personnalisé Wi-Fi profil** :

    |Nom du paramètre|Plus d’informations|
    |----------------|--------------------|
    |**Fichier de configuration de profil**|Cliquez sur **Importer** pour sélectionner le fichier XML contenant les paramètres de profil Wi-Fi que vous souhaitez importer dans Intune.|
    |**Nom du profil configuration personnalisée (présenté aux utilisateurs)**|Affiche le nom du profil de configuration Wi-Fi tel qu’il sera affiché pour les utilisateurs sur leur appareil.|
    |**Détails de profil de configuration**|Affiche le code XML pour le profil de configuration que vous avez sélectionné.|

5.  Lorsque vous avez terminé, cliquez sur **Enregistrer la stratégie**.

6.  La nouvelle stratégie s’affiche dans le nœud de **Stratégies de Configuration** de l’espace de travail de **stratégie** .

## Déployer le profil

Un profil est un type de stratégie, afin d’utiliser l’espace de travail de stratégie à déployer.

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis cliquez sur **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** :

    -   **Pour déployer la stratégie** - sélectionnez un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis cliquez sur **Ajouter** &gt; **OK**.

    -   **Pour fermer la boîte de dialogue sans le déployer** - cliquez sur **Annuler**.


Un résumé de l’état et les alertes dans la page **vue d’ensemble** de l’espace de travail de **stratégie** d’identifient les problèmes avec la stratégie qui nécessitent votre attention. En outre, un résumé de l’état apparaît dans l’espace de travail du tableau de bord.

## Paramètres de sécurité
Ces tableaux ont les détails pour les paramètres de sécurité sont disponibles pour les profils de Mac OS X Wi-Fi, iOS et Android. 

### Paramètres de sécurité des appareils Android

  |Nom du paramètre|Plus d’informations|Contexte d’utilisation :|
|----------------|--------------------|-------------|
|**Type de sécurité**|Sélectionnez le protocole de sécurité du réseau sans fil :<br /><br />-   **WPA-/ WPA2-Entreprise**<br />-   **Aucune authentification (Open)** si le réseau est sécurisé.|Toujours|
|**Type EAP**|Choisissez le type d’authentification EAP (Extensible Protocol) utilisé pour authentifier des connexions sans fil sécurisées :<br /><br />-   **CELUI-CI**<br />-   **PEAP**<br />-   **EAP-TLS**|Vous avez sélectionné le type de sécurité **WPA-/ WPA2-Entreprise** .|
|**Sélectionnez les certificats racine pour la validation du serveur**|Cliquez sur **Sélectionner**, puis choisissez le profil de certificat racine de confiance utilisé pour authentifier la connexion. **Importantes :** Pour créer le profil de certificat racine de confiance, voir [accès aux ressources sécurisé avec les profils de certificat](secure-resource-access-with-certificate-profiles.md).|N’importe quel **Type EAP** est sélectionnée.|
|**Méthode d’authentification**|Sélectionnez la méthode d’authentification pour la connexion :<br /><br />-   **Certificats** pour spécifier le certificat client<br />-   **Nom d’utilisateur et mot de passe** pour spécifier une autre méthode pour l’authentification|Le **type EAP** est **PEAP** ou **EAP-TLS**.|
|**Sélectionnez un mode non-EAP pour l’authentification (identité interne)**|Sélectionnez comment vous allez authentifier la connexion :<br /><br />-   **Aucun**<br />-   **Mot de passe non chiffré (PAP)**<br />-   **HIP négociation d’authentification CHAP (Protocol)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP Version 2 (MS-CHAP v2)**<br /><br />Les options disponibles dépendent du type EAP sélectionné.|La **méthode d’authentification** est le **nom d’utilisateur et mot de passe**.|
|**Activer la protection de la confidentialité (identité externe)**|Spécifier le texte envoyé en réponse à une demande d’identité EAP. Ce texte peut être n’importe quelle valeur. Lors de l’authentification, cette identité anonyme est envoyée au départ et enfin l’identification réel envoyé dans un tunnel sécurisé.|Le **type EAP** est **PEAP** ou **EAP-TLS**.|
|**Sélectionnez un certificat client pour l’authentification du client (certificat d’identité)**|Cliquez sur **Sélectionner**, puis choisissez le profil de certificat SCEP utilisé pour authentifier la connexion. **Importantes :** Pour créer un profil de certificat SCEP, voir [accès aux ressources sécurisé avec les profils de certificat](secure-resource-access-with-certificate-profiles.md).|Le type de sécurité est **WPA-/ WPA2-Entreprise**et n’importe quel **type EAP** est sélectionnée.|

### Paramètres de sécurité des appareils iOS et Mac OS X

  |Nom du paramètre|Plus d’informations|Contexte d’utilisation :|
|----------------|--------------------|-------------|
|**Type de sécurité**|Sélectionnez le protocole de sécurité réseau sans fil :<br /><br />-   **WPA-Personnel/WPA2-personnel**<br />-   **WPA-/ WPA2-Entreprise**<br />-   **WEP**<br />-   **Aucune authentification (Open)** si le réseau est sécurisé.|Toujours|
|**Type EAP**|Choisissez le type d’authentification EAP (Extensible Protocol) utilisé pour authentifier des connexions sans fil sécurisées :<br /><br />-   **CELUI-CI**<br />-   **PEAP**<br />-   **CELUI-CI**<br />-   **EAP AST**<br />-   **SAUTER**<br />-   **ASSISTANT DE EAP**|Vous avez sélectionné un type de sécurité de **WPA-/ WPA2-Entreprise**.|
|**Noms de certificat serveurs approuvés**|Sélectionnez le profil de certificat racine de confiance utilisé pour authentifier la connexion. **Importantes :** Pour créer le profil de certificat racine de confiance, voir [accès aux ressources sécurisé avec les profils de certificat](secure-resource-access-with-certificate-profiles.md).|Vous avez sélectionné un type EAP de **Celui-ci**, **PEAP**, **EAP-TLS** ou **EAP-FAST**.|
|**Utiliser protégé Access d’informations d’identification (PAC)**|Permet d’utiliser les informations d’identification de l’accès protégé pour établir un tunnel authentifié entre le client et le serveur d’authentification. Un fichier PAC existant est utilisé le cas échéant.|Le **type EAP** est **EAP-FAST**.|
|**Mise en service PAC**|Dispositions du fichier PAC à vos appareils.<br /><br />Lorsqu’il est utilisé, vous pouvez également sélectionner **Disposition PAC manière anonyme** pour vous assurer que le fichier PAC est mis en service sans authentification du serveur.|**Utiliser protégé d’informations d’identification (PAC Access)** est sélectionné.|
|**Méthode d’authentification**|Sélectionnez la méthode d’authentification utilisée pour la connexion :<br /><br /><ul><li>**Certificats** pour spécifier le certificat client</li><li>**Nom d’utilisateur et mot de passe** pour spécifier l’une des méthodes suivantes non EAP pour l’authentification (également appelé identité interne) :<br /><br /><ul><li>**Aucun**</li><li>**Mot de passe non chiffré (PAP)**</li><li>**HIP négociation d’authentification CHAP (Protocol)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP Version 2 (MS-CHAP v2)**</li><li>**CELUI-CI**</li></ul></li></ul>|Le **type EAP** est **PEAP**ou **EAP-TLS**.|
|**Sélectionnez un certificat client pour l’authentification du client (certificat d’identité)**|Sélectionnez le profil de certificat SCEP utilisé pour authentifier la connexion. **Importantes :** Pour créer un profil de certificat SCEP, voir [accès aux ressources sécurisé avec les profils de certificat](secure-resource-access-with-certificate-profiles.md).|Lorsque le type de sécurité est **WPA-/ WPA2-Entreprise** et le **type EAP** est **Celui-ci**, **PEAP** ou **EAP-TLS**.|
|**Activer la protection de la confidentialité (identité externe)**|Spécifier le texte envoyé en réponse à une demande d’identité EAP. Ce texte peut être n’importe quelle valeur.<br /><br />Lors de l’authentification, cette identité anonyme est initialement envoyée, suivi de l’identification réelle envoyée dans un tunnel sécurisé.|Lorsque le **type EAP** est défini sur **PEAP**, **EAP-TLS** ou **EAP-FAST**.|


### Voir aussi
Apprenez à créer un profil Wi-Fi avec une clé pré partagée en [partagée profil Wi-Fi clé](pre-shared-key-wi-fi-profile.md)
