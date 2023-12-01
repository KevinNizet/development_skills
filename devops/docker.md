# Docker

## 🎓 J'ai compris et je peux expliquer

- la création d'une image docker ✅
- l'éxécution d'un container ✅
- l'orchestration de containers avec docker-compose ✅


## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

### Utilisation dans un projet ✅

[lien github](https://github.com/KevinNizet/the-good-corner/tree/graphQL)

Description :
Pour le Docker-compose de l'application : 

services:
#backend
  backend:
    build: ./backend
    ports:
      - 5001:5001
    volumes:
      - ./backend/src:/app/src
    env_file: ./backend/.env
  #database
  db:
    image: postgres
    ports:
      - 5432:5432 
    volumes:
      - /var/lib/postgresql/data
    env_file: .env
  #Adminer pour PostGreSQL : gestion de la bdd
  adminer:
    image: adminer
    restart: always
    ports:
      - 8080:8080


Ce fichier docker-compose.yml constitué en cours de développement de l'application configure trois services: un backend, une base de données Postgres, et un outil de gestion de base de données (Adminer). Ces services peuvent être démarrés ensemble en utilisant la commande docker-compose up, créant ainsi un environnement cohérent pour le développement et le déploiement d'une application avec une base de données PostgreSQL. Le fichier détaille également les paramètres d'exposition de ports, les volumes partagés et les fichiers d'environnement nécessaires pour chaque service.
Il permet notamment d'avoir un backend robuste et figé tout en poursuivant le développement du Frontend non dockerisé. 

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :
Construction d'images Docker (modèle en lecture seule) d'une application afin de les charger sur un conteneur afin de l'éxécuter de façon indépendante. 
L'utilité principale dans le cadre professionnelle est de permettre au reste de l'équipe d'utiliser une application développée sur un système d'exploitation différent (Windows VS Mac). Cela facilite le déploiement et permet d'accélerer le cycle de développement. 


## 🌐 J'utilise des ressources

### Titre

- DockerHub : https://hub.docker.com/
- Description : librairie en ligne pour un large choix d'images dockers officielles (ex: Node).


