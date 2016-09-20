---
title: "Limiter l’accès aux réseaux avec Cisco ISE | Microsoft Intune"
description: "Utilisez ISE Cisco avec Intune afin que les périphériques soient Intune inscrit et stratégie de respecter les exigences avant d’accéder Wi-Fi et VPN contrôlés par Cisco ISE."
keywords: 
author: nbigman
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: 972848a33764e7073fd9c1867e0a7df643dd630e
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# À l’aide de Cisco ISE avec Microsoft Intune
Intune intégration avec Cisco identité Services moteur (ISE) vous permet de créer des stratégies de réseau dans votre environnement ISE en utilisant l’état d’inscription de l’appareil et conformité Intune. Vous pouvez utiliser ces stratégies pour vous assurer que l’accès à votre réseau d’entreprise est limité aux périphériques qui sont gérées par Intune et la conformité avec les stratégies Intune.

## Étapes de configuration

Pour activer cette intégration, vous n’avez pas besoin effectuer une configuration de votre client Intune. Vous devrez fournir des autorisations à votre serveur Cisco ISE à accéder à votre client Intune. Une fois que cela est fait, le reste de la configuration s’est-il passé dans votre serveur Cisco ISE. Cet article vous explique comment fournir un votre serveur ISE avec les autorisations pour accéder à votre client Intune.

### Étape 1 : Gestion des certificats
Exportez le certificat de la console Azure Active Directory (AD Azure), puis importez-les dans le magasin de certificats approuvés de la console ISE :

#### Internet Explorer 11


   un. Exécuter Internet Explorer en tant qu’administrateur, puis connectez-vous à la console Azure AD.

   b. Sélectionnez l’icône de verrou dans la barre d’adresses et choisissez **Afficher les certificats**.

   c. Sous l’onglet **Détails** des propriétés du certificat, cliquez sur **Copier dans un fichier**.

   d. Dans la page Bienvenue dans **l’Assistant Exportation de certificat** , cliquez sur **suivant**.

   e. Dans la page **format de fichier d’exportation** , conservez la valeur par défaut, **DER codé binaire x.509 (. Limitée)**, cliquez sur **suivant**.  

   f. Dans la page **fichier à exporter** , cliquez sur **Parcourir** pour sélectionner un emplacement dans lequel vous voulez enregistrer le fichier, puis attribuez un nom de fichier. S’il semble que vous êtes en sélectionnant un fichier à exporter, vous nommez réellement le fichier sera enregistré dans le certificat exporté. Choisissez **suivant** &gt; **fin**.

   g. À partir de la console ISE, importez le certificat Intune (le fichier que vous avez exporté) dans le magasin de **Certificats de confiance** .

#### Safari

 un. Se connecter à la console Azure AD.

b. Cliquez sur l’icône de verrou &gt; **plus d’informations**.  

   c. Cliquez sur **Afficher le certificat** &gt; **Détails**.

   d. Sélectionnez le certificat, puis **Exporter**. 

   e. À partir de la console ISE, importez le certificat Intune (le fichier que vous avez exporté) dans le magasin de **Certificats de confiance** .

> [!IMPORTANT]
>
> Vérifiez la date d’expiration du certificat, car vous aurez exporter et importer un nouveau certificat à la fin de celui-ci.


### Obtenir un certificat auto-signé à partir de ISE 

1.  Dans la console ISE, accédez à **Administration** > **certificats** > **Certificats système** > **Générer sélectionner un certificat signé**.  
2.       Exportez le certificat auto-signé.
3. Dans un éditeur de texte, modifiez le certificat exporté : [commentaire] : <> je préfère pas mettez une période à la fin de ces deux instructions, je pense qu’il peut être difficile.
 - Supprimer **situés à commencer certificat situés à**
 - Supprimer **situés à mettre fin à certificat situés à**
 
Assurez-vous que tout le texte est une seule ligne


### Étape 2 : Créer une application pour ISE dans votre client Azure AD
1. Dans la console Azure AD, sélectionnez **Applications** > **Ajouter une Application** > **Ajouter une application de développe de mon organisation**.
2. Indiquez un nom et une URL pour l’application. L’URL pourrait être site de votre société.
3. Télécharger le manifeste d’application (fichier JSON).
4. Modifier le fichier manifeste JSON. Dans le paramètre appelé **keyCredentials**, fournissent le texte du certificat modifié à l’étape 1 en tant que la valeur de paramètre.
5. Enregistrez le fichier sans modifier son nom.
6. Fournir votre application avec des autorisations à Microsoft Graph et l’API Intune Microsoft.

 un. Pour Microsoft Graph, sélectionnez les éléments suivants :
    - **Autorisations des applications**: lire les données de l’annuaire
    - **Droits délégués**:
        - Accéder aux données de l’utilisateur à tout moment
        - Utilisateurs de se connecter dans

 b. Pour l’API Intune Microsoft, dans les **autorisations des applications**, sélectionnez **obtenir l’état du périphérique et la conformité à partir de Intune**.

7. Sélectionnez les **Points de terminaison de vue** et copiez les valeurs suivantes pour une utilisation de la configuration des paramètres ISE :

|Valeur portail Azure AD|Champ correspondant dans le portail ISE|
|-------------------|---------------------------------|
|Point de terminaison de l’API Microsoft Azure AD Graph|URL de découverte automatique|
|Point de terminaison OAuth 2.0 jetons|URL émission jeton|
|Mettre à jour votre code avec votre ID Client|ID de client|

### Étape 4 : Télécharger le certificat auto-signé de ISE dans l’application ISE que vous avez créé dans Azure Active Directory
1.     Obtenez la valeur de certificat en base 64 codé et l’empreinte numérique d’un fichier de certificat public .cer X509. Cet exemple utilise PowerShell :
   
      
    `$cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2`
     `$cer.Import(“mycer.cer”)`
      `$bin = $cer.GetRawCertData()`
      `$base64Value = [System.Convert]::ToBase64String($bin)`
      `$bin = $cer.GetCertHash()`
      `$base64Thumbprint = [System.Convert]::ToBase64String($bin)`
      `$keyid = [System.Guid]::NewGuid().ToString()`
 
    Stocker les valeurs pour base64Thumbprint $, base64Value $ et $keyid, pour être utilisé dans l’étape suivante.
2.       Téléchargez le certificat par le biais du fichier manifeste. Connectez-vous au [portail de gestion Azure](https://manage.windowsazure.com)
2.      Dans le composant logiciel enfichable Azure AD de trouver l’application que vous souhaitez configurer avec un certificat X.509.
3.      Téléchargez le fichier manifeste d’application. 
5.      Remplacer le « KeyCredentials » vide : [], propriété avec la JSON suivant.  Le type complexe KeyCredentials présentée dans[l’entité et référence de type complexe](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType).

 
    `“keyCredentials“: [`
    `{`
     `“customKeyIdentifier“: “$base64Thumbprint_from_above”,`
     `“keyId“: “$keyid_from_above“,`
     `“type”: “AsymmetricX509Cert”,`
     `“usage”: “Verify”,`
     `“value”:  “$base64Value_from_above”`
     `}2. `
     `], `
 
Par exemple :
 
    `“keyCredentials“: [`
    `{`
    `“customKeyIdentifier“: “ieF43L8nkyw/PEHjWvj+PkWebXk=”,`
    `“keyId“: “2d6d849e-3e9e-46cd-b5ed-0f9e30d078cc”,`
    `“type”: “AsymmetricX509Cert”,`
    `“usage”: “Verify”,`
    `“value”: “MIICWjCCAgSgAwIBA***omitted for brevity***qoD4dmgJqZmXDfFyQ”`
    `}`
    `],`
 
6.      Enregistrez la modification dans le fichier manifeste d’application.
7.      Télécharger le fichier manifeste d’application modifiée via la gestion Azure mourir.
8.      Facultatif : Télécharger le manifeste à nouveau, pour vérifier que votre certificat X.509 figure dans l’application.

>[!NOTE]
>
> KeyCredentials étant une collection de sites, vous pouvez télécharger plusieurs certificats X.509 pour les scénarios de survol ou supprimer des certificats dans les scénarios compromis.


### Étape 4 : Configurer les paramètres de ISE
Dans la console d’administration ISE, fournissent les valeurs de paramètre suivantes :
  - **Type de serveur**: Mobile Device Manager
  - **Type d’authentification**: jeton – informations d’identification Client
  - **Découverte automatique**: Oui
  - **URL de découverte automatique**: *Entrez la valeur à l’étape 1.*
  - **ID Client**: *Entrez la valeur à l’étape 1.*
  - **Jetons émission URL**: *Entrez la valeur à l’étape 1.*



## Informations partagées entre votre client Intune et votre serveur Cisco ISE
Ce tableau répertorie les informations sont partagées entre votre client Intune et votre serveur ISE Cisco pour les périphériques qui sont gérés par Intune.

|Propriété|  Description|
|---------------|------------------------------------------------------------|
|complianceState|Chaîne true ou false qui indique si l’appareil est conforme ou non conforme.|
|isManaged|La chaîne true ou false qui indique si le client est géré par Intune ou non.|
|adresse MAC|L’adresse MAC de l’appareil.|
|numéro de série|Le numéro de série de l’appareil. Elle s’applique uniquement aux appareils iOS.|
|IMEI|La IMEI (15 chiffres décimaux : 14 chiffres plus un chiffre à cocher) ou nombre (16 décimales) de IMEISV inclut des informations sur l’origine, le modèle et le numéro de série de l’appareil. La structure de ce nombre est spécifiée dans 3GPP TS 23.003. Elle s’applique uniquement aux périphériques avec des cartes de l’Assistant.|
|UDID|APPAREIL identificateur Unique, qui est une séquence de lettres et de chiffres 40. Il est spécifique aux appareils iOS.|
|meid|L’identificateur équipement mobile, qui est un numéro unique qui identifie un élément physique d’équipement mobile CDMA. Le format de nombre est défini par le rapport 3GPP2 R0048 s. Toutefois, en pratique, il puisse être vu comme un IMEI, mais avec décimales nombre hexadécimales. Un MEID est 56 bits (14 chiffres hexadécimales). Il est composée de trois champs, y compris un code régionaux 8 bits (enregistrement de ressource), un code fabricant 24 bits et un numéro de série 24 bits affectée par le fabricant.|
|osVersion|La version du système d’exploitation pour le périphérique.
|modèle|Modèle de périphérique.
|fabricant|Le fabricant du périphérique.
|azureDeviceId|L’ID de l’appareil après avoir rejoint avec Azure AD un espace de travail. Il est un GUID vide pour les périphériques qui ne sont pas joints.|
|lastContactTimeUtc|La date et l’heure lorsque l’appareil dernière vérification à l’aide du service de gestion des Intune.


## Expérience utilisateur

Lorsqu’un utilisateur tente d’accéder aux ressources à l’aide d’un périphérique unenrolled, ils reçoivent une invite d’inscription, tel que celui illustré ici :

![Exemple d’invite d’inscription](../media/cisco-ise-user-iphone.png)

Lorsqu’un utilisateur choisit d’inscription, ils sont redirigés vers le processus d’inscription Intune. L’expérience d’inscription d’un utilisateur pour Intune est décrit dans les rubriques suivantes :

- [Inscrire votre appareil Android dans Intune](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [Inscrire votre appareil iOS dans Intune](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [Inscrire votre appareil Mac OS X dans Intune](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [Inscrire votre appareil Windows dans Intune](/intune/enduser/enroll-your-device-in-intune-windows)</br>

Vous trouverez également un [ensemble téléchargeable d’instructions d’inscription](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) que vous pouvez utiliser pour créer des instructions personnalisées pour votre expérience utilisateur.


### Voir aussi

[Identité Cisco Services Guide administrateur moteur, version 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)
