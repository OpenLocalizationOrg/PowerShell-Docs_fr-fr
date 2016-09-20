---
title: "Renvoyer à la ligne applications Android avec application outil d’habillage | Microsoft Intune"
description: "Utilisez les informations dans cette rubrique pour apprendre à renvoyer à la ligne de vos applications Android sans modifier le code de l’application elle-même. Préparer les applications afin que vous pouvez appliquer des stratégies de gestion de l’application mobile."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
ms.openlocfilehash: 51da3e13af385a3263cc9c6f282d569295b1106b
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Préparer les applications Android pour la gestion des applications mobiles avec l’outil d’habillage de l’application Intune
Utilisez l' **Microsoft Intune application habillage outil pour Android** pour modifier le comportement de vos applications Android internes à vous permettent de configurer les fonctionnalités de l’application sans modifier le code de l’application elle-même.

L’outil est une application de ligne de commande Windows qui s’exécute dans PowerShell et crée un emballage autour de votre application. Une fois que l’application est traitée, vous pouvez ensuite modifier les fonctionnalités de l’application à l’aide de [stratégies de gestion des applications mobiles](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) que vous configurez.


Avant d’exécuter l’outil, passez en revue les [Considérations relatives à la sécurité pour l’exécution de l’application outil d’habillage](#security-considerations-for-running-the-app-wrapping-tool). Pour télécharger l’outil, voir [Microsoft Intune application habillage outil pour Android](https://www.microsoft.com/download/details.aspx?id=47267).

>[!IMPORTANT]
>La version de l’application, un outil qui prend en charge des appareils ne pas inscrits dans Intune, d’habillage est disponible pour la version d’évaluation. Si vous souhaitez participer à la version d’évaluation, vous pouvez télécharger l’outil à partir de [cette page github](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview) pour Android.

Le scénario est décrite dans la rubrique [applications métiers protéger sur appareils ne pas inscrits dans Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md) .


## Étape 1 remplissent les conditions préalables à l’aide de l’application outil d’habillage

-   Vous devez exécuter l’application d’habillage outil sur un ordinateur Windows exécutant Windows 7 ou version ultérieure.

-   Votre application d’entrée doit être un package d’application Android valide avec le fichier d’extension **.apk** et :

    -   Ne peut pas être chiffré

    -   Doit pas déjà été encapsulé par l’application outil d’habillage

    -   Doivent être écrits pour Android 4.0 ou version ultérieure

-   L’application doit être développée par, ou pour votre société. Vous ne pouvez pas utiliser cet outil pour traiter les applications téléchargées à partir de Google Play Store.

-   Pour exécuter l’application outil d’habillage, vous devez installer la dernière version de l' [Environnement d’exécution Java](http://java.com/download/) et vérifiez que la variable de chemin d’accès Java a été définie pour **C:\ProgramData\Oracle\Java\javapath** dans vos variables d’environnement Windows. Pour plus d’informations, consultez la [documentation Java](http://java.com/download/help/).

    > [!NOTE]
    > Dans certains cas, la version 32 bits de Java peut entraîner des problèmes de mémoire. Nous vous recommandons d’installer la version 64 bits à la place.

## Étape 2 installer l’application outil d’habillage

1.  À partir de la Center Download Microsoft, téléchargez et ouvrez le fichier d’installation de l’outil d’habillage application sur un ordinateur Windows.

2.  Acceptez le contrat de licence, puis terminer l’installation.

Notez le dossier dans lequel vous avez installé l’outil. L’emplacement par défaut est : **C:\Program Files (x86) \Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Étape 3, puis exécutez l’application outil d’habillage

1.  Sur l’ordinateur Windows où vous avez installé l’application outil d’habillage, ouvrez une fenêtre de PowerShell en mode administrateur.

2.  Dans le dossier où vous avez installé l’outil, importer l’application habillage du module de PowerShell l’outil :

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Exécutez l’outil à l’aide de la commande **AppWrappingTool appeler** avec les paramètres suivants.

|Paramètre|Plus d’informations|Exemples|
|-------------|--------------------|---------|
|**-InputPath**&lt;chaîne&gt;|Chemin d’accès de l’application Android source (.apk).| |
|**-OutputPath**&lt;chaîne&gt;|Chemin d’accès à l’application Android « sortie ». Si c’est le même emplacement que InputPath, l’emballage échouera.| |
|**-KeyStorePath**&lt;chaîne&gt;|Chemin d’accès au fichier combinaison de touches qui contient la paire clée publique/privée pour la signature.| |
|**-KeyStorePassword**&lt;SecureString&gt;|Mot de passe permettant de déchiffrer la combinaison de touches. Android nécessite que toutes les applications packages (.apk) pour être connecté. Utilisez l’outil de clé Java pour générer la KeyStorePassword comme illustré dans l’exemple. En savoir plus sur la [combinaison de touches](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).|keytool.exe - genkey - v - combinaison de touches keystorefile-alias ks - keyalg RSA - clé 2048 - validité 50000 |
|**-KeyAlias**&lt;chaîne&gt;|Nom de la clé à utiliser pour la signature.| |
|**KEYAuthentification -**&lt;SecureString&gt;|Mot de passe permettant de déchiffrer la clé privée qui sera utilisée pour la signature.| |
|**-SigAlg**&lt;SecureString&gt;|Nom de l’algorithme de signature à utiliser pour la signature. L’algorithme doit être compatible avec la clé privée.|Exemples : SHA256withRSA, SHA1withRSA, MD5withRSA|


**&lt;Paramètres_courants&gt; ** 
 (facultatif – prend en charge les paramètres PowerShell courantes telles que débogage détaillé, etc..)

- Pour obtenir la liste des paramètres courants, voir le [Centre de Script Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Pour afficher l’aide de l’outil, entrez la commande :

    ```
    Help Invoke-AppWrappingTool
    ```

**Exemple :**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app.wrapped\HelloWorld_wrapped2.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\keystorefile" -keyAlias ks -SigAlg SHA1withRSA -Verbose

Vous demandera puis des chaînes **KeyStorePassword** **KEYAuthentification**.

L’application encapsulée est générée et enregistrée, ainsi qu’un fichier journal, dans le chemin d’accès de sortie que vous avez spécifié.

## Considérations relatives à la sécurité pour l’exécution de l’application outil d’habillage
Pour empêcher l’usurpation d’adresse potentiels, divulgation d’informations et les attaques de privilège :

-   Assurez-vous que l’application métier d’entrée, des applications de sortie et combinaison de touches Java sont sur le même ordinateur exécutant l’outil de retour à la ligne de l’application.

-   Importez l’application de sortie à la console Intune sur le même ordinateur où l’outil est en cours d’exécution. Voir [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) pour plus d’informations sur l’outil de clés Java.

-   Si l’application de sortie et l’outil se trouvent sur un chemin d’accès de Convention d’affectation de noms (UNC) et que vous exécutez pas l’outil et les fichiers d’entrée sur le même ordinateur, configurer l’environnement pour être sûr à l’aide de [Internet protocole sécurité](http://en.wikipedia.org/wiki/IPsec) ou [PMI Server Message bloc de signature](https://support.microsoft.com/en-us/kb/887429).

-   Assurez-vous que l’application provient d’une source fiable, qui peut-être permettre à l’application accéder le jeton AAD pendant l’exécution.

-   Sécuriser le répertoire de sortie qui contient l’application renvoyé à la ligne. Envisagez d’utiliser un répertoire au niveau utilisateur pour la sortie.



### Voir aussi
- [Déterminez comment préparer les applications pour la gestion des applications mobiles avec Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Utiliser le Kit de développement pour activer les applications pour la gestion des applications mobiles](use-the-sdk-to-enable-apps-for-mobile-application-management.md)
