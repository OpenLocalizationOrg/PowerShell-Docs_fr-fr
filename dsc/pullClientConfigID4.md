# Configuration d’un client extraire à l’aide des ID de configuration dans PowerShell 4.0

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Chaque nœud cible doit être invité à utiliser le mode d’extraction et avec l’URL spécifiée dans lequel il peut contacter le serveur extraire pour obtenir des configurations. Pour ce faire, vous devez configurer le Gestionnaire de Configuration Local (PPCM) avec les informations nécessaires. Pour configurer le PPCM, vous créez un type spécial de configuration connu sous une « metaconfiguration ». Pour plus d’informations sur la configuration de la PPCM, voir [Windows PowerShell 4.0 vous le souhaitez état Configuration Local Gestionnaire de Configuration](metaConfig4.md)

Le script suivant configure le PPCM à extraire des configurations à partir d’un serveur nommé « PullServer ».

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

Dans le script, **DownloadManagerCustomData** passe l’URL du serveur collecteur et (dans cet exemple) permet une connexion non sécurisée. 

Après l’exécution de ce script, il crée un nouveau dossier de sortie nommé **SimpleMetaConfigurationForPull** et place un fichier MOF metaconfiguration il.

Pour appliquer la configuration, utilisez **Set-DscLocalConfigurationManager** avec paramètres pour **nom_ordinateur** (utilisez « hôte local ») et le **chemin d’accès** (le chemin d’accès à l’emplacement du fichier de localhost.meta.mof du nœud cible). Par exemple : 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## ID de configuration
Le script définit la propriété **Id_de_configuration** de la PPCM vers un GUID qui a été créé précédemment à cet effet (vous pouvez créer un GUID à l’aide de l’applet de commande **New-Guid** ). **Id_de_configuration** est utilisée par le PPCM pour rechercher la configuration appropriée sur le serveur extraire. Le fichier MOF configuration sur le serveur extraire doit être nommé `ConfigurationID.mof`, où *Id_de_configuration* est la valeur de la propriété **Id_de_configuration** de PPCM du nœud cible.
