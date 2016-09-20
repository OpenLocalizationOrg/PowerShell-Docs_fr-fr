---
title: Configurer la gestion de Windows Phone 8.0 | Microsoft Intune
description: Activer la gestion des appareils mobiles (MDM) pour les appareils Windows Phone 8.0 avec Microsoft Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 61e9b6c3-8795-49b0-8ab2-a9a05ee3ea1f
ms.reviewer: priyar
ms.suite: ems
ms.openlocfilehash: c6aff6de22c01db680b5a7bb2c6f68e8185b4350
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Configurer la gestion des périphériques pour Windows Phone 8.0

Windows Phone 8.0 requiert un certificat Symantec pour installer l’application portail d’entreprise Intune et autoriser la gestion des appareils. Un certificat est également requis pour signer des applications métier. La rubrique suivante s’applique uniquement aux Windows Phone 8.0. Pour gérer Windows Phone 8.1 ou version ultérieure, y compris Windows 10 Mobile, voir [configurer l’inscription de Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md).

> [!IMPORTANT]
> À partir de septembre de 2016, l’application portail d’entreprise pour Windows 8.0 et Windows Phone 8.0 ne sera plus disponible au téléchargement.

-   **Windows Phone 8** - certificat requis
-   **Windows Phone 8.1 et Windows 10 Mobile** nécessitent une uniquement si de certificat :

    -   Vous voulez déployer l’application portail d’entreprise à l’aide Intune

    -   Vous devez déployer applications (UE » côté-chargé ») secteur d’activité


![Diagramme de configuration requise de certificat](../media/wpcertreqs.png)

  > [!IMPORTANT]
  > Le certificat de Symantec permet de gérer certains Windows et Windows Phone appareils mobiles [doit être renouvelé périodiquement](renew-a-symantec-code-signing-certificate.md).

Configuration requise pour la gestion des appareils mobiles Windows Phone dépendre comment vous pouvez gérer les appareils mobiles.  Définition des deux enregistrements CNAME dans l’enregistrement DNS de votre entreprise simplifie d’inscription pour des utilisations. Si vos utilisateurs à télécharger l’application portail d’entreprise à partir du magasin, puis une fois que vous avez configuré les paramètres DNS vous souhaitez de configurer le portail d’entreprise et d’informer les utilisateurs procédure d’inscription.  Pour Windows Phone 8.0 ou Windows Phone 8.1 où vous allez déployer le portail d’entreprise, vous devez un certificat Symantec à signer par code l’application.

## Configurer la configuration requise pour activer la gestion de Windows Phone
1.  **Configurer la Intune** Si vous n’avez pas déjà, préparer pour la gestion des appareils mobiles en [définissant l’autorité de gestion des périphériques mobiles](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) comme **Microsoft Intune** et la configuration MDM.

2.  **Définir un alias DNS pour l’adresse du serveur d’inscription** (facultatif)

    Un DNS alias (type d’enregistrement CNAME) permet aux utilisateurs plus faciles à inscrire leur appareil en remplissant automatiquement le nom du serveur lors de l’inscription.

    1.  Dans la [console d’administration Intune](http://manage.microsoft.com), cliquez sur **Administration** &gt; **Gestion des appareils mobiles** &gt; **Windows Phone**.

    2.  Tapez l’URL du domaine vérifié du site Web de société dans la zone **Spécifiez un nom de domaine vérifié** , puis sur **La détection automatique de Test**.

    3.  Créer des enregistrements de ressource **CNAME** DNS pour le domaine de votre entreprise. Les enregistrements de ressource CNAME doivent contenir les informations suivantes :

        |Nom d’hôte|Pointe vers|DURÉE DE VIE|
        |-------------|-------------|-------|
        |enterpriseenrollment.company_domain.com|enterpriseenrollment s.manage.microsoft.com |1 heure|
        |enterpriseregistration.company_domain.com|enterpriseregistration.Windows.NET|1 heure|
        Par exemple, si le site Web de votre entreprise est contoso.com, vous le feriez créer un enregistrement CNAME dans le système DNS qui redirige EnterpriseEnrollment.contoso.com vers manage.microsoft.com. S’il existe plus d’un domaine vérifié, créez un enregistrement CNAME pour chaque domaine.

        -   `enterpriseenrollment-s.manage.microsoft.com` – Prend en charge une redirection au service Intune avec la reconnaissance domaine de nom de domaine de messagerie

        -   `enterpriseregistration.windows.net` – Association de poste de travail prend en charge des appareils mobiles. Il prend en charge également accès conditionnel pour Windows 8.1

    ![Boîte de dialogue Paramètres de gestion des appareils Windows Phone Mobile](../media/windows-phone-enrollment.png)

3.  **Gestion des certificats pour prendre en charge l’application de signature** [Requis pour Windows Phone 8.0 et Windows Phone 8.1 qui ne sont pas accéder au magasin de Windows Phone et/ou besoin des applications métier].

    Pour prendre en charge l’application portail d’entreprise pour Windows Phone 8.0 et déployer des applications d’entreprise pour Windows Phone 8.1, vous devez obtenir un **Certificat de signature de Code Symantec entreprise Mobile**. Vous ne pouvez pas utiliser un certificat émis par votre propre autorité de certification uniquement le certificat Symantec est approuvé par les appareils Windows Phone. Ce certificat est requis pour :

    -   Signer l’application portail d’entreprise pour le déploiement sur [!INCLUDE[winphone8_client_1](../includes/winphone8_client_1_md.md)] pour la gestion d’inscription et téléphone

    -   Applications professionnelles de la société se fait [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] les déployer vers les téléphones Windows

    Les étapes ci-dessous vous aidera à obtenir les certificats requis et se l’application portail d’entreprise. Vous devrez un compte Centre de développement Windows Phone et, vous devrez acheter un certificat Symantec.

    1.  **Joindre le centre de développement Windows Phone** Rejoignez le [Centre de développement Windows Phone](http://go.microsoft.com/fwlink/?LinkId=268442) à l’aide des informations de compte d’entreprise lors de la connexion pour acheter compte de votre société. Cette demande doit être autorisées par un responsable de la société avant que vous recevez un certificat de signature de code.

    2.  **Obtenir une société Symantec certificat** Acheter un certificat à partir du [site Web de Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) à l’aide de votre Symantec ID. Après avoir acheté le certificat, l’approbateur d’entreprise auxquels vous avez désigné dans votre compte Centre de développement Windows Phone recevront un message électronique demandant une approbation de la demande de certificat. Pour plus d’informations sur la configuration minimale requise du certificat Symantec, reportez-vous à la [Pourquoi Windows Phone nécessite un certificat Symantec ?](https://technet.microsoft.com/en-us/library/dn764959.aspx#BKMK_Symantec) Windows inscription d’un appareil Forum aux questions.

    3.  **Certificats d’importation** Une fois que la demande a été approuvée, vous recevrez un message électronique contenant les instructions pour l’importation des certificats. Suivez les instructions dans le message électronique pour importer les certificats.

    4.  **Vérifier les certificats importés** Pour vérifier que les certificats ont été correctement importés, atteindre le composant logiciel enfichable **certificats** , cliquez sur **certificats**, puis sélectionnez **Rechercher des certificats**. Dans le champ **contient** , entrez « Symantec », puis cliquez sur **Rechercher**. Les certificats que vous avez importé doivent apparaître dans les résultats.

        ![Trouver le certificat Symantec](../media/wit.gif)

    5.  **Exporter un certificat de signature** Après avoir vérifié que les certificats sont présents, vous pouvez exporter le fichier .pfx pour signer le portail d’entreprise. Sélectionnez le certificat Symantec avec **objectif à atteindre** « signature de code. » Cliquez sur le certificat de signature de code et sélectionnez **Exporter**.

        ![Exporter le certificat de signature](../media/wit-walk-cert2.gif)

        Dans l' **Assistant Exportation de certificat**, sélectionnez **Oui, exporter la clé privée** , puis sur **suivant**. Échanger des informations personnelles select **– PKCS #12 (. PFX)** et vérifiez **inclure tous les certificats dans le chemin d’accès de certification si possible**. Exécuter l’Assistant. Pour plus d’informations, voir [comment exporter un certificat avec la clé privée](http://go.microsoft.com/fwlink/?LinkID=203031).

    6.  **Télécharger et se l’application portail d’entreprise**

        Prise en charge pour l’inscription de Windows Phone nécessite l’application portail d’entreprise Windows Phone 8.0 être connectée et téléchargée dans Intune.

        1.  **Télécharger l’application portail d’entreprise** Téléchargez l' [application portail d’entreprise Intune pour Windows Phone](http://go.microsoft.com/fwlink/?LinkId=268440) à partir du centre de téléchargement. L’emplacement d’installation par défaut est `C:\Program Files (x86)\Microsoft Corporation\Windows Intune Company Portal for Windows Phone`.

        2.  **Télécharger le Windows Phone 8.0 SDK** Téléchargez le [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=615570).

        3.  **Authentification de code de l’application portail d’entreprise** Utiliser l’application XAPSignTool téléchargés avec le Kit de développement pour vous connecter le portail d’entreprise avec le fichier .pfx que vous avez créé à partir du certificat Symantec. Pour plus d’informations, voir [comment signer une application d’entreprise à l’aide de XapSignTool](http://go.microsoft.com/fwlink/?LinkID=280195).

    7.  **Télécharger l’application portail d’entreprise à Intune** Télécharger le fichier de l’application portail d’entreprise signé et votre certificat de signature de code pour rendre l’application disponible pour les utilisateurs finaux.

        1.  Dans la [console d’administration Intune](http://manage.microsoft.com) sur **Administration** &gt; **Windows Phone**.

        2.  Cliquez sur le **Télécharger un fichier application connecté** et vous connecter avec votre identifiant Intune

        3.  Dans la page **d’installation du logiciel** pour **spécifier l’emplacement des fichiers de configuration du logiciel**, accédez à l’emplacement d’application de portail d’entreprise code signé (.xap pour Windows Phone 8.0) ou .aspx pour Windows Phone 8.1.

            Si vous êtes l’évaluation Intune et le téléchargement d’un fichier de l’application code signé dans un compte d’évaluation Intune, décochez la case **utiliser le fichier d’application du portail d’entreprise signé par le certificat de signature de code exemple Symantec** .

        4.  Ajoutez le fichier de certificat (.pfx) que vous avez exporté au **certificat de signature de Code** et créez un mot de passe pour le certificat.

        5.  Dans la page **description de logiciel** , renseignez les champs mémoriser que les utilisateurs voient ces informations sur les périphériques lors de l’affichage des détails sur l’application dans le portail d’entreprise.

        6.  Exécuter l’Assistant. Les utilisateurs qui inscrire un appareil Windows Phone 8.0 recevront désormais l’application portail d’entreprise sur leurs appareils lors de l’inscription. Les utilisateurs de Windows Phone 8.1 peuvent installer l’application portail d’entreprise à partir de la version de la banque de l’application portail d’entreprise.  Si les appareils Windows Phone 8.1 sont bloqués à partir du magasin de Windows Phone ou que vous voulez déployer l’application portail d’entreprise à l’aide Intune, vous devez télécharger et signer l’application portail d’entreprise Windows Phone 8.1 (SSP.appx).

4.  **Indiquer aux utilisateurs comment accéder aux ressources d’entreprise avec le portail d’entreprise** Vos utilisateurs devez savoir comment inscrire leur appareil et à quoi s’attendre une fois qu’il est enregistré dans la gestion. [Ce qu’indiquer à vos utilisateurs finaux sur l’utilisation de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)

## Déployer les Windows Phone 8.1 application du portail d’entreprise
Vous pouvez déployer l’application portail d’entreprise pour appareils Windows Phone 8.1 avec Intune au lieu de l’installation à partir du magasin de Windows Phone. Vous devez toujours activer inscription d’un appareil Windows Phone en suivant les étapes ci-dessus en utilisant le certificat Symantec. Vous devez ensuite télécharger l’application portail d’entreprise Windows Phone 8.1 et connectez-vous avec votre certificat Symantec.  Cela est nécessaire uniquement si vos utilisateurs n’utilisent pas le magasin d’entreprise et que vous voulez déployer le portail d’entreprise pour appareils Windows Phone 8.1.


1.  **Télécharger l’application portail d’entreprise**

    Téléchargez le [Microsoft Intune société portail application pour Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) à partir du centre de téléchargement et exécutez le fichier (.exe) extraction automatique. Ce fichier contient deux fichiers :

    -   Application de l’installation CompanyPortal.appx– le portail d’entreprise pour Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1 – un script PowerShell que vous pouvez utiliser pour signer le fichier de l’application portail d’entreprise afin qu’il peut être déployé sur les appareils Windows Phone 8.1

2.  **Téléchargez le Kit de développement de Windows Phone** Téléchargez le [Windows Phone SDK 8.0](http://go.microsoft.com/fwlink/?LinkId=615570) (http://go.microsoft.com/fwlink/?LinkId=268439) et installez le Kit de développement sur votre ordinateur. Ce SDK est nécessaire pour générer un jeton d’inscription d’application.

3.  **Générer un fichier AETX** Générer un fichier application d’inscription jeton (.aetx) à partir du fichier Symantec PFX à l’aide de AETGenerator.exe, composant de Windows Phone SDK 8.0. Pour obtenir des instructions sur la façon de créer un fichier AETX, voir [comment générer un jeton de l’inscription d’application pour Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)

4.  **Téléchargez le Kit de développement pour Windows 8.1 Windows** Téléchargez et installez le [Kit de développement Windows Phone](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Notez que le script PowerShell inclus avec l’application portail d’entreprise utilise la valeur par défaut l’emplacement, d’installation `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Si vous installez ailleurs, vous devez inclure l’emplacement dans un paramètre de l’applet de commande.

5.  **Authentification de code de l’application à l’aide de PowerShell** En tant qu’administrateur, ouvrir **Windows PowerShell** sur l’ordinateur hôte installé avec le Kit de développement Windows, le Symantec entreprise Mobile Code certificat de signature, accédez au fichier se WinPhoneCompanyPortal.ps1 et exécuter le script.

    **Exemple 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    Cet exemple signe la CompanyPortal.appx en C:\temp\ et génère la CompanyPortalEnterpriseSigned.appx. Il vous voulez utiliser le mot de passe PFX 1234 et lire l’ID de l’Éditeur du fichier PFX. Il lit le numéro d’entreprise à partir du fichier cert.aetx également.

    **Exemple 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    Cet exemple signe la CompanyPortal.appx en C:\temp\ et génère la CompanyPortalEnterpriseSigned.appx. Il serait utilisez le mot de passe PFX 1234 et l’ID de l’éditeur spécifié.

    **Paramètres :**

    -   `-InputAppx` – Le chemin d’accès local vers le fichier CompanyPortal.appx entre guillemets simples. Par exemple « C:\temp\CompanyPortal.appx »

    -   `-OutputAppx` – Le nom de fichier et le chemin local pour l’application portail d’entreprise signé entre guillemets simples. Par exemple, « C:\temp\CompanyPortalEnterpriseSigned.appx »

    -   `-PfxFilePath` – Le nom de fichier et le chemin local du fichier exporté PFX du certificat Symantec. Par exemple, « C:\signing\cert.pfx »

    -   `-PfxPassword` – Le mot de passe utilisé pour signer le fichier PFX entre guillemets simples. Par exemple « 1234 »

    -   `-AetxPath` – Le chemin d’accès local vers le fichier .aetx qui est utilisé pour lire le numéro d’entreprise si l’argument 'EnterpriseId' n’est pas définie. Cet argument ou EnterpriseId doit être fourni. Par exemple « C:\signing\cert.aetx »

    -   `-PublisherId` -L’ID de l’éditeur de l’entreprise. Si absent, le champ « Objet » du certificat de signature de Code Symantec entreprise Mobile est utilisé. Par exemple, « OID.0.9.2342.19200300.100.1.1=1000000001, CN = « Test, Inc. », OU = Test 1'

    -   `-SdkPath` -Le chemin d’accès au dossier racine du Kit de développement Windows pour Windows 8.1. Cet argument est facultatif et valeur par défaut est ${env:ProgramFiles(x86)} \Windows Kits\8.1.

    -   `-EnterpriseId` -L’ID d’entreprise. Cet argument ou 'AetxPath' doit être fourni. Si cet argument n’est fourni, le numéro d’entreprise est lu à partir du fichier AETX. Par exemple, 1000000001

6.  Déploiement de l’entreprise 8.1 Windows Phone Company Portal (SSP.appx).

    > [!IMPORTANT]
    > Le ssp.xap et le portail d’entreprise à partir du magasin peuvent être installé en même temps, qui peut être difficile pour les utilisateurs. Pour que tous les utilisateurs à l’aide de la ssp.xap, créer une application bloquée pour la version de la banque de l’application portail d’entreprise. Pour que tous les appareils Windows Phone 8.1 pour utiliser uniquement la version store de l’application portail d’entreprise, vous avez trois possibilités :
    >
    > -   Si vous ne sideload applications et que vous n’avez pas besoin prendre en charge Windows Phone 8.0, ne pas télécharger le ssp.xap signé.
    > -   Si des applications sideloaded sont nécessaires et si aucun périphérique Windows Phone 8 s’inscrire, modifier le déploiement ssp.xap créée automatiquement à partir de « disponible » à « désinstaller ».
    > -   Si sideloaded applications doivent être installées et appareils Windows Phone 8.0 doivent s’inscrire et recevoir le ssp.xap, créer un nouveau déploiement du logiciel de la ssp.xap et déployer avec l’action **désinstaller** . Appareils Windows Phone 8.0 ne prend en charge forcé installer ou désinstaller des applications, afin qu’ils ignore le déploiement. Appareils Windows Phone 8.1 prend en charge l’action de désinstallation et supprime la ssp.xap.
