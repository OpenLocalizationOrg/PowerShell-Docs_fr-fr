# Configuration du Gestionnaire de Configuration Local

> S’applique à : Windows PowerShell 5.0

Le Gestionnaire de Configuration Local (PPCM) est le moteur du module Windows PowerShell vous le souhaitez état Configuration (DSC). La PPCM s’exécute sur chaque nœud cible et est responsable de l’analyse et adopter configurations qui sont envoyées vers le nœud. Il est également chargé pour un nombre d’autres aspects de DSC, y compris les éléments suivants.

* Déterminer le mode d’actualisation (envoyé ou extrait).
* Spécifier la fréquence à laquelle un nœud extrait et Active les configurations.
* Associer le nœud serveurs extraire.
* Spécification des configurations partielles.

Vous utilisez un type spécial de configuration pour configurer le PPCM pour spécifier chacun de ces comportements. Les sections suivantes décrivent comment configurer la PPCM.

> **Remarque**: cette rubrique concerne le PPCM introduite dans Windows PowerShell 5.0. Pour plus d’informations sur la configuration de la PPCM dans Windows PowerShell 4.0, voir Windows PowerShell 4.0 vous le souhaitez état Configuration Local Gestionnaire de Configuration.

## Écriture et établir une configuration PPCM

Pour configurer le PPCM, vous créez et exécutez un type spécial de configuration. Pour spécifier une configuration PPCM, vous utilisez l’attribut DscLocalConfigurationManager. La figure suivante montre une configuration simple qui affecte la PPCM mode « pousser ».

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
} 
```

Vous appelez et exécutez la configuration pour créer la configuration MOF, comme vous le feriez une configuration normale (pour plus d’informations sur la création de la configuration MOF, voir prise en main Configuration de l’état souhaité Windows PowerShell). Contrairement aux configurations normales, vous ne pas appliquer une configuration PPCM en appelant de l’applet de commande [Démarrer DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) . Vous appelez à la place, l’applet de commande Set-DscLocalConfigurationManager, en fournissant le chemin d’accès à la configuration MOF en tant que paramètre. Une fois que vous mettez en place la configuration, vous pouvez voir les propriétés de la PPCM en appelant l’applet de commande [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) .

Une configuration PPCM peut contenir des blocs d’uniquement pour un ensemble limité de ressources. Dans l’exemple précédent, la seule ressource appelée est **paramètres**. Les autres ressources disponibles sont :

* **ConfigurationRepositoryWeb**: Spécifie un serveur extraire HTTP configurations. 
* **ConfigurationRepositoryShare**: Spécifie un serveur extraire PME configurations.
* **ResourceRepositoryWeb**: Spécifie un serveur extraire HTTP pour les modules.
* **ResourceRepositoryShare**: Spécifie un serveur extraire PME pour les modules.
* **ReportServerWeb**: Spécifie un serveur extraire HTTP à laquelle les rapports sont envoyés.
* **PartialConfiguration**: Spécifie les configurations partielles.

## Paramètres de base

Autre que spécifiant serveurs extraire et configurations partielles, toutes les propriétés de la PPCM sont configurés dans un bloc de **paramètres** . Les propriétés suivantes sont disponibles dans un bloc de **paramètres** .

|  Propriété  |  Type  |  Description   | 
|--- |--- |---| 
| ConfigurationModeFrequencyMins| UInt32| À quelle fréquence, en minutes, la configuration actuelle est activée et appliquée. Cette propriété est ignorée si la propriété ConfigurationMode est définie sur ApplyOnly. La valeur par défaut est 15. __Remarque__: la valeur de cette propriété doit être un multiple de la valeur de la propriété __RefreshFrequencyMins__ , soit la valeur de la propriété __RefreshFrequencyMins__ doit être un multiple de la valeur de cette propriété.| 
| RebootNodeIfNeeded| bool| Cela défini sur __$true__ pour redémarrer automatiquement le nœud après une configuration qui nécessite le redémarrage est appliquée. Dans le cas contraire, vous devrez redémarrer manuellement le nœud de n’importe quelle configuration qui en a besoin. La valeur par défaut est __$false__.| 
| ConfigurationMode| chaîne | Spécifie comment la PPCM réellement s’applique la configuration et les nœuds cible. Cela peut prendre les valeurs suivantes : __« ApplyOnly »__: DSC applique la configuration et n’a aucun effet supplémentaire à moins d’avoir une nouvelle configuration est envoyée au nœud cible ou une nouvelle configuration est extrait à partir d’un serveur. Après l’application d’origine d’une nouvelle configuration, DSC ne vérifie pas les dérives à partir d’un état précédemment configuré. __« ApplyAndMonitor »__: il s’agit de la valeur par défaut. La PPCM s’applique à toutes les nouvelles configurations. Après l’application d’origine d’une nouvelle configuration, si le nœud cible passe automatiquement à partir de l’état souhaité, DSC indique la différence dans les journaux __« ApplyAndAutoCorrect »__: DSC s’applique à toutes les nouvelles configurations. Après l’application d’origine d’une nouvelle configuration, si le nœud cible passe automatiquement à partir de l’état souhaité, DSC indique la différence dans les journaux et ré-s’applique la configuration en cours.| 
| ActionAfterReboot| chaîne| Spécifie que se passe-t-il après un redémarrage lors de l’application de configuration. Les valeurs possibles sont les suivants : __« ContuinueConfiguration »__: continuez d’appliquer la configuration en cours. __« StopConfiguraiton »__: arrêter la configuration en cours.| 
| RefreshMode| chaîne| Spécifie comment la PPCM obtient configurations. Les valeurs possibles sont les suivants : __« Désactivé »__: configurations DSC sont désactivées pour ce nœud. __« Pousser »__: Configurations sont initiées par l’applet de commande Démarrer DscConfiguration l’appel. La configuration est appliquée immédiatement vers le nœud. Il s’agit de la valeur par défaut. __Extraire :__ Le nœud est configuré pour vérifier régulièrement les configurations à partir d’un serveur extraire. Si cette propriété est définie pour extraire, vous devez spécifier un serveur extraire dans un bloc __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__ . Pour plus d’informations sur les serveurs extraire, voir [configuration d’un serveur extraire DSC](pullServer.md).| 
| CertificateID| chaîne| GUID qui spécifie un certificat utilisé pour sécuriser les informations d’identification pour l’accès à la configuration. Pour plus d’informations, voir ? [à sécuriser les informations d’identification dans Windows PowerShell vous le souhaitez état Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).| 
| Id_de_configuration| chaîne| GUID qui identifie le fichier de configuration pour accéder à partir d’un serveur extraire en mode extraire. Extrait le nœud configurations sur l’extraction serveur si le nom de la configuration MOF est nommé ConfigurationID.mof. __Remarque :__ Si vous définissez cette propriété, inscrire le nœud avec un serveur extraire à l’aide de __clés de Registre__ et ne fonctionne pas. Pour plus d’informations, voir [la configuration d’un client extrait les noms de configuration](pullClientConfigNames.md).| 
| RefreshFrequencyMins| UInt32| L’intervalle de temps, en minutes, à laquelle la PPCM vérifie un serveur extraire pour obtenir des configurations mis à jour. Cette valeur est ignorée si la PPCM n’est pas configuré en mode extraire. La valeur par défaut est de 30. __Remarque :__  La valeur de cette propriété doit être un multiple de la valeur de la propriété __ConfigurationModeFrequencyMins__ , soit la valeur de la propriété __ConfigurationModeFrequencyMins__ doit être un multiple de la valeur de cette propriété.| 
| AllowModlueOverwrite| bool| __$TRUE__ si nouvelles configurations téléchargement à partir du serveur de configuration sont autorisés à remplacent les anciens sur le nœud cible. Dans le cas contraire, $FALSE.| 
| DebugMode| bool| Si la valeur __$TRUE__, cela entraîne la PPCM recharger les ressources DSC, même si elles ont été précédemment mis en cache. Valeur $FALSE pour utiliser les ressources mises en cache. En règle générale, vous devez définir cette propriété sur __$TRUE__ pendant le débogage d’une ressource et sur __$FALSE__ pour production. La valeur par défaut est __$FALSE__.| 
| ConfigurationDownloadManagers| CimInstance]| Obsolète. Utiliser des blocs de __ConfigurationRepositoryWeb__ et __ConfigurationRepositoryShare__ pour définir la configuration des serveurs extraire.| 
| ResourceModuleManagers| CimInstance]| Obsolète. Utiliser des blocs __ResourceRepositoryWeb__ et __ResourceRepositoryShare__ pour définir des ressources extraits serveurs.| 
| ReportManagers| CimInstance]| Obsolète. Utiliser des blocs de __ReportServerWeb__ pour définir des serveurs d’extraction de rapports.| 
| PartialConfigurations| CimInstance| Non disponible. N’utilisez pas.| 
| StatusRetentionTimeInDays | UInt32| Le nombre de jours que la PPCM conserve l’état de la configuration en cours.| 

## Extraire des serveurs

Un serveur d’extraction est un service web OData ou un partage de PME qui est utilisé comme un emplacement central pour les fichiers DSC. Configuration PPCM prend en charge la définition des types de serveurs extraire suivants :

* **Serveur de configuration**: un référentiel pour les configurations DSC. Définir les serveurs de configuration à l’aide de blocs de **ConfigurationRepositoryShare** (pour les serveurs PME) et **ConfigurationRepositoryWeb** (pour les serveurs web).
* Serveur de ressources — un référentiel pour les ressources DSC, empaquetés en tant que modules PowerShell. Définir les serveurs de ressources à l’aide de blocs de **ResourceRepositoryShare** (pour les serveurs PME) et **ResourceRepositoryWeb** (pour les serveurs web).
* Serveur de rapports, un service DSC envoie des données de rapport au. Définir les serveurs de rapports à l’aide des blocs de **ReportServerWeb** . Un serveur de rapports doit être un service web.

Pour plus d’informations sur la configuration et l’utilisation de serveurs extraire, voir [configuration d’un serveur extraire DSC](pullServer.md).

## Blocs de serveur de configuration

Pour définir une configuration basée sur serveur, vous créez un bloc **ConfigurationRepositoryWeb** . Un **ConfigurationRepositoryWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---| 
|AllowUnsecureConnection|bool|Valeur **$TRUE** pour autoriser les connexions depuis le nœud au serveur sans authentification. Défini sur **$FALSE** pour exiger une authentification.|
|CertificateID|chaîne|GUID qui représente le certificat utilisé pour l’authentification au serveur.|
|ConfigurationNames|String]|Tableau de noms de configurations à collecter par le nœud cible. Celles-ci sont utilisées uniquement si le nœud est enregistré avec le serveur extraire à l’aide d’un **RegistrationKey**. Pour plus d’informations, voir [la configuration d’un client extrait les noms de configuration](pullClientConfigNames.md).|
|RegistrationKey|chaîne|GUID qui enregistre le nœud avec le serveur extraire. Pour plus d’informations, voir [la configuration d’un client extrait les noms de configuration](pullClientConfigNames.md).|
|ServerURL|chaîne|L’URL du serveur de configuration.|

Pour définir un serveur de configuration basée sur les PME, vous créez un bloc **ConfigurationRepositoryShare** . Un **ConfigurationRepositoryShare** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|Informations d’identification|MSFT_Credential|Les informations d’identification utilisées pour authentifier au partage PME.|
|Chemin source|chaîne|Le chemin d’accès de la part de PME.|

## Blocs de serveur de ressources

Pour définir une ressource basée sur le web serveur, vous créez un bloc **ResourceRepositoryWeb** . Un **ResourceRepositoryWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Valeur **$TRUE** pour autoriser les connexions depuis le nœud au serveur sans authentification. Défini sur **$FALSE** pour exiger une authentification.|
|CertificateID|chaîne|GUID qui représente le certificat utilisé pour l’authentification au serveur.|
|RegistrationKey|chaîne|GUID qui identifie le nœud au serveur extraire. Pour plus d’informations, voir comment enregistrer un nœud avec un serveur extraire DSC.|
|ServerURL|chaîne|L’URL du serveur de configuration.|
 
Pour définir un serveur de ressource basés sur des PME, vous créez un bloc **ResourceRepositoryShare** . **ResourceRepositoryShare** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|Informations d’identification|MSFT_Credential|Les informations d’identification utilisées pour authentifier au partage PME.|
|Chemin source|chaîne|Le chemin d’accès de la part de PME.|

## Blocs de serveur de rapports

Un serveur de rapports doit être un service web OData. Pour définir un serveur de rapports, vous créez un bloc **ReportServerWeb** . **ReportServerWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---| 
|AllowUnsecureConnection|bool|Valeur **$TRUE** pour autoriser les connexions depuis le nœud au serveur sans authentification. Défini sur **$FALSE** pour exiger une authentification.|
|CertificateID|chaîne|GUID qui représente le certificat utilisé pour l’authentification au serveur.|
|RegistrationKey|chaîne|GUID qui identifie le nœud au serveur extraire. Pour plus d’informations, voir comment enregistrer un nœud avec un serveur extraire DSC.|
|ServerURL|chaîne|L’URL du serveur de configuration.|

## Configurations partielles

Pour définir une configuration partielle, vous créez un bloc **PartialConfiguration** . Pour plus d’informations sur les configurations partielles, voir [configurations DSC partielle](partialConfigs.md). **PartialConfiguration** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---| 
|ConfigurationSource|String]|Tableau des noms des serveurs de configuration, précédemment définies dans **ConfiguratoinRepositoryWeb** et blocs **ConfigurationRepositoryShare** , où la configuration partielle est extrait à partir de.|
|DependsOn|chaîne {}|Une liste de noms d’autres configurations doivent être effectuées avant que cette configuration partielle soit appliquée.|
|Description|chaîne|Texte utilisé pour décrire la configuration partielle.|
|ExclusiveResources|String]|Tableau des ressources exclusifs à cette configuration partielle.|
|RefreshMode|chaîne|Spécifie comment DC obtient cette configuration partielle... Les valeurs possibles sont les suivantes : **désactivé**: cette configuration partielle est désactivée. **Notifications Push**: la configuration partielle est envoyée au nœud en appelant l’applet de commande [Publier DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) . Une fois toutes les configurations partielles pour le nœud sont envoyées ou extrait à partir d’un serveur, la configuration peut être démarrée en appelant `Start-DscConfiguration –UseExisting`. Il s’agit de la valeur par défaut. **Extraire**: le nœud est configuré pour vérifier régulièrement la configuration partielle à partir d’un serveur extraire. Si cette propriété est définie sur « Extraire », vous devez spécifier un serveur extraire en définissant la propriété **ConfigurationSource** . Pour plus d’informations sur les serveurs extraire, voir [configuration d’un serveur extraire DSC](pullServer.md).|
|ResourceModlueSource|String]|Tableau des noms des serveurs de ressources à partir duquel télécharger les ressources nécessaires pour cette configuration partielle. Ces noms doivent faire référence à des serveurs de ressources définis précédemment dans blocs **ResourceRepositoryWeb** et **ResourceRepositoryShare** .|

## Voir aussi 

### Concepts
Prise en main de Windows PowerShell vous le souhaitez état Configuration [configuration d’un serveur extraire DSC](pullServer.md) 
[Windows PowerShell 4.0 vous le souhaitez état Configuration Local Gestionnaire de Configuration](metaConfig4.md) 

### Autres ressources
[Jeu-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) 
[la configuration d’un client extrait les noms de configuration](pullClientConfigNames.md) 
