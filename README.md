# Git commands

https://git-scm.com/book/fr/v2/Les-bases-de-Git-D%C3%A9marrer-un-d%C3%A9p%C3%B4t-Git

## Status
```sh
git status -short
git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
```
2 colonnes : à gauche => état de l'index :: à droite => état du dossier de travail

## Ignore
```sh
# pas de fichier .a
*.a

# mais suivre lib.a malgré la règle précédente
!lib.a

# ignorer uniquement le fichier TODO à la racine du projet
/TODO

# ignorer tous les fichiers dans le répertoire build
build/

# ignorer doc/notes.txt, mais pas doc/server/arch.txt
doc/*.txt

# ignorer tous les fichiers .txt sous le répertoire doc/
doc/**/*.txt
```

## Log
```sh
git log
git log -p -2
git log --stat
git log --pretty=oneline
git log --pretty=format:"%h - %an, %ar : %s"
git log --pretty=format:"%h %s" --graph
git log --since=2.weeks
```

## Configuration

List all config variables
```sh
git config --list
```

Set a config variable
```sh
git config --global user.name "John Doe"
```

Get a config variable
```sh
git config user.name
```

## Aide

Show help for commands
```sh
git help <command>
```

## Commandes basiques

Init a repo
```sh
git init
```

Add to working tree
```sh
git add <filename>
git add '*.txt'
git add .
```

Add and commit
```sh
git commit -a -m "my commit message"
```

Commit
```sh
git commit -m "my commit message"
```

Clone HTTPS
```sh
git clone https://github.com/project <foldername>
```

Clone SSH
```sh
git clone https://github.com/project <foldername>
```

Diff
git diff ne montre pas les modifications réalisées depuis la dernière validation — seulement les modifications qui sont non indexées
```sh
git diff
git diff --staged
git difftool --tool-help
```

Effacer des fichiers
```sh
git rm <filename>
git rm -f <filename>
git rm --cached <filename>
```

Déplacer des fichiers
```sh
git mv <filename> <newname>
```

Annuler des actions
```sh
git commit -m 'validation initiale'
git add fichier_oublie
git commit --amend
```

Désindexer un fichier déjà indexé
```sh
git reset HEAD <filename>
```

Réinitialiser un fichier modifié
```sh
git checkout -- <filename>
``` 

## Travailler avec des dépôts distants

Afficher les dépôts distants
```sh
git remote -v
```

Ajouter des dépôts distants
```sh
git remote add <name> <url>
```

Récupérer et tirer depuis des dépôts distants
```sh
git fetch <remote-name>
```

Pousser son travail sur un dépôt distant
```sh
git push <nom-distant> <nom-de-branche>
```

Inspecter un dépôt distant
```sh
git remote show <nom-distant>
```

Retirer et renommer des dépôts distants
```sh
git remote rename <old> <new>
git remote rm <name>
```

## Enregistrer des modifications dans le dépôt
![alt text](https://git-scm.com/book/en/v2/images/lifecycle.png "Git Lifecycle")

## Tags

Lister les étiquettes (tags)
```sh
git tag
```

Créer une étiquette annotée (tag
```sh
git tag -a <tagname> -m "mon message associé au tag"
git show <tagname>
```

Créer un tag après coup
```sh
git tag -a <tagname> <revision-id>
```

Partager des tags
```sh
git push <origin> <tagname>
git push <origin> --tags
```

Extraire un tag
```sh
git checkout -b <branchname> <tagname>
```

## Branches

Créer une branche
```sh
git branch <branchname>
git log --oneline --decorate
```

Extraire une branche
```sh
git checkout <branchname>
git log --oneline --decorate --graph --all
```

Shortcut
```sh
git checkout -b <branchname>
```

Effacer une branche
```sh
git branch -d <branchname>
```

Merger une branche
```sh
git checkout <branch-destination>
git merge <branch-source>
```

Merger une branche avec conflits
```sh
git checkout <branch-destination>
git merge <branch-source>
Auto-merging <file>
CONFLICT (content): Merge conflict in <file>
Automatic merge failed; fix conflicts and then commit the result.
git mergetool
...
git commit
```

Gestion des branches
```sh
git branch
git branch -v
git branch --merged
git branch --no-merged
git branch -vv
```

Gestion des branches distantes
```sh
(distant)/(branche) => origin/master (remote branch)
git fetch origin (synchroniser local et distant)
git push <remote-name> <branch-name> (push a local branch to remote)
git push <remote-name> <branch-name>:<branch-name-remote>
git checkout -b <branch-name> <remote-name>/<branch-name>
```

## Rebasing
Avec la commande rebase, vous pouvez prendre toutes les modifications qui ont été validées sur une branche et les rejouer sur une autre.
Rebaser rejoue les modifications d’une ligne de commits sur une autre dans l’ordre d’apparition, alors que la fusion joint et fusionne les deux têtes.

Gestion des branches
```sh
git checkout <branch-name-source>
git rebase <branch-name-destination>
Ne rebasez jamais des commits qui ont déjà été poussés sur un dépôt public
```
