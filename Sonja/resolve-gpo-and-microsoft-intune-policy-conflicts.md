---
title: "Résoudre les conflits de stratégie stratégie de groupe et Intune | Microsoft Intune"
description: "Découvrez comment résoudre les conflits entre les stratégies de configuration de stratégie de groupe et Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: bf5198f352e71e818e56a5c757951da2575dea8b
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Résoudre les conflits de stratégie Microsoft Intune et les objets (stratégie de groupe)
Intune utilise des stratégies pour vous aider à gérer les paramètres sur les PC Windows. Par exemple, vous pouvez utiliser une stratégie pour contrôler les paramètres du pare-feu Windows sur les PC. De nombreux paramètres Intune sont similaires aux paramètres que vous pouvez configurer avec stratégie de groupe Windows. Toutefois, il est possible que, dans certains cas, les deux méthodes peuvent entrer en conflit avec chacun une autre.

Lorsque les conflits se produisent, stratégie de groupe au niveau du domaine est prioritaire sur Intune stratégie, à moins que le PC ne peut pas se connecter au domaine. Dans ce cas, Intune stratégie est appliquée à l’ordinateur client.

## Que faire si vous utilisez la stratégie de groupe
Vérifiez que les stratégies que vous appliquez ne sont pas gérés par la stratégie de groupe. Pour permettre d’éviter les conflits, vous pouvez utiliser une ou plusieurs des méthodes suivantes :

-   Déplacez votre PC à une unité d’organisation Active Directory (unité d’organisation) qui n’a pas de paramètres de stratégie de groupe appliqués avant d’installer le client Intune. Vous pouvez également bloquer l’héritage sur les unités d’organisation qui contiennent des PC inscrit dans Intune auquel vous ne souhaitez pas appliquer les paramètres de stratégie de groupe de stratégie de groupe.

-   Utiliser un filtre de groupe de sécurité pour limiter les objets stratégie de groupe uniquement à PC qui ne sont pas gérés par Intune.

-   Désactiver ou supprimer les objets de stratégie de groupe qui sont en conflit avec les stratégies Intune.

Pour plus d’informations sur Active Directory et stratégie de groupe Windows, voir la Documentation de votre serveur de Windows.

## Comment filtrer la stratégie de groupe existant pour éviter les conflits avec la stratégie Intune
Si vous avez identifié stratégie de groupe dont paramètres sont en conflit avec les stratégies Intune, vous pouvez utiliser des filtres de groupes de sécurité pour limiter ces objets uniquement à PC qui ne sont pas gérés par Intune.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Vous pouvez appliquer la stratégie de groupe uniquement aux groupes de sécurité qui sont spécifiées dans la zone **Filtrage de sécurité** de la console de gestion de stratégie de groupe pour un objet de stratégie de groupe sélectionné. Par défaut, la stratégie de groupe s’appliquent aux *Utilisateurs authentifiés*.

-   Dans le composant logiciel enfichable **ordinateurs et utilisateurs Active Directory** , créez un nouveau groupe de sécurité qui contient des ordinateurs et que vous ne souhaitez pas Intune pour gérer les comptes d’utilisateurs. Par exemple, vous pouvez nommer le groupe *Pas dans Microsoft Intune*.

-   Dans la console de gestion de stratégie de groupe, sous l’onglet **délégation** de la stratégie de groupe sélectionné, cliquez sur Nouveau groupe de sécurité pour déléguer des autorisations de **lecture** et **Appliquer la stratégie de groupe** appropriées à des utilisateurs et ordinateurs dans le groupe de sécurité. (Autorisations**Appliquer la stratégie de groupe** sont disponibles dans la boîte de dialogue **Options avancées** .)

-   Ensuite, appliquer le nouveau filtre de groupe de sécurité à un objet de stratégie de groupe sélectionné et supprimez le filtre par défaut **Utilisateurs authentifiés** .

Nouveau groupe de sécurité doit être maintenu en tant que l’inscription dans les modifications de service Intune.

### Voir aussi
[Gérer les PC Windows avec Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
