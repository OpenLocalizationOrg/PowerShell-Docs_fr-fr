# DSC pour Linux nxSshAuthorizedKeys ressource

La ressource **nxAuthorizedKeys** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour gérer autorisés ssh clés pour un utilisateur spécifié.

## Syntaxe

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| KeyComment| Un commentaire unique pour la clé. Il est utilisé pour identifier les clés.| 
| Garantir| Indique si la clé est définie. Définir cette propriété à « Absent » pour garantir que la clé n’existe pas dans le fichier l’utilisateur clés autorisés. Configurer une présentation « » pour garantir que la clé est définie dans le fichier de clé autorisé de l’utilisateur.| 
| Nom d’utilisateur| Le nom d’utilisateur pour gérer ssh autorisé clés pour. Si ne pas défini, l’utilisateur par défaut est « root ».| 
| Clé| Le contenu de la clé. Ceci est nécessaire si **s’assurer** qu’est défini sur « Heure actuelle ».| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l' **ID** du bloc de script de configuration de ressources que vous voulez exécuter tout d’abord est **ResourceName** et son type est le **type de ressource**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

L’exemple suivant définit un public ssh autorisé clés pour l’utilisateur « monuser ».

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```

