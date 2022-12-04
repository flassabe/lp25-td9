# Manipulation du système de fichiers (suite)

Dans ce TP, nous allons poursuivre la manipulation du système de fichiers avec la création de répertoires, et la suppression de répertoires et de fichiers, ainsi que l'écriture non séquentielle de fichiers.

## Exercice 1 : création de répertoires

Pour cet exercice, vous devez écrire un programme nommé `my_mkdir` qui prend en paramètre le nom du répertoire à créer, et éventuellement le paramètre `-p`. Il est donc nécessaire de traiter séparément le cas où `argc` vaut 3 de celui où il vaut 2.

Le paramètre du répertoire à créer peut être un chemin complet, par exemple `Documents/LP25/TP4` Dans ce cas, il est nécessaire de tester le passage par les répertoires intermédiaires (vous pouvez utiliser la fonction `chdir` pour vous déplacer dans l'arborescence). Si le chemin jusqu'à la destination n'existe pas (dans l'exemple, si `Documents` ou `Documents/LP25` n'existe pas), le comportement du programme dépend de l'utilisation ou non de l'option `-p` :

- si l'option est absente, le programme échoue
- si l'option est présente, alors les répertoires intermédiaires manquants sont créés

Le programme crée ensuite le répertoire cible s'il n'a pas échoué à parcourir et/ou créer le chemin vers ce dernier.

Ce programme repose notamment sur la fonction `mkdir`.

## Exercice 2 : suppression de fichiers

Pour cet exercice, vous écrirez le programme `my_rm` qui prend un ou plusieurs paramètres. Ces paramètres sont des fichiers réguliers que le programme supprimera. Pour chaque fichier en paramètre, le programme teste son existence. Si le fichier existe, il le supprime, sinon il affiche un message d'erreur et passe au fichier suivant.

Pour cet exercice, vous utiliserez notamment la fonction `remove`.

## Exercice 3 : suppression de répertoires

Pour cet exercice, vous écrirez le programme `my_rmdir` qui prend en paramètre le nom d'un dossier à supprimer, ainsi que l'option facultative `-r`. Le programme supprime le dossier cible :

- s'il existe et qu'il est vide et que l'option `-r` n'est pas active
- s'il existe et que l'option `-r` est active, auquel cas, il supprime récursivement le contenu du dossier cible.

Si l'option `-r` est active, vous devez demander confirmation à l'utilisateur qu'il veut supprimer le répertoire cible.

Pour cet exercice, vous utiliserez notamment la fonction `rmdir`.

## Exercice 4 - création de FIFO

Une FIFO est une interface permettant de transmettre des informations entre une entrée et une sortie. La FIFO soit son nom à l'ordre des messages : _First In, First Out_, c'est à dire que le premier élément entré est le premier élément sorti (donc les informations sont reçues dans le même ordre qu'elles ont été transmises).

Pour cet exercice, vous devez créer une FIFO et tester son usage. Le premier programme, nommé `fifo-read.c` crée la FIFO et y lit. Vous utiliserez pour celà la fonction `mkfifo` (voir `man 3 mkfifo` pour les détails d'usage de la fonction). Le mode de création peut être défini en octal ou par des combinaisons de flags comme :

- `S_IRUSR` : droit de lecture pour le propriétaire
- `S_IWUSR` : droit d'écriture pour le propriétaire
- `S_IXUSR` : droit d'exécution pour le propriétaire
- `S_IRGRP` : droit de lecture pour le groupe
- `S_IWGRP` : droit d'écriture pour le groupe
- `S_IXGRP` : droit d'exécution pour le groupe
- `S_IROTH` : droit de lecture pour les autres
- `S_IWOTH` : droit d'écriture pour les autres
- `S_IXOTH` : droit d'exécution pour les autres

Pour tester le fonctionnement de votre fonction, vous écrirez un second programme, `fifo-write.c`, qui ouvre la FIFO en écriture et y écrit ce qui est saisi par l'utilisateur. Ce qui est écrit dans la FIFO doit être reçu et affiché par le programme de création de la FIFO. Vous devrez ouvrir 2 terminaux pour lancer un des programmes dans chaque terminal.

## Bilan

Dans ce TD, vous avez eu l'occasion de prendre en main les fonctions C :

- `chdir` : pour se déplacer dans l'arborescence, comme la commande shell `cd`
- `mkdir` : pour créer un répertoire
- `remove` : pour supprimer un fichier, comme la commande shell `rm`
- `rmdir` : pour supprimer un dossier vide
- `mkfifo` : pour créer une FIFO
