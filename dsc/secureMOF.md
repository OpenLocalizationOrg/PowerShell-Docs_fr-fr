# Sécurisation du fichier MOF

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

DSC indique les nœuds cible quelle configuration elles doivent avoir en envoyant un fichier MOF avec ces informations à chaque nœud, lorsque le Gestionnaire de Configuration Local (PPCM) met en œuvre la configuration de votre choix. Étant donné que ce fichier contient les détails de la configuration, il est important de maintenir sécurisée. Pour ce faire, vous pouvez définir le Gestionnaire de Configuration Local pour vérifier les informations d’identification d’un utilisateur. Cette rubrique décrit comment transmettre les informations d’identification en toute sécurité sur le nœud cible en les chiffrant avec des certificats.

## Conditions préalables

Pour chiffrer correctement les informations d’identification utilisées pour une configuration DSC sécurisée, vérifiez que vous disposez des éléments suivants :

* **Certains moyens d’émission et la distribution de certificats**. Cette rubrique et ses exemples part du principe que vous utilisez une autorité de Certification Active Directory. Pour plus d’informations sur les Services de certificat Active Directory, voir [Présentation des Services de certificat Active Directory](https://technet.microsoft.com/library/hh831740.aspx) et de [Services de certificat Active Directory dans Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Accès comme administrateur aux nœuds appropriés cible**.
* **Chaque nœud cible dispose d’un certificat de chiffrement compatibles avec enregistré son magasin personnel**. Dans Windows PowerShell, le chemin d’accès au magasin est certificat : \LocalMachine\My. Les exemples dans cette rubrique utilisent le modèle « authentification de poste de travail », que vous pouvez trouver (ainsi que d’autres modèles de certificats) auprès de [Modèles de certificats par défaut](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Si vous comptez cette configuration en cours d’exécution sur un ordinateur autre que le nœud cible, **Exporter la clé publique du certificat**et importez-le sur l’ordinateur que vous exécutez la configuration à partir de. Vérifiez que vous exportez uniquement la clé **publique** ; maintenir la sécurité de la clé privée.

## Processus global

1. Configurer les certificats, les clés et les empreintes, de s’assurer que chaque nœud cible a copies du certificat et l’ordinateur de configuration comporte la clé publique et l’empreinte numérique.
1. Créer un bloc de données de configuration qui contient le chemin d’accès et l’empreinte numérique de la clé publique.
1. Créer un script de configuration qui définit la configuration de votre choix pour le nœud cible et configure déchiffrement sur les nœuds cible par la Configuration locale d’exécution des commandes gestionnaire pour déchiffrer les données de configuration en utilisant le certificat et son empreinte.
1. Exécutez la configuration, qui sera définir les paramètres du Gestionnaire de Configuration locale et démarrer la configuration DSC.

## Données de configuration

Le bloc de données de configuration définit les nœuds cible à traiter, s’il faut ou non pour chiffrer les informations d’identification, les moyens de chiffrement et d’autres informations. Pour plus d’informations sur le bloc de données de configuration, consultez [Configuration séparer et données d’environnement](configData.md).

Cet exemple montre un bloc de données de configuration qui spécifie un nœud cible pour agir sur targetNode nommée, le chemin vers le fichier de certificat de clé publique (nommé targetNode.cer) et l’empreinte numérique pour la clé publique.

```powershell
$ConfigData= @{ 
    AllNodes = @(     
            @{  
                # The name of the node we are describing 
                NodeName = "targetNode" 

                # The path to the .cer file containing the 
                # public key of the Encryption Certificate 
                # used to encrypt credentials for this node 
                CertificateFile = "C:\publicKeys\targetNode.cer" 

         
                # The thumbprint of the Encryption Certificate 
                # used to decrypt the credentials on target node 
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8" 
            }; 
        );    
    }
```

## Script de configuration

Dans le script de configuration lui-même, utilisez la `PsCredential` paramètre pour vous assurer que les informations d’identification sont stockées pour les délais. Lorsque vous exécutez l’exemple fourni, DSC vous invite à entrer les informations d’identification et puis chiffrer le fichier MOF à l’aide de la CertificateFile est associé au nœud cible dans la plage de données de configuration. Cet exemple de code copie un fichier à partir d’un partage sécurisée à un utilisateur.

```
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
    } 
}
```

## La configuration de déchiffrement

Avant de `Start-DscConfiguration` peuvent fonctionner, vous devez indiquer le Gestionnaire de Configuration Local sur chaque nœud cible le certificat à utiliser pour déchiffrer les informations d’identification, à l’aide de la ressource CertificateID pour vérifier l’empreinte du certificat. Cet exemple de fonction recherche le certificat local approprié (vous devrez peut-être le personnaliser afin qu’il recherche le certificat exact que vous souhaitez utiliser) :

```powershell
# Get the certificate that works for encryption 
function Get-LocalEncryptionCertificateThumbprint 
{ 
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid 
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify()) 
        { 
            return $_.Thumbprint 
        } 
    } 
}
```

Avec le certificat identifié par son empreinte, le script de configuration pouvant être mis à jour pour utiliser la valeur :

```powershell
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
        
        LocalConfigurationManager 
        { 
             CertificateId = $node.Thumbprint 
        } 
    } 
}
```

## La configuration en cours d’exécution

À ce stade, vous pouvez exécuter la configuration, qui aura pour résultat deux fichiers :

* Un *. meta.mof fichier qui configure le Gestionnaire de Configuration Local pour déchiffrer les informations d’identification en utilisant le certificat qui est stocké dans le magasin de l’ordinateur local et identifié par son empreinte. Définir DscLocalConfigurationManager s’applique la *. meta.mof fichier.
* Un fichier MOF qui applique réellement la configuration. Démarrage DscConfiguration applique la configuration.

Ces commandes effectuerez ces étapes :

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Voici un exemple complet qui comprend toutes ces étapes, ainsi qu’une applet de commande d’assistance qui exporte et copie les clés publiques :

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )
    

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }
        
        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key 
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"         

    $ConfigData=    @{
        AllNodes = @(     
                        @{  
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );    
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration") 

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer") 

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}
```