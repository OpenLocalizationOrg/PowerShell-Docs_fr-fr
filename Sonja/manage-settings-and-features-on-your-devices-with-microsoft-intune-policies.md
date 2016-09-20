---
title: "Gérer les paramètres de périphérique avec les stratégies | Microsoft Intune"
description: "Intune permet de créer et déployer des stratégies qui contrôlent les paramètres et les fonctionnalités sur les appareils inscrits que vous gérez."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 0dc10ea029d078840a584424f7900f340189b960
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft
Microsoft Intune *stratégies* sont des groupes de paramètres qui contrôlent les fonctionnalités des ordinateurs et appareils mobiles. Créer des stratégies à l’aide de modèles qui contiennent les paramètres recommandés ou personnalisés, et vous déployez les groupes périphérique ou utilisateur.

## Types de stratégies

Stratégies Intune se trouvent dans les catégories suivantes. La catégorie que vous utilisez affecte la façon dont vous créez et déployez la stratégie.


- **Stratégies de configuration**: elles sont utilisées pour gérer les paramètres de sécurité et de fonctionnalités sur vos appareils. Utilisez les informations dans cette rubrique pour en savoir plus sur la procédure à suivre pour créer et déployer des stratégies de ces en Explorer les paramètres disponibles.
- **Stratégies de conformité appareil**: ceux-ci définissent les règles et les paramètres qui un appareil doit respecter afin d’être considérées comme des stratégies de respecter les exigences par access conditionnelle. Vous pouvez également utiliser des stratégies de conformité pour surveiller et mettre à jour la conformité des périphériques indépendants accès conditionnel.
Pour plus d’informations, voir [stratégies de conformité appareil dans Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Stratégies d’accès au conditionnelle**: ces politiques vous aident à sécurisation des e-mails et autres services, en fonction de conditions que vous spécifiez.
Pour plus d’informations, voir [restreindre l’accès à la messagerie électronique et services Office 365 avec Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Stratégies d’inscription appareil d’entreprise**: pour plus d’informations sur les stratégies d’inscription d’un appareil d’entreprise, voir [configurer la gestion de Mac avec Microsoft Intune et iOS](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Stratégies d’accès de ressources**: ces politiques travailler ensemble pour aider vos utilisateurs à accéder aux fichiers et des ressources dont ils ont besoin pour travailler avec succès, où qu’ils soient.
Pour plus d’informations, voir [Activer l’accès aux ressources d’entreprise avec Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


Pour une liste complète des stratégies Intune, voir [référence de la stratégie Microsoft Intune](microsoft-intune-policy-reference.md).




## Créer une stratégie de configuration

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **stratégie** &gt; **Stratégies de Configuration** &gt; **Ajouter**.

2.  Sélectionnez la stratégie que vous voulez, choisissez d’utiliser les paramètres recommandés pour la stratégie (le cas échéant ; vous pouvez modifier ces paramètres ultérieurement) ou choisissez de créer une stratégie personnalisée avec vos propres paramètres.

    > [!TIP]
    > Pour choisir la stratégie de droite, voir la [référence de la stratégie Microsoft Intune](microsoft-intune-policy-reference.md).

3.  Lorsque vous êtes prêt, cliquez sur **Créer une stratégie**.

4.  Dans la page **Créer une stratégie** , configurez un nom et une description facultative de la stratégie.

5.  Configurer les paramètres de stratégie requis, puis sélectionnez **Enregistrer la stratégie**.

    Si vous avez besoin d’aide avec les paramètres de stratégie, sélectionnez un type de stratégie dans la liste suivante :

    - [Paramètres pour les appareils iOS](ios-policy-settings-in-microsoft-intune.md)
    - [Paramètres pour les appareils Android](android-policy-settings-in-microsoft-intune.md)
    - [Paramètres pour les appareils Windows 8 et Windows 8.1](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Paramètres pour les appareils Windows Phone 8.1](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Paramètres pour Windows 10 appareils mobiles et de bureau](windows-10-policy-settings-in-microsoft-intune.md)
    - [Paramètres pour les appareils Windows d’équipe](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Paramètres de mise à niveau de Windows edition](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Paramètres pour les appareils de Mac OS X](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Paramètres pour Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Paramètres de la stratégie de termes et conditions](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Paramètres généraux pour les appareils mobiles (hérité)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  Dans la boîte de dialogue de confirmation, cliquez sur **Oui** pour déployer la stratégie maintenant, ou sélectionnez **non** pour créer la stratégie sans le déployer.

Vous pouvez afficher et modifier la nouvelle stratégie en parcourant les sections pour chaque type de stratégie dans l’espace de travail de **stratégie** .

Lorsque vous créez une stratégie qui utilise les paramètres recommandés, le nom de la nouvelle stratégie est une combinaison du nom du modèle, date et heure. Lorsque vous modifiez la stratégie, le nom est mis à jour avec la date et heure de la modification.

Après avoir créé une stratégie, vous souhaiterez généralement déployer à un ou plusieurs groupes d’utilisateurs ou de périphériques.

> [!TIP]
> Vous ne déployer tous les types de stratégie. Par exemple, la stratégie de gestion des (MAM) application mobile n’est pas déployée. Ce type de stratégie à la place est associé à une application, puis déployer.

## Déployer une stratégie de configuration

1.  Dans l’espace de travail **stratégie** , sélectionnez la stratégie que vous voulez déployer, puis **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** :

    -   Pour déployer la stratégie, sélectionnez un ou plusieurs groupes auxquels vous voulez déployer la stratégie, puis sélectionnez **Ajouter** &gt; **OK**.

    -   Pour fermer la boîte de dialogue sans déploiement de la stratégie, cliquez sur **Annuler**.

Lorsque vous sélectionnez une stratégie déployée, vous pouvez afficher d’autres informations relatives au déploiement dans la partie inférieure de la liste des stratégies.

## Gérer les stratégies

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), sélectionnez la **stratégie**et naviguez jusqu'à et sélectionnez la stratégie que vous voulez gérer.

2.  Sélectionnez une des actions suivantes :

- **Modifier**: ouvrez les propriétés de la stratégie sélectionnée afin que vous pouvez apporter des modifications.
- **Supprimer**: supprimer la stratégie sélectionnée.<br>Lorsque vous supprimez une stratégie, celui-ci est supprimé de tous les groupes auxquels elle a été déployée.
- **Gérer le déploiement**: sélectionnez le groupe que vous voulez déployer la stratégie, puis **Ajouter**.


## Forum aux questions sur les stratégies Intune

### Combien de temps faut-il pour les appareils mobiles obtenir une stratégie ou applications après que qu’ils ont été déployés ?
Lorsqu’une stratégie ou une application est déployée, Intune commence immédiatement d’essayer être averti de l’appareil sur lequel il doit vérifier à l’aide du service Intune. Cette action prend généralement moins de cinq minutes.

Si un périphérique n’archiver pour obtenir la stratégie après que la première notification est envoyée, Intune effectue trois autres tentatives.  Si le périphérique est en mode hors connexion (par exemple, il est désactivé ou pas connecté à un réseau), il ne peut pas reçu les notifications. Dans ce cas, le périphérique obtiendrez la stratégie sur sa planifiée au prochain archivage avec le service Intune comme suit :

- iOS et Mac OS x : chaque 6 heures.
- Android : Toutes les 8 heures.
- Windows Phone : Toutes les 8 heures.
- Inscrit les appareils Windows RT : toutes les 24 heures.
- Windows 8.1 et Windows 10 PC inscrite en tant que périphériques : toutes les 8 heures.

Si le périphérique a été inscrite simplement, la fréquence d’archivage est plus fréquente, comme suit :

- iOS et Mac OS x : toutes les 15 minutes pour 6 heures et puis toutes les 6 heures.
- Android : Toutes les trois minutes pendant 15 minutes, puis toutes les 15 minutes pour 2 heures et puis toutes les 8 heures.
- Windows Phone : Toutes les 5 minutes pendant 15 minutes, puis toutes les 15 minutes pour 2 heures et puis toutes les 8 heures.
- PC Windows inscrite en tant que périphériques : chaque 3 minutes avant que 30 minutes et puis toutes les 8 heures.

Les utilisateurs peuvent également ouvrir l’application portail d’entreprise et synchroniser le périphérique pour vérifier immédiatement pour la stratégie à tout moment.

### Quelles actions entraînent Intune à envoyer immédiatement une notification à un appareil ?
Appareils vérifier avec Intune soit lorsqu’ils reçoivent une notification indiquant que leur demande d’archivage ou pendant leur archivage planifiée.  Lorsque vous ciblez un périphérique ou utilisateur spécifiquement avec une action tel qu’une réinitialisation, verrouiller, réinitialisation du code secret, le déploiement des applications, déploiement de profil (Wi-Fi, VPN, messagerie, etc.) ou déploiement de la stratégie, Intune commence immédiatement à essayer être averti de l’appareil qu’il faut vérifier à l’aide du service Intune pour recevoir ces mises à jour.

Autres modifications, telles que les informations de contact dans le portail d’entreprise, de stratégies de révision n’entraînent pas une notification immédiate aux périphériques.

### Si plusieurs stratégies sont déployés à l’utilisateur ou l’appareil, comment puis-je savoir quels paramètres seront appliquent-elles ?
Lorsque deux ou plusieurs stratégies sont déployées sur le même utilisateur ou le périphérique, l’évaluation pour lequel le paramètre est appliqué au niveau du paramètre individuel se produit-il ?

-   Paramètres de stratégie de conformité ont toujours la priorité sur les paramètres de stratégie de configuration.

-   Le paramètre de stratégie de conformité plus restrictif est appliqué si elle est évaluée par rapport à la même paramètre dans une stratégie de conformité différents.

-   Si un paramètre est en conflit avec un paramètre dans une stratégie de configuration différents de stratégie de configuration, ce conflit s’affichera dans la console Intune. Vous devez résoudre manuellement ces conflits.

### Que se passe-t-il lorsque les stratégies de gestion des applications mobiles sont en conflit avec eux ? Quel sera appliquée à l’application ?
Conflit valeurs sont les paramètres plus restrictifs disponibles dans une stratégie MAM, sauf correspondant au numéro de saisie des champs (par exemple, code confidentiel de tentatives avant Rétablir).  Les champs d’entrée numéros seront définis la même comme les valeurs, comme si vous avez créé une stratégie MAM dans la console à l’aide de l’option Paramètres recommandés.

Conflits de se produire lorsque les deux paramètres de stratégie sont identiques.  Par exemple, vous avez configuré deux stratégies MAM qui sont identiques à l’exception du paramètre de copier/coller.  Dans ce scénario, le paramètre de copier/coller est fixé à la valeur la plus restrictive, mais le reste des paramètres est appliqué configuré.

Si une stratégie est déployée à l’application et entre en vigueur, et ensuite une seconde est déployée, la première partie prendra priorité et restez appliqué, tandis que la seconde affiche en conflit. Si elles sont appliquées en même temps, ce qui signifie qu’il n’existe aucune stratégie précédente, puis ils les deux seront en conflit. Les paramètres en conflit seront fixés aux valeurs plus restrictifs.

### Que se passe-t-il quand un conflit stratégies personnalisées iOS ?
Intune ne correspond pas la charge utile de fichiers de Configuration de Apple ou une stratégie personnalisée ouvrir Mobile Alliance Uniform Resource Identifier (URI OMA). Il sert simplement le mécanisme de remise.

Lorsque vous déployez une stratégie personnalisée, vérifiez que la configuration de ces paramètres ne sont pas en conflit avec la conformité, la configuration ou d’autres stratégies personnalisées. Dans le cas d’une stratégie personnalisée avec des conflits de paramètres, l’ordre dans lequel les paramètres sont appliqués est aléatoire.

### Que se passe-t-il lorsqu’une stratégie est supprimée ou n’est plus applicable ?
Lorsque vous supprimez une stratégie, ou que vous supprimez un périphérique d’un groupe auquel une stratégie a été déployée, les paramètres et la stratégie sont été supprimés de l’appareil selon les listes suivantes.

#### Appareils inscrits

- Wi-Fi, VPN, certificat et les profils de messagerie : ces profils sont supprimés de tous les appareils inscrits pris en charge.
- Tous les autres types de stratégie :
    - **Windows et les appareils Android**: paramètres ne sont pas supprimées de l’appareil.
    - **Appareils Windows Phone 8.1**: les paramètres suivants sont supprimés :
        - Demander un mot de passe pour la déverrouiller les appareils mobiles
        - Autoriser les mots de passe simples
        - Longueur minimale
        - Obligatoires type de mot de passe
        - Expiration du mot de passe (jours)
        - N’oubliez pas de l’historique de mot de passe
        - Nombre d’échecs de signe répétées autorisé avant que l’appareil est sélective
        - Minutes d’inactivité avant de mot de passe est nécessaire
        - Tapez votre mot de passe requis – nombre minimal de jeux de caractères
        - Autoriser l’appareil photo
        - Exiger le chiffrement sur appareil mobile
        - Autoriser le stockage amovible
        - Autoriser le navigateur web
        - Autoriser le magasin d’applications
        - Permettre la capture d’écran
        - Autoriser géolocalisation
        - Autoriser le compte Microsoft
        - Autoriser les copier et coller
        - Autoriser le Wi-Fi attache
        - Autoriser la connexion automatique libérer des points d’accès Wi-Fi
        - Autoriser les rapports de zone réactive Wi-Fi
        - Autoriser usine par défaut
        - Autoriser Bluetooth
        - Autoriser NFC
        - Autoriser le Wi-Fi

    - **iOS**: tous les paramètres sont supprimés, à l’exception :
        - Autoriser l’itinérance vocale
        - Autoriser l’itinérance de données
        - Autoriser la synchronisation automatique en cas d’itinérance

#### PC Windows exécutant le logiciel client Intune

- **Paramètres de Protection de point de terminaison**: paramètres sont restaurés dans leurs valeurs recommandées. La seule exception est le paramètre **Joindre de Service de Protection Microsoft Active** , dont la valeur par défaut est **Aucun**. Pour plus d’informations, consultez [l’aide de sécuriser les PC Windows avec Endpoint Protection pour Intune Microsoft](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Paramètres de mises à jour logicielles**: paramètres sont réinitialisés à l’état par défaut pour le système d’exploitation. Pour plus d’informations, voir [Conserver PC Windows à jour avec les mises à jour logicielles dans Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Paramètres du centre de Intune Microsoft**: les informations de contact qui a été configurées par la stratégie sont supprimées des ordinateurs.
- **Paramètres du pare-feu Windows**: paramètres sont réinitialisés par défaut pour le système d’exploitation. Pour plus d’informations, consultez [l’aide de sécuriser les PC Windows avec Endpoint Protection pour Intune Microsoft](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).


### Comment puis-je actualiser les stratégies sur un appareil pour vous assurer qu’ils sont en cours (s’applique aux PC Windows exécutant le logiciel client Intune uniquement) ?

1.  Dans n’importe quel groupe de périphériques, sélectionnez les appareils sur lequel vous voulez actualiser les stratégies, puis **Tâches à distance** &gt; **Stratégies actualiser**.
2.  Cliquez sur **Tâches à distance** dans le coin inférieur droit de la console d’administration Intune pour vérifier l’état des tâches.

### Où puis-je trouver l’aide de la résolution des problèmes de stratégies ?

Consultez [les stratégies de résolution des problèmes dans Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune).
