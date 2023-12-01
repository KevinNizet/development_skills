# REST API

## 🎓 J'ai compris et je peux expliquer

- les verbes HTTP ✅
- les statuts HTTP ✅
- les endpoints ✅
- CORS ✅
- la nomenclature recommandée pour les routes ✅

## 💻 J'utilise

### Un exemple personnel commenté ✅

### Utilisation dans un projet ✅

[lien github](https://github.com/KevinNizet/the-good-corner)

#### Description :

**Endpoints :**

Les endpoints sont les URL spécifiques à une ressource.
Exemple : https://api.example.com/users pourrait être l'endpoint pour accéder à la liste des utilisateurs. Si l'on souhaitait voir les produits, on aurait mis "/products" par exemple. 

Dans le cadre du projet de cours, voici par exemple un extrait de requêtes HTTP : 

**Categories - createOne**
POST http://localhost:5001/categories
content-type: application/json

{
  "name": "Animaux et cie"
}

==> Permet de créer une catégorie 

**Categories - patchOne**
PATCH  http://localhost:5001/categories/1
content-type: application/json

{
  "name": "Updated category"
}

==> Permet de mettre à jour la catégorie d'ID 1.

**Categories - getAll**
GET http://localhost:5001/categories

==> Permet d'afficher l'ensemble des catégories définies

**CORS (Cross-Origin Resource Sharing) :**

CORS est un mécanisme de sécurité qui contrôle l'accès aux ressources d'un serveur depuis une origine différente.
Les serveurs doivent inclure des en-têtes CORS appropriés pour autoriser ou refuser les requêtes provenant de domaines différents. 

Dans le cadre du développement d'une application web, CORS ne résout pas tous les problèmes de sécurité, et d'autres mesures doivent également être prises pour protéger les applications web contre d'autres types d'attaques, comme les attaques de script intersite (XSS) ou les attaques de requête intersite (CSRF).

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

Dans le cadre de la pratique en entreprise, j'ai été par exemple amené à rédiger des test unitaires et notamment à "mocker" des requêtes HTPP. En effet, dans ce cas,le but est d'un mock est de simuler un appel HTPP et l'interaction avec la fonction testée. 
Les réponses attendues lors du test nécessitent donc d'utiliser le bon verbe HTTP (GET, POST, DELETE) ainsi que les codes corrects concernant le statut HTTP (200 en cas de succés, 404 en cas de ressource non trouvée...)


## 🌐 J'utilise des ressources

### Titre

- Documentation MDN : https://developer.mozilla.org/fr/docs/Glossary/REST
- Documentation wikipédia sur les codes HTPP : https://fr.wikipedia.org/wiki/Liste_des_codes_HTTP

