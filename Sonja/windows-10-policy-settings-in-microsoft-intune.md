---
title: "Paramètres de stratégie Windows 10 | Microsoft Intune"
description: "Utilisez les paramètres de stratégie répertoriés dans cette rubrique pour vous aider à configurer les paramètres intégrés et personnalisés pour les appareils Windows 10 Mobile et inscrit bureau Windows 10."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 712883874f022ceb3f38473839fe0d6e4c373164
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie Intune pour appareils Windows 10 dans Microsoft Intune

Cette rubrique contient des informations pour vous aider à comprendre les paramètres de stratégie Intune, vous pouvez utiliser pour gérer les appareils Windows 10. Lisez cette rubrique en parallèle avec les procédures [Gérer les paramètres et fonctionnalités sur vos appareils avec Microsoft Intune stratégies](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) pour configurer les paramètres intégrés et personnalisés pour les appareils Windows 10 Mobile et inscrit bureau Windows 10. Vous ne pouvez pas utiliser ces politiques avec les ordinateurs qui exécutent le [logiciel client Intune PC](/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Vous avez le choix entre deux types de stratégie :

- **Stratégie personnalisée** - utiliser la Microsoft Intune **stratégie personnalisée** pour Windows 10 et Windows 10 Mobile déployer les paramètres OMA-URI (ouvrir Mobile Alliance Uniform Resource Identifier) qui peuvent être utilisés pour contrôler les fonctionnalités sur les appareils. Windows 10 rend de nombreux paramètres disponibles via la [Stratégie de Configuration de fournisseur de services (stratégie)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Stratégie de configuration général** - Utilisez cette stratégie type lorsque vous souhaitez sélectionner des paramètres dans la liste intégrée fournie avec Microsoft Intune.

## Paramètres de stratégie personnalisés

Fournissez les paramètres suivants dans une stratégie personnalisée :

## &nbsp;&nbsp;&nbsp;Général

Entrez un nom et éventuellement une description pour vous aider à identifier dans la console Intune cette stratégie.

## &nbsp;&nbsp;&nbsp;Paramètres d’OMA URI

Pour chaque paramètre OMA URI que vous voulez ajouter, entrez les informations suivantes. Utiliser la [référence de paramètres de Windows 10 URI](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) dans cette rubrique pour en savoir plus sur les paramètres que vous pouvez utiliser : 

- **Définition du nom** - Entrez un nom unique pour le paramètre OMA URI pour vous aider à identifier dans la liste des paramètres.
- **Description des paramètres** - Entrez éventuellement une description pour le paramètre.
- **Type de données** - choisissez :
    - **Chaîne**
    - **Chaîne (XML)**
    - **Date et heure**
    - **Nombre entier**
    - **Virgule flottante**
    - **Valeur booléenne**
- **OMA-URI (respecter la casse)** - spécifier l’OMA-URI que vous souhaitez fournir un paramètre pour.
- **Valeur** - spécifier la valeur à associer à l’OMA-URI que vous avez entré.

### Exemple
Dans la capture d’écran ci-dessous, le paramètre **Conectivity/AllowVPNOverCellular** a été activé. Un appareil Windows 10 vous permet d’ouvrir une connexion VPN sur un réseau cellulaire.

> ![Exemple d’une stratégie personnalisée contenant les paramètres de VPN](./media/custom-policy-example.png)

## Paramètres Windows 10 URI
Utilisez cette section pour en savoir plus sur les paramètres de OMA URI que vous pouvez configurer avec une **Stratégie de Windows 10 personnalisée**.

## &nbsp;&nbsp;&nbsp;Stratégie

|Nom de la stratégie et URI|Plus d’informations|
|---------------|------------|-----------|
|**Autoriser les mises à jour automatiques**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Ordinateur de bureau uniquement<br>**Type de données :** Nombre entier<br />**Valeurs :** **0**  -  **5** (par défaut : **1**)|
|**Jour de l’installation échéancier**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Mobile uniquement<br>**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - quotidiennement (par défaut)<br>**1** - dimanche<br>**2** - lundi<br>**3** - mardi<br>**4** - mercredi<br>**5** - jeudi<br>**6** - vendredi<br>**7** - samedi|
|**Moment de l’installation échéancier**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** à **23** heures (minuit est**0** ) (par défaut : **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - utilisateur ne peut pas configurer le minuteur de la période de grâce mot de passe ; valeur est définie comme « chaque heure »<br>**1** - utilisateur peut définir le minuteur de la période de grâce mot de passe (par défaut)|
|**Wi-Fi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – n’autorisent pas **utiliser connexion Wi-Fi**.<br>**1** –**Autoriser l’utilisation connexion Wi-Fi** (valeur par défaut)|
|**Wi-Fi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Ordinateurs de bureau et mobiles<br>**Type de données :** Nombre entier<br />**Valeurs :** **0** – ne pas autoriser le partage Internet **1** – autoriser Internet partage (par défaut)|
|**Wi-Fi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Wi-Fi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – connexion aucune Wi-Fi en dehors de la gestion des périphériques sa mise en service est autorisé.<br>**1** – Ajout nouveau réseau SSID au-delà de la déjà MDM sa mise en service celles autorisé (par défaut)|
|**Système/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Système/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Ordinateurs de bureau et mobiles<br>**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – non autorisé (entreprise uniquement)<br>**1** – limité<br>**2** -plein (par défaut)<br>**3** - informations plein et les diagnostics|
|**Système/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – non autorisé<br>**1**- paramètres (par défaut)<br>**2**- paramètres et essais|
|**Sécurité/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - ne pas autoriser le mode vol Anti<br>Préférences de l’utilisateur **1** (par défaut)|
|**Connectivité/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Système/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Connectivité/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Connectivité/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - VPN n’est pas autorisé via cellulaire<br>**1** – VPN peut utiliser n’importe quelle connexion notamment cellulaire (par défaut)|
|**Connectivité/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Connectivité/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Connectivité/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – ne pas autoriser l’utilisateur à activer Bluetooth.<br>**1** – en réservés. L’utilisateur peut activer et configurer Bluetooth (non pris en charge dans Windows Phone 8.1 des périphériques mobiles, EAS, ordinateur de bureau de Windows 10 ou Windows 10 Mobile)<br>**2** - en autorisée. L’utilisateur peut activer et configurer Bluetooth (par défaut)|
|**Expérience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Expérience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Expérience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Expérience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – ne permettent pas d’itinérance, **1** – autoriser d’itinérance (par défaut)|
|**Expérience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Comptes/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Comptes/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Sécurité/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Sécurité/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Recherche/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** (par défaut), **1**|
|**Recherche/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0**, **1** (par défaut)|
|**Recherche/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** (par défaut), **1**|
|**Recherche/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** (par défaut), **1**|
|**Recherche/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** (par défaut), **1**|
|**Recherche/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0**, **1** (par défaut)|
|**Recherche/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** (par défaut), **1**|
|**Sécurité/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Sécurité/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** (par défaut), **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – ne pas autoriser<br>Ouverture du dictionnaire étendu est désactivé.<br>Un utilisateur ne peut pas :<br>-Ajouter une nouvelle ouverture du dictionnaire étendu<br />-Ajouter un nouveau fichier de configuration de l’intégration de recherche<br>-Utiliser la fonctionnalité de candidats cloud<br>-Envoyer word enregistrés de l’utilisateur.<br>**1** - autoriser<br>Ouverture du dictionnaire étendu peut être ajouté et utilisé par défaut. En outre, la fonction de l’intégration de recherche peut être utilisée par défaut.<br>Un utilisateur peut :<br>Utilisez la fonctionnalité de candidats cloud.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - mauvaise conversion se déconnecter.<br>**1** - mauvaise conversion ouverture de session (par défaut)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé **1** – autorisé (par défaut)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - aucun caractère n’est filtrée (par défaut)<br>**1** - caractères tout sauf JIS MAJ sont filtrées|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br />**0** - aucun caractère n’est filtrée (par défaut)<br>**1** - tout sauf la JIS0208 caractères sont filtrées|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - aucun caractère n’est filtrée (par défaut)<br>**1** - tout sauf la JIS0208 caractères ou EUDC sont filtrées|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Paramètres/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Expérience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Recherche/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – stricte, le plus élevé filtrage contre les contenus gros<br>**1** – modérer modéré, filtrage contre les contenus gros (valide recherche résultats ne seront pas filtrés - par défaut)|
|**Expérience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**Forcer la taille de début**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - permet de modifier la taille d’utilisateur (par défaut)<br>**1** - forcer non plein écran<br>**2** - force en mode plein écran|
|**Mise à jour/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0**: ne diffèrent pas de mise à niveau (rester dans la branche actuels, bloc de contrôle - par défaut)<br>**1**: activer les mises à jour et mises à niveau vers être différé (appareil suit branche actuels des règles d’entreprise, CBB,)<br />Pour plus d’informations, voir :<br>[Introduction à la maintenance de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de déploiement de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Mise à jour/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Ordinateurs de bureau et mobiles<br>**Description :** Stratégie différer mises à jour logicielles pour jusqu'à 4 semaines<br />**Type de données :** Nombre entier<br />**Valeurs :**<br> **0**: appliquer des mises à jour immédiatement (par défaut)<br>**1**-**4**: nombre de semaines différer mises à jour logicielles.<br />Pour plus d’informations, voir :<br>[Introduction à la maintenance de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de déploiement de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Mise à jour/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Ordinateurs de bureau et mobiles<br>**Description :** Stratégie différer mises à jour de la fonctionnalité de jusqu'à 8 mois<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0**: appliquer des mises à jour immédiatement (par défaut)<br>**1**-**8**: nombre de mois différer mises à jour de la fonctionnalité.<br />Pour plus d’informations, voir :<br>[Introduction à la maintenance de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de déploiement de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Mise à jour/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Ordinateurs de bureau et mobiles<br>**Description :** Permet à un périphérique arrêter de recevoir des mises à jour et mises à niveau pour 5 semaines.<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0**: appliquer des mises à jour immédiatement (par défaut)<br>**1**: pause et mises à jour (expire après 5 semaines)|

## &nbsp;&nbsp;&nbsp;Windows Defender

|Nom de la stratégie et URI|Plus d’informations|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – surveiller tous les fichiers (par défaut)<br>**1** – les fichiers entrants moniteur<br>**2** -moniteur les fichiers sortants|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - **90** – représente quel programme malveillant combien de temps est conservé<br>**Par défaut :** **0** – reste dans le dossier de quarantaine indéfiniment et ne supprime pas automatiquement|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**1** – analyse rapide (par défaut)<br>**2** - analyse complète|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - tous les jours (par défaut)<br>**1** - lundi<br>**2** - mardi<br>**3** - mercredi<br>**4** - jeudi<br>**5** - vendredi<br>**6** - samedi<br>**7** - dimanche<br>**8** – aucune analyse planifiée|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - 12:00 am<br>**60** – 1:00 am<br>**120** – 2:00 am (par défaut)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 17 h<br>**540** – 9:00 am<br>**600** – 10:00:00<br>**660** -11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** -3:00 pm<br>**960** – 4:00 pm<br>**1020** – 17 h<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1381** – fenêtre Gestion|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Ordinateur de bureau uniquement<br>**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** - 12:00 am<br>**60** – 1:00 am<br>**120** – 2:00 am (par défaut)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 17 h<br>**540** – 9:00 am<br>**600** – 10:00:00<br>**660** -11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** -3:00 pm<br>**960** – 4:00 pm<br>**1020** – 17 h<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1380** – 11:00 pm|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0**  -  **100** (par défaut : **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br>**Valeurs :** **0** – non autorisé (par défaut), **1** – autorisées|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé (par défaut), **1** – autorisées|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisées (par défaut) – s’exécute également lorsque RTP est activé si la valeur autorisé|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – ne pas vérifier des signatures sur un intervalle<br>**1** - vérifier la présence de toutes les heures des signatures<br>**2** -vérifier toutes les heures 2, etc..<br>**24** – à cocher tous les jours<br>**Valeur par défaut :** 8 – vérifier toutes les 8 heures|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – non autorisé, **1** – autorisés (par défaut)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – toujours demander un mot (par défaut)<br>Exemples de **1** – safe envoyer automatiquement<br>**2** -ne jamais envoyer<br>**3** -envoyer tous les échantillons automatiquement|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Ordinateur de bureau uniquement<br />**Type de données :** Chaîne<br />**Valeurs :**<br>* &lt;liste des extensions, séparés par des points-virgules&gt; * Par exemple **obj ; bibliothèque**<br>**Par défaut :** Aucune extension exclues|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Ordinateur de bureau uniquement<br />**Type de données :** Chaîne<br />**Valeurs :**<br />*&lt;liste des chemins d’accès séparés par des points-virgules&gt;*<br />Exemple : **c:\test;c:\test1.exe**<br />**Valeur par défaut :** Aucun chemin d’accès n’est exclus|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Ordinateur de bureau uniquement<br />**Type de données :** Chaîne<br />**Valeurs :**<br>*&lt;liste des chemins d’accès séparés par des points-virgules&gt;*<br>Exemple : **c:\test.exe;c:\test1.exe**<br>**Valeur par défaut :** Aucun processus n’est exclu|

## &nbsp;&nbsp;&nbsp;Navigateur de bord

|Nom de la stratégie et URI|Plus d’informations|
|---------------|------------|-----------|
|**Autoriser le navigateur**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Mobile uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0**: navigation, **1**: la navigation sur (par défaut)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0**: ne pas afficher les suggestions de **1**: afficher les suggestions (par défaut)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0**: désactivé (sites intranet ouverts dans le navigateur de bord - par défaut))<br>**1** - activé (sites intranet ouvert dans Internet Explorer).|
|**Autoriser pas effectuer le suivi**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Mobile et de bureau)<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – désactivé (DNT ne pas envoyé : par défaut), **1** -Enabled (envoyer DNT)|
|**Configurer SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – n’autorisent pas, **1** – autoriser (par défaut)|
|**Autoriser les fenêtres contextuelles**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – bloquer les fenêtres contextuelles (par défaut), **1** – autoriser les fenêtres publicitaires intempestives|
|**Activer les Cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – autoriser les cookies de tous les sites web (par défaut)<br>**1** – bloquer les cookies tiers uniquement<br>**2** -bloquer tous les cookies|
|**Autoriser l’enregistrement mot de passe**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Ordinateurs de bureau et mobiles<br />**Type de données :** Nombre entier<br />**Valeurs :**<br>**0** – Gestionnaire de mot de passe est désactivé ; <br>**1** – mot de passe gestionnaire est activé (par défaut)|
|**Autoriser la recopie incrémentée**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Ordinateur de bureau uniquement<br />**Type de données :** Nombre entier<br />**Valeurs :** **0** – désactivé (valeur par défaut), **1** – activé|
|**Configurer la liste des sites**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Ordinateur de bureau uniquement<br />**Type de données :** Chaîne<br />**Valeurs :<br>**0** – n’est pas configuré<br>**1** – enterprise mode liste utiliser Internet Explorer si configuré (par défaut)<br>**2 ** – spécifier un emplacement de la liste des sites entreprise|

## Paramètres de stratégie de configuration générale

Utilisez la **stratégie de configuration générale** de Microsoft Intune pour Windows 10 pour configurer les paramètres prédéfinis pour les appareils Windows 10 Mobile et inscrit bureau Windows 10. 

## &nbsp;&nbsp;&nbsp;Mot de passe

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|
|**Exiger un mot de passe pour la déverrouiller appareils**|-|
|**Obligatoires type de mot de passe**|Indique si le mot de passe doit être numérique uniquement ou alphanumérique|
|**Obligatoires type de mot de passe** - **jeux de nombre minimal de caractères**|Il existe quatre jeux de caractères, minuscules, majuscules, nombres et symboles. Ce paramètre spécifie le nombre de ces ensembles doit être inclus dans le mot de passe.|
|**Longueur minimale**|S’applique à Windows 10 Mobile uniquement|
|**Nombre d’échecs de signe répétés autorisé avant que l’appareil est sélective**|Pour les appareils exécutant Windows 10 : si le périphérique a BitLocker activé, il sera placé dans le mode de récupération BitLocker après connexion échoue le nombre de fois que vous spécifiez. Si l’appareil n’est pas BitLocker activé, ce paramètre n’applique pas.<br>Pour les appareils exécutant Windows 10 Mobile : efface après la connexion à défaillance le nombre de fois que vous spécifiez, l’appareil.|
|**Minutes d’inactivité avant la désactivation écran**|Spécifie la durée pendant laquelle qu'un périphérique doit être inactif avant de l’écran est verrouillé.|
|**Expiration du mot de passe (jours)**|Spécifie la durée après laquelle le mot de passe doit être modifié.|
|**N’oubliez pas de l’historique de mot de passe**|Indique si vous souhaitez empêcher l’utilisateur final de créer des mots de passe utilisés précédemment.|
|**N’oubliez pas de l’historique de mot de passe** - **empêcher la réutilisation des mots de passe précédents**|Spécifie le nombre de mots de passe précédemment utilisés par le périphérique à retenir.|
|**Demander un mot de passe lorsque l’appareil est retournée à partir d’un état d’inactivité**|Si activé, l’utilisateur doit entrer un mot de passe pour déverrouiller le périphérique. (Windows 10 Mobile uniquement)|

## &nbsp;&nbsp;&nbsp;Chiffrement

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|
|**Exiger le chiffrement sur appareil mobile**|Activer le chiffrement sur les appareils mobiles.<br>(Windows 10 Mobile uniquement)|

## &nbsp;&nbsp;&nbsp;Système

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|
|**Permettre la capture d’écran**|Nous allons l’utilisateur capturer l’écran du périphérique en tant qu’image. (Windows 10 Mobile uniquement)|
|**Autoriser unenrollment manuel**|Permet à l’utilisateur de supprimer manuellement le compte de l’espace de travail à partir de l’appareil.|
|**Autoriser l’installation de certificat racine manuel**|S’applique à Windows 10 Mobile|
|**Autoriser les diagnostics et l’utilisation des données soient envoyées à Microsoft**|Les valeurs possibles sont :<br><br>**No** - aucune donnée n’est envoyée à Microsoft<br>**Base** - informations limitées est envoyé toto Microsoft<br>**Amélioré** - amélioré les données de diagnostic sont envoyées à Microsoft<br>**Complète (recommandé)** -envoie les mêmes données sous la forme **amélioré**, ainsi que des données supplémentaires sur l’état du périphérique|


## &nbsp;&nbsp;&nbsp;Compte et synchronisation

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|---------------------|
|**Autoriser le compte Microsoft**|Permet à l’utilisateur associer un compte Microsoft avec le périphérique.|
|**Permettre l’ajout de comptes Microsoft non manuellement**|Permet à l’utilisateur Ajouter des comptes de messagerie à l’appareil qui ne sont pas associés à un compte Microsoft.|
|**Permet de synchroniser les paramètres pour les comptes Microsoft**|Autoriser les paramètres de périphérique et application associés à un compte Microsoft pour la synchronisation entre les périphériques.|

## &nbsp;&nbsp;&nbsp;Microsoft Edge

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|
|**Autoriser le navigateur web**|Autoriser l’utilisation d’un navigateur web bord sur l’appareil.<br>(Windows 10 Mobile uniquement)|
|**Autoriser les suggestions de recherche dans la barre d’adresses**|Vous permet de votre moteur de recherche suggérer des sites en cours de frappe les expressions de recherche.|
|**Autoriser l’envoi de trafic intranet dans Internet Explorer**|Permet aux utilisateurs ouvrent des sites Web intranet dans Internet Explorer.<br>(Windows 10 bureau uniquement)|
|**Autoriser ne suivez pas**|Configure le navigateur de bord à envoyer ne suivez pas les en-têtes aux sites Web que les visiteurs.|
|**Activer SmartScreen**|-|
|**Autoriser les scripts actifs**|Permet de scripts, comme Javascript à exécuter dans le navigateur de bord.|
|**Autoriser les fenêtres contextuelles**|S’applique à Windows 10 bureau uniquement|
|**Activer les cookies**|-|
|**Autoriser la recopie incrémentée**|Autoriser les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur.<br>(Windows 10 bureau uniquement)|
|**Autorisez le Gestionnaire de mot de passe**|Activer ou désactiver la fonctionnalité Gestionnaire de mot de passe de bord.|
|**Emplacement du Mode entreprise site liste**|Indique où trouver la liste des sites web qui s’ouvre en mode entreprise. Les utilisateurs ne peuvent pas modifier cette liste.<br>(Windows 10 bureau uniquement)|

## &nbsp;&nbsp;&nbsp;Applications

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|---------------------|
|**Autoriser le magasin d’applications**|S’applique à Windows 10 Mobile uniquement|



## &nbsp;&nbsp;&nbsp;Réseau cellulaire

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|---------------------|
|**Autoriser l’itinérance de données**|Autoriser l’itinérance entre réseaux lorsqu’ils accèdent à des données.|
|**Autoriser le VPN sur réseau cellulaire**|Contrôle si le périphérique peut accéder à des connexions VPN lorsque connecté à un réseau cellulaire.|
|**Autoriser l’itinérance VPN sur réseau cellulaire**|Contrôle si le périphérique peut accéder connexions VPN cas d’itinérance sur un réseau cellulaire.|

## &nbsp;&nbsp;&nbsp;Matériel

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|
|**Autoriser l’appareil photo**|-|
|**Autoriser le stockage amovible**|Indique si les périphériques de stockage externes comme une carte SD peuvent être utilisés avec le périphérique.|
|**Autoriser le Wi-Fi**|S’applique à Windows 10 Mobile uniquement|
|**Autoriser le partage internet**|Permettre l’utilisation de partage sur le périphérique de connexion Internet.|
|**Autoriser la configuration manuelle de Wi-Fi**|Contrôle si l’utilisateur peut configurer leurs propres connexions Wi-Fi, ou qu’ils peuvent utiliser uniquement connexions configurées par un profil de Wi-Fi.<br>(Windows 10 Mobile uniquement)|
|**Autoriser la connexion automatique libérer des points d’accès Wi-Fi**|Vous permet de l’appareil se connecter automatiquement aux points d’accès Wi-Fi gratuits et accepter automatiquement les termes et conditions de la connexion.|
|**Autoriser géolocalisation**|Indique si le périphérique peut utiliser les informations d’emplacement services.|
|**Autoriser NFC**|Permet du périphérique à utiliser ses capacités près champ Communications.|
|**Autoriser Bluetooth**|-|
|**Autoriser le mode identifiable Bluetooth**|Nous allons cet appareil être découvert par d’autres périphériques Bluetooth.|
|**Autoriser Bluetooth publicitaires**|Permet aux périphériques de recevoir des annonces sur Bluetooth.|
|**Permettre une réinitialisation de téléphone**|Contrôles si usine utilisateur peuvent réinitialiser leur appareil.|
|**Autoriser la connexion USB**|Contrôles si appareils peuvent accéder périphériques de stockage externes via une connexion USB.|
|**Autoriser le mode antivol**|Configurer le mode Windows antivol est activé ou désactivé.|

## &nbsp;&nbsp;&nbsp;Fonctionnalités

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|----------------------|---------------------|
|**Autoriser les copier et coller**|S’applique à Windows 10 Mobile uniquement|
|**Autorise l’enregistrement de voix**|S’applique à Windows 10 Mobile uniquement|
|**Autoriser Cortana**|Activer ou désactiver l’assistant voix Cortana.|
|**Autoriser les notifications centre action**|Activer ou désactiver les notifications de centre d’action dans l’écran de verrouillage appareil.<br>(Windows 10 Mobile uniquement)|

## &nbsp;&nbsp;&nbsp;Windows Defender

Tous les paramètres sont pour le bureau Windows 10 uniquement.

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|-|-|
|**Autoriser la surveillance en temps réel**|Permet d’analyse en temps réel pour les logiciels malveillants, les logiciels espions et autres logiciels indésirables.|
|**Autoriser le comportement de surveillance**|Vous permet de Defender vérifier pour certains modèles connus d’activité suspecte sur appareils mobiles.|
|**Activer le système de contrôle de réseau**|Le système d’Inspection réseau (INS) vous aide à protéger les périphériques contre les attaques de réseau à l’aide de signatures de problèmes de sécurité connus de Microsoft Endpoint Protection Center pour détecter et bloquer le trafic malveillant.|
|**Passez en revue tous les téléchargements**|Contrôles si Defender analyse tous les fichiers téléchargés à partir d’Internet.|
|**Autoriser l’analyse de scripts**|Vous permet de Defender analyser les scripts qui sont utilisées dans Internet Explorer.|
|**Contrôler l’activité de fichier et un programme**|Activez ce paramètre pour autoriser Defender contrôler l’activité de fichier et un programme sur les appareils.|
|**Jours pour effectuer le suivi des programmes malveillants résolu**|Permet de Defender continuer effectuer le suivi des programmes malveillants résolu pour le nombre de jours que vous spécifiez afin que vous puissiez manuellement à cocher préalablement affecté appareils. Si vous définissez le nombre de jours à **0**, les logiciels malveillants est conservé dans le dossier de quarantaine et ne sont pas automatiquement supprimé. |
|**Autoriser l’accès de l’interface utilisateur client**|Contrôle si l’interface utilisateur de Windows Defender est masqué aux utilisateurs finaux.<br>Lorsque ce paramètre est modifié, il prend effet la prochaine fois que PC l’utilisateur final est redémarré.|
|**Planifier une analyse rapide quotidienne**|Vous permet de planifier une analyse rapide qui se produit tous les jours à la fois que vous sélectionnez.|
|**Planifier une analyse du système**|Vous permet de planifier une analyse complète ou rapide du système qui se produit régulièrement sur le jour et une fois que vous sélectionnez.|
|**Limiter l’utilisation de l’UC lors d’une analyse**|Vous permet de limiter la quantité d’UC analyses sont autorisés à utiliser (compris entre **1** et **100**)|
|**Analyser les fichiers d’archive**|Permet d’analyser les fichiers archivés tels que des fichiers Zip ou Cab à Defender.|
|**Analyser les messages électroniques**|Permet de Defender analyser les messages entrants sur l’appareil.|
|**Analyser les lecteurs amovibles**|Vous permet de Defender analyser les lecteurs amovibles comme clés USB.|
|**Analyser les lecteurs réseau mappés**|Vous permet de Defender analyser les fichiers sur un lecteur réseau mappé.<br>Si les fichiers sur le disque sont en lecture seule, Defender ne pourront pas supprimer n’importe quel programme malveillant figurant dans les.|
|**Analyser les fichiers ouverts à partir des dossiers partagés du réseau**|Defender vous permet d’analyser les fichiers sur les lecteurs réseau partagé (par exemple, ceux accessible à partir d’un chemin UNC.<br>Si les fichiers sur le disque sont en lecture seule, Defender ne pourront pas supprimer n’importe quel programme malveillant figurant dans les.|
|**Intervalle de mise à jour de signature**|Spécifiez l’intervalle à laquelle Defender vérifie pour les nouveaux fichiers de signature.|
|**Autoriser la protection de cloud**|Autoriser ou bloquer le Service Microsoft Active la Protection de recevoir des informations sur l’activité des programmes malveillants à partir d’appareils que vous gérez. Ces informations sont utilisées pour améliorer le service à l’avenir.|
|**Inviter les utilisateurs pour la présentation des exemples**|Contrôle si fichiers qui peuvent nécessiter plus analyse par Microsoft pour déterminer si elles sont malveillants sont automatiquement envoyées à Microsoft.|
|**Détection des applications potentiellement indésirables**|Ce paramètre peut être utilisé pour protéger des équipements de bureau de Windows inscrits par rapport à l’exécution d’un logiciel classé par Windows Defender comme potentiellement indésirables. Vous pouvez protéger contre ces applications en cours d’exécution, ou utiliser le mode d’audit pour rapport après avoir installé une application potentiellement indésirable.|
|**Fichiers et dossiers à exclure lors d’une analyse ou à l’aide de la protection en temps réel**|Ajouter un ou plusieurs fichiers et dossiers, tels que **C:\Path** ou **%ProgramFiles%\Path\filename.exe** à la liste exclusions. Ces fichiers et dossiers ne pas être inclus dans les analyses en temps réel ou planifiées.|
|**Extensions de fichier à exclure lors d’une analyse ou à l’aide de la protection en temps réel**|Ajouter une ou plusieurs extensions de fichier, tels que **jpg** ou **txt** à la liste exclusions. Tous les fichiers avec les extensions de ne pas être inclus dans les analyses en temps réel ou planifiées.|
|**Processus à exclure lors d’une analyse ou à l’aide de la protection en temps réel**|Ajouter un ou plusieurs processus du type **.exe**, **.com**ou **.scr** à la liste exclusions. Ces processus ne pas être inclus dans les analyses en temps réel ou planifiées.| 


## &nbsp;&nbsp;&nbsp;Mises à jour

|Nom du paramètre|Informations supplémentaires (le cas échéant)|
|----------------|---------------|
|**Autoriser les mises à jour automatiques**|Activez ce paramètre pour autoriser les mises à jour automatiques. Ensuite, configurez un des paramètres suivants pour contrôler le comportement de mise à jour :<br />**Notification de téléchargement**<br />**Installation automatique au moment de maintenance**<br />**Automatique installez et redémarrez au moment de maintenance**<br />**Automatique installez et redémarrez à heure planifiée** **Remarque :** Lorsque cette option est sélectionnée, vous pouvez également configurer les paramètres suivants : **Supprimer notification à l’utilisateur final** et **définir installer jour mises à jour planifiées**.<br>(Windows 10 bureau uniquement)|
|**Autoriser les fonctionnalités en version précommerciale**|Permet à Microsoft de déployer des paramètres de version préliminaire et les fonctionnalités pour appareils Windows 10. Vous pouvez choisir d’autoriser uniquement, les paramètres ou tous les paramètres de version préliminaire et fonctionnalités doit être installé.|

### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


