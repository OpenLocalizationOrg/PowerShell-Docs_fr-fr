---
title: "Rechercher un nom de famille package (PFN) pour un réseau VPN per application | Microsoft Intune"
description: "Rechercher une PFN afin que vous pouvez configurer un réseau privé virtuel par application."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ms.reviewer: tycast
ms.suite: ems
ms.openlocfilehash: 194e6e2b20c90cce5adcc684a4674e972d0cdc1b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Rechercher un nom de famille package (PFN) pour une configuration VPN per application

Il existe deux façons de trouver un PFN afin que vous pouvez configurer un réseau privé virtuel par application.

## Rechercher une PFN pour une application qui est installée sur un ordinateur Windows 10

Si l’application que vous utilisez est déjà installée sur un ordinateur Windows 10, vous pouvez utiliser l’applet de commande [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell pour obtenir la PFN.

La syntaxe de Get-AppxPackage est la suivante :

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
Vous devrez peut-être exécuter PowerShell en tant qu’administrateur pour récupérer le PFN.

Par exemple, pour obtenir des informations sur les applications universels est installé sur votre ordinateur, utilisez `Get-AppxPackage`.

Pour obtenir des informations sur une application lorsque vous connaissez le nom ou une partie du nom, utilisez `Get-AppxPackage *<app_name>`. Notez l’utilisation du caractère générique, qui s’avère particulièrement utile si vous n’êtes pas sûr du nom complet de l’application. Par exemple, pour obtenir les informations de OneNote, utilisez `Get-AppxPackage *OneNote`.


Voici les informations récupérées pour OneNote :

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## Rechercher une PFN si l’application n’est pas installée sur un ordinateur

1.  Accédez à https://www.microsoft.com/en-us/store/apps.
2.  Entrez le nom de l’application dans la barre de recherche. Dans notre exemple, recherchez OneNote.
3.  Cliquez sur le lien à l’application. Notez que l’URL a une série de lettres à la fin. Dans notre exemple, l’URL ressemble à ceci : `https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`.
4.  Dans un autre onglet, collez l’URL suivante, `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`. Remplacer `<app id>` de l’id de l’application que vous avez obtenu à partir de https://www.microsoft.com/en-us/store/apps - cette série de lettres à la fin de l’URL à l’étape 3. Dans notre exemple de OneNote, coller : `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

Microsoft Edge affiche les informations que vous le souhaitez. dans Internet Explorer, cliquez sur **Ouvrir** pour afficher les informations. La valeur PFN est indiquée sur la première ligne. Voici les résultats dans notre exemple :


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
