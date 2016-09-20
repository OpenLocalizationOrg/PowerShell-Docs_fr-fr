---
title: Endpoint Protection pour les PC Windows | Microsoft Intune
description: "Sécurisez vos ordinateurs gérés avec Endpoint Protection, qui offre une protection en temps réel contre les logiciels malveillants."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 8bcc70ba6451f13f80319229b191b6feb2d5664e
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Sécuriser les PC Windows avec la Protection de point de terminaison de l’aide de Microsoft Intune
Microsoft Intune peut vous aider à sécuriser vos ordinateurs gérés avec Endpoint Protection, qui offre une protection en temps réel contre les logiciels malveillants, conserve les programmes malveillants définitions à jour et analyse automatiquement les ordinateurs. Endpoint Protection fournit également des outils qui vous aident à gérer et analyser les attaques de programmes malveillants.

Si vous n’avez pas encore installé le client Intune sur vos ordinateurs, voir [installer le client PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Utilisez les informations dans les sections suivantes pour vous aider à configurer, déployer et surveiller Endpoint Protection.

## Choisir quand utiliser Endpoint Protection
Comme un administrateur informatique, une de vos priorités supérieure est tout en conservant les ordinateurs que vous gérez gratuites des programmes malveillants et des virus. Avant de déployer Intune sur PC Windows de votre organisation, vous devez décider comment protéger vos ordinateurs en sélectionnant l’une des options suivantes et en configurant ses paramètres de stratégie associées :

|Vous souhaitez :|Paramètres de stratégie de Protection de point de terminaison|Plus d’informations|
|--------------|---------------------------------------|--------------------|
|Utilisez Microsoft Intune Endpoint Protection uniquement si aucune application de protection de point de terminaison tiers n’est installée.<br /><br />Vous pouvez utiliser Microsoft Intune Endpoint Protection sur tous les ordinateurs où une application de protection de point de terminaison tiers n’est pas installée.|Installer la Protection du point de terminaison = **Oui**<br /><br />Activer la Protection de point de terminaison = **Oui**<br /><br />Installer Endpoint Protection même si une application de protection de point de terminaison tiers est installée = **No**|Si un tiers endpoint protection des applications, Microsoft Intune Endpoint Protection n’est pas installée et est désinstallée s’il a été installé précédemment.|
|Utilisez Microsoft Intune Endpoint Protection, même si une application de protection de point de terminaison tiers est installée.<br /><br />Avec cette approche, vous exécuterez Microsoft Intune Endpoint Protection et l’application de la protection de point de terminaison tiers simultanément. En raison d’éventuels problèmes de performances, nous ne recommandons cette configuration. |Installer la Protection du point de terminaison = **Oui**<br /><br />Activer la Protection de point de terminaison = **Oui**<br /><br />Installer Endpoint Protection même si une application de protection de point de terminaison tiers est installée = **Oui**|Contexte d’utilisation :<br /><br />-Vous souhaitez basculer à l’aide de Microsoft Intune Endpoint Protection.<br />-Vous déployez un nouveau client qui utilisera Microsoft Intune Endpoint Protection.<br />-Vous mettez à niveau les clients qui utiliseront Microsoft Intune Endpoint Protection.|
|Utiliser Intune sans Microsoft Intune Endpoint Protection. Vous plutôt une application de protection de point de terminaison tiers.|Installer la Protection du point de terminaison = **No**|Si vous n’utilisez pas une application de protection de point de terminaison tiers, cette configuration n’est pas recommandée, car elle peut exposer les ordinateurs de votre organisation pour les programmes malveillants ou autres attaques.<br /><br />Microsoft Intune Endpoint Protection n’est pas installée et il est désinstallée s’il a été installé précédemment.|
Pour basculer entre l’application en cours endpoint protection Microsoft Intune Endpoint Protection, procédez comme suit :

1.  Laisser votre application de protection de point de terminaison actuelle en cours d’exécution pendant que vous déployez le logiciel client Intune à ces ordinateurs.

2.  Vérifiez que Microsoft Intune Endpoint Protection est installée et contribue à sécuriser les ordinateurs clients.

3.  Supprimer le logiciel de protection de point de terminaison tiers par :

    -   À l’aide de la distribution de logiciels Intune pour déployer un outil de suppression de logiciel est fourni par le fabricant de l’application de la protection de point de terminaison tiers. Pour plus d’informations, voir [déployer des applications avec Microsoft Intune](deploy-apps.md).

    -   Suppression de l’application de la protection de point de terminaison tiers manuellement.

> [!NOTE]
> Intune ne sera pas désinstallé automatiquement les applications de protection de point de terminaison tiers.

## Configurer Microsoft Intune Endpoint Protection
Utilisez les étapes suivantes pour vous aider à configurer Endpoint Protection pour Intune Microsoft.

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **stratégie** > **Ajouter une stratégie**.

2.  Développez **Gestion de l’ordinateur**, puis sélectionnez **Paramètres de l’Agent Intune Microsoft**. Sélectionnez **créer et déployer une stratégie personnalisée** pour spécifier une stratégie pour les paramètres de Protection de point de terminaison. Cliquez sur le bouton **Créer une stratégie** .

Vous pouvez utiliser les paramètres recommandés ou personnaliser les paramètres. Si vous avez besoin de plus d’informations sur la façon de créer et déployer des stratégies, consultez la rubrique [tâches de gestion courantes PC Windows avec le client ordinateur Intune Microsoft](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Paramètres de Protection du point de terminaison](./media/pol-sa-pc-endpoint-policy.png)

Vous pouvez afficher la stratégie Endpoint Protection déployée dans la page de **Toutes les stratégies** de l’espace de travail de **stratégie** .

## Spécifier les paramètres de service Endpoint Protection

|Paramètre de stratégie|Plus d’informations|
|------------------|--------------------|
|**Installer la Protection du point de terminaison**|La valeur **Oui** à installer Endpoint Protection sur les ordinateurs gérés. Si une application de protection de point de terminaison tiers est détectée pendant l’installation, Endpoint Protection ne sera pas installée, à moins que le paramètre **Installer Endpoint Protection même si une application de protection de point de terminaison tiers est installée** est défini sur **Oui**. **Remarque :** Intune Endpoint Protection est installée sur les ordinateurs gérés par défaut. Si vous ne voulez pas installer Endpoint Protection de vos ordinateurs gérés, vous devez définir explicitement cette stratégie sur **non**. Si Endpoint Protection a été installée précédemment et que la stratégie est mis à jour sur **non**, le client Endpoint Protection sera désinstallé.<br />Valeur recommandée : **Oui**|
|**Installer Endpoint Protection même si une application de protection de point de terminaison tiers est installée**|La valeur **Oui** à installer Microsoft Intune Endpoint Protection même si une application de protection de point de terminaison tiers est détectée.<br /><br />Valeur recommandée : **Oui**|
|**Activer la Protection de point de terminaison**|La valeur **Oui** à activer Microsoft Intune Endpoint Protection ordinateurs sur lesquels le client Endpoint Protection.<br /><br />Si définie sur **non**, Microsoft Intune Endpoint Protection est installée, l’interface utilisateur du client Endpoint Protection n’est pas affichée aux utilisateurs, et toutes les fonctionnalités de protection n’inactives.<br /><br />Valeur recommandée : **Oui**|
|**Désactiver l’interface utilisateur du Client**|La valeur **Oui** pour masquer l’interface utilisateur du client Microsoft Intune Endpoint Protection des utilisateurs (nécessite un redémarrage de l’ordinateur client soient prises en compte).<br /><br />Valeur recommandée : **Aucun**|
|**Installer Endpoint Protection même si une application de protection de point de terminaison tiers est installée**|La valeur **Oui** pour imposer l’installation de Microsoft Intune Endpoint Protection, même si une application de protection de point de terminaison tiers est détectée.<br /><br />Valeur recommandée : **Aucun**|
|**Créer un point de restauration système avant la mise à jour les logiciels malveillants**|Définie sur **Oui** pour créer un Point de restauration système Windows avant le début de la mise à jour n’importe quel programme malveillant.<br /><br />Valeur recommandée : **Oui**|
|**Effectuer le suivi des programmes malveillants résolu (jours)**|Active la Protection de point de terminaison pour effectuer le suivi des programmes malveillants résolu pendant une durée spécifiée afin que vous pouvez vérifier manuellement les ordinateurs infectés précédemment.<br /><br />Vous pouvez spécifier une valeur comprise entre 0 et 30 jours.<br /><br />Valeur recommandée : **7 jours**|
Si vous avez défini les valeurs de stratégie pour les paramètres **Installer Endpoint Protection** et **Activer Endpoint Protection** **Oui**et la valeur de stratégie pour **Installer Endpoint Protection même si une application de protection de point de terminaison tiers est installée** sur **Aucun**, Microsoft Intune Endpoint Protection détecte qu’une autre application de la protection de point de terminaison est installée. Cela signifie que Endpoint Protection ne sera pas installée, ou sera désinstallée s’il est déjà présent. Toutefois, Microsoft Intune Endpoint Protection signale concernant l’état de l’autre application de la protection du point de terminaison dans Intune.

  Microsoft Security Essentials vous avertit protection en temps réel lors de menaces telles que les virus et les logiciels espions sont l’installation eux-mêmes ou exécuter sur votre PC. Le moment dans ce cas, vous verrez un message dans la zone de notification à la partie droite de la barre des tâches.

### Spécifier les paramètres de protection en temps réel

|Paramètre de stratégie|Plus d’informations|
|------------------|--------------------|
|**Activer la protection en temps réel**|Active la surveillance et l’analyse de tous les fichiers et les applications accessibles. Il bloque également tous les fichiers malveillants et applications avant qu’ils puissent s’exécuter sur des ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Passez en revue tous les téléchargements**|Permet l’analyse de tous les fichiers et les pièces jointes qui sont téléchargés à partir d’Internet pour les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Contrôler l’activité des fichiers et programmes sur les ordinateurs**|Permet l’analyse des fichiers entrants et sortants et les activités de programmes sur les ordinateurs. Avec ce paramètre, Endpoint Protection pouvez contrôler quand les programmes et fichiers commencent à exécuter et vous avertir pour toutes les actions qu’ils effectuent ou actions effectuées sur ceux-ci.<br /><br />Valeur recommandée : **Oui**|
|**Fichiers analysés**|Vous permet de choisir si une seule entrant, sortant uniquement, ou tous les fichiers sont analysés.<br /><br />Valeur recommandée : **surveiller tous les fichiers**|
|**Activer le contrôle du comportement**|Permet à Microsoft Intune Endpoint Protection contrôler certains modèles d’activité suspecte sur des ordinateurs clients.<br /><br />Valeur recommandée : **Oui**|
|**Activer le système de contrôle de réseau**|Permet d’Inspection système NIS (Network) sur des ordinateurs clients. NIS utilise des signatures d'entre connus à partir du [Centre de Protection contre les logiciels malveillants de Microsoft](http://go.microsoft.com/fwlink/?LinkId=234249) pour aider à détecter et bloquer le trafic réseau malveillant.<br /><br />Valeur recommandée : **Oui**|

  ![Paramètres en temps réel pour Endpoint Protection](./media/pol-sa-pc-policy-realtime.png)

### Spécifier les paramètres de planification de balayage

|Paramètre de stratégie|Plus d’informations|
|------------------|--------------------|
|**Planifier une analyse rapide quotidienne**|Permet de planifier une analyse rapide quotidienne des fichiers système importants sur les ordinateurs et fichiers fréquemment utilisés. Cette analyse rapide a un effet minime sur les performances.<br /><br />Valeur recommandée : **Oui**|
|**Exécuter une analyse rapide si vous avez manqué deux analyses consécutives**|Configure Endpoint Protection pour exécuter automatiquement une analyse rapide sur les ordinateurs si ils ont manqué deux analyses rapides consécutives.<br /><br />Valeur recommandée : **Oui**|
|**Planifiez une analyse complète**|Configure une analyse complète de tous les fichiers et ressources sur le disque dur local. Cette analyse peut prendre du temps et peut affecter les performances de l’ordinateur (le volume de temps qu'il faut dépend du nombre des fichiers et des ressources qui sont analysés).<br /><br />Valeur recommandée : **Aucun**|
|**Lancer une analyse complète si vous avez manqué deux analyses complètes consécutives**|Configure Endpoint Protection pour exécuter automatiquement une analyse complète sur les ordinateurs si ils ont manqué deux analyses consécutives.<br /><br />Recommander valeur : non configuré|

### Spécifier les paramètres d’options analyse

|Paramètre de stratégie|Plus d’informations|
|------------------|--------------------|
|**Lancer une analyse complète après l’installation de Endpoint Protection**|La valeur **Oui** à laisser Endpoint Protection exécuter automatiquement une analyse complète une fois qu’il est installé sur des ordinateurs. Cette analyse s’exécute uniquement lorsque les ordinateurs sont inactifs pour réduire l’impact sur la productivité des utilisateurs.<br /><br />Valeur recommandée : **Oui**|
|**Exécuter automatiquement une analyse complète lorsque cela est nécessaire pour un suivi de suppression des logiciels malveillants**|La valeur **Oui** à laisser Endpoint Protection exécuter automatiquement une analyse complète du système sur les ordinateurs après la suppression de programmes malveillants et aider à vérifier que d’autres fichiers n’ont pas été affectées.<br /><br />Valeur recommandée : **Oui**|
|**Démarrer une analyse planifiée uniquement lorsque l’ordinateur est inactif**|La valeur **Oui** pour empêcher les analyses planifiées de lorsque les ordinateurs sont en cours d’utilisation pour éviter toute perte de la productivité des utilisateurs.<br /><br />Valeur recommandée : **Oui**|
|**Recherchez les dernières définitions de logiciels malveillants avant de lancer une analyse**|La valeur **Oui** pour permettre aux Endpoint Protection vérifier automatiquement les dernières définitions de logiciels malveillants avant de démarrer une analyse sur les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Analyser les fichiers d’archive**|La valeur **Oui** pour configurer la Protection de point de terminaison pour rechercher les programmes malveillants dans les fichiers d’archive (telles que les fichiers .zip ou .cab) sur des ordinateurs.<br /><br />Valeur recommandée : **Aucun**|
|**Analyser les messages électroniques**|La valeur **Oui** pour configurer la Protection de point de terminaison pour analyser les messages électroniques entrants lorsqu’ils arrivent sur les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Analyser les fichiers ouverts à partir des dossiers partagés du réseau**|La valeur **Oui** pour configurer la Protection de point de terminaison pour analyser les fichiers ouverts depuis des dossiers partagés sur le réseau. Il s’agit généralement de fichiers qui sont accessibles à l’aide d’un chemin d’accès de Convention d’affectation de noms (UNC). L’activation de cette fonctionnalité peut entraîner des problèmes pour les utilisateurs qui ont accès en lecture seule, car ils ne peuvent pas supprimer les logiciels malveillants.<br /><br />Valeur recommandée : **Aucun**|
|**Analyser les lecteurs réseau mappés**|La valeur **Oui** pour configurer la Protection de point de terminaison pour analyser les fichiers sur les lecteurs réseau mappés. L’activation de cette fonctionnalité peut entraîner des problèmes pour les utilisateurs qui ont accès en lecture seule, car ils ne peuvent pas supprimer les logiciels malveillants.<br /><br />Valeur recommandée : **Aucun**|
|**Analyser les lecteurs amovibles**|La valeur **Oui** pour configurer la Protection de point de terminaison pour rechercher des programmes malveillants et les logiciels indésirables sur les lecteurs amovibles, comme les lecteurs flash USB, lorsque vous exécutez une analyse complète sur les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Limiter l’utilisation de l’UC lors d’une analyse**|Définir le pourcentage maximal d’utilisation de l’UC pouvant être utilisées pendant les analyses planifiées sur les ordinateurs. Vous pouvez définir cette valeur à partir de 1 à 100 pour cent.<br /><br />Valeur recommandée : **50 %**|

### Choisissez Paramètres des actions par défaut

Le paramètre de **Choisir comment Endpoint Protection agit sur les programmes malveillants des niveaux d’alerte suivants** Spécifie l’action par défaut qui Endpoint Protection prend lorsqu’un logiciel malveillant de différents niveaux d’alerte est détecté. Pour chaque niveau d’alerte, vous pouvez supprimer le logiciel malveillant, mettre en quarantaine ou agir recommandé de Microsoft.

Valeur recommandée : **action recommandée**, qui permet de Endpoint Protection recommander action.   

### Décider si les paramètres de fichiers et dossiers exclus

Le paramètre de **fichiers et dossiers à exclure lors d’une analyse ou à l’aide de protection en temps réel** exclut certains fichiers ou dossiers lorsqu’une analyse est exécuter ou lorsque la protection en temps réel est utilisée sur les ordinateurs.

### Décider si les paramètres de processus exclus

Le paramètre de **processus pour exclure lors de l’exécution d’une analyse ou à l’aide de protection en temps réel** vous permet d’exclure des processus spécifiques lorsqu’une analyse est exécuter ou lorsque la protection en temps réel est utilisée sur les ordinateurs. Vous pouvez exclure uniquement les fichiers avec les extensions suivantes : **.exe**, **.com**ou **.scr**.

### Décider si le fichier exclu paramètres types

Le paramètre **extensions de fichier à exclure lors d’une analyse ou à l’aide de la protection en temps réel** vous permet d’exclure les extensions de nom de fichier spécifique lorsqu’une analyse est exécuter ou lorsque la protection en temps réel est utilisée sur les ordinateurs.

### Spécifier les paramètres de Service Microsoft Active Protection
Service de Protection Microsoft Active est une Communauté en ligne qui vous permet de décider comment répondre à des menaces potentielles. La Communauté permet également d’arrêter la diffusion de nouvelles infections par logiciels malveillants. Vous pouvez **Rejoindre de Service de Protection Microsoft Active** en sélectionnant **Oui**, puis en spécifiant le **Niveau d’adhésion**:
  - **Base** - informations de base envoie à Microsoft sur les programmes malveillants détectés. Cela inclut d'où vient le logiciel, les actions que vous appliquez ou que Endpoint Protection applique automatiquement, et s’il faut les mesures ont réussi.
  - **Options avancées** - envoie plus d’informations à Microsoft sur les logiciels malveillants, les logiciels espions et les logiciels potentiellement indésirables. Cela inclut des informations sur l’emplacement du logiciel, les noms de fichiers, comment fonctionne le logiciel, et comment il a affecté votre ordinateur.

Vous pouvez également **réception définitions dynamiques basées sur les rapports de Service Microsoft Active la Protection**.

## Choisir les tâches de gestion pour Endpoint Protection
Les tâches suivantes vous aideront à effectuer diverses tâches de gestion sur les ordinateurs gérés qui s’exécutent Endpoint Protection :
 - Mettre à jour les définitions de programmes malveillants
  - Intune console - à partir de l’espace de travail **groupes** , sélectionnez les ordinateurs sur lesquels vous souhaitez mettre à jour. Choisissez une **tâche à distance** &gt; **mettre à jour les définitions de programme malveillant**.
  - Ordinateur géré - démarrez le logiciel client Endpoint Protection dans la zone de notification Windows. Sélectionnez l’onglet **mise à jour** , puis **mettre à jour**.
 - Exécutez une analyse des programmes malveillants :
  - Intune console - à partir de l’espace de travail **groupes** , sélectionnez les ordinateurs sur lesquels vous souhaitez analyser. Sélectionnez **exécuter un programme malveillant une analyse complète** ou **exécuter une analyse rapide des programmes malveillants**.
  - Ordinateur géré - démarrez le logiciel client Endpoint Protection dans la zone de notification Windows. Sélectionnez **rapide**, **complète**ou **personnalisée**, puis **Analyser maintenant**.

Vous pouvez afficher l’état d’une tâche à distance en cliquant sur le lien **Tâches à distance** dans le coin inférieur droit de la console Intune. La boîte de dialogue **État des tâches à distance** listes de tâches à distance en cours, état des tâches, nom de l’appareil et toutes les erreurs signalées. Il fournit également un lien vers la résolution des problèmes, le cas échéant.

## Protection de point de terminaison de moniteur
Vous surveiller l’état des logiciels malveillants sur vos ordinateurs à l’aide de l’espace de travail de **Protection** de la [console d’administration Microsoft Intune](https://manage.microsoft.com/). Cet espace de travail contient deux pages :
 - **Présentation de la protection** -affiche les problèmes importants en tant que liens que vous pouvez choisir pour plus d’informations. Problèmes qui peuvent être affichés sont les suivants :
  - **Instances de logiciels malveillants qui ont besoin de suivi** , cliquez sur le lien pour afficher la liste des programmes malveillants problèmes, y compris l’action de suivi devant être prises pour résoudre le problème. Vous pouvez explorer davantage cette liste pour voir quels ordinateurs sont affectées.
  - **Ordinateurs avec les logiciels malveillants qui ont besoin de suivi** -cliquez sur le lien pour afficher tous les ordinateurs avec les programmes malveillants non résolues problèmes, ainsi que l’action de suivi devant être prises pour résoudre le problème.
  - **Appareils qui ne sont pas protégées** , cliquez sur le lien pour afficher les ordinateurs qui ne sont pas protégés par un logiciel de protection de point de terminaison, car aucun logiciel est installé, ou une erreur est générée. Sélectionnez un ordinateur pour afficher davantage de détails.
  - **Appareils avec une autre application de la protection de point de terminaison en cours d’exécution** , cliquez sur le lien pour afficher les ordinateurs qui exécutent une application de protection de point de terminaison tiers.
 - **Tous les programmes malveillants** - affiche une liste de tous les actifs des programmes malveillants qui sont trouve sur vos ordinateurs. Vous pouvez explorer cette liste pour afficher tous les ordinateurs qui sont affectés par des programmes malveillants particulières, ou vous pouvez sélectionner l’une des opérations suivantes :
  - **Afficher les propriétés** – ouvre une page avec plus d’informations sur les programmes malveillants sélectionné.
  - **En savoir plus sur ce contre les logiciels malveillants** – ouvre une rubrique dans le Microsoft Malware Protection Center avec plus d’informations sur le logiciel malveillant.

> [!IMPORTANT]
> L’espace de travail de **Protection** n’est pas affiché dans la console d’administration jusqu'à ce que vous avez installé le client et gérez au moins un ordinateur client.

  ![Protection de point de terminaison de moniteur](./media/pol-sa-ep-monitor.png)

### Comment afficher les chemins d’accès de détection récente pour les programmes malveillants sur les ordinateurs
Intune peut afficher les chemins d’accès de jusqu'à 10 des instances plus récemment détectés des programmes malveillants sur un appareil. Le **Chemin d’accès de détection récent** est désactivée par défaut. Pour activer ce mode d’affichage :

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **groupes** > **Tous les périphériques** > **contre les logiciels malveillants**.

2.  Clic droit sur un en-tête de colonne. Une liste des colonnes disponibles s’affiche.

3.  Activez la case à cocher **détection récente** dans la liste. La colonne **Récentes chemins d’accès de détection** apparaît et affiche les 10 les plus récemment analysés instances de logiciels malveillants sur l’appareil.

## Exécuter une analyse des programmes malveillants ou mettre à jour des définitions de programmes malveillants sur un ordinateur
Intune peut exécuter soit une analyse des programmes malveillants rapide ou complet en utilisant Endpoint Protection ou Windows Defender sur un PC géré à distance qui a installé le client Intune.

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), accédez à des **groupes** > **vue d’ensemble** > **Tous les périphériques** > **Tous les ordinateurs**et sélectionnez l’ordinateur que vous souhaitez cibler.

2. Sélectionnez la liste déroulante de **Tâches à distance** , puis la tâche à exécuter sur l’ordinateur distant.




## Besoin d’aide supplémentaire ?
Pour obtenir de l’aide et support, voir [Résoudre les problèmes Endpoint Protection dans Microsoft Intune](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune).

### Voir aussi
[Stratégies pour protéger des PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
