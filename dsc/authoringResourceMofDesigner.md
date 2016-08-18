# À l’aide de l’outil Concepteur de ressources

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

L’outil Concepteur de ressources est un ensemble d’applets de commande exposés par le module **xDscResourceDesigner** qui facilitent la création de ressources de Windows PowerShell vous le souhaitez état Configuration (DSC). Les applets de commande dans cette ressource aident à créer le schéma MOF, le module de script et la structure de répertoires pour votre nouvelle ressource. Pour plus d’informations sur les ressources DSC, voir [Custom Windows PowerShell vous le souhaitez état Configuration les ressources de Build](authoringResource.md).
Dans cette rubrique, nous allons créer une ressource DSC qui gère les utilisateurs Active Directory.
Utilisez l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour installer le module **xDscResourceDesigner** .

>**Remarque**: **Install-Module** est incluse dans le module **PowerShellGet** , qui est inclus dans PowerShell 5.0. Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 [PackageManagement PowerShell Modules](https://www.microsoft.com/en-us/download/details.aspx?id=49186)aperçu.

## Création de propriétés de la ressource
La première chose à faire est de décider sur les propriétés qui expose la ressource. Cet exemple, nous allons définir un utilisateur Active Directory avec les propriétés suivantes.
 
Nom du paramètre Description
* **Nom d’utilisateur**: propriété qui identifie de manière unique un utilisateur de clé.
* **Assurez-vous que**: Spécifie si le compte d’utilisateur doit être présent ou Absent. Ce paramètre aura seulement deux valeurs possibles.
* **DomainCredential**: le mot de passe du domaine de l’utilisateur.
* **Le mot de passe**: le mot de passe pour l’utilisateur à autoriser une configuration changer le mot de passe si nécessaire.

Pour créer les propriétés, nous utilisons l’applet de commande **New-xDscResourceProperty** . Les commandes PowerShell suivantes créent les propriétés décrites ci-dessus.

```powershell
PS C:\> $UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
PS C:\> $Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
PS C:\> $DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
PS C:\> $Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## Création de la ressource

Maintenant que les propriétés de la ressource ont été créées, nous pouvons appeler la cmdlet **New-xDscResource** pour créer la ressource. L’applet de commande **New-xDscResource** prend la liste des propriétés en tant que paramètres. Il prend également le chemin d’accès où le module doit être créé, le nom de la nouvelle ressource et le nom du module dans lequel elle se trouve. La commande PowerShell suivante crée la ressource.

```powershell
PS C:\> New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

L’applet de commande **New-xDscResource** crée le schéma MOF, un script de ressource squelette, la structure de répertoires requis pour votre nouvelle ressource et un manifeste pour le module qui expose la nouvelle ressource.

Le fichier de schéma MOF est à **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**et son contenu est les suivantes.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
[Key] string UserName;
[Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
[Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
[Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

Le script de ressources est à **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Il n’inclut pas la logique réelle pour mettre en œuvre la ressource, vous devez ajouter vous-même. Le contenu du script squelette est les suivants :

```powershell
function Get-TargetResource
{
[CmdletBinding()]
[OutputType([System.Collections.Hashtable])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$returnValue = @{
UserName = [System.String]
Ensure = [System.String]
DomainAdminCredential = [System.Management.Automation.PSCredential]
Password = [System.Management.Automation.PSCredential]
}

$returnValue
#>
}


function Set-TargetResource
{
[CmdletBinding()]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."

#Include this line if the resource requires a system reboot.
#$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$result = [System.Boolean]

$result
#>
}


Export-ModuleMember -Function *-TargetResource
```

## Mise à jour de la ressource

Si vous souhaitez ajouter ou modifier la liste des paramètres de la ressource, vous pouvez appeler la cmdlet **Update-xDscResource** . L’applet de commande met à jour la ressource avec une nouvelle liste de paramètres. Si vous avez déjà ajouté une logique dans votre script de ressources, il reste intacte.

Par exemple, supposons que vous souhaitez inclure le dernier journal dans le temps à l’utilisateur dans notre ressource. Plutôt que l’écriture de la ressource à nouveau complètement, vous pouvez appeler la **New-xDscResourceProperty** pour créer la nouvelle propriété, puis appelez **xDscResource de mise à jour** et ajouter votre nouvelle propriété à la liste de propriétés.

```powershell
PS C:\> $lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
PS C:\> Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## Test d’un schéma de ressource

L’outil Concepteur de ressources expose une cmdlet plus qui peut être utilisée pour tester la validité d’un schéma MOF que vous avez écrit manuellement. Appelez l’applet de commande **Test-xDscSchema** , en passant le chemin d’accès d’un schéma de ressource MOF en tant que paramètre. L’applet de commande effectue la copie des erreurs dans le schéma.

### Voir aussi

#### Concepts
[Créer des ressources de Configuration d’état personnalisée Windows PowerShell que vous le souhaitez](authoringResource.md)

#### Autres ressources
[xDscResourceDesigner Module](https://powershellgallery.com/packages/xDscResourceDesigner)
