# Comment utiliser Git
Une démonstration de l'utilisation de Git avec Github. Ce projet vous permet de prendre en main rapidement Git en association avec Github.
Les commandes sont directement saisies dans une console. J'utilise terminal sur MAC OS X.

Je liste les commandes de base. Il existe des commandes plus complexes. Des options peuvent être ajoutées aux commandes de base.


## Mémento des principales commandes Git
- **git init :** initialisation d'un projet (si le projet est créé depuis github, ne pas utiliser cette commande) ou réinitialisation d'un projet existant
- **git status :** vérifier le statut, l'état (si modification de fichier) du répertoire de travail (le repository)
- **git add nom_du_fichier :** ajoute un nouveau fichier (du répertoire de travail) à l'index
- **git commit -m "Phrase_explication_détaillée_du_commit" :** Ajouter les fichiers de l'index dans un commit
- **git commit -am "Phrase_explication" :** ajouter les fichiers au repositery, directement sans le add si le fichier est déjà ajouté - update de fichiers
- **git log :** Voir l'historique des modifications du commit sous forme de liste
- **git checkout sha_du_commit :** se positionner sur un ancien commit - attention le retour à un commit efface les commits les plus récents - si push après retour
- **git checkout master :** retour au commit principal - le dernier
- **git clone https_ssh_adresse_du_repositery_github :** rapatrier / clôner les sources d'un remote github vers un ordinateur local
- **git push origin master :** envoyer les modifications des fichiers (le commit) vers github (le remote)
- **git pull origin master :** récupérer les modifications effectuées par d'autres développeurs sur un remote
- **git pull url_du_repositery :** récupérer les fichiers d'initialisation en local après la création d'un repositery distant
- **git branch nom_de_la_branche :** créer une branche
- **git checkout nom_de_la_branche_créée :** se positionner sur la branche créée (raccourci de création)
- **git checkout -b nom_de_la_branche :** créer une branche et se positionner sur la branche créée
- **git push --set-upstream origin branche-test-01 :** envoyer la branche créée sur le remote Github
- **git push :** envoyer les commit dans la branche créée sur le remote (possibilité d'ommettre origin et nom_de_la_branche)
- **git merge nom_de_la_branche_à_fusionner :** fusionner les modifications de 2 branches, ici positionné sur master, la branche "nom_de_la_branche_à_fusionner" va fusionner avec la branche master. Attention, rien n'empêche de fusionner master avec une branche secondaire en se positionnant sur une branche secondaire et en codant -> git merge master. Merge ne supprime la branche
- **git branch -d nom_de_la_branche_à_supprimer :** supprimer une branche en local
- **git push origin :nom_de_la_branche_à_supprimer :** supprimer une branche sur le remote github (distante)
- **git blame nom_du_fichier_à_vérifier :** savoir qui a modifié une ligne de code précise, la commande affiche une liste avec les modifications effectuées sur le fichier ainsi que le nom de la personne qui a fait la modification
- **git show identifiant_du_sha :** afficher le détail précis des modifications sur un fichier et dans un commit précis. L'identifiant du sha est récupéré lors de l'utilisation de la commande blame. Cet identifiant est placé en début de ligne
- **git stash :** mettre de côté des modifications sur un fichier en cours d'écriture (temporairement) - sans faire de commit - travailler sur d'autres modifications - permet alors de faire un commit des modifications sans faire de commit sur les modifications mises de côté
- **git stash pop :** reprendre le développement en cours sur les modifications mises de côté - pop supprime les données dans stash
- **git remote set-url origin new_url :** modifier l'url du repositery distant - origin ici (si le nom du repositery n'est pas modifié)

## Commandes terminal
- **mkdir :** créer un répertoire
- **cd nom_dossier_créé :** se placer dans le dossier créée
- **cat nom_du_fichier :** lire le contenu d'un fichier par l'intermédiaire d'un terminal

## Actions classiques de base
1. Coder
2. Commit
3. Push

##Lexique
- **Origin :** nom du remote par défaut si remote unique dans un projet
- **Master :** nom de la branche principale d'un repository
- **Une branche :** "un autre chemin" pour tester, expérimenter, modifier le code existant du "chemin principal" (master) ou bien crééer une nouvelle fonction sans toucher au code master

## Quelques concepts de Git
###Qu'est-ce qu'un commit :
		
Le commit est la validation (l’enregistrement dans un dépôt sur l’ordinateur de travail) d’un ou plusieurs fichiers qui ont été placés préalablement dans un index. Cet index est préparé et enrichi grâce à la fonction <commit add nom_du_fichier>.

On peut définir le commit comme un instantané (à moment T) ou une capture («figée») des fichiers qui composent un projet - une version d’un projet.

Pour valider les modifications des fichiers placés dans l’index (pour les «figer» dans le temps) on utilise la fonction <git commit>.

Cette opération s’effectue en local.

Les fichiers ne sont pas encore envoyés sur le remote (dépôt, repository ou référentiel) à distance.

Ils seront envoyés grâce à la fonction <git push nom_du_remote nom_de_la_branche>.


###À quoi sert la commande git log :

La commande git log permet de voir tout l’historique des commit sous forme de liste.

On trouve dans cette liste pour chaque commit :
- la clé unique sha du commit,
- l’auteur du commit,
- la date du commit,
- l’explication (normalement clairement détaillée) sous forme de commentaire du pourquoi du commit (création d’un fichier, modification de texte, ajout d’un fonction, d’une définition etc.).


###Qu'est-ce qu'une branche :

La branche principale d’un projet, par défaut, est appelée «master»

Cette branche est composée de l’ensemble des commit du projet.
On peut définir la branche comme étant un pointeur vers le dernier commit en cours.

La branche est une sorte de route linéaire. On peut revenir en arrière et pointer sur un ancien commit pour récupérer une ancienne portion de code ou un fichier écrasé.

Dans cette branche on retrouve l’intégralité des fichiers du projet en cours.

Lorsque l’on souhaite tester un code ou développer une fonction complémentaire on créée une ou plusieurs branches secondaires («parallèles» à la branche master).

Une fois les tests effectués et les contenus validés sur cette ou ces branches secondaires, on peut les fusionner avec la branche principale.