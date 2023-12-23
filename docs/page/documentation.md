> Pour rédiger la documentation on utilise `MkDocs`, pour l'installation et l'utilisation vous pouvais suivre directement leur [documentation](https://www.mkdocs.org/getting-started/).

## Mise en page
On utilse ici le `markdown` pour rédiger la documentation. On va donc faire une liste des choses savoir pour le rédaction en markdown. Dans un premier temps l'extension des fichier sera `.md`.

- **Titres :** Vous pouvez créer un titre en utilisant le symbole `#`. Plus il y a de symboles `#`, plus le titre est petit. Par exemple :
```markdown
# Titre de niveau 1
## Titre de niveau 2
### Titre de niveau 3
```
- **Paragraphes :** Pour créer un paragraphe, il suffit d'écrire du texte. Pour créer un nouveau paragraphe, laissez une ligne vide.
- **Paragraphes avec indentation :** Pour créer un paragraphe avec indentation, il suffit de mettre un `>` devant le texte. Par exemple :
```markdown
> Ceci est un paragraphe avec indentation.
```
- **Autre type de paragraphe :** Pour créer un paragraphe avec un autre type de paragraphe, il suffit de faire `tab` avant chaque ligne. Par exemple :
```markdown
    Ceci est un paragraphe avec un autre type de paragraphe.
```
- **Saut a la ligne :** Pour passer a la ligne suivante il suffie de mettre **2** espace a la fin de la ligne.
- **Liens :** Pour créer un lien, utilisez la syntaxe `[texte du lien](URL)`. Par exemple :
```markdown
[Google](https://www.google.com)
```
- **Images :** Pour insérer une image, utilisez la syntaxe `![texte alternatif](URL)`. Par exemple :
```markdown
![Logo Google](https://www.google.com/images/logo.png)
```
- **Listes :** Pour créer une liste à puces, utilisez le symbole `*` ou `-`. Pour une liste numérotée, utilisez `1.`, `2.`, etc. Par exemple :
```markdown
* Élément 1
* Élément 2

1. Élément 1
2. Élément 2
```
- **Texte en gras :** Pour mettre du texte en gras, entourez-le de deux astérisques `**` ou de deux tirets bas `__`. Par exemple :
```markdown
**texte en gras**
__autre texte en gras__
```
- **Texte en italique :** Pour mettre du texte en italique, entourez-le d'un astérisque `*` ou d'un tiret bas `_`. Par exemple :
```markdown
*texte en italique*
_autre texte en italique_
```
- **Code :** Pour afficher du code, utilisez les accents graves `` ` ``. Pour un bloc de code, utilisez trois accents graves. Par exemple :
```markdown
`code inline`
```
Bloc de code :
```markdown
    ```{langage-du-code}
    Le code en bloc 
    ```
```

- **Tableau** : Pour créer un tableau, utilisez la syntaxe suivante :
```markdown
| Titre 1 | Titre 2 |
|---------|---------|
| Ligne 1 | Ligne 2 |
| Ligne 3 | Ligne 4 |
```
Ce qui donne :     

| Titre 1 | Titre 2 |
|---------|---------|
| Ligne 1 | Ligne 2 |
| Ligne 3 | Ligne 4 |

## Gestion des dossier et des fichiers
Pour l'organisation des fichier on a donc le dossier `./documents` qui va contenir tout les documents qui vont être disponible sur la documentation, un dossier `./img` qui va contenir les images qui vont être utilisé dans la documentation et un dossier `./page` qui va contenir les pages de la documentation ici elle vont être organiser en fonction de l'arboressence de la documentation.
Pour avoir alors une organisation plus claire on va alors organiser en sous dossier les documents en fonction des thème ou page lier selon se qui convient le mieux.

## Thême 
Le thême utiliser ici est le thême [`material`](https://github.com/squidfunk/mkdocs-material) qui peut être installer avec `pip install mkdocs-material`. Leur [docummentation](https://squidfunk.github.io/mkdocs-material/) permet d'ajouter un certain nombre d'option en plus de celle de base de `mkdocs` qui permet de personnaliser la documentation.

## Bouton 
Pour réaliser un bouton on utilise la syntaxe suivante : 
```markdown
[test](./test.md){ .md-button }
```

## Hébergement en local avec docker 
On va donc utilise ici le docker qui nous fornie par [`material`](https://github.com/squidfunk/mkdocs-material), pour sa on utilise documentation de [`squidfunk/mkdocs-material`](https://hub.docker.com/r/squidfunk/mkdocs-material).  
Pour l'installation on utilise la commande : `docker pull squidfunk/mkdocs-material`
Pour lancer le docker on utilise la commande : `docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material`