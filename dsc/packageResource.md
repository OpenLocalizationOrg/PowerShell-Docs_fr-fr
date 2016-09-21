# Ressource de Package DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource de **Package** dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour installer ou désinstaller des packages, tels que les packages Windows Installer et setup.exe, sur un nœud cible.

## Syntaxe

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Nom| Indique le nom du package pour lequel vous voulez vous assurer un état spécifique.| 
| Chemin d’accès| Indique le chemin d’accès où se trouve le package.| 
| ID de produit| Indique l’ID de produit qui identifie de façon unique le package.| 
| Arguments| Chaîne d’arguments qui seront passées au lot exactement comme dans les listes.| 
| Informations d’identification| Permet d’accéder au package sur une source à distance. Cette propriété n’est pas utilisée pour installer le package. Le package est toujours installé sur le système local.| 
| Garantir| Indique si le package est installé. Définir cette propriété à « Absent » pour garantir que le package n’est pas installé (ou désinstaller le package si elle est installée). Configurer « Présenter » (la valeur par défaut) pour vous assurer que le package est installé.| 
| Journaux| Indique le chemin d’accès complet où vous souhaitez que le fournisseur d’enregistrer un fichier journal pour installer et désinstaller le package.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est **ResourceName** et son type est le **type de ressource**, la syntaxe pour l’utilisation de cette propriété est « DependsOn = « [du type de ressource] ResourceName » « ».| 
| Code retour| Indique le code de retour attendu. Si le rendement effectif code ne correspond pas à que la valeur attendue fournies ici, que la configuration renverra une erreur.| 

## Exemple

Cet exemple exécute le programme d’installation .msi se trouve à l’emplacement spécifié et dont l’ID de produit spécifié.

```powershell
Package PackageExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path  = "$Env:SystemDrive\TestFolder\TestProject.msi"
    Name = "TestPackage"
    ProductId = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
} 
```
