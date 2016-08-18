# Écriture d’une ressource DSC personnalisée avec les classes de PowerShell

> S’applique à : Windows, Windows PowerShell, 5.0

Avec l’introduction de classes de PowerShell dans Windows PowerShell 5.0, vous pouvez maintenant définir une ressource DSC en créant une classe. La classe définit le schéma et l’implémentation de la ressource, il n’est donc pas nécessaire pour créer un fichier MOF séparé. La structure de dossiers d’une ressource basée sur la classe est également plus simple, car un dossier **DSCResources** n’est pas nécessaire.

Dans une ressource de DSC basé sur une classe, le schéma est défini en tant que propriétés de la classe qui peut être modifié avec des attributs pour spécifier le type de propriété... La ressource est implémentée par les méthodes **Get()**, **Set()**et **Test()** (équivalents pour les fonctions de **Test-TargetResource** dans une ressource de script, **Set-TargetResource**et **Get-TargetResource**.

Dans cette rubrique, nous allons créer une ressource simple nommée **FileResource** qui gère un fichier dans un chemin d’accès spécifié.

Pour plus d’informations sur les ressources de DSC, voir [Custom Windows PowerShell vous le souhaitez état Configuration les ressources de Build](authoringResource.md)

## Structure de dossiers d’une ressource de classe

Pour implémenter une ressource personnalisée DSC avec une classe de PowerShell, créez la structure de dossier suivante. La classe est définie dans **MyDscResource.psm1** et le manifeste de module est défini dans **MyDscResource.psd1**.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## Créez la classe

Le mot clé class vous permet de créer une classe de PowerShell. Pour spécifier qu’une classe est une ressource DSC, utilisez l’attribut **DscResource()** . Le nom de la classe est le nom de la ressource DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### Déclarer des propriétés

Le schéma de ressource DSC est défini en tant que propriétés de la classe. Nous déclarez trois propriétés comme suit.

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

Notez que les propriétés sont modifiées par attributs. La signification des attributs est la suivante :

- **DscProperty(Key)**: la propriété est obligatoire. La propriété est une clé. Les valeurs de toutes les propriétés marquées comme clés doivent combiner pour identifier de manière unique une instance de la ressource au sein d’une configuration.
- **DscProperty(Mandatory)**: la propriété est obligatoire.
- **DscProperty(NotConfigurable)**: la propriété est en lecture seule. Les propriétés marquées avec cet attribut ne peut pas être définies à une configuration, mais sont remplies par la méthode **Get()** s’il est présent.
- **DscProperty()**: la propriété est configurable, mais il n’est pas nécessaire.

Les propriétés **$Path** et **$SourcePath** sont des chaînes. Le **$CreationTime** est une propriété [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) . La propriété **$Ensure** est un type d’énumération, défini comme suit.

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### Les méthodes de mise en œuvre

Les méthodes **Get()**, **Set()**et **Test()** sont similaires pour les fonctions de **Test-TargetResource** dans une ressource de script, **Set-TargetResource**et **Get-TargetResource**.

Ce code inclut également la fonction CopyFile(), une fonction d’assistance qui copie le fichier à partir de **$SourcePath** à **$Path**. 

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### Le fichier complet
Votre fichier de classe suit.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## Créer un manifeste

Pour rendre une ressource basée sur les classes disponibles pour le moteur de DSC, vous devez inclure une instruction **DscResourcesToExport** dans le fichier manifeste qui demande le module pour exporter la ressource. Notre manifeste ressemble à ceci :

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

## Tester la ressource

Après avoir enregistré les classes et les fichiers manifeste dans la structure de dossiers, comme décrit précédemment, vous pouvez créer une configuration qui utilise la nouvelle ressource. Pour plus d’informations sur la manière d’exécuter une configuration DSC, voir [configurations de Enacting](enactingConfigurations.md). La configuration suivante vérifie si le fichier à `c:\test\test.txt` existe et, dans le cas contraire, cette méthode copie le fichier à partir de `c:\test.txt` (vous devez créer `c:\test.txt` avant d’exécuter la configuration).

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    } 
}
Test
Start-DscConfiguration -Wait -Force Test
```

## Voir aussi
### Concepts
[Créer des ressources de Configuration d’état personnalisée Windows PowerShell que vous le souhaitez](authoringResource.md)
