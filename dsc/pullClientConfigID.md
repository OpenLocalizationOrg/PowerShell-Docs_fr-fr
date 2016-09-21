# Configuration d’un client extraire à l’aide des ID de configuration

> S’applique à : Windows PowerShell 5.0

Chaque nœud cible doit être invité à utiliser le mode d’extraction et avec l’URL spécifiée dans lequel il peut contacter le serveur extraire pour obtenir des configurations. Pour ce faire, vous devez configurer le Gestionnaire de Configuration Local (PPCM) avec les informations nécessaires. Pour configurer le PPCM, vous créez un type spécial de configuration, puissance ait été réduite avec l’attribut **DSCLocalConfigurationManager** . Pour plus d’informations sur la configuration de la PPCM, voir [configuration du Gestionnaire de Configuration Local](metaConfig.md).

> **Remarque**: cette rubrique s’applique à PowerShell 5.0. Pour plus d’informations sur la configuration d’un client d’extraction dans 4.0 PowerShell, consultez [la configuration d’un client d’extraction à l’aide des ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

Le script suivant configure le PPCM à extraire des configurations à partir d’un serveur nommé « CONTOSO-PullSrv ».

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = 1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }      
    }
}
PullClientConfigID
```

Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur extraire. L' **argument URLServeur**

Après l’exécution de ce script, il crée un nouveau dossier de sortie nommé **PullClientConfigID** et place un fichier MOF metaconfiguration il. Dans ce cas, le fichier MOF metaconfiguration sera nommé `localhost.meta.mof`.

Pour appliquer la configuration, contactez l’applet de commande **Set-DscLocalConfigurationManager** , avec le **chemin d’accès** défini à l’emplacement du fichier MOF metaconfiguration. Par exemple : `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## ID de configuration

Le script définit la propriété **Id_de_configuration** de PPCM vers un GUID qui a été créé précédemment à cet effet (vous pouvez créer un GUID à l’aide de l’applet de commande **New-Guid** ). **Id_de_configuration** est utilisée par le PPCM pour rechercher la configuration appropriée sur le serveur extraire. Le fichier MOF configuration sur le serveur extraire doit être nommé _Id_de_configuration_.mof, où _Id_de_configuration_ est la valeur de la propriété **Id_de_configuration** de PPCM du nœud cible.

## Serveur collecteur PME

Pour configurer un client pour extraire les configurations d’un serveur de PME, utilisez un bloc **ConfigurationRepositoryShare** . Dans un bloc **ConfigurationRepositoryShare** , spécifiez le chemin d’accès au serveur en définissant la propriété **chemin source** . La metaconfiguration suivante configure le nœud cible à extraire à partir d’un serveur extraire PME nommé **SMBPullServer**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## Serveurs de ressource et de rapport

Par défaut, le nœud client obtient les ressources nécessaires à partir d’et statut des rapports sur le serveur d’extraction de configuration. Toutefois, vous pouvez spécifier des serveurs extraire différents pour les ressources et création de rapports.
Pour spécifier un serveur de ressources, vous utilisez un **ResourceRepositoryWeb** (pour un serveur d’extraire web) ou un bloc **ResourceRepositoryShare** (pour un serveur d’extraire PME).
Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb** . Un serveur de rapports ne peut pas être un serveur de PME.
La metaconfiguration suivante configure un client d’extraction pour accéder à sa configuration à partir de **CONTOSO-PullSrv** et ses ressources à partir de **CONTOSO-ResourceSrv**et d’envoyer des rapports d’état à **CONTOSO-ReportSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## Voir aussi

* [Configuration d’un client extrait les noms de configuration](pullClientConfigNames.md)