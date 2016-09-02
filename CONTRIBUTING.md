# Qui contribuent à la Documentation PowerShell

## Signer un CLA

Vous pouvez contribuer à tous les référentiels PowerShell, vous devez [signer un Microsoft Contribution licences contrat CLA ()](https://cla.microsoft.com/). Si vous avez déjà impliquées dans le cas de référentiels PowerShell dans le passé, Félicitations ! Vous avez déjà effectué cette étape.

## Rédiger une documentation PowerShell

Un des moyens plus simples à contribuer à PowerShell est en vous aidant à écrire et modifier la documentation. Ensemble de notre documentation hébergée sur des référentiels est écrite à l’aide de [Promotions AROMATISES référentiels](https://help.github.com/articles/github-flavored-markdown/).

Pour [Modifier un fichier existant](https://help.github.com/articles/editing-files-in-another-user-s-repository/), simplement naviguer vers cette dernière et cliquez sur le bouton « Modifier ». Référentiels créera automatiquement votre propre branche de notre référentiel où vous pouvez effectuer vos modifications. Une fois que vous avez terminé, enregistrez vos modifications et soumettre une demande d’extraction pour obtenir vos modifications fusionnées en amont. Une fois votre pull demande est créé, 

Si vous souhaitez contribuer nouvelle documentation, d’abord vérifier [les problèmes marqués comme étant « en cours »](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress) pour vous assurer que vous n'êtes pas dupliquer les efforts.
Si aucun participant ne semble pas fonctionner sur ce que vous avez planifié :
* Ouvrir un nouveau problème marqué comme étant « en cours » pour leur indiquer ce que vous travaillez sur
* Créer une branche de notre référentiel et commencer à ajouter la nouvelle documentation basée sur les promotions lui
* Lorsque vous êtes prêt à votre documentation de collaboration, soumettre une demande de type pull vers la branche *principale*

#### Référentiels AROMATISES promotions (GFM)

Tous les articles de ce référentiel utilisent des [Référentiels AROMATISES promotions (GFM)](https://help.github.com/articles/github-flavored-markdown/).

Si vous recherchez un bon éditeur, essayez de [Promotions pavé](http://markdownpad.com/) ou référentiels fournit également une interface web pour la modification des promotions avec mise en surbrillance de la syntaxe et la possibilité d’afficher un aperçu des modifications. 

Partie de la syntaxe GFM plus simple comprend :

* **Différences par rapport aux paragraphes, les sauts de ligne :** Dans les promotions il n’existe pas de code HTML `<br />` ou `<p />` élément. En revanche, un nouveau paragraphe est désigné par une ligne vide entre les deux blocs de texte.

> **Remarque**: ajoutez un saut de ligne unique après chaque phrase afin de simplifier la sortie de ligne de commande de diffs et de l’historique.
Cela n’est pas actuellement adoptée dans l’ensemble de documents de PowerShell, mais nous travaillerez sur cette voie au fil du temps. N’hésitez pas à aider. 

* **Italique :** Le code HTML `<em>some text</em>` est écrit en tant que `*some text*`
* **Gras :** Le code HTML `<strong>some text</strong>` élément est écrit en tant que `**some text**`
* **Titres :** Les en-têtes HTML sont désignés à l’aide de `#` caractères au début de la ligne. Le nombre de `#` caractères correspond au niveau hiérarchique de l’en-tête (par exemple, `#` = `<h1>` et `###` = ```<h3>```).
* **Listes numérotées :** Pour émettre une liste numérotée (ordonnée) commencer la ligne avec `1. `.  
Si vous souhaitez que plusieurs éléments dans un élément de liste unique, mettre votre liste comme suit :
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
Pour obtenir ce résultat :

1.  Pour le premier élément (tel que celui-ci), insérez un taquet de tabulation la valeur 1. 

    Pour inclure un deuxième élément (tel que celui-ci), insérez un saut de ligne après la première et aligner les retraits.

* **Des listes à puces :** Les listes à puces (non ordonnés) sont pratiquement identiques aux listes ordonnées, hormis le fait que les `1. ` est remplacée par `* `, `- `, ou `+ `. Plusieurs listes élément fonctionnent de la même manière à l’instar des listes ordonnées.
* **Liens :** La syntaxe d’un lien hypertexte est `[visible link text](link url)`.
Liens peuvent aussi avoir des références, qui seront abordés dans la section « Références d’Image et de lien » ci-dessous.