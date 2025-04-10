## Explications
Dans un premier temps j'ai créé 2 dossiers : 'Frontend' et 'Backend".

# Backend
J'ai créé une api qui permet de récupérer parmit 3 citations, une citation aléatoire.
J'ai ensuite créé un fichier Dockerfile pour pouvoir construire l'image et
Je l'ai ensuite construit avec la commande : `docker build -t backend .`
Et lancé avec la commande : `docker run -d -p 5000:5000 backend backend`.

En allant sur localhost:5000/api/citation je retrouve alors mes citations de manière aléatoire.

# Frontend
J'ai créé un front qui fait un appelle a l'api du back pour afficher une citation aléaatoire.
J'ai ensuite créé un fichier Dockerfile pour pouvoir construire l'image et
Je l'ai ensuite construit avec la commande : `docker build -t frontend .`
Et lancé avec la commande : `docker run -d -p 3000:3000 frontend frontend`.

En allant sur localhost:3000 je retrouve alors mes citations qui s'affiche de manière aléatoire.

Une fois que ça marche correctement localement, on peut se permettre d'arrêter et/ou de supprimer les images et container.

# Docker-Compose
Afin de partager plus facilement mon projet, j'ai du le partager sur Docker Hub. Pour ça, il faut créer à la racine du projet un fichier `docker-compose.yml`.
La dedans, il faut donner un nom aux images qui va être publié dans Docker Hub. Ensuite les relier (en fonction du port dans notre cas).

Une fois la configuration terminé, lancé les commandes suivante : 
`docker-compose build`
`docker-compose up -d`
--- Pour la connexion, vérifiez si vous êtes connecté ---
`docker login`
`docker push <repo/nomimg>`

# De votre côté
Pour que vous puissiez récupérer, vous devez créer un fichier `docker-compsoe.yml` qui récupère les images.
Même si vous ne les avez pas localement, il va les rechercher sur Docker Hub. 

Ce qu'il faut lancer une fois le fichier créé : `docker-compose up -d`

## Questions de réflexion

1. Quelle différence fais-tu entre un `Dockerfile` et un `docker-compose.yml` ?
<span style="color:green">Le Dockerfile sert à construire l’image d’un conteneur (donc décrit comment installer les dépendances, copier les fichiers, etc)
alors que le docker-compose.yml sert à orchestrer plusieurs conteneurs.</span>

2. Quels sont les avantages de séparer les services dans une architecture Docker ?
<span style="color:green">Les avantages de séparer les services permettent d'être facilement maintenable. De plus il est facile de mettre à jour ou redémarrer individuellement des uns des autres.</span>

3. En quoi Docker Compose facilite-t-il le travail en équipe et le déploiement ?
<span style="color:green">Docker Compose permet à tous les membres de l’équipe de déployer un projet avec une seule commande tout en ayant la même config.</span>

4. Pourquoi est-il utile de publier une image sur Docker Hub même pour un projet perso ?
<span style="color:green">Il est utile de publier une image sur Docker Hub car ça permet d’y accéder depuis n’importe quelle machine,
de partager facilement le projet</span>