---
title: "Inscription des appareils iOS appartenant à l’entreprise | Microsoft Intune"
description: "Inscription des appareils iOS appartenant à l’entreprise en utilisant le Apple appareil inscription d’un programme (PED) ou la configuration du Apple"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 7fb28509d78159fa9bec8d12a1cab534a039f328
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Inscription des appareils iOS appartenant à l’entreprise dans Microsoft Intune
Microsoft Intune prend en charge l’inscription des appareils iOS appartenant à l’entreprise via le programme d’inscription Apple appareil (PED) ou l’outil de [Configuration du Apple](http://go.microsoft.com/fwlink/?LinkId=518017) s’exécutant sur un ordinateur Mac.

**Prérequises :** Un [certificat de service de Notification Push Apple](set-up-ios-and-mac-management-with-microsoft-intune.md) est requis.

Vous pouvez vous inscrire appareils iOS d’entreprise inscrite de trois façons : à l’aide de la configuration du Apple, DEP ou le portail d’entreprise.

## Utiliser l’outil de configuration Apple

Vous pouvez vous inscrire les appareils iOS en exportant un profil d’inscription d’entreprise et connexion puis ces appareils mobiles à un Mac exécutant Apple le programme de configuration. Configuration du Apple prend en charge deux formes de l’inscription :

- **Assistant de configuration de l’inscription**: réinitialise le périphérique paramètres par défaut et prépare le programme d’installation par utilisateur de l’appareil. Cette méthode nécessite l’administrateur pour vous connecter l’appareil iOS via USB à un ordinateur Mac [Configuration du Apple](http://go.microsoft.com/fwlink/?LinkId=518017) préconfigurer l’inscription en cours d’exécution. Appareils sont remis à leurs utilisateurs, exécutez le processus de l’Assistant de configuration. Ce processus configure le périphérique avec leur travail ou l’école les informations d’identification et termine le processus d’inscription. Pour plus d’informations, voir [appareils iOS inscrire à l’aide de la configuration du Apple et Assistant de configuration](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **L’inscription directe**: crée un fichier compatible avec Apple le programme de configuration à utiliser lors de la préparation de l’appareil. Le périphérique inscrit n’est pas usine par défaut, mais il n’a aucune affiliation utilisateur. Cette méthode nécessite l’administrateur à se connecter l’appareil iOS via USB à un ordinateur Mac [Apple le programme de configuration](http://go.microsoft.com/fwlink/?LinkId=518017) d’inscription de l’appareil. Pour plus d’informations, voir [appareils iOS inscrire à l’aide d’inscription directe Apple le programme de configuration](ios-direct-enrollment-in-microsoft-intune.md).

## Utiliser le programme d’inscription d’un appareil (PED)
DEP déploie un profil d’inscription « sur l’air » sur les appareils achetées par le biais logicielle. Lorsqu’un utilisateur exécute l’Assistant de configuration sur le périphérique, l’appareil est inscrit à Intune.  Appareils inscrits via la fonctionnalité ne peut pas être unenrolled par les utilisateurs. Pour plus d’informations, voir [appareils iOS inscrire DISPOSITIF inscription d’un programme](ios-device-enrollment-program-in-microsoft-intune.md).

## Utiliser le portail d’entreprise sur les appareils inscrits DEP ou inscrit à la configuration du Apple

Appareils qui sont configurés avec affinité utilisateur peuvent installer et exécuter l’application portail d’entreprise pour télécharger des applications et gestion des appareils. Une fois que les utilisateurs reçoivent leurs appareils, il doit exécuter un certain nombre de mesures supplémentaires pour terminer l’installation et installer l’application portail d’entreprise.

Affinité utilisateur est nécessaire pour prendre en charge les éléments suivants :
  - Applications de gestion (MAM) application mobile
  - Conditionnelle accès aux données de messagerie et société
  - Application du portail d’entreprise

**Comment les utilisateurs inscrire appareils iOS appartenant à l’entreprise avec affinité utilisateur**
1. Quand les utilisateurs activez sur leur appareil, ils êtes invités à terminer l’installation. Pendant l’installation, les utilisateurs doivent fournir leurs informations d’identification. Ils doivent utiliser les informations d’identification (c'est-à-dire le nom personnel unique ou UPN) qui sont associées à son abonnement dans Intune.

2. Pendant l’installation, les utilisateurs doivent fournir un ID Apple. Ils doivent fournir un ID Apple pour autoriser le périphérique pour installer le portail d’entreprise. Ils offrent également l’ID dans le menu Paramètres iOS lorsque le programme d’installation est terminée.

3. Après l’installation terminée, l’appareil iOS doit installer l’application portail d’entreprise à partir de l’App Store.

4. L’utilisateur peut désormais se connecter à l’application portail d’entreprise en utilisant le nom UPN qu’il a utilisé lors de la configuration de l’appareil.

5. Après la connexion, l’utilisateur est invité à inscrire leur appareil. La première étape consiste à identifier leur appareil. L’application présente une liste d’iOS appareils qui ont déjà été d’entreprise inscrit et affecté à Intune compte l’utilisateur. Ils doivent choisir le périphérique correspondant.

  Si cet appareil n’est pas déjà entreprise inscrit, ils doivent choisir **nouvel appareil** pour continuer le flux d’inscription standard.

6. Dans l’écran suivant, l’utilisateur doit confirmer le numéro de série du nouvel appareil. L’utilisateur peut cliquer sur le lien **Confirmer le numéro de série** pour lancer l’application de paramètres pour vérifier le numéro de série. L’utilisateur doit entrer puis les quatre derniers caractères du numéro de série dans l’application portail d’entreprise.

  Cette étape vérifie que l’appareil est le périphérique d’entreprise Intune inscrit. Si le numéro de série sur le périphérique ne correspond pas, l’appareil incorrect a été activé. L’utilisateur doit revenir à l’écran précédent et sélectionnez un autre périphérique.

7. Une fois le numéro de série vérifié, l’application portail d’entreprise redirige vers le site Web portail d’entreprise pour finaliser l’inscription. Le site Web invite ensuite l’utilisateur pour revenir à l’application.

8. L’inscription est terminée. L’utilisateur peut désormais utiliser cet appareil avec l’ensemble des fonctionnalités.

### À propos d’entreprise appartenant périphériques sans affinité utilisateur gérés

Appareils qui sont configurés avec aucune affinité utilisateur ne prennent pas en charge le portail d’entreprise et ne doit pas avoir l’application installé. Le portail d’entreprise est destiné aux utilisateurs qui ont des informations d’identification d’entreprise et qui nécessitent un accès aux ressources d’entreprise personnalisés (par exemple, courrier électronique). Appareils inscrit sans affinité utilisateur ne sont pas destinés à avoir un utilisateur dédié à se connecter. Kiosk, point de vente ou utilitaire partagé périphériques sont les scénarios d’utilisation classiques pour les périphériques qui sont inscrits sans affinité utilisateur.

Si attrait d’un utilisateur est requis, assurez-vous que le profil d’inscription de l’appareil a **Affinité utilisateur** sélectionné avant d’inscription de l’appareil. Pour modifier l’état affinité sur un appareil, vous devez supprimer l’appareil et réinscrire il.



### Voir aussi
[Préparer d’inscription des appareils dans Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)
