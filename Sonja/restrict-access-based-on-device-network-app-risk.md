---
title: "Limiter l’accès à l’aide de la protection contre les menaces mobile | Microsoft Intune"
description: "Limiter l’accès aux ressources d’entreprise en fonction de l’appareil, de réseau et d’application risque."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: f5e05805d363d43e067f7281ccf545823c83ecb3
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès à la ressource entreprise en fonction du périphérique, du réseau et risque d’application
Vous pouvez contrôler l’accès à partir d’appareils mobiles aux ressources d’entreprise, en fonction de l’évaluation des risques effectuée par affût, une solution de protection (plan de référence) menace mobile qui est intégrée à Microsoft Intune. Le risque est basé sur télémétrie le par le service SMTP affût collecte à partir d’appareils pour faiblesses du système d’exploitation (OS), les applications malveillantes installées et profils de réseau. En fonction de l’évaluation des risques vous pouvez configurer des stratégies d’accès conditionnel dans Intune et autoriser ou périphériques de bloc qui ont été déterminées non conforme en raison des menaces détectées sur ces appareils.  C’est actuellement pris en charge uniquement pour les appareils **Android** exécutant **4.1 et versions ultérieures** et inscrit dans Microsoft Intune.  
## Quel problème résolu ?
Sociétés et organisations besoin de protéger des données sensibles à partir de nouvelles menaces qui incluent des menaces physiques, application et celles basées sur le réseau, ainsi que les vulnérabilités du système d’exploitation.

Traditionnellement, sociétés et organisations effectuent une position active de la protection contre les attaques de PC. Mobile est une zone de nouvelle souvent accède s’affiche-t-il. Bien que les plateformes mobiles ont une protection intégrée de système d’exploitation à l’aide de techniques telles qu’isolement d’application et banques d’application consommateur neufs, ces plateformes continuent à subir les attaques sophistiquées. Les appareils mobiles sont plus utilisés par des employés à effectuer le travail et doivent pouvoir accéder aux informations qui peuvent être critiques, les appareils suivants doivent être protégées à partir d’une variété d’attaques sophistiquées.

Intune vous donne la possibilité de contrôler l’accès aux ressources de l’entreprise et fournissent des données en fonction de l’évaluation des risques que les solutions de plan de référence comme affût.

## Comment faire protection mobile Intune et affût protéger les ressources de l’entreprise ?
Application mobile d’affût (affût du travail), en cours d’exécution sur les appareils mobiles, capture le système de fichiers, la pile réseau et télémétrie périphériques et d’applications (le cas échéant) et l’envoyer vers le service en nuage affût menace mobile protection (plan de référence) pour calculer un risque d’agrégation appareil pour menaces mobiles. Vous pouvez également modifier la classification du niveau de risque pour les menaces dans la console de plan de référence pour l’adapter à vos besoins.  
La stratégie de conformité dans Intune propose désormais une nouvelle règle de protection de menace mobile affût basée sur l’évaluation des risques affût le plan de référence. Lorsque cette règle est activée, Microsoft Intune évalue ensuite la conformité appareil avec la stratégie que vous avez activé.

Si le périphérique est déterminé comme non conforme à la stratégie de conformité, l’accès aux ressources telles que Exchange Online et SharePoint Online peuvent bloqué à l’aide de stratégies d’accès conditionnelle. Lorsque l’accès est bloqué, les utilisateurs finaux sont fournis avec une procédure pas à pas pour aider à résoudre le problème et accéder aux ressources de l’entreprise. Cette procédure pas à pas est lancé à l’affût application de travail.

## Exemples de scénarios
Voici quelques scénarios courants :
### Menace à partir des applications malveillantes :
Lorsque des applications malveillantes tels que des programmes malveillants est détecté sur l’appareil, vous pouvez empêcher ces appareils à partir de :
* Connexion à la messagerie d’entreprise avant de résoudre la menace.
* Synchronisation des fichiers d’entreprise à l’aide de l’OneDrive pour l’application de travail.
* Accéder aux applications critiques.

**Accès bloqué lors de la détection des applications malveillantes :**
![diagramme montrant accès conditionnel stratégie bloquant l’accès lors de l’appareil est déterminé comme étant irrégulière en raison d’applications malveillantes sur l’appareil](../media/mtp/malicious-apps-blocked.png)

**APPAREIL déblocage et est en mesure d’accéder aux ressources de l’entreprise lorsque la menace est résolue :**

![diagramme montrant la stratégie d’accès conditionnelle accorder l’accès lorsque l’appareil est déterminé soit conforme après la mise à jour](../media/mtp/malicious-apps-unblocked.png)
### Menace au réseau :
Détecter les menaces à votre réseau tels que les attaques dans milieu et limiter l’accès à des réseaux Wi-Fi en fonction du risque d’appareil.

**Accès au réseau via Wi-Fi bloqué :**
![diagramme montrant conditionnelle accéder bloquant l’accès Wi-Fi en fonction des menaces réseau](../media/mtp/network-wifi-blocked.png)

**Accès accordé sur la mise à jour :**

![diagramme montrant les accès conditionnel autoriser l’accès de mise à jour de la menace](../media/mtp/network-wifi-unblocked.png)
### Menace au réseau (empêchent l’accès à SharePoint Online) :

Détecter les menaces à votre réseau tels que les attaques dans milieu et empêcher la synchronisation des fichiers d’entreprise en fonction du risque d’appareil.

**Accès bloqué SharePoint Online basé sur réseau menace détectée sur l’appareil :**

![Diagramme montrant les accès conditionnel bloquer l’accès des appareils à SharePoint Online en fonction de détection des menaces](../media/mtp/network-spo-blocked.png)


**Accès accordé sur la mise à jour :**

![Diagramme montrant les accès conditionnel autoriser l’accès une fois la menace réseau est résolue](../media/mtp/network-spo-unblocked.png)

## Étapes suivantes
Voici les principales étapes à suivre pour implémenter cette solution :
1.  [Configurer votre abonnement avec protection contre les menaces mobiles affût](set-up-your-subscription-with-lookout-mtp.md)
2.  [Activer le plan de référence affût de connexion dans Intune](enable-lookout-mtp-connection-in-intune.md)
3.  [Configurer et déployer affût d’une application de travail](configure-and-deploy-lookout-for-work-apps.md)
4.  [Configurer la stratégie de conformité](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Résoudre les problèmes d’intégration affût](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)
