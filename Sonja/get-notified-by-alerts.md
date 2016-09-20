---
title: "Être informé par alertes | Microsoft Intune"
description: "Découvrez comment alertes rester en contact vous quoi de neuf dans Microsoft Intune."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 396ea714-0433-4bd5-a934-8d0b477f28e4
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: da881ccb5ed26fbec77e1964ff85f7adccb48d53
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Être informé par Microsoft Intune alertes
Alertes de rester en contact avec vos activités dans Microsoft Intune.

Par exemple, les alertes peuvent vous informer sur les événements suivants :

-   Un problème avec le connecteur Exchange qui affecte la gestion des appareils mobiles

-   Programme malveillant a été détecté sur un ordinateur

-   Un conflit entre deux stratégies Intune a été détecté


## Fonctionnement des alertes
Alertes sont générées basées sur des **types d’alerte**, un ensemble de règles préconfigurés intégré à Intune. Par exemple, le type d’alerte, **stockage Cloud a 10 % ou moins d’espace libre**, vous avertit lorsque vous exécutez déconnecter d’espace pour stocker vos applications dans le cloud. Vous pouvez activer ou désactiver des types d’alertes et configurer les propriétés pour chaque type d’alerte. Par exemple, utilisez le type d’alerte ci-dessus, vous pouvez configurer :

-   **État :** Si ce type d’alerte est activé ou désactivé

-   **Gravité :** Comment grave est cette alerte ?


|Gravité|Plus d’informations|
|--------|-------|
    |![Alerte critique](../media/Critical-Alert.jpg)|Indique un problème grave que vous devez examiner dès que possible, par exemple, si les logiciels malveillants a été détectée sur un ordinateur.|
    |![Alerte d’avertissement](../media/Warning-Alert.jpg)|Indique un problème qui n’est pas actuellement graves mais peut devenir graves si vous n’Assistez, par exemple, mises à jour de sécurité sont en attente d’être installé.|
    |![Alerte d’information](../media/Informational-Alert.jpg)|Indique les informations qui n’est pas essentielles à vos activités, par exemple, une nouvelle version du connecteur Exchange sont disponibles.|

Autres types d’alertes peuvent avoir différents éléments que vous pouvez configurer, tel que le pourcentage de périphériques qui doivent être affectées par un problème qu’une alerte est générée.

**Lorsque les critères dans un type d’alerte est remplie, une alerte est générée et affichée dans la console d’administration Intune.**

En outre, vous pouvez configurer Intune pour vous avertir par courrier électronique lorsqu’une alerte est générée.

## Configurer des alertes
Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **administrateur** &gt; **alertes et des Notifications**, puis choisissez une des opérations suivantes :

|Tâche|Description|
|--------|---------------|
|**Types d’alertes**|Choisissez le type d’alerte que vous souhaitez configurer et effectuez l’une des opérations suivantes :<br /><br />Cliquez sur **configurer**. Dans la boîte de dialogue **Configurer Type d’alerte** , configurer les paramètres de votre choix et cliquez sur **OK**.<br /><br />**Activer** ou **désactiver** l’alerte.<br /><br />Développez le nœud **Types d’alerte** , puis sélectionnez une catégorie pour afficher uniquement les types d’alertes dans cette catégorie.|
|**Destinataires**|Cliquez sur **Ajouter** pour ajouter une nouvelle adresse de messagerie qui recevront les notifications de messagerie que vous avez configurées.<br /><br />Vous pouvez également **Modifier** ou **Supprimer des** destinataires existants.<br /><br />Pour recevoir des notifications, vous devez également ajouter cette adresse de messagerie en tant que destinataire sous **Règles de Notification**.|
|**Règles de notification**|Configure des règles qui définissent qui sera envoyé à un message d’alerte. Vous pouvez :<br /><br />**Choisir une règle existante** - sélectionnez une règle, puis **Sélectionner des destinataires**. Vous pouvez ensuite sélectionner tous les destinataires recevront un message électronique lorsqu’une alerte qui répond à cette règle est générée.<br /><br />**Créer une nouvelle règle** - Entrez un nom pour la règle, sélectionnez les catégories d’alerte et la gravité d’alerte qui s’appliquent aux règles, sélectionnez les groupes de périphériques que la règle s’applique à, puis sélectionnez les utilisateurs recevront un message électronique lorsqu’une alerte est générée.<br /><br />Vous pouvez également **Activer**, **désactiver**, **Modifier**ou **Supprimer** une règle existante.|

## Utilisation des alertes
Utilisez les options suivantes pour vous aider à travailler avec les alertes de la console d’administration Intune.

|Option|Description|
|----------|---------------|
|**Afficher les alertes actives**|Choisissez une des :<br /><br />**Afficher un résumé des alertes** - dans l’espace de travail de **tableau de bord** , les erreurs supérieure apparaissent dans le volet alertes. Cliquez sur le volet pour afficher des informations plus détaillées.<br /><br />En outre, vous pouvez afficher un résumé des alertes dans la page **vue d’ensemble** de l’espace de travail **alertes** .<br /><br />**Afficher toutes les alertes** - dans l’espace de travail **alertes** , sélectionnez **Toutes les alertes**.|
|**Avis de vue**|Choisissez une des :<br /><br />Dans l’espace de travail de **tableau de bord** , sélectionnez **notifications**.<br /><br />Dans l’espace de travail **alertes** , sélectionnez **Toutes les alertes** &gt; **notifications**.|
|**Fermer une alerte**|Dans la liste des alertes, sélectionnez l’alerte à fermer, puis **Fermez alerte**.<br /><br />Alertes fermés sont définitivement supprimés après 90 jours.|
|**Réactiver une alerte fermée**|Dans la liste des alertes, définissez les **filtres de** liste déroulante **fermé**.<br /><br />Dans la liste des alertes fermés, sélectionnez l’alerte que vous souhaitez réactiver, puis **Réactiver une alerte**.|
Alertes Intune resteront actifs jusqu'à ce que :

-   Le problème qui a provoqué l’alerte est fixe

-   Vous fermez manuellement l’alerte

-   45 jours se sont écoulés depuis la génération de l’alerte

> [!TIP]
> Si le même message d’alerte est généré par appareils exécutant différents systèmes d’exploitation, vous pouvez voir plusieurs versions de la même alerte dans la liste des alertes.

### Voir aussi
[Surveillance et des rapports avec Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
