# Création d’une ressource DSC C#

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

En règle générale, une ressource personnalisée Windows PowerShell vous le souhaitez état Configuration (DSC) est implémentée dans un script PowerShell. Toutefois, vous pouvez également implémenter la fonctionnalité d’une ressource personnalisée DSC en écrivant les applets de commande en c#. Pour obtenir une introduction sur les applets de commande en c#, consultez [écriture d’une applet de commande Windows PowerShell](https://technet.microsoft.com/en-us/library/dd878294.aspx).

Outre l’implémentation de la ressource en c# comme des applets de commande, le processus de création du schéma MOF, création de la structure de dossiers, importation et à l’aide de la ressource DSC personnalisée sont identique à celle décrite dans [l’écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md).

## Écriture d’une ressource basée sur l’applet de commande
Cet exemple, nous avons implémenterez une ressource simple qui gère un fichier texte et son contenu.

### Écriture du schéma MOF

Voici la définition de ressource MOF.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### Configuration du projet Visual Studio
#### Configuration d’un projet de l’applet de commande

1. Ouvrez Visual Studio.
1. Créez un projet c# et fournir le nom.
1. Sélectionnez **Bibliothèque de classes** dans les modèles de projet disponibles.
1. Cliquez sur **Ok**.
1. Ajoutez une référence d’assembly à System.Automation.Management.dll à votre projet.
1. Modifiez le nom de l’assembly pour correspondre au nom de la ressource. Dans ce cas, l’assembly doit être nommé **MSFT_XDemoFile**.

### Écriture du code de l’applet de commande

Le code c# suivant implémente les applets de commande **Get-TargetResource**, **Set-TargetResource**et **Test-TargetResource** .

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
           } 
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
        [Parameter(Mandatory = true)]
        public string Path { get; set; }
 
        [Parameter(Mandatory = false)]
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }
 
        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### Déploiement de la ressource

Le fichier dll compilées doit être enregistré dans une structure de fichier similaire à une ressource basée sur un script. Voici la structure de dossiers pour cette ressource.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### Voir aussi
#### Concepts
[Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)
#### Autres ressources
[Écriture d’une applet de commande Windows PowerShell](https://msdn.microsoft.com/en-us/library/dd878294.aspx)