# Job 02 Déployement du jeu Mario dans un conteneur

## Première étape : la recherche du jeu Mario

### La commande à exécuté

#### Ce qu'il se passe

docker search : permet de chercher le jeu mario. Comme dans un catalogue de bibliothèque de logiciels. Je dois prendre celui qui correspond.

## Deuxième étape : Télécharger l'image

### La commande à exécuté 

docker pull sevenajay/mario:latest

#### Ce qu'il se passe

1. Sevenajay est le nom d'utilisateur qui a publié cette image sur Dockeur Hub
2. Mario est le nom de l'image elle-même.
3. :latest est la denière version à jour.

Une fois la commande faire, le téléchargement se lance, affichant les couches (layers) de l'image. Comme avec un mille-feuille, chaque couche contient une modification par rapport  àla précédente.

## Troisième étape : vérifier que l'image est bien là

### La commande à faire 

docker images

#### Ce qu'il se passe

Cette commande liste toutes les images stockées localement sur mon ordinateur. Il 'affiche le hello-world et sevenajay/mario.

## Quatrième étape : Lancer le conteneur avec le mapping de port

### La commande à exécuter

docker run -d -p 4545:80 sevenajay/mario:latest

#### Ce qu'il se passe

1. docker run : Créer et lance conteneur à partir d'une image.
2. -d : mode detach (détaché). le conteneur tourne en arrière-plan au lieu de bloquer le terminal
3. -p 4545:80 : le port de l'image du conteneur, et le port de l'ordi. Mario tourne sur le port 80 à l'intérieur du conteneur. Ça crée un pont : "tout ce qui arrive sur le port 4545 de ma machine, redirige-le vers le port 80 du conteneur." Le format est toujours port_hôte:port_conteneur
4. sevenajay/mario:latest : l'image à utiliser pour créer le conteneur.

## Cinquième étape : Vérifier que le conteneur tourne

### La commande à faire 

docker ps

#### Ce que cela fait 

Montre le tableau de bord du conteneur : qui tourne, depuis quand, sur quel port

## Sixième étape : Jouer à Mario

### Commande à faire 

Dans le navigateur : http://localhost:4545

#### Ce que ça fait

LE 4545 c'est le port mappé. L'interphone va rediriger la requête vers le port 80 du conteneur, où le serveur web du jeu Mario attend.

## Septième étape : arrêter le conteneur

### Commande à exécuté

docker stop "l'ID du conteneur"

#### Ce qu'il se passe

Arrête le conteneur.
