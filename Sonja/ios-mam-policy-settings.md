---
title: "paramètres de stratégie iOS MAM | Microsoft Intune"
description: "Cette rubrique décrit les paramètres de stratégie de gestion de l’application mobile pour les appareils iOS."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
ms.openlocfilehash: ba258bfb3140ffc79aa38ef2f46497346cdc6bfa
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
#  paramètres de stratégie de gestion de l’application mobile iOS
Les paramètres de stratégie décrites ci-dessous peuvent être [configuré](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) pour une stratégie MAM sur la carte de **paramètres** dans le portail Azure.

Il existe deux catégories de paramètres de la stratégie, déplacement de données et les paramètres d’accès :

##  Paramètres de transfert de données
Le terme **qu'applications géré une stratégie** est utilisé pour faire référence aux applications qui sont configurés avec les stratégies MAM.

- **Empêcher les sauvegardes iTunes et iCloud :** Cliquez sur **Oui** pour désactiver, ou **Aucune** sauvegarde de données de la stratégie de l’entreprise géré applications.

  **Valeur par défaut = Yes**

- **Autoriser l’application pour transférer des données vers d’autres applications :**   Choisissez une des options pour indiquer les applications doit peuvent recevoir des données à partir des applications de stratégie gérée :
  - **Stratégie gérée applications**: autoriser le transfert pour que les applications qui ont la stratégie MAM.
  - **Toutes les applications**: autoriser le transfert vers n’importe quelle application
  - **Aucun**: ne pas autoriser le transfert de données à n’importe quelle application, y compris les autres applications gérés par stratégie.

  En outre, si vous définissez cette option **Stratégie gérées applications** ou **Aucun**, la fonction iOS 9 qui permet la recherche Spotlight pour rechercher des données dans les applications est bloquée.

  **Ce paramètre ne contrôle pas l’utilisation de la fonction Ouvrir dans sur les appareils mobiles. Pour gérer les ouvrir dans, voir [ici](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)**.

  **Valeur par défaut = applications gérés par stratégie**

- **Autoriser l’application pour recevoir des données provenant d’autres applications :**  Spécifier les applications qui sont autorisées à transférer des données dans les applications de stratégie gérée :
  -  **Stratégie gérée applications**: autoriser les transferts de données uniquement à partir d’autres stratégies gérées applications.
  -  **Toutes les applications**: autoriser le transfert de données à partir de n’importe quelle application
  -  **Aucun**: ne pas autoriser le transfert de données à partir de n’importe quelle application.

  **Valeur par défaut = toutes les applications**

- **Empêcher les enregistrer en tant que :** Cliquez sur **Oui** pour désactiver l’utilisation de l’option Enregistrer sous dans n’importe quelle application qui utilise cette stratégie. Sélectionnez **non** si vous voulez autoriser l’utilisation de la zone Enregistrer sous.

  **Valeur par défaut = Yes**

- **Restreindre couper, copier et coller avec d’autres applications :** Indiquez quand couper, copier et coller des doivent être limité. Choisir :
  -   **Bloqués :** N’autorisez pas couper, copier et coller les opérations entre les applications de stratégie gérée.
  -   **Applications gérées stratégie**: autoriser uniquement les commandes Couper, copier et coller les opérations entre les applications de stratégie gérée.
  -   **Stratégie gérées applications avec coller dans**: autoriser Couper ou copier entre les applications de stratégie gérée. Autoriser Couper ou des données copiées à partir de n’importe quelle application pour être collé dans cette application.
  - **N’importe quelle application**: aucune restriction pour couper, copier et coller les opérations entre les applications.

  **Valeur par défaut = stratégie applications gérées avec coller dans**

- **Restreindre le contenu web à afficher dans le navigateur gérées :** Lorsque ce paramètre est activé, tous les liens dans l’application seront ouvre dans le navigateur gérées.

  Pour les périphériques qui ne sont pas inscrit dans Intune, les liens web dans les applications géré par une stratégie peuvent uniquement ouvrir dans l’application de navigateur gérés à l’aide de la stratégie de gestion de l’application mobile.

  Si vous utilisez Intune pour gérer vos périphériques, voir [Gérer les accès à internet à l’aide de stratégies de navigateur gérées avec Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

    **Valeur par défaut = Yes**

- **Chiffrer les données d’application :** Pour les applications qui sont associées à un [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] stratégie de gestion de l’application mobile, données est chiffré inactives à l’aide de chiffrement niveau périphérique fourni par le système d’exploitation. Lorsqu’un code confidentiel est nécessaire, les données sont chiffrées par les paramètres de la stratégie de gestion de l’application mobile. Comme indiqué dans la documentation Apple, [les modules utilisés par iOS 7 sont certifié FIPS140 - 2](http://support.apple.com/en-us/HT202739).

  Dans les paramètres de stratégie, vous pouvez spécifier des valeurs de code confidentiel de chiffrement.  Ces valeurs déterminent lorsque les données sont chiffrées. Les options sont :
  - **Lorsque l’appareil est verrouillé :** Toutes les données d’application associées à cette stratégie est chiffré pendant que l’appareil est verrouillé.
  -   **Lorsque l’appareil est verrouillé (à l’exception des fichiers ouverts) :** Toutes les données d’application associées à cette stratégie est chiffré lorsque l’appareil est verrouillé, à l’exception des données dans les fichiers qui sont actuellement ouvrent dans l’application.
  -   **Après appareil redémarrer :** Toutes les données d’application associées à cette stratégie est chiffré au redémarrage de l’appareil, jusqu'à ce que l’appareil est déverrouillé pour la première fois.
  -   **Utiliser les paramètres de l’appareil :** Données de l’application sont chiffrées basé sur les paramètres par défaut sur l’appareil.
  Lorsque vous activez ce paramètre, l’utilisateur final est nécessaire pour configurer et utiliser un code confidentiel pour accéder à leur appareil.  S’il n’existe aucun code confidentiel, les applications ne seront lance pas et que l’utilisateur final devra pour définir un code confidentiel avec un message-« votre société nécessaire que vous devez d’abord activer un code confidentiel pour accéder à cette application du périphérique. »

  **Par défaut la valeur - chiffrement option n’est pas sélectionnée.**
- **Synchronisation des contacts désactiver :**  Cliquez sur **Oui** pour empêcher les informations de contact de se synchroniser avec l’application de livre adresse native sur l’appareil. Si vous choisissez **non**, l’application sera enregistrée les informations de contact à l’application de livre adresse native sur l’appareil.

  Lorsque vous effectuez une réinitialisation sélective et supprimer des données d’entreprise, les contacts synchronisés directement à partir de l’application avec le carnet d’adresses natif sont supprimés. Tous les contacts synchronisés du carnet d’adresses native avec une autre source externe ne peut pas être nettoyés. Actuellement cela s’applique uniquement à l’application **Microsoft Outlook** .

  **Valeur par défaut = Yes**
##  paramètres de stratégie d’accès iOS
Le terme **qu'applications géré une stratégie** est utilisé pour faire référence aux applications qui sont configurés avec les stratégies MAM.
- **Exiger le code secret pour l’accès :**  Cliquez sur **Oui** pour exiger un code confidentiel pour utiliser les applications de stratégie gérée. L’utilisateur est invité à configuré ces paramètres pour la première fois qu’ils exécutent l’application dans un contexte de travail.

  **Valeur par défaut = Yes**
    -  **Autoriser simple code confidentiel :** Spécifiez si vous voulez autoriser les utilisateurs à utiliser des séquences de code confidentiel simples tel que 1234 ou 1111. **Valeur par défaut = Yes**.
    - **Longueur du code confidentiel :** Spécifier le nombre minimal de chiffres dans un code confidentiel. **Valeur par défaut = 4**
    - **Nombre de tentatives avant de réinitialisation du code PIN :** Spécifier le nombre de tentatives de saisie du code confidentiel pouvant être effectuées avant que l’utilisateur doit réinitialiser le code confidentiel.
  **Il n’existe aucune valeur par défaut pour ce paramètre**.

  - **Exiger empreinte au lieu de code confidentiel (iOS 8.0 +) :** Cliquez sur **Oui** pour exiger une identité empreinte au lieu d’un code confidentiel numérotée pour l’accès de l’application.
Sur les appareils iOS, vous pouvez autoriser l’utilisateur s’identifient à l’aide d’empreinte sur les appareils iOS au lieu d’un code confidentiel numéroté. Lorsque l’utilisateur final essaie d’accéder à cette application à l’aide de leur compte professionnel, ils sont invités à fournir son identité empreinte au lieu de taper un code confidentiel.

    **Valeur par défaut = Yes**
- **Nécessitent des informations d’identification d’entreprise pour accéder à :** Cliquez sur **Oui** pour exiger des informations d’identification d’entreprise au lieu d’un code confidentiel pour l’accès de l’application. **Si vous choisissez Oui, ce paramètre remplace la configuration requise pour le code confidentiel ou tactile identifiant.** L’utilisateur sera invité à fournir leurs informations d’identification d’entreprise.

  **Valeur par défaut = non**
- **Bloc gérées applications de s’exécuter sur des appareils racine ou jailbroken :** Cliquez sur **Oui** pour bloquer les applications de s’exécuter sur des appareils racine ou jailbroken. L’utilisateur continue à être en mesure d’utiliser les applications pour les tâches personnelles, mais devra utiliser un autre appareil pour le travail.

  **Valeur par défaut = Yes**
- **Revérifier les conditions d’accès (minutes)**|-   **délai d’expiration :** temps (en minutes) avant les conditions d’accès pour l’application sont revérifiées.
  -   **Période en mode hors connexion :** Si le périphérique est en mode hors connexion, spécifier la durée (en minutes) avant les conditions d’accès pour l’application sont revérifiée.

  **Valeur par défaut = délai d’expiration de 30 minutes et 720 minutes période en mode hors connexion**
  - **En mode hors connexion intervalle avant que les données de l’application sont sélective (jours) :** Vous pouvez choisir effacer les données de la société si un appareil n’a pas été en mode hors connexion pour une période donnée.  Spécifier le nombre de jours pendant lesquels qu'un périphérique peut être en mode hors connexion avant que les données d’entreprise sont supprimées de l’appareil. **Entrer une valeur de 0 sera désactiver ce paramètre**.

  **Valeur par défaut = 90 jours**
