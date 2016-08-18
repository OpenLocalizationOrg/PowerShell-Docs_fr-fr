# Ressource de fichier de DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource de fichier dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour gérer les fichiers et dossiers sur le nœud cible.

## Syntaxe
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ] 
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ] 
    [ MatchSource = [bool] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| DestinationPath| Indique l’emplacement où vous souhaitez vérifier l’état d’un fichier ou un répertoire.| 
| Attributs| Spécifie l’état souhaité d’attributs pour le fichier cible ou un répertoire.| 
| Somme de contrôle| Indique le type de somme de contrôle à utiliser pour déterminer si les deux fichiers sont les mêmes. Si la __somme de contrôle__ n’est pas spécifié, que le nom de fichier ou répertoire est utilisé pour la comparaison. Les valeurs valides sont : SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.| 
| Contenu| Spécifie le contenu d’un fichier, par exemple une chaîne particulière.| 
| Credential| Indique les informations d’identification qui sont nécessaires pour accéder aux ressources, tels que les fichiers de code source, si ce type d’accès est requis.| 
| Vérifiez| Indique si le fichier ou le répertoire existe. Définir cette propriété à « Absent » pour s’assurer que le fichier ou répertoire n’existe pas. Affectez-lui « Présent » pour s’assurer que le fichier ou répertoire n’existe pas. La valeur par défaut est « Présent ».| 
| Force| Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou de supprimer un répertoire qui n’est pas vide) provoquera une erreur. À l’aide de la propriété Force remplace ces erreurs. La valeur par défaut est __$false__.| 
| Recurse| Indique si les sous-répertoires sont inclus. Définir cette propriété sur __$true__ pour indiquer que vous souhaitez sous-répertoires à inclure. La valeur par défaut est __$false__. **Remarque**: cette propriété n’est valide que lorsque la propriété Type est définie au répertoire.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous souhaitez exécuter est tout d’abord __ResourceName__ et son type est __ResourceType__, la syntaxe d’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| SourcePath| Indique le chemin d’accès à partir de laquelle copier la ressource de fichier ou un dossier.| 
| Type| Indique si la ressource en cours de configuration est un répertoire ou un fichier. Définir cette propriété à « Répertoire » pour indiquer que la ressource est un répertoire. Définissez-la sur « Fichier » pour indiquer que la ressource est un fichier. La valeur par défaut est « Fichier ».| 
| MatchSource| Si défini sur __$false__la valeur par défaut, puis tous les fichiers sur la source (par exemple, les fichiers A, B et C) seront ajoutés à la destination de la première fois que la configuration est appliquée. Si un nouveau fichier (D) est ajouté à la source, il ne sera pas ajoutée à la destination, même lorsque la configuration est appliquée renouveler ultérieurement. Si la valeur est __$true__, puis chaque fois que la configuration est appliquée, nouveaux fichiers trouvés par la suite sur la source (tel que le fichier D dans cet exemple) sont ajoutés à la destination.| 

## Exemple

L’exemple suivant montre comment utiliser la ressource de fichier pour vérifier qu’un répertoire avec le chemin d’accès `C:\Users\Public\Documents\DSCDemo\DemoSource` sur une source d’ordinateur (par exemple, le serveur de « pull ») est également présent (ainsi que tous les sous-répertoires) sur le nœud cible. Il écrit un message de confirmation dans le journal lorsque vous avez terminé et comprend une instruction pour vous assurer que l’opération de vérification des fichiers s’exécute avant l’opération de journalisation.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```
