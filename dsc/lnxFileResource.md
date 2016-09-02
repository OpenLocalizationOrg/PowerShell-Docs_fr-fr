# DSC pour Linux nxFile ressource

La ressource **nxFile** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour gérer les fichiers et répertoires sur un nœud de Linux.

## Syntaxe

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| DestinationPath| Spécifie l’emplacement où vous souhaitez vérifier l’état d’un fichier ou un répertoire.| 
| SourcePath| Spécifie le chemin d’accès à partir de laquelle copier la ressource de fichier ou un dossier. Ce chemin d’accès peut être un chemin d’accès local, ou un `http/https/ftp` URL. Remote `http/https/ftp` URL sont uniquement pris en charge lorsque la valeur de la propriété **Type** est fichier.| 
| Vérifiez| Détermine s’il convient de vérifier si le fichier existe. Définir cette propriété à « Présent » pour s’assurer que du fichier existe. Définissez-la à « Absent » pour garantir que le fichier n’existe pas. La valeur par défaut est « Présent ».| 
| Type| Indique si la ressource en cours de configuration est un répertoire ou un fichier. Définir cette propriété à « répertoire » pour indiquer que la ressource est un répertoire. Définissez-la à « fichier » pour indiquer que la ressource est un fichier. La valeur par défaut est « fichier »| 
| Contenu| Spécifie le contenu d’un fichier, telle qu’une chaîne particulière.| 
| Somme de contrôle| Définit le type à utiliser pour déterminer si les deux fichiers sont les mêmes. Si la **somme de contrôle** n’est pas spécifié, que le nom de fichier ou répertoire est utilisé pour la comparaison. Les valeurs sont : « ctime », « mtime », ou « md5 ».| 
| Recurse| Indique si les sous-répertoires sont inclus. Définir cette propriété sur **$true** pour indiquer que vous souhaitez sous-répertoires à inclure. La valeur par défaut est **$false**. **Remarque :** Cette propriété est valide uniquement lorsque la propriété **Type** est définie au répertoire.| 
| Force| Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou de supprimer un répertoire qui n’est pas vide) provoquera une erreur. À l’aide de la propriété **Force** remplace ces erreurs. La valeur par défaut est **$false**.| 
| Liens| Spécifie le comportement de votre choix pour les liens symboliques. Définir cette propriété à « suivre » pour suivre les liens symboliques et agir sur la cible de liens (par exemple. Copiez les fichiers au lieu de la liaison). Définir cette propriété à « gérer » agir sur le lien (par exemple. Copiez le lien lui-même). Définir cette propriété à « ignorer » pour ignorer les liens symboliques.| 
| Group| Nom du **groupe** propriétaire du fichier ou un répertoire.| 
| Mode| Spécifie les autorisations souhaitées pour la ressource, dans la notation octale ou symbolique. (par exemple, 777 ou rwxrwxrwx). Si vous utilisez la notation symbolique, ne fournissent pas le premier caractère qui désigne un répertoire ou un fichier.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant que cette ressource est configurée. Par exemple, si l' **ID de** la ressource configuration du bloc de script que vous souhaitez exécuter est tout d’abord **ResourceName** et son type est **ResourceType**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Informations supplémentaires


Linux et Windows utilisent des caractères de saut de ligne différents dans des fichiers texte par défaut, et cela peut entraîner des résultats inattendus lorsque vous configurez certains fichiers sur un ordinateur Linux avec __nxFile__. Il existe plusieurs manières de gérer le contenu d’un fichier de Linux tout en évitant les problèmes causés par les caractères de saut de ligne inattendus :

Étape 1 : Copier le fichier à partir d’une source distante (http, https ou ftp) : créez un fichier sur Linux avec le contenu de votre choix et préparer l’ou les nœuds, vous allez configurer sur un serveur web ou ftp accessible. Définissez la propriété __SourcePath__ dans la ressource __nxFile__ avec le site web ou ftp URL vers le fichier.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    
}
        
}
```


Étape 2 : Lire le contenu du fichier dans le script PowerShell avec [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) après la définition de la propriété __$OFS__ d’utiliser le caractère de saut de ligne Linux.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = "$Contents"
}

}
```


Étape 3 : Utiliser une fonction de PowerShell pour remplacer les sauts de ligne Windows avec des caractères de saut de ligne de Linux.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = $Contents
    
}
}
```

## Exemple

L’exemple suivant vérifie que le répertoire `/opt/mydir` existe, et l’existence d’un fichier avec le contenu spécifié ce répertoire...

```
Import-DSCResource -Module nx 

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@ 
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```

