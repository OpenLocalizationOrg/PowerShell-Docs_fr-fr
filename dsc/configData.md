# Séparation des données de Configuration et environnement

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Dans Windows PowerShell vous le souhaitez état Configuration (DSC), il est possible de séparer les données de configuration de la logique de votre configuration. Une autre façon de concevoir le système est à prendre en compte la configuration structurelle (par exemple, une configuration peut nécessiter que IIS soit installé) séparément à partir de la configuration de l’environnement (en d’autres termes, si la situation est un environnement de test et de production une — les noms de nœud serait différents, mais la configuration qui leur sont appliquée sont les mêmes). Il présente les avantages suivants :

* Elle vous permet de réutiliser vos données de configuration pour les différentes ressources, les nœuds et les configurations.
* La logique de configuration n’est plus réutilisable si elle ne contient-elle pas les données codées en dur. Ceci est similaire à une bonne instructions de scripts pour les fonctions.
* Si une partie des données doit être modifié, vous pouvez apporter les modifications dans un seul emplacement, gagner du temps et réduire les erreurs.

## Exemples et concepts fondamentaux

Pour spécifier la partie de l’environnement de la configuration, DSC utilise le paramètre **ConfigurationData** , qui est une table de hachage (ou elle peut prendre un fichier .psd1 qui contient la table de hachage). Cette table de hachage doit avoir au moins une clé **AllNodes**, ce qui a pour valeur structurée. Par exemple :

```powershell
$MyData = 
@{
    AllNodes = @();
    NonNodeData = ""   
}
```

Notez la clé AllNodes, dont la valeur est un tableau. Chaque élément de ce tableau est également une table de hachage, ce qui nécessite NodeName en tant que clé :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

Chaque entrée de table de hachage dans AllNodes correspond aux données de configuration pour un nœud dans la configuration. En plus de la clé NodeName requise, vous pouvez ajouter des autres clés pour la table de hachage ainsi que, par exemple :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1";
            
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

DSC propose trois variables spéciales à utiliser dans le script de configuration :

* **$AllNodes**: fait référence à l’ensemble des nœuds. Vous pouvez utiliser le filtrage avec **. WHERE()** et **. ForEach()**, de sorte qu’au lieu de coder en dur les noms de nœud pour sélectionner les nœuds particulière pour l’action, vous pourriez écrire quelque chose de semblable à celle-ci pour sélectionner l’ordinateur virtuel-1 et 3 de la machine virtuelle dans l’exemple ci-dessus :

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node**: une fois que l’ensemble de nœuds est filtrée, vous pouvez utiliser $Node pour faire référence à l’entrée particulière. Par exemple :

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

Pour appliquer une propriété à tous les nœuds, vous pouvez définir NodeName = « * ». Par exemple, pour donner à tous les nœuds de la propriété LogPath, vous pouvez procéder :

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData**: vous pouvez utiliser cette variable au sein d’une configuration pour accéder à la table de hachage de données de configuration transmise en tant que paramètre. Par exemple :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

Vous trouverez un exemple complet inclus dans le [module de xWebAdministration](https://powershellgallery.com/packages/xWebAdministration).