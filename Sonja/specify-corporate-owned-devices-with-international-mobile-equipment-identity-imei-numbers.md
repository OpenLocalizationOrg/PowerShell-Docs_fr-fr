---
title: "Spécifier les numéros IMEI | Microsoft Intune"
description: "Microsoft Intune permet aux administrateurs d’importer des numéros IMEI pour les plateformes d’appareil mobile pour aider à identifier les appareils mobiles appartenant à l’entreprise"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 09902b33cc63b991ec3de3b82860fa93d347f472
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Spécifier les périphériques appartenant à l’entreprise avec les numéros d’identité (IMEI) international appareils mobiles
Microsoft Intune permet aux administrateurs d’importer les numéros d’identité (IMEI) international équipement mobile pour les plateformes d’appareil mobile avec un numéros IMEI pour aider à identifier les appareils mobiles appartenant à l’entreprise. Une fois inscrit à Intune, appareils avec numéros IMEI importées peuvent être affichés sous **groupes** > **vue d’ensemble** > **Tous les périphériques**. **Groupe de périphériques** répertorie les périphériques d’affichage avec numéros IMEI importées en tant que **société** dans la colonne de **la propriété** .

1. Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) choisir **les groupes** &gt; **Tous les périphériques** &gt; **Tous les périphériques Pre-enrolled d’entreprise** &gt; **Par IMEI (toutes les plates-formes)**, puis cliquez sur **Ajouter les unités**. Vous pouvez ajouter des périphériques de deux façons :

    -   **Télécharger un fichier CSV contenant les numéros de série** – créer séparées par des virgules (.csv) valeur liste de deux colonnes sans en-tête, limité à 5 000 unités ou 5 Mo par fichier csv.

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Détails de l’appareil #1&gt;|
        |&lt;IMEI #2&gt;|&lt;Détails de l’appareil #2&gt;|
        Ce fichier .csv lorsqu’ils sont affichés dans un éditeur de texte apparaît sous la forme :

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Ajouter manuellement des détails de l’appareil** - Entrez les détails de nombre et appareil IMEI de cinq appareils

   *Détails* sont pour une utilisation hors projet pour vous pouvez d’identifier le numéro IMEI est associé à un appareil. Ces informations ne sont pas envoyées à l’appareil mais seront affichent dans la console Intune.

2.   Cliquez sur **suivant**.
3.  Dans le volet de **Révision appareils** , vous pouvez vérifier les numéros IMEI appareil sont importées. Vous pouvez également décider si vous voulez remplacer les **Détails** de numéros IMEI ré-importés. Vous pouvez décocher la case à cocher **Remplacer** pour conserver les détails en cours. Cliquez sur **Terminer** pour importer les numéros IMEI.
4.  Les numéros IMEI et les descriptions ajoutées sont ajoutées à la liste **Par IMEI (toutes les plates-formes)** .

Lorsque le périphérique associé à ce numéro IMEI inscrit, généralement lorsqu’un utilisateur installe l’application portail d’entreprise et termine le processus d’inscription, le périphérique seront marqués comme entreprise appartenant et la s’affichent comme inscrit dans le groupe **IMEI appareils** .
