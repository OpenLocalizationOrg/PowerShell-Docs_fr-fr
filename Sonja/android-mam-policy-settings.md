---
title: "Paramètres de la stratégie MAM Android | Microsoft Intune"
description: "Cette rubrique décrit les paramètres de stratégie de gestion de l’application mobile sur les appareils Android."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
ms.openlocfilehash: 652f3aac9bd0925bd8e8718df04c0eb4b5629902
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie de gestion de l’application mobile Android dans Microsoft Intune
Les paramètres de stratégie décrites ci-dessous peuvent être [configuré](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) pour une stratégie MAM sur la carte de **paramètres** dans le portail Azure.
Il existe deux catégories de paramètres de la stratégie, déplacement de données et les paramètres d’accès :

##  Paramètres de transfert de données
Le terme **qu'applications géré une stratégie** est utilisé pour faire référence aux applications qui sont configurés avec les stratégies MAM.
- **Des sauvegardes empêcher Android :** Cliquez sur **Oui** pour désactiver, ou **Aucune** sauvegarde de données de stratégie de l’entreprise géré applications.

  **Valeur par défaut = Yes**
- **Autoriser l’application pour transférer des données vers d’autres applications :** Sélectionnez une des options pour indiquer les applications doit peuvent recevoir des données d’entreprise à partir des applications de stratégie gérée :
  -   **Stratégie gérée applications**: autoriser le transfert pour que les applications qui ont la stratégie MAM
  -   **Toutes les applications**: autoriser le transfert vers n’importe quelle application
  -   **Aucun**: ne pas autoriser le transfert de données pour une application

  **Valeur par défaut = applications gérés par stratégie**
- **Autoriser l’application pour recevoir des données provenant d’autres applications :** Spécifier les applications qui sont autorisées à transférer des données dans les applications de stratégie gérée :
  -   **Stratégie gérée applications**: autoriser les transferts de données uniquement à partir d’autres stratégies gérées applications
  -   **Toutes les applications**: autoriser le transfert de données à partir de n’importe quelle application
  -   **Aucun**: ne pas autoriser le transfert de données à partir de n’importe quelle application

      **Valeur par défaut = toutes les applications**

-   **Empêcher les enregistrer en tant que :** Cliquez sur **Oui** pour désactiver l’utilisation de l’option Enregistrer sous dans n’importe quelle application qui utilise cette stratégie. Sélectionnez **non** si vous voulez autoriser l’utilisation de la zone Enregistrer sous.

  **Valeur par défaut = Yes**
- **Restreindre couper, copier et coller avec d’autres applications :** Indiquez quand couper, copier et coller des doivent être limité. Choisir :
  -   **Bloqués :** N’autorisez pas couper, copier et coller les opérations entre les applications de stratégie gérée.
  -   **Applications gérées stratégie**: autoriser uniquement les commandes Couper, copier et coller les opérations entre les applications de stratégie gérée.
  -   **Stratégie gérées applications avec coller dans**: autorisez Couper ou copier entre les applications de stratégie gérée. Autoriser Couper ou des données copiées à partir de n’importe quelle application pour être collé dans cette application.
  -   **N’importe quelle application**: aucune restriction pour couper, copier et coller les opérations entre les applications.

    **Valeur par défaut = stratégie applications gérées avec coller dans**
-   **Restreindre le contenu web à afficher dans le navigateur gérées :** Lorsque ce paramètre est activé, tous les liens dans l’application seront ouvre dans le navigateur gérées.

  Pour les périphériques qui ne sont pas inscrit dans Intune, des liens web dans les applications géré par une stratégie ne seront ouvre dans l’application de navigateur gérés à l’aide de la stratégie de gestion de l’application mobile.

  Si vous utilisez Intune pour gérer vos périphériques, voir [Gérer les accès à internet à l’aide de stratégies de navigateur gérées avec Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

    **Valeur par défaut = Yes**
- **Chiffrer les données d’application :** Cliquez sur **Oui** pour activer le chiffrement. Lorsque ce paramètre est activé, pour les applications qui sont associées à une stratégie de gestion de l’application mobile, le chiffrement est fourni par Microsoft. Données sont chiffrées synchrone au cours des opérations d’e/s de fichier. Contenu sur le stockage de l’appareil est toujours être chiffré.
  >[!NOTE]
  >La méthode de chiffrement n’est pas certifié FIPS140-2

  **Valeur par défaut = Yes**

- **Synchronisation des contacts désactiver :** Cliquez sur **Oui** pour empêcher les informations de contact de se synchroniser avec l’application de livre adresse native sur l’appareil. Si vous choisissez **non**, l’application enregistre les informations de contact à l’application de livre adresse native sur l’appareil.<br/>Lorsque vous effectuez une réinitialisation sélective et supprimer des données d’entreprise, les contacts synchronisés directement à partir de l’application avec le carnet d’adresses natif sont supprimés. Tous les contacts synchronisés du carnet d’adresses native avec une autre source externe ne peut pas être nettoyés. Actuellement cela s’applique uniquement à l’application **Microsoft Outlook** .

  **Valeur par défaut = Yes**

##  Paramètres de stratégie d’accès Android
Le terme **qu'applications géré une stratégie** est utilisé pour faire référence aux applications qui sont configurés avec les stratégies MAM

- **Exiger le code secret pour l’accès :** Cliquez sur **Oui** pour exiger un code confidentiel pour utiliser les applications de stratégie gérée. L’utilisateur est invité à configuré ces paramètres pour la première fois qu’ils exécutent l’application dans un contexte de travail.

 **Valeur par défaut = Yes**

 -  **Autoriser simple code confidentiel :** Spécifiez si vous voulez autoriser les utilisateurs à utiliser des séquences de code confidentiel simples tel que 1234 ou 1111. **Valeur par défaut = Yes**.
 - **Longueur du code confidentiel :** Spécifier le nombre minimal de chiffres dans un code confidentiel. **Valeur par défaut = 4**
 - **Nombre de tentatives avant de réinitialisation du code PIN :** Spécifier le nombre de tentatives de saisie du code confidentiel pouvant être effectuées avant que l’utilisateur doit réinitialiser le code confidentiel. **Il n’existe aucune valeur par défaut pour ce paramètre.**
- **Nécessitent des informations d’identification d’entreprise pour accéder à :** Cliquez sur **Oui** pour exiger des informations d’identification d’entreprise au lieu d’un code confidentiel pour l’accès de l’application.  Si vous choisissez **Oui**, ce paramètre remplace la configuration requise pour le code confidentiel ou tactile identifiant.  L’utilisateur sera invité à fournir leurs informations d’identification d’entreprise.

  **Valeur par défaut = non**
- **Bloc gérées applications de s’exécuter sur des appareils racine ou jailbroken :** Cliquez sur **Oui** pour bloquer les applications de s’exécuter sur des appareils racine ou jailbroken. L’utilisateur continue à être en mesure d’utiliser les applications pour les tâches personnelles, mais devra utiliser un autre appareil pour le travail.

  **Valeur par défaut = Yes**
- **Revérifier les conditions d’accès (minutes)**-   **délai d’expiration :** temps (en minutes) avant les conditions d’accès pour l’application sont revérifiées.
  -   **Période en mode hors connexion :** Si le périphérique est en mode hors connexion, spécifier la durée (en minutes) avant les conditions d’accès pour l’application sont revérifiée.

    **Valeurs par défaut = délai d’expiration de 30 minutes et 720 minutes période en mode hors connexion**

-   **En mode hors connexion intervalle avant que les données de l’application sont sélective (jours) :** Vous pouvez choisir les données d’entreprise à distance si un appareil n’a pas été en mode hors connexion pour une période donnée.  Spécifier le nombre de jours pendant lesquels qu'un périphérique peut être en mode hors connexion avant que les données d’entreprise sont supprimées de l’appareil. **Conseil :** Entrer une valeur de 0 de désactiver ce paramètre.

  **Valeur par défaut = 90 jours**
- **Bloquer capture d’écran et Assistant Android (Android shamallow 6 ou version ultérieure) :** Cliquez sur **Oui** pour bloquer la capture d’écran et **Android Assistant** fonctionnalités du périphérique lors de l’utilisation de cette application.
