# GitHub

Utilisation de GitHub dans le cadre de la formation. 
Utilisation de GitLab et de GitGraph dans le cadre de l'expérience en entreprise

## 🎓 J'ai compris et je peux expliquer

- l'initialisation d'un projet ✅
- travailler avec des branches ✅
- faire une PR ✅
- utiliser git rebase pour faire des commits propres ✅
- utiliser les gitHub actions ✅

## 💻 J'utilise

### Un exemple personnel commenté ✅

### Utilisation dans un projet ✅

[lien github](https://github.com/KevinNizet/the-good-corner/tree/graphQL)

Description :
Dans le cadre de ce projet de cours, j'ai choisi de créer une branche graphQL permettant d'implémenter ce service. 
Dans la branche principale, j'ai choisi de conserver la gestion du backend via une API REST. Cette fonctionnalité aurait du être placée sur une branche dédiée (et non sur la branche main).
Cependant, étant le seul à travailler sur ce projet servant d'exercice, j'ai préféré simplifier la gestion des branches. 

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ✅

Description :

cf.ci-dessous

## 🌐 J'utilise des ressources

### Titre

- Gitmoji : https://gitmoji.dev/
- Description : j'utilise Gitmoji afin d'avoir des commits différenciés en fonction de leur type. 

Dans le cadre de ma pratique professionnelle en entreprise, cela permet notamment ensuite de créer des Changelogs automatiques lorsque nous mettons en production la release d'une nouvelle version. 
C'est un gain de temps considérable car cela génére automatiquement une liste classé par type de commit de tous les changements apportés par cette nouvelle version. 

- Altassian : https://www.atlassian.com/git/tutorials/merging-vs-rebasing
- Description : j'utilise cette documentation pour gérer correctement mes commits

En effet, en entreprise, j'ai appris à gérer les branches de développement par des git rebase, et la différence que cela implique par apport à des merges. 
Le workflow mis en place permet d'avoir un historique propre des commits et une lecture simplifiée des branches. 

Les pull request sont également réalisées à chaque développement de feature terminé. C'est alors l'occasion d'avoir une revue de son code, ou d'en réaliser une sur la pull request d'un autre développeur. 
Le workflow demande a ce que toute pull request soit revue par un ou plusieurs pair. C'est l'occasion d'échanger sur les bonnes pratiques et de s'améliorer constamment dans la rédaction du code. 

- GitLab : https://gitlab.com/gitlab-org/gitlab

En entreprise, la plateforme dédiée pour l'ensemble des opérations est GitLab. 
Je l'utilise pour l'hébergement des différentes repos de code, la versionnage et les release des applications. 
L'équipe l'utilisate également dans le cadre de la méthode Agile. 
La plateforme est également utilisée pour le CI/CD avec la configuration des pipelines de test tournant à chaque pull request. 