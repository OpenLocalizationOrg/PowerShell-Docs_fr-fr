---
title: "Configurations personnalisées les profils VPN | Microsoft Intune"
description: "Configurations personnalisées permet de créer des profils VPN dans Intune."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 6f6a18318070aa9e7d6dfc27a820d9d8f2054069
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configurations personnalisées les profils VPN

## Créer une configuration personnalisée
Vous pouvez utiliser des configurations personnalisées pour créer des profils VPN dans Intune. Pour créer une configuration personnalisée :

   1. Dans la console d’administration Intune, **stratégie** > **Ajouter une stratégie** > *<Expand platform>* > **configuration personnalisée** > **Créer une stratégie**.
   2. Indiquez un nom pour la stratégie.
   3. Pour chaque paramètre URI, cliquez sur **Ajouter**, puis fournissez les informations requises. Voici un exemple :

   ![Boîte de dialogue configuration personnalisée VPN profil](./media/Intune_Add_VPN_URI.png)

   4.  Une fois que vous avez entré toutes les paramètres d’URI, choisissez **Enregistrer la stratégie**, puis déployez ensuite la stratégie.

## Déployer une stratégie de configuration

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis cliquez sur **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** :

    -   **Pour déployer la stratégie** - choisir un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis cliquez sur **Ajouter** &gt; **OK**.

    -   **Pour fermer la boîte de dialogue sans le déployer** - cliquez sur **Annuler**.

Lorsque vous choisissez une stratégie déployée, vous pouvez afficher d’autres informations sur le déploiement dans la partie inférieure de la liste des stratégies.

##Exemple de paramètres d’URI pour une configuration de profil VPN personnalisée
Voici quelques exemples d’entrées pour les valeurs URI créer une configuration personnalisée pour un réseau VPN dans une société fictif appelée Contoso. Pour plus d’informations, telles que le type de données pour chaque entrée, voir [VPNv2 fournisseur](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx).

Native Contoso VPN (IKEv2) : ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

VPN.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

EAP ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns = « http://www.microsoft.com/provisioning/EapHostConfig »&gt;&lt;EapMethod&gt;&lt;tapez xmlns = « http://www.microsoft.com/provisioning/EapCommon »&gt;13&lt;/tapez&gt;&lt;VendorId xmlns = « http://www.microsoft.com/provisioning/EapCommon »&gt;0&lt;/VendorId&gt;&lt;xmlns VendorType = « http://www.microsoft.com/provisioning/EapCommon »&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns = « http://www.microsoft.com/provisioning/EapCommon »&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns = « http://www.microsoft.com/provisioning/EapHostConfig »&gt;&lt;Eap xmlns = « http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1 »&gt;&lt;Type&gt;13 &lt;/Tapez&gt;&lt;EapType xmlns = « http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1 »&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns = « http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2 »&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns = « http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2 »&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** Vrai

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

Vrai **./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** % ProgramFiles% % (x86) \Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** % ProgramFiles% % (x86) \Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Pour des questions sur l’utilisation des ces paramètres ou plus d’informations sur ce qu’elles font, les clients doivent se reporter à la documentation de fournisseur de service de configuration : https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx.

## Paramètres d’URI pour Android par application VPN sur PulseSecure
### URI PERSONNALISÉE POUR LA LISTE PACKAGE
-  Type de données = chaîne
-  OMA URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList
-  Valeur = séparées par des délimiteurs package liste.
   - Délimiteurs : point-virgule ( ;), deux-points ( :)), une virgule (,), barre verticale (|)

Exemples :
- com.Android.chrome
- com.Android.chrome;com.Android.Browser

### URI PERSONNALISÉE EN MODE (FACULTATIF)
- Type de données = chaîne
- OMA URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Notes
> - Utiliser le même *nom* que vous avez affecté au profil personnalisé
> - Valeurs possibles : *GLOBAL*, *liste d’autorisation*, de *liste de blocage*
> - Valeurs par défaut pour *GLOBAL* si aucun Liste_de_packages ne sont fourni (compatibilité descendante avec les profils au niveau du système)
> - *Liste d’autorisation* si un Liste_de_packages sont fourni par défaut


### Voir aussi
(Connexions VPN dans Microsoft Intune) [vpn-connexions-dans-microsoft-intune.md]
