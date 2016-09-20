---
title: "Wi-Fi à l’aide de PSK | Microsoft Intune"
description: "Configuration personnalisée permet de créer un profil Wi-Fi avec une clé partagée."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e977c7c7-e204-47a6-b851-7ad7673ceaab
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 35906378f7d489cebbf7b65a5025ad2040c56895
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Créer un profil Wi-Fi avec une clé communiquée
Voici comment utiliser **Configuration personnalisée de Intune** pour créer un profil Wi-Fi avec une clé partagée. Cette rubrique comporte également un exemple montrant comment créer un profil basés sur EAP Wi-Fi.

> [!NOTE]
-   Vous trouverez plus facile de copier le code à partir d’un ordinateur qui se connecte à ce réseau, comme décrit ci-dessous.
- Pour Android, vous avez également la possibilité de l’utilisation de ce [Générateur PSK Android](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) fourni par Johnathon Biersack.
-   Vous pouvez ajouter plusieurs touches et réseaux en ajoutant davantage de paramètres OMA URI.
-  Pour iOS, utiliser le programme de configuration Apple sur un poste de Mac pour configurer le profil. Vous pouvez également utiliser cette [iOS PSK Mobile Config générateur](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/) fourni par Johnathon Biersack.


1.  Pour créer un réseau Wi-Fi profil avec une clé partagée pour Android ou Windows ou un profil basés sur EAP Wi-Fi, lorsque vous créez une stratégie choisissez **Configuration personnalisée** pour cette plate-forme appareil plutôt qu’un profil Wi-Fi.

2.  Fournir un nom et une description.
3.  Ajouter un nouveau paramètre OMA URI :

   un.   Entrez un nom pour ce paramètre de réseau Wi-Fi.

   b.   Entrez une description du paramètre OMA URI ou laissez vide.

   c.   **Type de données**: la valeur « String(XML) »

   d.   **OMA URI**:

    - **Pour Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>paramètres
    - **Pour Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
Veillez à inclure le caractère point au début.

    SSID est le SSID pour lequel vous créez la stratégie. Par exemple,
    `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **Champ de valeur** est l’endroit où vous collez votre code XML. Voici un exemple. Chaque valeur doit être adapté à vos paramètres réseau. Consultez la section commentaires du code pour quelques indications.
4. Cliquez sur **OK**, enregistrer et déployez ensuite la stratégie.

    > [!NOTE]
    > Cette stratégie peut uniquement être déployée aux groupes d’utilisateurs.

La prochaine fois que chaque appareil vérifie, la stratégie est appliquée et un profil Wi-Fi sont créé sur l’appareil. Le périphérique ne pourrez pas connecter automatiquement au réseau.
## Profil de Windows Wi-Fi ou Android

Voici un exemple du code XML pour un profil Android ou Windows Wi-Fi :

> [!IMPORTANT]
> 
> `<protected>false</protected>`doit être définie sur **false**, comme **true** peut entraîner l’appareil va-t-il se passer d’un mot de passe chiffré, puis tentez déchiffrer, ce qui peut entraîner un échec de la connexion.
> 
>  `<hex>53534944</hex>` doit être définie sur la valeur hexadécimale de `<name><SSID of wifi profile></name>`.
>  Appareils Windows 10 peuvent renvoyer une erreur false *0x87D1FDE8 Échec de la mise à jour* , mais seront toujours déployés avec le profil.

    <!--
    <Name of wifi profile> = Name of profile
    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
    <nonBroadcast><true/false></nonBroadcast>
    <Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
    <Type of encryption> = Type of encryption used by the network
    <protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
    <password> = Password to connect to the network
    <hex>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
    -->
    <WLANProfile
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <hex>53534944</hex>
        <name><SSID of wifi profile></name>
        </SSID>
        <nonBroadcast>false</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication><Type of authentication></authentication>
            <encryption><Type of encryption></encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial>MyPassword</keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>

## Profil de Wi-Fi basés sur EAP
Voici un exemple du code XML pour un profil basés sur EAP Wi-Fi :

    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>

## Créer le fichier XML à partir d’une connexion Wi-Fi existante
Vous pouvez également créer un fichier XML à partir d’une connexion Wi-Fi existante :
1. Sur un ordinateur est connecté à ou a récemment connecté au réseau sans fil, ouvrez le dossier suivant : C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}.

    Il est préférable d’utiliser un ordinateur qui n’est pas connecté à plusieurs réseaux sans fil, car vous devez effectuer une recherche dans chaque profil pour trouver le bon.
3.     Recherche dans les fichiers XML pour trouver celui avec le nom correct.
4.     Une fois que vous avez trouvé le fichier XML correct, copiez et collez le code XML dans le champ données de la page de paramètres OMA URI.

## Déploiement de la stratégie

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** :

    -   **Pour déployer la stratégie** - sélectionnez un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis **Ajouter** &gt; **OK**.

    -   **Pour fermer la boîte de dialogue sans le déployer** - cliquez sur **Annuler**.

Lorsque vous sélectionnez une stratégie déployée, vous pouvez afficher plus d’informations sur le déploiement dans la partie inférieure de la liste des stratégies.

### Voir aussi
[Connexions Wi-Fi dans Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
