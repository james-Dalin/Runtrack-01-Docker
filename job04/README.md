# JOB 04 - Exercice pratique : modif d'une page HTML dans un conteneur

## Commandes principales utilisées

1. docker run -d -p 8080:80 nginx
2. docker ps
3. http://localhost:8080 <== pour le navigateur
4. docker exec -ti CONTAINER_DI bash 
5. cd /usr/share/nginx/html 
6. ls
7. echo "..." Pour modifier le fichier
8. exit
9. docker stop CONTAINER_ID
10. docker ps -a
11. docker system prune

## Explication de ce que j'ai fait

Avec la commande docker run -d -p 8080:80 nginx, 
j'ai spécifié où était le bon port, là nginx attend la réponse. 
Je dis en gros que quand mon navigateur frappe au port 8080 de ma machine,
redirige vers le port 80 du conteneur où Nginx écoute.
Exactement comme avec Mario.

Ensuite, j'ai vérifié que le conteneur était actif, 
donc j'ai entré la commande docker ps pour vérifier ça.

Une fois cela fait, 
je rentre l'adresse du "localhost" pour voir apparaître le texte.

## La nouveauté 

La nouveauté est ici : de pouvoir entrer dans un conteneur.

la commande "docker exec -ti CONTAINER_ID" bash permet de faire cette démarche.
Au lieu de faire run pour créer un conteneur, je fais un exec pour rentrer à l'intérieur d'un conteneur existant.

Le -ti permet de d'allouer un terminal à docker et d'activer le mode interactif.

Le Bash permet de mettre un programme que je veux lancer à l'intérieur du conteneur. Je dis à Docker :"ouvre-moi un terminal à l'intérieur de ce conteneur"

Le prompt changera. La flèche et le signe disparaîtront pour laisser place à ceci ==> root@f2a8b2f534ed:/#

Root veut dire je suis l'administrateur du conteneur, dont l'identifiant sont les chiffres et les lettres. Le slash vuet que je suis à la racine du conteneur.

## La navigation

cd /usr/share/nginx/htmluser permet de me déplacer jusqu'au fichier html de nginx

"ls" permet d'afficher les détails d'un fichier

## La modification

Avec echo"...", j'ai pu modifier la page index pour afficher ce que je veux. 
À la fin de la modification, le chevron qui pointe vers la droite va écraser l'ancien fichier pour le réécrire entièrement
Je rafraîchis la page pour voir le résultat. Ensuite, je sors du conteneur pour revenir sur le terminal en faisant "exit"

Au passage, j'arrête également le conteneur, exactement comme je l'ai fait avec le jeu Mario en faisant docker stop CONTAINEUR_ID.

L'avant-dernière étape consiste à supprimer le conteneur avec la commande docker rm CONTAINER_ID

Je révérifie si cela à fonctionner avec docker ps -a

## Le grand ménage

Pour finir, la ligne de commande docker system prune permet de faire un néttoyage total.
