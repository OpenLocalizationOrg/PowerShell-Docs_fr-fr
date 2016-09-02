# Ressources de composite : à l’aide d’une configuration DSC en tant que ressource

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Dans des situations réelles, les configurations peuvent devenir longs et complexes, l’appel de nombreuses ressources différents et en définissant un grand nombre de propriétés. Pour vous aider à résoudre cette complexité, vous pouvez utiliser une configuration de Windows PowerShell vous le souhaitez état Configuration (DSC) en tant que ressource pour les autres configurations. Ce que nous appelons une ressource de composite. Une ressource composite est une configuration DSC qui accepte des paramètres. Les paramètres de la configuration d’agissent en tant que les propriétés de la ressource. La configuration est enregistrée en tant que fichier avec une **. schema.psm1** extension et prend au lieu du schéma MOF et la ressource de script dans une ressource DSC classique (pour plus d’informations sur les ressources DSC, voir [Windows PowerShell vous le souhaitez état Configuration ressources](resources.md).

## Création de la ressource de composite

Dans notre exemple, nous avons créer une configuration qui appelle un certain nombre de ressources existantes pour configurer des ordinateurs virtuels. Au lieu de spécifier les valeurs à définir dans des blocs de configuration, la configuration accepte un nombre de paramètres qui sont ensuite utilisés dans les blocs de configuration.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Creae VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### Enregistrement de la configuration comme une ressource de composite

Pour utiliser la configuration paramétrée comme une ressource DSC, enregistrez-le dans une structure de répertoire similaire à celui de toute autre ressource MOF et nommez-le avec une **. schema.psm1** extension. Cet exemple, nous allons nommez le fichier **xVirtualMachine.schema.psm1**. Vous devez également créer un manifeste nommé **xVirtualMachine.psd1** qui contient la ligne suivante. Notez qu’il s’agit en plus de **MyDscResources.psd1**, le module de manifeste pour toutes les ressources sous le dossier **MyDscResources** .

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Lorsque vous avez terminé, la structure de dossier doit être comme suit.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSC Resources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

La ressource est désormais accessibles à l’aide de l’applet de commande Get-DscResource, et ses propriétés sont accessibles par cette applet de commande ou à l’aide **Ctrl + Espace** de saisie semi-automatique dans Windows PowerShell ISE.

## À l’aide de la ressource de composite

Vous créez ensuite une configuration qui appelle la ressource de composite. Cette configuration appelle la ressource de composite xVirtualMachine pour créer un ordinateur virtuel et appelle ensuite la ressource **xComputer** pour le renommer.

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## Voir aussi
### Concepts
* [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)
* [Configuration d’état de Windows PowerShell souhaitée en main](overview.md)
