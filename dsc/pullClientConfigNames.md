# Configuration d’un client extraire à l’aide de noms de configuration

> S’applique à : Windows PowerShell 5.0

Chaque nœud cible doit être invité à utiliser le mode d’extraction et avec l’URL spécifiée dans lequel il peut contacter le serveur extraire pour obtenir des configurations. Pour ce faire, vous devez configurer le Gestionnaire de Configuration Local (PPCM) avec les informations nécessaires. Pour configurer le PPCM, vous créez un type spécial de configuration, décorée avec l’attribut **DSCLocalConfigurationManager** . Pour plus d’informations sur la configuration de la PPCM, voir [configuration du Gestionnaire de Configuration Local](metaConfig.md).

> **Remarque**: cette rubrique s’applique à PowerShell 5.0. Pour plus d’informations sur la configuration d’un client d’extraction dans 4.0 PowerShell, consultez [la configuration d’un client d’extraction à l’aide des ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

Le script suivant configure le PPCM à extraire des configurations à partir d’un serveur nommé « CONTOSO-PullSrv » :

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur extraire. La propriété **ServerURL qui** Spécifie le point de terminaison pour le serveur extraire.

La propriété **RegistrationKey** est une clé partagée entre tous les nœuds de client pour un serveur extraire et ce serveur extraire. La même valeur est stockée dans un fichier sur le serveur extraire. La propriété **ConfigurationNames** indique le nom de la configuration destinée au nœud client. Sur le serveur extraire, le fichier MOF configuration pour ce nœud client doit être nommé *ConfigurationNames*.mof, où *ConfigurationNames* correspond à la valeur de la propriété **ConfigurationNames** définie dans cette metaconfiguration.

Après l’exécution de ce script, il crée un nouveau dossier de sortie nommé **PullClientConfigID** et place un fichier MOF metaconfiguration il. Dans ce cas, le fichier MOF metaconfiguration sera nommé `localhost.meta.mof`.

Pour appliquer la configuration, contactez l’applet de commande **Set-DscLocalConfigurationManager** , avec le **chemin d’accès** défini à l’emplacement du fichier MOF metaconfiguration. Par exemple : `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> **Remarque**: les clés d’enregistrement fonctionnent uniquement avec les serveurs web extraire. Vous devez toujours utiliser **Id_de_configuration** avec un serveur extraire PME. Pour plus d’informations sur la configuration d’un serveur extraire à l’aide de **Id_de_configuration**, reportez-vous à [la configuration d’un client d’extraction à l’aide des ID de configuration](pullClientConfigID.md)

## Serveurs de ressource et de rapport

Par défaut, le nœud client obtient les ressources nécessaires à partir d’et statut des rapports sur le serveur d’extraction de configuration. Toutefois, vous pouvez spécifier des serveurs extraire différents pour les ressources et création de rapports.
Pour spécifier un serveur de ressources, vous utilisez un **ResourceRepositoryWeb** (pour un serveur d’extraire web) ou un bloc **ResourceRepositoryShare** (pour un serveur d’extraire PME).
Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb** . Un serveur de rapports ne peut pas être un serveur de PME.
La metaconfiguration suivante configure un client d’extraction pour accéder à sa configuration à partir de **CONTOSO-PullSrv** et ses ressources à partir de **CONTOSO-ResourceSrv**et d’envoyer des rapports d’état à **CONTOSO-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
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

* [La configuration d’un client d’extraction avec l’ID de configuration](pullClientConfigID.md)
* [La configuration d’un serveur DSC web extraire](pullServer.md)
