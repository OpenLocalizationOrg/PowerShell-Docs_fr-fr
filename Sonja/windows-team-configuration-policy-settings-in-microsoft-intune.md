---
title: "Paramètres de stratégie de configuration de l’équipe de Windows | Microsoft Intune"
description: "Utiliser la Intune Microsoft ** Windows 10 équipe configuration générale stratégie ** pour configurer les paramètres pour inscrit appareils Windows 10 équipe tels que le Hub de Microsoft Surface."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: a8a6e72468cfabf316cb15b5926841e5308325d5
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Paramètres de stratégie de configuration de l’équipe de Windows dans Microsoft Intune
Utilisez la **stratégie de configuration générale de l’équipe Windows 10** de Microsoft Intune pour configurer les paramètres pour les appareils Windows 10 équipe inscrits tels que le Hub de Microsoft Surface.

|Nom du paramètre|Plus d’informations|
|----------------|-----------|
|**Autoriser l’écran pour réactiver automatiquement lorsqu’une personne dans la salle**|Permet au périphérique de sortir automatiquement lorsque son capteur détecte une personne dans la salle.|
|**Code confidentiel est nécessaire pour projection sans fil**|Indique si vous devez taper un code confidentiel avant de pouvoir utiliser les fonctionnalités de projection sans fil de l’appareil.|
|**Définir une période de maintenance des mises à jour de l’appareil**|Configure la fenêtre lors de mises à jour peuvent avoir lieu à l’appareil. Vous pouvez configurer l’heure de début de la fenêtre et la durée (de 1 à 5 heures).|
|**Activer des perspectives opérationnelles Azure**|Azure Insights opérationnelles, partie de la collecte de suite, Microsoft Operations Manager stocke et analyse les données du fichier journal à partir d’appareils Windows 10 d’équipe.<br /><br />Pour vous connecter analyse Azure opérationnelles, vous devez spécifier un **ID de l’espace de travail** et une **Touche de l’espace de travail**.|
|**Activer la projection sans fil Miracast**|Activez cette option si vous souhaitez laisser l’appareil Windows 10 équipe utiliser vos périphériques Miracast activé pour project.<br /><br />Si vous activez cette option, **Sélectionnez Miracast** canaux, sélectionnez le canal Miracast utilisé pour le contenu de projet.|
|**Sélectionnez les informations de réunion affichées sur l’écran d’accueil**|Si vous activez cette option, vous pouvez choisir les informations qui seront affichera sur la vignette **réunions** de l’écran **d’accueil** . Vous pouvez :<br /><br />-   **Afficher l’organisateur et l’heure uniquement**<br />-   **Afficher l’organisateur, heure et son objet (objet masqué pour les réunions privées)**|
|**URL de l’image d’arrière-plan Lockscreen**|Activez ce paramètre afficher un arrière-plan personnalisé dans l’écran **d’accueil** des appareils Windows 10 équipe à partir de l’URL que vous spécifiez.<br /><br />L’image doit être au format PNG et l’URL doit commencer par **https://**.|


### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

