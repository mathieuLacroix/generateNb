# generateNb

Script python pour générer les notebooks pour l'iut de Villetaneuse.

Le script prend en paramètre un notebook et utilise les tags des cellules pour générer les notebooks, latex et pdf correspondants (suivant les options du script).

## Tags

Pour personnaliser les différentes versions du notebook (selon si on génère une version corrigée, pour les étudiants, un pdf, etc), on utilise des tags.

**Remarque :** pour éditer les tags `Menu -> Affichage -> Barre d'outils de cellules -> Tags`. Pour ajouter un tag à une cellule, il faut saisir le tag et cliquer sur "Ajouter un mot clé".

Les tags utilisés sont :
- `answer` : indique que la cellule (de code ou de markdown) est une réponse à un exercice. Dans la version générée pour les étudiants, le contenu de cette cellule sera supprimée. Un en-tête "Correction" sera ajouté avant dans la version corrigée.

- `keepOutput` :  par défaut, tous les outputs sont supprimés. Si c'est important de le garder (c'est une figure générée par exemple), on met ce tag (Si l'output d'une réponse d'un TD ou TP, il sera quand même supprimé pour les versions pour les étudiants)

- `removeFromLatex` : pour supprimer les cellules dans le document latex (essentiellement pour les cellules contenant les imports inutiles pour le TD par exemple).

- `removeFromStudent` : pour supprimer certaines cellules dans le notebook pour les étudiants (essentiellement pour les corrections contenant une archive et dont la réponse ne peut être écrite directement dans le notebook (création de package par exemple))

- `comment` : pour ajouter des commentaires sur le notebooks (ce qu'il faut changer, etc). Les cellules taggées avec `comments` sont supprimées lors de la génération.

## Règles à suivre

- Pour chaque chapitre, les images doivent être dans un répertoire `img` et les fichiers additionnels dans un répertoire `files`.

-  Les noms des fichiers doivent contenir `_origin` à la fin et suivre les règles de l'année dernière. Par exemple, les noms des notebooks pour le chapitre 1 doivent être :
    - cours1_origin.ipynb
    - td1_origin.ipynb
    - tp1_origin.ipynb
    - fiche_origin.ipynb
    - répertoire img (optionnel)
    - répertoire file (optionnel)

- Le titre du TD doit être "TD . : titre du td" (où . est remplacé par le numéro). Par exemple : "TD 1 : Complexité". De plus, le titre ne doit pas contenir "center". En markdown, cela fait  "# TD 1 : Complexité".

- Idem pour le titre du TP.

- Le titre du cours est "Chapitre . : titre du cours". Par exemple "# Chapitre 1 : Complexité"

- Pour les TD et TP :
    - les exercices sont des titres de niveau 2 ("## Exercice 1 : Afficher hello world" par exemple)
    - les questions des exercices sont des titres de niveau 3 ("### Question 1" par exemple)


## Utilisation du script

Liste des options :

* `-c` : crée une copie clean (supprime les outputs, etc)
* `-s` : crée une version pour les étudiants
* `-t` : crée une version corrigée
* `-l` : crée le document latex associé
* `-p` : crée le document pdf associé (à partir du latex)
* `-o` : pour indiquer un répertoire de sortie (où seront mis les documents)

Par exemple, pour générer tous les documents pour le chapitre 1 :
```bash
./generateNb cours1_origin.ipynb -cp
./generateNb td1_origin.ipynb -stp
./generateNb tp1_origin.ipynb -st
```
