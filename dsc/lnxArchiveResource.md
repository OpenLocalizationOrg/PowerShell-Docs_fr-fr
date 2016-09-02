# DSC pour Linux nxArchive ressource

La ressource **nxArchive** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour décompresser les fichiers d’archives (.tar, .zip) sur un chemin spécifique sur un nœud de Linux.

## Syntaxe

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| SourcePath| Spécifie le chemin d’accès source du fichier d’archive. Il doit s’agir d’une .tar, .zip, ou. tar.gz fichier. | 
| DestinationPath| Spécifie l’emplacement où vous souhaitez vérifier que le contenu de l’archive est extraits.| 
| Somme de contrôle| Définit le type à utiliser pour déterminer si l’archive de code source a été mis à jour. Les valeurs sont : « ctime », « mtime », ou « md5 ». La valeur par défaut est « md5 ».| 
| Force| Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou de supprimer un répertoire qui n’est pas vide) provoquera une erreur. À l’aide de la propriété **Force** remplace ces erreurs. La valeur par défaut est **$false**.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant que cette ressource est configurée. Par exemple, si l' **ID de** la ressource configuration du bloc de script que vous souhaitez exécuter est tout d’abord **ResourceName** et son type est **ResourceType**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| Vérifiez| Détermine s’il convient de vérifier si le contenu de l’archive existe sur la **Destination**. Définir cette propriété pour la « présentation » pour garantir que le contenu existe. Définissez-la à « Absent » pour s’assurer qu’ils n’existent pas. La valeur par défaut est « Présent ».| 

## Exemple

L’exemple suivant montre comment utiliser la ressource **nxArchive** pour s’assurer que le contenu d’un fichier d’archive appelée `website.tar` existent et sont extraits à un emplacement de destination donné...

```
Import-DSCResource -Module nx 

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
} 
```
