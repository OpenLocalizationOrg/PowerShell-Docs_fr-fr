---
title: Migrer vers Intune | Microsoft Intune
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: b2e4e606327a452a49cd2066a13e030db808836c
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Migrer vers Intune


La migration vers Intune à partir de votre solution de gestion mobilité existantes peut-être suivre la séquence générale des étapes suivantes :

![Étapes de migration pour Intune](./media/migrate-intune-steps.png)

## Informer les utilisateurs

Une fois que vous maîtrisez que le déploiement pilote Intune a atteint vos besoins, communiquer avec d’autres utilisateurs sur la migration de leurs périphériques pour Intune à venir. Messages électroniques, des instructions et des [posters](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT) permettent de définir des attentes et fournir des détails d’inscription sur les utilisateurs étapes reste à accomplir pour conserver la connectivité continue aux ressources de l’entreprise et aux applications. Vérifiez que votre équipe de support est prêt à aider les utilisateurs dans le processus de migration.

## Modifier votre solution de gestion mobilité existant

Selon la façon dont vous souhaitez gérer les stratégies d’accès conditionnelle entre votre solution de gestion existantes entreprise mobilité et Intune, vous devrez peut-être désactiver vos stratégies d’accès conditionnelle existantes. Vous serez désactiver vos stratégies d’accès conditionnelle existantes ou les stratégies d’accès conditionnelle existant pour ne pas inclure les utilisateurs/appareils que vous voulez migrer vers Intune d’étendue.  N’ont pas Intune et votre solution de gestion de mobilité entreprise existant appliquer des stratégies d’accès conditionnelle sur les mêmes utilisateurs/périphériques.

## Activer la stratégie d’accès conditionnelle Intune (facultatif)

Si vous avez décidé d’appliquer immédiatement les stratégies d’accès conditionnelle sans une période de grâce de la migration de périphériques, activer les stratégies d’accès conditionnel dans Intune dans cette étape.  Vérifiez que cette question est bien communiquée avec vos utilisateurs et votre équipe de support technique.  Si des périphériques Intune ne sont pas inscrit et ne sont pas compatibles avec les stratégies Intune, les utilisateurs ne pourront pas accéder aux ressources d’entreprise jusqu'à ce qu’ils s’inscrire à Intune et les périphériques sont compatibles avec les stratégies Intune.

## Appareils unenrolling à partir de votre solution de gestion mobilité existantes

Appareils doivent être unenrolled à partir de votre solution de gestion de mobilité entreprise existantes avant de s’inscrire à Intune. Nous vous recommandons consiste à autoriser les utilisateurs à unenroll leurs appareils eux-mêmes pour la meilleure expérience utilisateur.  Veillez à respecter les conseils unenrollment par le fournisseur de solutions pour vous assurer que vous correctement supprimez les utilisateurs et périphériques de votre plateforme, assurant une interruption minimale de possible à vos utilisateurs finaux.

## Inscription des appareils dans Intune

Utilisateurs programmés pour une migration doivent immédiatement inscrire au programme d’Intune soit regagner ou éviter la perte d’accès aux applications, de messagerie et de ressources de l’entreprise. Si vous avez configuré accès conditionnel et les utilisateurs tentent de vous connecter à la messagerie avant de s’inscrire à Intune, son accès est bloqué et un message électronique d’inscription les utilisateurs. Guides de ce courrier électronique pour inscrire leur appareil dans Intune.  Par ailleurs, les utilisateurs peuvent s’inscrire dans Intune via l’application portail d’entreprise Intune ou en mode natif par le biais du système d’exploitation sur Windows 8.1 et Windows 10 Mobile. Pour obtenir des instructions sur les étapes de l’inscription par plate-forme, reportez-vous à [quoi indiquer à vos utilisateurs finaux sur l’utilisation de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md) .

## Configurer l’accès conditionnelle Intune (facultatif)

Si vous avez autorisé une période de grâce pour l’application access conditionnelle, activer les stratégies d’accès conditionnel dans Intune pour démarrer l’application lors de la période que vous avez communiqué à vos utilisateurs finaux est terminé. Tous les appareils pour répondre aux exigences de la stratégie d’accès conditionnelle Intune devrez immédiatement.

## S’inscrire restant périphériques et des utilisateurs

À présent que vous avez activé l’accès conditionnelle, tous les utilisateurs sont requis pour inscrire au programme d’Intune et répondre à des stratégies de conformité de votre organisation pour accéder aux ressources d’entreprise. Si vous avez migré vos utilisateurs dans une progressive d’inscription (pas toutes à la fois), répétez les étapes précédentes jusqu'à ce que tous les appareils et les utilisateurs sont inscrits et gérés par Intune.

## Retirer la solution enterprise mobilité management précédent

Une fois que vous avez effectué une migration tous vos utilisateurs et appareils pour Intune et que vous ont validées que les migrations au Intune sont réussies, vous pouvez retirer la solution enterprise mobilité management précédente ou annuler l’abonnement à partir du service. Veillez à suivre les instructions du fournisseur de solution pour vous assurer que supprimer les besoins de l’infrastructure inutiles et annuler les licences d’abonnement/correctement.

## Ressources de migration supplémentaires

Avez-vous besoin d’aide supplémentaire avec la migration vers Intune ? Nous fournissons des options des experts pour vous assurer que votre migration sans problème :

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Microsoft Consulting Services](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Support technique et vont Intune](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Forum TechNet Intune de Microsoft](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## Obtenir une copie téléchargeable de ce guide

Pour obtenir une copie téléchargeable de ce guide dans son intégralité, visitez la [Galerie TechNet](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387).
