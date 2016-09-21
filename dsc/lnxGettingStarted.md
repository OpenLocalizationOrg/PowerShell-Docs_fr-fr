# Prise en main avec vous le souhaitez état Configuration (DSC) pour Linux

Cette rubrique explique comment procéder à l’aide de PowerShell souhaité état Configuration (DSC) pour Linux. Pour obtenir des informations générales sur DSC, voir [Prise en main Configuration de l’état souhaité Windows PowerShell](overview.md).

## Versions de système opération Linux prises en charge

Les versions de système d’exploitation Linux suivantes sont prises en charge pour DSC pour Linux.
- CentOS 5, 6 et 7 (x86/x64)
- Debian GNU/Linux 6 et 7 (x86/x64)
- Oracle Linux 5, 6 et 7 (x86/x64)
- Chapeau rouge Enterprise Linux Server 5, 6 et 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 et 12 (x86/x64)
- Serveur Ubuntu 12.04 LTS et 14.04 LTS (x86/x64)

Le tableau suivant décrit les dépendances ackage requis pour DSC pour Linux.

|  Package requis |  Description |  Version minimale | 
|---|---|---|
| glibc| Bibliothèque GNU| 2... 4-31.30| 
| Python| Python| 2.4 – 3.4| 
| omiserver| Ouvrez Gestion de l’Infrastructure| 1.0.8.1| 
| OpenSSL| Bibliothèques OpenSSL| 0.9.8 ou 1.0| 
| ctypes| Bibliothèque de Python CTypes| Doit correspondre à Python version| 
| libcurl| Coin bibliothèque client http| 7.15.1| 

## Installer DSC Linux

Vous devez installer l' [Infrastructure de gestion des Open (OMI)](https://collaboration.opengroup.org/omi/) avant d’installer DSC pour Linux.

### L’installation OMI

Configuration de l’état souhaité pour Linux nécessite le serveur CIM ouvrir Gestion Infrastructure (OMI), version 1.0.8.1. OMI peut être téléchargé à partir du groupe Ouvrir : [Ouvrir Gestion Infrastructure (OMI)](https://collaboration.opengroup.org/omi/).

Pour installer OMI, installez le package appropriée pour votre système Linux (.rpm ou .deb) et version OpenSSL (ssl_098 ou ssl_100) et l’architecture (x64/x86). Packages t/min sont appropriées pour CentOS, Red chapeau Enterprise Linux, SUSE Linux Enterprise Server et Oracle Linux. Packages DEB sont adaptés Debian GNU/Linux et Ubuntu Server. Les packages ssl_098 sont appropriées pour les ordinateurs avec OpenSSL 0.9.8 installé tandis que les packages ssl_100 sont appropriées pour les ordinateurs avec OpenSSL 1.0 est installé.

> **Remarque**: pour déterminer la version installée OpenSSL, exécutez la commande `openssl version`.

Exécutez la commande suivante pour installer OMI sur un système CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### L’installation DSC

Pour installer DSC, installez le package appropriée pour votre système Linux (.rpm ou .deb) et version OpenSSL (ssl_098 ou ssl_100) et l’architecture (x64/x86). Packages t/min sont appropriées pour CentOS, Red chapeau Enterprise Linux, SUSE Linux Enterprise Server et Oracle Linux. Packages DEB sont adaptés Debian GNU/Linux et Ubuntu Server. Les packages ssl_098 sont appropriées pour les ordinateurs avec OpenSSL 0.9.8 installé tandis que les packages ssl_100 sont appropriées pour les ordinateurs avec OpenSSL 1.0 est installé.

> **Remarque**: pour déterminer la version installée OpenSSL, exécutez la version openssl commande.
 
Exécutez la commande suivante pour installer DSC sur un système CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## À l’aide de DSC pour Linux

Les sections suivantes expliquent comment créer et exécuter des configurations DSC sur les ordinateurs Linux.

### Création d’un document MOF configuration

Le mot-clé Windows PowerShell Configuration est utilisé pour créer une configuration pour les ordinateurs Linux, comme pour les ordinateurs Windows. Les étapes suivantes décrivent la création d’un document de configuration d’un ordinateur Linux à l’aide de Windows PowerShell.

1. Importer le module nx. Le module Windows PowerShell nx contient le schéma pour les ressources intégrées pour DSC pour Linux et doit être installé sur votre ordinateur local et importé dans la configuration.

    -Pour installer le module nx, copiez le répertoire module nx soit `%UserProfile%\Documents\WindowsPowerShell\Modules\` ou `C:\windows\system32\WindowsPowerShell\v1.0\Modules`. Le module nx est inclus dans le DSC Linux package d’installation (MSI). Pour importer le module nx dans votre configuration, utilisez la commande __Importer DSCResource__ :
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. Définir une configuration et générer le document de configuration :

```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### Distribuer la configuration de l’ordinateur Linux

Documents de configuration (fichiers MOF) peuvent être installés sur l’ordinateur Linux à l’aide de l’applet de commande [Démarrer DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) . Pour pouvoir utiliser cette applet de commande, ainsi que les .aspx [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379)ou applets de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) à distance sur un ordinateur Linux, vous devez utiliser une CIMSession. L’applet de commande [New-CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) est utilisé pour créer une CIMSession sur l’ordinateur Linux.

Le code suivant montre comment créer une CIMSession pour DSC pour Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **Remarque**:
* En mode « Pousser », les informations d’identification utilisateur doivent être l’utilisateur racine sur l’ordinateur Linux.
* Seules les connexions SSL/TLS sont prises en charge pour DSC Linux, le nouveau-CimSession doivent être utilisés avec le paramètre UseSSL défini sur $true.
* Le certificat SSL utilisé par OMI (pour DSC) est spécifié dans le fichier : `/opt/omi/etc/omiserver.conf` avec les propriétés : pemfile et fichier de clé.
Si ce certificat n’est pas approuvé par l’ordinateur Windows que vous exécutez l’applet de commande [New-CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) sur, vous pouvez choisir d’ignorer la validation des certificats avec les Options de CIMSession : `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Exécutez la commande suivante pour distribuer la configuration DSC vers le nœud Linux.

`Start-DSCConfiguration -Path:"C:\temp" -cimsession:$sess -wait -verbose`

### Distribuer la configuration avec un serveur d’extraction

Configurations peuvent être distribuées sur un ordinateur Linux avec un serveur extraire, comme pour les ordinateurs Windows. Pour des instructions sur l’utilisation d’un serveur extraire, voir [Windows PowerShell vous le souhaitez Configuration extraire serveurs d’état](pullServer.md). Pour plus d’informations et limitations liées à l’utilisation des ordinateurs Linux avec un serveur extraire, consultez les Notes de publication pour la Configuration de l’état souhaité pour Linux.

### Utilisation de configurations localement

DSC pour Linux inclut des scripts pour fonctionner avec la configuration de l’ordinateur local Linux. Ces scripts sont localiser dans `/opt/microsoft/dsc/Scripts` et inclure les éléments suivants :
* GetConfiguration.py

 Retourne la configuration en cours appliquée à l’ordinateur. Similaire à l’applet de commande Get-DscConfiguration de l’applet de commande Windows PowerShell.

`# sudo ./GetConfiguration.py`

* GetMetaConfiguration.py

 Retourne la meta-configuration en cours appliquée à l’ordinateur. Similaire à l’applet de commande [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) applet de commande.

`# sudo ./GetMetaConfiguration.py`

* InstallModule.py

 Installe un module ressource DSC personnalisé. Nécessite le chemin d’accès à un fichier .zip contenant la bibliothèque d’objets partagé module et les fichiers de schéma MOF.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Supprime un module de ressources DSC personnalisé. Nécessite le nom du module à supprimer.

`# sudo ./RemoveModule.py cnx_Resource`

* SendConfigurationApply.py

 Applique un fichier de configuration de MOF sur l’ordinateur. Similaire à l’applet de commande [Démarrer DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) . Nécessite le chemin d’accès à la configuration MOF à appliquer.

`# sudo ./RemoveModule.py cnx_Resource`

* SendMetaConfiguration.py

 Applique un fichier Meta Configuration MOF sur l’ordinateur. Similaire à l’applet de commande [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) . Nécessite le chemin vers le modèle de Configuration Meta MOF à appliquer.

`# sudo ./SendMetaConfiguration.py –configurationmof /tmp/localhost.meta.mof`

## Configuration de l’état pour les fichiers journaux Linux vous le souhaitez PowerShell

Les fichiers journaux suivants sont générés pour DSC pour les messages Linux.

|Fichier journal|Répertoire|Description|
|---|---|---|
|omiserver.log|/ opter/omi/var/log /|Messages relatifs à l’opération du serveur OMI CIM.|
|DSC.log|/ opter/omi/var/log /|Messages relatifs à l’opération les Gestionnaire de Configuration Local (PPCM) et DSC d’opérations de ressources.|
