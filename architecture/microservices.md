# Microservices

## 🎓 J'ai compris et je peux expliquer

- les différences avec l'architecture monolithique ✅

Dans le cadre d'une architecture monolithique, les fonctions et les services sont inséparables et fonctionnent comme un seul bloc. Cela rend l'application peut scalable et difficilement optimisable car l'architecture en est vite rendue complexe à l'échelle d'un grand projet. L'avatange principale de cette architecture rédise dans une facilité de rédaction des tests ainsi que du débugage (la base de code étant exécutée dans un même environnement).

Dans une architecture de microservices, les fonctions clés peuvent s'éxécuter de façon indépendantes. Le code métier est ainsi isolé et de nouvelles fonctionnalités peuvent être développées plus aisément sans impacter sur l'ensemble du fonctionnement de l'application. L'avantage principal de ce modèle architectural est un déploiement continu et plus rapide suite à chaque développement.

- la communication asynchrone entre services ❌ / ✔️
- le deploiement d'un cluster ❌ / ✔️

## 💻 J'utilise

Dans le cadre de la formation, les projets auxquels j'ai pu participer possèdent tous une architecture monolithique.

### Un exemple personnel commenté ❌ / ✔️

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ✅

Cependant, dans le cadre des projets d'entreprise sur lesquels j'ai travaillé, les applications mobiles développées possédent une dépendance à un cloud et à des composantes tierces pour certaines fonctionnalités. Cela peut être assimilé à du microservice.
En effet, Strapi, un CMS open source est utilisé sur une partie du contenu de l'application afin de conserver la possiblité de mettre à jour le texte affiché ainsi que des catégories en s'affranchissant de la nécessité de publier une nouvelle version sur les stores.
L'application envoi des requêtes à Hubspot, un CRM utilisé par le client pour gérer les leads et la base client.
De la même façon, l'application mobile communique avec un appareil connecté. La plateforme ThingsBoard est ainsi requetée pour la gestion du parc d'appareil connecté et l'affichage des données remontées.
Enfin, l'authentification des utilisateurs de l'application est généralisée via Auth0 avec la mise en place du SSO (Single - sign on).

Description :

## 🌐 J'utilise des ressources

### Titre

- lien : https://aws.amazon.com/fr/compare/the-difference-between-monolithic-and-microservices-architecture/
  https://cloud.google.com/learn/what-is-microservices-architecture?hl=fr
- description : AWS (Amazon Web Service) et Google Cloud
