---
title: "Contrôler Windows Hello pour les paramètres sur les appareils | Microsoft Intune"
description: "Découvrez comment Intune s’intègre à Windows Hello pour les entreprises, une méthode de connexion de remplacement qui utilise un compte Azure Active Directory ou Active Directory pour remplacer un mot de passe, une carte à puce ou une carte à puce virtuelle."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: c2c2774dd85d8ce9c056248f801220e06f17063b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Contrôle Windows Hello pour les paramètres sur les appareils avec Microsoft Intune
Microsoft Intune s’intègre à Windows Hello entreprise (anciennement Microsoft Passport du travail), une méthode de connexion de remplacement qui utilise un compte Azure Active Directory ou Active Directory pour remplacer un mot de passe, une carte à puce ou une carte à puce virtuelle.

Bonjour entreprise vous permet d’utiliser un *mouvement utilisateur* pour vous connecter, au lieu d’un mot de passe. Un mouvement utilisateur peut être un simple code confidentiel, une authentification biométrique tels que Windows Hello ou un appareil externe tel qu’un lecteur d’empreinte.

Intune s’intègre à découvrir pour les entreprises de deux façons :

-   Vous pouvez utiliser une stratégie Intune pour contrôler les mouvements utilisateurs pouvant et ne pouvez pas utiliser pour vous connecter.

-   Vous pouvez stocker les certificats d’authentification dans le Windows Hello de fournisseur de stockage de clés d’entreprise (KSP). Pour plus d’informations, voir [accès aux profils de certificat dans Microsoft Intune ressources sécurisé](secure-resource-access-with-certificate-profiles.md).

## Créer un Windows Hello de stratégie d’entreprise

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **administrateur** &gt; **Gestion des appareils mobiles** &gt; **Windows** &gt; **Windows Hello pour les entreprises** pour ouvrir le Windows Hello entreprise.

    ![Windows Hello entreprise](../media/passport.png)

2.  Choisissez une des paramètres suivants :
    - **Désactiver Windows Hello pour les entreprises sur les appareils inscrits**. Si vous ne voulez pas utiliser Windows Hello pour les entreprises, sélectionnez ce paramètre. Tous les autres paramètres dans l’écran puis sont indisponibles.
    - **Activer Windows Hello pour les entreprises sur les appareils inscrits**. Sélectionnez ce paramètre si vous voulez configurer Windows Hello pour les paramètres.
    - **Non configuré**. Sélectionnez ce paramètre si vous ne voulez pas utiliser Intune au contrôle Windows Hello pour les paramètres. N’importe quel existantes Windows Hello pour les paramètres sur les appareils Windows 10 ne vont pas être modifiée. Tous les autres paramètres dans l’écran ne sont pas disponibles.
3.  Si vous avez sélectionné **Activer Windows Hello pour les entreprises sur les appareils inscrits**, configurer les paramètres requis qui seront appliquées à tous les appareils Windows 10 et Windows 10 Mobile inscrits.
4.  Lorsque vous avez terminé, cliquez sur **Enregistrer**.


## Paramètres pour le Windows Hello de stratégie d’entreprise

- **Utiliser un Module de plateforme sécurisée (plateforme)**. Une puce de module de plateforme sécurisée fournit une couche supplémentaire de sécurité des données.<br>Choisissez une des valeurs suivantes :
    - **Obligatoire** (par défaut). Seuls les périphériques avec une plateforme sécurisée accessible peuvent prévoir Windows Hello pour les entreprises.
    - **Par défaut**. Tout d’abord les périphériques tentent d’utiliser un module de plateforme sécurisée. Si ce n’est pas disponible, ils peuvent utiliser le chiffrement logiciel.
- **Exiger la longueur minimale du code confidentiel**/**nécessitent longueur maximale du code confidentiel**. Configure les périphériques pour utiliser les longueurs de code confidentiel minimales et maximales que vous spécifiez pour vous assurer une connexion sécurisée. La longueur du code confidentiel par défaut est 6 caractères, mais vous pouvez appliquer une longueur minimale de 4 caractères. La longueur maximale du code confidentiel est 127 caractères.
- **Exiger des minuscules dans le code confidentiel**/**requièrent des lettres majuscules dans le code confidentiel**/**exiger des caractères spéciaux dans le code confidentiel**. Vous pouvez appliquer un code confidentiel renforcé en exigeant l’utilisation de majuscules, minuscules et caractères spéciaux dans le code confidentiel. Choisir :
    - **Autorisée**. Les utilisateurs peuvent utiliser le type de caractère dans son code confidentiel, mais il n’est pas obligatoire.
    - **Obligatoire**. Les utilisateurs doivent inclure au moins un des types de caractères dans son code confidentiel. Par exemple, il est courant afin d’exiger au moins une lettre majuscule et un caractère spécial.
    - **Non autorisé** (par défaut). Les utilisateurs ne doivent pas utiliser ces types de caractères dans son code confidentiel. (Cela est également le comportement si le paramètre n’est pas configuré.)<br>Incluent des caractères spéciaux : **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [\] ^ _ & #96 ; {& #124 ;} ~**.
- **Expiration de code confidentiel (jours)**. Il est recommandé de spécifier une période d’expiration pour un code confidentiel, après laquelle les utilisateurs doivent modifier. La valeur par défaut est jours 41.
- **Historique du code confidentiel oublié**. Limite la réutilisation des codes confidentiels précédemment utilisés. Par défaut, les 5 derniers chevilles ne peut pas être réutilisées.
- **Autoriser l’authentification biométrique**. Active l’authentification biométrique, tels que la reconnaissance du visage ou empreinte, au lieu d’un code confidentiel pour Windows Hello pour les entreprises. Les utilisateurs doivent toujours configurer un code confidentiel de travail en cas d’échec de l’authentification biométrique. Choisir :
    - **Oui**. Windows Hello pour les entreprises permet une authentification biométrique.
    - **No**. Windows Hello pour les entreprises empêche l’authentification biométrique (pour tous les types de comptes).
- **Utiliser améliorée anti-l’usurpation d’adresse, lorsqu’elles sont disponibles**. Configure si les fonctionnalités anti-l’usurpation d’identité de Windows Hello sont utilisées sur les périphériques qui prennent en charge (par exemple, détecter une photographie d’une face au lieu d’une face de réelle).<br>Si cela est défini sur **Oui**, Windows vous oblige tous les utilisateurs d’utiliser l’usurpation d’identité anti visage lorsque qui est pris en charge.
- **Connexion utiliser téléphone**. Si cette option est définie sur **Oui**, les utilisateurs peuvent utiliser un passport à distance à utiliser comme un appareil portable companion pour l’authentification de l’ordinateur de bureau. L’ordinateur de bureau doit être jointes Azure Active Directory et l’appareil sont remplis doit être configuré avec un Windows Hello pour ÉPINGLER Business.

## Informations complémentaires
Pour plus d’informations sur Microsoft Passport, consultez [le guide](https://technet.microsoft.com/library/mt589441.aspx) dans la documentation de Windows 10.
