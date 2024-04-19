# Integration continue

Organisation du travail en entreprise en CI/CD : intégration continue et développement continue

## 🎓 J'ai compris et je peux expliquer

- les enjeux de l'integration continue ✅
- la mise en place d'une github action ✅

## 💻 J'utilise

### Un exemple personnel commenté ✅

Exemple du script de lancé au moment du déploiement continu pour générer les images docker :

```
#!/bin/sh
# fetch-and-deploy.sh
docker compose -f docker-compose.prod.yml down && \
    docker compose -f docker-compose.prod.yml pull && \
    GATEWAY_PORT=8001 docker compose -f docker-compose.prod.yml up -d;
```

Exemple de la commande permettant de rendre ce script exécutable :

```
sudo chmod +x fetch-and-deploy.sh
```

Exemple de la commande pour lancer le script :

```
`./fetch-and-deploy.sh
```

Exemple du fichier de configuration de Nginx : 
```
events {}

http {
  include mime.types;

  server {
    listen 80;

    location /api {
      proxy_pass http://backend:5000;
    }

    location / {
      proxy_pass http://frontend:3000;
    }
  }
}
```

### Utilisation dans un projet ✅

[lien github](https://github.com/WildCodeSchool/2023-09-wns-rouge-greenquest)

Une CI backend et frontend a été mise en place sur ce projet.

Exemple avec la CI backend mise en place dans ce fichier .yml :

```
name: jest-and-docker-backend

on:
  push:

jobs:
  has-changes:
    runs-on: ubuntu-latest
    outputs:
      has-changes: ${{ steps.check-changes.outputs.backend }}
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Get current branch name
        id: get_branch_name
        run: echo "::set-output name=branch::$(git rev-parse --abbrev-ref HEAD)"
      - name: Check for changes in backend directory
        id: check-changes
        uses: dorny/paths-filter@v3
        with:
          base: ${{ github.ref }}
          filters: |
            backend:
              - 'backend/**'
      - name: Inspect has-changes output
        run: |
          echo "has-changes: ${{ steps.check-changes.outputs.backend }}"

  test-back:
    needs: has-changes
    runs-on: ubuntu-latest
    if: needs.has-changes.outputs.has-changes == 'true'
    steps:
      - name: Check out code
        uses: actions/checkout@v4
      - name: Goto backend and run tests
        run: cd backend && npm i && npm test

  docker:
    needs: test-back
    if: github.ref == 'refs/heads/dev'
    runs-on: ubuntu-latest
    steps:
      - name: Set up QEMU
        uses: docker/setup-qemu-action@v3
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          push: true
          context: "{{defaultContext}}:backend"
          tags: ${{ secrets.DOCKERHUB_REPO_BACKEND }}:latest, ${{ secrets.DOCKERHUB_REPO_BACKEND }}:${{ github.sha }}
```

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ✅

Description :
Dans le cadre de la pratique professionnelel en entreprise, une CI est mise en place afin de tester quotidiennement le code des applications mobiles.
Cela permet notammnent de s'assurer de l'absence de régression et de vérifier que le code prêt à merger sur une branche est bien fonctionnel et testé.

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 📽️ J'en fais la démonstration

Dans le cadre de la mise en place de la livraison continue avec la configuration du serveur via Caddy et Nginx, j'ai réalisé un schéma récapitualtif

- J'ai fait une [présentation](https://docs.google.com/presentation/d/1LAE8HmOVSnes2aYdum-MDnqwoJPeJIlP4IzJLbhhjII/edit?usp=sharing) ✅
