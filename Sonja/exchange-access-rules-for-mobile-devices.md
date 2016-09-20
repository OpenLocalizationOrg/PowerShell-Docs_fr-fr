---
title: "Échanger des règles d’accès pour les appareils mobiles | Microsoft Intune"
description: "Règles d’accès Exchange ActiveSync pour autoriser ou bloquer les connexions du périphérique avec EAS"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: c40978080967e3fb92aeb905218fd875e61e7efe
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Règles d’accès Exchange pour les appareils mobiles
Règles d’accès Exchange pour les appareils mobiles déterminent le niveau d’accès des appareils Exchange ActiveSync. Ces paramètres affectent tous les appareils mobiles, y compris ceux qui ne sont pas inscrit dans Microsoft Intune. Vous pouvez Commençons par définir une **Règle par défaut**, ce qui s’appliquent à n’importe quel appareil mobile qui ne dispose pas d’une règle personnalisée qui lui est appliquée.

Le tableau suivant contient les niveaux d’accès gérés par Exchange ActiveSync :

|Niveau d’accès|Description|
|----------------|---------------|
|**Autoriser les périphériques pour accéder à Exchange**|Dans l’état *Autoriser l’accès* , les appareils mobiles peuvent synchroniser via Exchange ActiveSync et se connecter au serveur Exchange pour récupérer messagerie et de gérer le calendrier, Contacts, tâches et Notes. Le problème persiste, que l’appareil est conforme à une stratégie de boîte aux lettres Exchange ActiveSync que vous avez configuré dans Exchange, à moins que l’utilisateur ou l’appareil mobile spécifique a été bloqué par l’administrateur Exchange.|
|**Bloquer les périphériques d’accéder à Exchange**|Dans l’état de *Bloquer l’accès* , les appareils mobiles sont bloqués et ne sont pas autorisés à se connecter au serveur Exchange. Périphériques reçoivent une erreur HTTP 403 refusé. L’utilisateur reçoit un message électronique à partir du serveur Exchange indiquant que l’appareil mobile n’a pas pu accéder à leur boîte aux lettres. Ce message ne peut pas être sur le périphérique mobile bloqué. À l’aide de la tâche de **Notification de définir l’utilisateur** , vous pouvez ajouter du texte personnalisé à ce message pour fournir des instructions pour les utilisateurs dont les périphériques sont bloqués. |
|**Mettre en quarantaine les appareils afin que vous pouvez autoriser ou bloquer les plus tard**|Lorsqu’un appareil mobile est mis en quarantaine, l’appareil mobile est autorisé à se connecter au serveur Exchange. Toutefois, il reçoit uniquement un accès limité à des données. L’utilisateur peut ajouter du contenu à leurs propres dossiers Calendrier, Contacts, tâches et Notes, mais le serveur ne permet pas de l’appareil récupérer n’importe quel contenu à partir de la boîte aux lettres de l’utilisateur. L’utilisateur reçoit un message électronique message indiquant que l’appareil mobile est mis en quarantaine. Ce message est envoyé à l’appareil et à la boîte aux lettres de l’utilisateur. À l’aide de la tâche de **Notification de définir l’utilisateur** , vous pouvez ajouter du texte personnalisé à ce message pour fournir des instructions pour les utilisateurs dont les périphériques sont mis en quarantaine.|

Une stratégie d’accès est une combinaison d’une **Règle par défaut** et les **Exceptions de plateforme** qui s’appliquent à tous les appareils mobiles qui sont connectés à Exchange. Le tableau suivant répertorie certaines stratégies d’accès aux exemple.

|Stratégie d’accès|Description|
|-------------------|---------------|
|Liste d’autorisation|Vous pouvez utiliser une *liste d’autorisation* pour accorder l’accès à une liste des périphériques connus et limiter l’accès pour tous les autres appareils. Pour ce faire, vous devez créer des règles personnalisées pour les plateformes d’appareil qui sont autorisés à accéder aux boîtes aux lettres d’un utilisateur. Dès que vous créez cette règle, vous devez définir la règle d’accès par défaut pour bloquer ou mettre en quarantaine tous les autres appareils. Pour ajouter un nouvel appareil à la liste verte, créer une règle personnalisée.|
|Liste de blocs|Vous pouvez utiliser une *liste de blocs* pour accorder l’accès à tous les périphériques par défaut, mais bloquer l’accès d’un ensemble d’appareils que vous ne souhaitez pas accéder à votre organisation. Créer une liste de blocs en créant des règles personnalisées pour plateformes d’appareil bloc que vous ne souhaitez pas synchroniser avec des boîtes aux lettres de l’organisation. Nous vous recommandons de définir la règle par défaut pour autoriser l’accès à tous les périphériques qui ne sont pas explicitement bloqués par les règles existantes. Pour ajouter un nouvel appareil ou un ensemble de périphériques à la liste rouge, créer une règle personnalisée.|
|Mixte verte et de liste|Outre la création de liste verte et de listes, vous pouvez mettre en quarantaine nouveaux appareils mobiles lorsqu’ils sont introduits dans l’organisation pendant que vous évaluez les. Par exemple, si vous avez une liste de blocage pour les appareils mobiles qui ne sont pas autorisés au sein de votre organisation et une liste verte pour les appareils mobiles qui sont autorisés au sein de l’organisation, vous pouvez définir la règle par défaut pour mettre en quarantaine. Tous les autres périphériques sont automatiquement mis en quarantaine. Cela vous permet de découvrir les nouveaux appareils lorsqu’ils sont introduits à l’organisation et décider si vous souhaitez ajouter à l’autoriser ou bloquer listes.|
La procédure suivante explique comment créer une règle personnalisée.

## Créer une règle d’accès par défaut

1.  Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), choisissez **stratégie** &gt; **Exchange ActiveSync**.

2.  Dans la liste des **Règles par défaut** , sélectionnez la règle d’accès que vous souhaitez appliquer à tous les appareils mobiles qui ne sont pas couverts par une règle ou exemption personnelle. Cliquez sur **Enregistrer**.

La procédure suivante explique comment créer une règle personnalisée :

## Créer une règle d’accès personnalisés

1. Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), choisissez **stratégie** &gt; **Exchange ActiveSync**.

2.  Dans **Plateforme Exceptions** de la liste, choisissez **Ajouter une règle**, puis créez une règle personnalisée. Cliquez sur **Enregistrer**.
