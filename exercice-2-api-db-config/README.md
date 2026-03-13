# Exercice 2 - API et base de donnees avec configuration

Objectif: orchestrer deux services avec Docker Compose en utilisant variables d'environnement, fichier `.env` et volume persistant.

## Contexte

Vous devez decrire une petite architecture composee:
- d'un service `db` base sur `postgres:15`
- d'un service `api` fourni sous forme d'un petit projet Node.js a construire

La base doit conserver ses donnees et la configuration sensible ne doit pas etre entierement ecrite en dur dans le YAML.

## Fichiers fournis

- `api/index.js`
- `api/package.json`
- `api/Dockerfile`
- `.env.example`

## Attendu

Votre rendu doit permettre:

- de lancer une base PostgreSQL et une API dans une meme stack Compose
- de construire l'API a partir des fichiers fournis
- d'externaliser la configuration a l'aide d'un fichier `.env`
- de connecter l'API a la base de donnees
- de conserver les donnees PostgreSQL dans un volume
- d'exposer l'API sur `http://localhost:3000`
- d'observer puis de nettoyer correctement la stack

Les commandes doivent etre fournies dans un fichier separe `COMMANDS.md`.

## Questions de reflexion

- Quelle difference entre `environment` et `env_file` ? environment permet de définir les variables d'environnement alors que env_file permet de dire ou trouver les valeurs qu'on a assigné à ces variables.
- Pourquoi un volume nomme est-il utile pour la base de donnees ? C'est utile car ça alloue une place aux données donc même en arrêtant le conteneur on garde les données
- Que garantit `depends_on` et que ne garantit-il pas ? depends_on permet de démarrer le service uniquement si ça dépendance est lancée

## Criteres de validation

- Les deux services sont decrits dans un meme fichier Compose
- Les variables sont externalisees proprement
- Le volume de la base est bien declare
- La stack peut etre supprimee avec et sans suppression du volume
