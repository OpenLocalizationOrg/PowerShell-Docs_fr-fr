---
title: "Configuration de votre abonnement avec plan de référence affût | Microsoft Intune"
description: "Les rubriques fournit des détails sur la configuration du plan de référence affût."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: 8e2c71127801afc21d52e08d13dd9099b263e801
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Configurer votre abonnement de protection contre les menaces mobiles affût
Pour préparer votre abonnement pour la par le service SMTP affût, prise en charge affût (enterprisesupport@lookout.com) devez les informations suivantes sur votre Azure Active Directory (AD Azure). 

* ID de client AD Azure
* ID d’objet Azure AD groupe d’accès complet à la console affût le plan de référence
* ID d’objet Azure AD groupe pour le plan de référence affût console l’accès restreint (facultatif)

Utilisez les informations dans la section suivante pour collecter les informations que nécessaires pour donner à l’équipe de support affût.  

## Importer vos contacts existants Azure AD
### Mise en ID de client Azure AD
Connectez-vous au portail de gestion Azure AD : https://manage.windowsazure.com et sélectionnez votre abonnement. 

![capture d’écran de la page Azure AD présentant le nom du client](../media/mtp/aad_tenant_name.png) lorsque vous sélectionnez le nom de votre abonnement, l’URL résultante inclut l’ID de l’abonnement.  Si vous rencontrez des problèmes trouver votre ID de l’abonnement, l' [article de support technique Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) fournit des conseils supplémentaires.   
### Obtenir votre ID de groupe d’annonces Azure
La console de plan de référence affût prend en charge 2 niveaux d’accès :  
* **Accès complet :** Azure AD administrateur peut créer un groupe pour les utilisateurs qui ont un accès complet et vous pouvez également qu’ils peuvent créer un groupe pour les utilisateurs auront accès restreint.  Seuls les utilisateurs à ces groupes seront en mesure de se connecter à la **Console de plan de référence affût**.
* **D’un accès limité :** Aucun l’accès à plusieurs configuration et l’inscription des modules de la console de plan de référence affût ; n’associés accès en lecture seule pour le module de **Stratégie de sécurité** de la console affût le plan de référence.  

Pour plus d’informations sur les autorisations, lisez [cet article](https://personal.support.lookout.com/hc/en-us/articles/114094105653) sur le site Web affût.

Dans la page Propriétés du groupe dans la console de gestion Azure AD, vous pouvez trouver l' **ID de l’objet groupe** .

![capture d’écran de la page de propriétés avec GroupID champ mis en surbrillance](../media/mtp/aad_group_object_id.png)

Une fois que vous avez collectées ces informations, contactez le support technique affût (messagerie : enterprisesupport@lookout.com).

Prise en charge affût sera fonctionnent avec votre contact principal intégrée à votre abonnement et créez votre compte d’entreprise de plan de référence affût, en utilisant les informations que vous avez collectées.


## Configurer votre abonnement avec affût le plan de référence
### Étape 1 : Configurer votre plan de référence
Une fois que la prise en charge affût crée votre compte d’entreprise de plan de référence affût, vous pouvez vous connecter à la Console de plan de référence affût.   Un message électronique à partir d’affût est envoyé au contact principal pour votre société avec un lien vers l’url de connexion : https://aad.lookout.com/les?action=consent

Vous devez utiliser un compte d’utilisateur dotés du rôle d’administrateur Global Azure AD lorsque vous tout d’abord vous connecter à la console affût le plan de référence, étant donné que le plan de référence affût exige cette option pour enregistrer votre client Azure AD.   Les connexions suivantes ne nécessitent pas autoriser l’utilisateur à ce niveau de privilèges Azure AD.  Dans cette première connexion, une page consentement s’affichera. Cliquez sur **Accepter** pour terminer l’enregistrement.

![capture d’écran de la première page de connexion heure de la console de plan de référence affût](../media/mtp/lookout_mtp_initial_login.png) une fois que vous avez accepté et accepté, vous êtes redirigé vers la Console de plan de référence affût. Les connexions suivantes après l’enregistrement initial, peut être effectuée à l’aide de l’URL : https://aad.lookout.com

Si vous rencontrez des problèmes de connexion, voir l' [article de résolution des problèmes](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration) .

Étapes suivantes présentent les tâches doivent être effectués pour terminer le plan de référence affût configurer au sein de la [Console de plan de référence affût](https://aad.lookout.com).

### Étape 2 : Configurer le connecteur Intune

Dans la console affût le plan de référence, accédez au module **système** , sélectionnez l’onglet **connecteurs** et sélectionnez **Intune**.

![capture d’écran de la console de plan de référence affût avec l’onglet connecteurs ouvert et l’option Intune sélectionnée](../media/mtp/lookout_mtp_setup-intune-connector.png)

L’option Paramètres de connexion, configurez la fréquence de pulsation en minutes.  À la fin de cette étape, votre lien Intune est prêt.  

![capture d’écran de l’onglet Paramètres de connexion avec affichant la fréquence de pulsation configuré](../media/mtp/lookout-mtp-connection-settings.png)

### Étape 3 : Configurer les groupes d’inscription
L’option **D’inscription gestion** , définissent un ensemble d’utilisateurs dont les périphériques doivent être inscrit auprès d’affût.   Il est recommandé de commencer avec un petit groupe d’utilisateurs à tester et de vous familiariser avec le fonctionnement de l’intégration.  Une fois que vous êtes satisfait de vos résultats de test, vous pouvez étendre l’inscription aux autres groupes d’utilisateurs.

Pour commencer avec les groupes inscriptions, tout d’abord définir un groupe de sécurité Azure AD qui serait un bonne premier jeu d’utilisateurs à s’inscrire dans le plan de référence affût. Une fois que le groupe créé dans Azure, AD, dans la Console de plan de référence affût, cliquez sur l’option de **Gestion de l’inscription** et ajoutez le groupe de sécurité Azure AD **Noms d’affichage** pour l’inscription.

Lorsqu’un utilisateur est dans un groupe d’inscription, tous leurs appareils mobiles qui sont identifiés et pris en charge dans Azure AD est inscrit et est éligible pour l’activation dans un plan de référence affût.  La première fois qu’ils s’ouvrent l’affût application travail sur leur appareil pris en charge, il est activé dans le plan de référence affût.
![capture d’écran de la page inscription du connecteur Intune](../media/mtp/lookout-mtp-enrollment.png)

Il est conseillé de laisser l’incrément pour vérifier les nouveaux appareils être la valeur par défaut 5 minutes.

>[!IMPORTANT]
> Le nom complet respecte la casse.  Utilisez le **Nom d’affichage** comme le montre le dans la page **Propriétés** du groupe de sécurité dans le portail Azure. Dans l’illustration ci-dessous, notez que la page de **Propriétés** du groupe de sécurité, le nom d’affichage est casse mixte.  Toutefois, le titre s’affiche en minuscules et ne doit pas être utilisé pour entrer dans la console affût le plan de référence.
>![capture d’écran du portail Azure, service Azure Active Directory, page de propriétés](../media/mtp/aad-group-display-name.png)

La version actuelle comporte les limites suivantes :  
* Il n’existe aucune validation pour afficher les noms des groupes.  Vérifiez que vous utilisez la valeur dans le champ **Nom d’affichage** figurant dans Azure portail pour le groupe de sécurité Azure AD.
* Créer des groupes au sein de groupes n’est pas actuellement pris en charge.  Groupes de sécurité Azure AD spécifié doit contenir uniquement des utilisateurs et groupes imbriqués pas.


### Étape 4 : Configurer la synchronisation d’état
L’option **d’État de synchronisation** , indiquez que le type de données doit être envoyé à Intune.  Pour l’instant, vous devez activer l’état de l’appareil et le statut de menace afin que l’intégration Intune affût fonctionner correctement.  Ces dernières sont activées par défaut.
### Étape 5 : Configurer les informations destinataires de messagerie de rapport d’erreur
L’option de **Gestion des erreurs** , entrez l’adresse de messagerie devant recevoir les rapports d’erreurs.

![capture d’écran de la page de gestion d’erreur Intune connecteur](../media/mtp/lookout-mtp-connector-error-notifications.png)

### Étape 6 : Configurer le courrier électronique les notifications
Si vous souhaitez recevoir des alertes par courrier électronique pour les menaces, connectez-vous à la [console de plan de référence affût](https://aad.lookout.com)avec le compte d’utilisateur devant recevoir les notifications.  Accédez à module du **système** , puis sur l’onglet **Préférences** , cliquez sur les notifications de votre choix et leur attribuer sur **activé**. Enregistrez vos modifications.

![capture d’écran de la page de préférences avec le compte d’utilisateur affiché](../media/mtp/lookout-mtp-email-notifications.png) si vous ne souhaitez plus recevoir des notifications par courrier électronique, les notifications de la valeur **désactivé** et enregistrer vos modifications.
### Étape 7 : Configurer la classification des menaces
Plan de référence affût considère menaces mobiles de différents types. Le [plan de référence affût les classifications des menaces](http://personal.support.lookout.com/hc/en-us/articles/114094130693) de bénéficier des niveaux de risque par défaut leur sont associées. Ils peuvent être modifiées à tout moment dans la suite besoins de votre entreprise.

![capture d’écran de la page de stratégie affichant menace et classifications](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Les niveaux de risque de données spécifiée qu'est un aspect important du plan de référence, car l’intégration Intune calcule la conformité appareil en fonction de ces niveaux de risque en cours d’exécution. En d’autres termes, Intune administrateur définit une règle de stratégie afin de déterminer un appareil n’est pas conforme si elle a une menace active avec un minimum de : haute, moyenne ou faible. La stratégie de classification de menace dans le plan de référence lecteurs directement le calcul de conformité appareil dans Intune.

## Inscription quotidienne
Une fois la configuration terminée, plan de référence affût commence à interroger Azure AD pour appareils mobiles qui correspondent aux groupes d’inscription spécifié.  Vous trouverez des informations sur les appareils inscrit sur le module appareils.  L’état initiale de périphériques est affichée comme étant en attente.  L’état de l’appareil changera lorsque l’affût travail application est installé, ouvert et activé sur le périphérique.  Vous trouverez plus d’informations sur comment obtenir l’affût application travail diffusées sur le périphérique dans la rubrique [configurer et déployer affût pour les applications de travail](configure-and-deploy-lookout-for-work-apps.md) .
## Étapes suivantes
[Activer le plan de référence affût connexion Intune](enable-lookout-mtp-connection-in-intune.md)
