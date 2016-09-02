# Écriture d’une ressource DSC personnalisée avec MOF

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Dans cette rubrique, nous seront définissent le schéma d’une ressource personnalisée Windows PowerShell vous le souhaitez état Configuration (DSC) dans un fichier MOF et mettre en œuvre de la ressource dans un fichier de script Windows PowerShell. Cette ressource personnalisée est pour créer et gérer un site web.

## Création du schéma MOF

Le schéma définit les propriétés de votre ressource qui peuvent être configurés par un script de configuration DSC.

### Structure de dossiers d’une ressource MOF

Pour implémenter une ressource personnalisée DSC avec un schéma MOF, créez la structure de dossier suivante. Le schéma MOF est défini dans le fichier Demo_IISWebsite.schema.mof et le script de ressources est défini dans Demo_IISWebsite.ps1. Si vous le souhaitez, vous pouvez créer un fichier de manifeste (psd1) du module.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Notez qu’il est nécessaire créer un dossier nommé DSCResources sous le dossier de niveau supérieur, et que le dossier de chaque ressource doit avoir le même nom que la ressource.

### Le contenu du fichier MOF

Voici un exemple de fichier MOF qui peut être utilisée pour une ressource de site Web personnalisé. Pour suivre cet exemple, enregistrez ce schéma dans un fichier et appelez le fichier *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")] 
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Notez les points suivants concernant le code précédent :

* `FriendlyName` définit le nom que vous pouvez utiliser pour faire référence à cette ressource personnalisée dans des scripts de configuration DSC. Dans cet exemple, `Website` équivaut au nom convivial `Archive` pour la ressource d’Archive intégrée.
* La classe que vous définissez pour vos ressources personnalisées doivent dériver de `OMI_BaseResource`.
* Le qualificateur de type, `[Key]`, sur une propriété indique que cette propriété s’identifier de manière unique l’instance de la ressource. A `[Key]` propriété est également requise.
* Le `[Required]` qualificateur indique que la propriété est requise (une valeur doit être spécifiée dans un script de configuration qui utilise cette ressource).
* Le `[write]` qualificateur indique que cette propriété est facultative lors de l’utilisation de la ressource personnalisée dans un script de configuration. Le `[read]` qualificateur indique qu’une propriété ne peut pas être définie à une configuration et est destiné uniquement à des fins de création de rapports.
* `Values` limite les valeurs qui peuvent être assignés à la propriété à la liste des valeurs définies dans `ValueMap`. Pour plus d’informations, consultez la rubrique [ValueMap et valeur qualificateurs](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* Y compris une propriété appelée `Ensure` dans votre ressource est recommandée comme moyen de maintenir un style cohérent avec les ressources DSC intégrées.
* Nommez le fichier de schéma pour la ressource personnalisée comme suit : `classname.schema.mof`, où `classname` est l’identificateur qui suit le `class` mot clé dans la définition de schéma.

### Écriture du script de ressources

Le script de ressources implémente la logique de la ressource. Dans ce module, vous devez inclure les trois fonctions appelées **Get-TargetResource**, **Set-TargetResource**et **Test-TargetResource**. Tous les trois fonctions doivent prendre un jeu de paramètres qui est identique à l’ensemble des propriétés définies dans le schéma MOF que vous avez créé pour votre ressource. Dans ce document, ce jeu de propriétés est dénommé « propriétés de la ressource ». Magasin de ces trois fonctions dans un fichier appelées <ResourceName>.psm1. Dans l’exemple suivant, les fonctions sont stockées dans un fichier appelé Demo_IISWebsite.psm1.

> **Remarque**: lorsque vous exécutez le script de configuration même sur votre ressource plusieurs fois, vous ne devriez recevoir aucune erreur et la ressource doit rester dans le même état qu’une fois l’exécution du script. Pour ce faire, vérifiez que vos fonctions **Get-TargetResource** et **Test-TargetResource** laisser la ressource non modifiée, et que plusieurs fois l’appel de la fonction de **Set-TargetResource** dans une séquence avec les mêmes valeurs de paramètre est toujours équivalente à l’appelant à la fois.

Dans l’implémentation de la fonction **Get-TargetResource** , utilisez les valeurs de propriété de ressource de clé qui sont fournis en tant que paramètres pour vérifier l’état de l’instance de la ressource spécifiée. Cette fonction doit renvoyer une table de hachage qui répertorie toutes les propriétés de ressource en tant que clés et les valeurs réelles de ces propriétés en tant que les valeurs correspondantes. Le code suivant fournit un exemple.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource 
{
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name; 
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }
  
        $getTargetResourceResult;
}
```

En fonction des valeurs spécifiées pour les propriétés de la ressource dans le script de configuration, **Set-TargetResource** devez effectuer l’une des opérations suivantes :

* Créer un nouveau site Web
* Mettre à jour un site Web existant
* Supprimer un site Web existant

L’exemple suivant illustre cela.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine. 
function Set-TargetResource 
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )
 
    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Enfin, la fonction **Test-TargetResource** doit prendre la même paramètre à définir en tant que **Get-TargetResource** et **Set-TargetResource**. Dans votre implémentation de **Test-TargetResource**, vérifiez l’état de l’instance de ressource qui est spécifié dans les paramètres de clés. Si le statut réel de l’instance de ressource ne correspond pas de valeurs spécifiées dans le paramètre défini, renvoyer **$false**. Sinon, retourne **$true**.

Le code suivant implémente la fonction de **Test-TargetResource** .

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to 
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result 
}
```

**Remarque**: pour faciliter le débogage, utilisez la cmdlet **Write-Verbose** dans votre implémentation de ces trois fonctions précédentes. Cette applet de commande écrit du texte dans le flux de message détaillé. Par défaut, le flux de message détaillé n’est pas affiché, mais vous pouvez l’afficher en changeant la valeur de la variable **$VerbosePreference** ou en utilisant le paramètre de **commentaires** dans les cmdlets DSC = nouveau.

### Création du manifeste de module

Enfin, utilisez l’applet de commande **New-ModuleManifest** pour définir un <ResourceName>fichier .psd1 de votre module de ressources personnalisée. Lorsque vous appelez cette cmdlet, faire référence au fichier de module (.psm1) de script décrit dans la section précédente. Inclure **Test-TargetResource** , **Set-TargetResource**et **Get-TargetResource**dans la liste des fonctions à exporter. Voici un exemple de fichier de manifeste.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```