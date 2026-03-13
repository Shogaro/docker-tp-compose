# Exercice 3 - Architecture complete avec reseaux

Objectif: decrire une architecture front + api + base de donnees dans un seul fichier Compose, avec reseaux dedies, build local et image nommee.

## Contexte

Vous devez mettre en place une architecture composee:
- d'un service `web` construit localement
- d'un service `api` construit localement
- d'un service `db` base sur `postgres:15`

Le front ne doit parler qu'a l'API. La base de donnees ne doit pas etre exposee vers l'hote et ne doit etre accessible que via le reseau backend.

## Fichiers fournis

- `web/Dockerfile`
- `web/index.html`
- `web/nginx.conf`
- `api/Dockerfile`
- `api/index.js`
- `api/package.json`
- `.env.example`

## Travail a faire

1. Creer un fichier `.env` a partir de `.env.example` et completer les valeurs.
2. Declarer une architecture Compose avec `web`, `api` et `db`.
3. Faire les choix de configuration necessaires pour:
   - construire les services applicatifs et nommer les images produites
   - externaliser la configuration sensible via le fichier `.env`
   - exposer uniquement les services utiles vers l'hote
   - conserver les donnees de la base
   - isoler correctement les communications reseau
4. Lancer la stack puis verifier son fonctionnement.
5. Nettoyer l'ensemble des ressources creees.

Les commandes doivent etre fournies dans un fichier separe `COMMANDS.md`.

## Questions de reflexion

- Pourquoi `api` doit-il etre connecte a deux reseaux dans cette architecture ? Car elle doit récupérer les infos du bakc pour les envoyer au front
- Quel interet de combiner `build` et `image` sur un meme service ? On peut créer notre image avec notre propre code
- Pourquoi la base ne doit-elle pas etre publiee avec `ports` dans ce cas ? Sinon ça expose la db ce qui n'est pas une bonne chose

## Criteres de validation

- Les trois services sont declares dans un seul fichier Compose
- Les reseaux `frontend` et `backend` sont utilises correctement
- Au moins un service combine `build` et `image`
- La base de donnees reste interne a la stack
