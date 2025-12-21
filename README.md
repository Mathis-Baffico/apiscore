# README — API (Cloud)

Ce README minimal décrit comment lancer l'API en local, quelles variables d'environnement sont nécessaires, et liste les endpoints exposés.

## Prérequis ✅

- Node.js (>=14)
- npm
- Une base de données MySQL accessible

## Installation et lancement en local 🔧

1. Se placer dans le dossier du projet (si nécessaire) :

```bash
cd Cloud
```

2. Installer les dépendances :

```bash
npm install
```

3. Créer un fichier `.env` à la racine du dossier `Cloud` (voir la section suivante pour les variables attendues).

4. Lancer l'API :

```bash
# en production
npm start
# ou en développement (si nodemon est installé)
npm run dev
# ou
node index.js
```

> Remarque : adaptez la commande de lancement au script défini dans votre `package.json` (ex: `start`, `dev`).

## Variables d'environnement (essentielles) 🔑

Placez ces clés dans votre `.env` ou exportez-les dans votre environnement :

- `PORT` — port sur lequel l'API écoute (ex: `3000`). Valeur par défaut généralement `3000`.
- `NODE_ENV` — `development` | `production` (optionnel).
- `DB_HOST` — hôte MySQL (ex: `localhost`).
- `DB_PORT` — port MySQL (par défaut `3306`).
- `DB_NAME` — nom de la base de données.
- `DB_USER` — utilisateur MySQL.
- `DB_PASSWORD` — mot de passe MySQL.

> Suggestion : ajoutez un fichier `env.example` avec ces clés (sans valeurs) pour partager la configuration de manière sûre.

## Endpoints disponibles 📡

- `GET /api/healthz`
  - Description : vérifie que l'API est opérationnelle.
  - Réponse (200) :

```json
{
  "status": "ok"
}
```

- `GET /api/matches`
  - Description : récupère la liste des matches (ou éléments correspondants selon l'implémentation).
  

```json

[
  {
    "match_date": "2025-11-25T21:00:00.000Z",
    "home_team": "Marseille",
    "away_team": "Crystal Palace",
    "status": "played",
    "home_score": 2,
    "away_score": 1,
    "id": 1,
    "tour": "5ème journée"
  },
  {
    "match_date": "2025-11-26T18:45:00.000Z",
    "home_team": "Paphos",
    "away_team": "Monaco",
    "status": "played",
    "home_score": 2,
    "away_score": 2,
    "id": 2,
    "tour": "5ème journée"
  },
  {
    "match_date": "2025-11-26T21:00:00.000Z",
    "home_team": "Paris-SG",
    "away_team": "Tottenham",
    "status": "played",
    "home_score": 5,
    "away_score": 3,
    "id": 3,
    "tour": "5ème journée"
  },
  {
    "match_date": "2025-12-09T21:00:00.000Z",
    "home_team": "Monaco",
    "away_team": "Galatasary",
    "status": "played",
    "home_score": 1,
    "away_score": 0,
    "id": 4,
    "tour": "6ème journée"
  },
  {
    "match_date": "2025-12-09T21:00:00.000Z",
    "home_team": "Union Saint-Gilloise",
    "away_team": "Marseille",
    "status": "played",
    "home_score": 2,
    "away_score": 3,
    "id": 5,
    "tour": "6ème journée"
  },
  {
    "match_date": "2025-12-10T21:00:00.000Z",
    "home_team": "Athletic Bilbao",
    "away_team": "Paris-SG",
    "status": "played",
    "home_score": 0,
    "away_score": 0,
    "id": 6,
    "tour": "6ème journée"
  },
  {
    "match_date": "2026-01-20T21:00:00.000Z",
    "home_team": "Real Madrid",
    "away_team": "Monaco",
    "status": "scheduled",
    "home_score": null,
    "away_score": null,
    "id": 7,
    "tour": "7ème journée"
  },
  {
    "match_date": "2026-01-20T21:00:00.000Z",
    "home_team": "Sporting Portugal",
    "away_team": "Paris-SG",
    "status": "scheduled",
    "home_score": null,
    "away_score": null,
    "id": 8,
    "tour": "7ème journée"
  },
  {
    "match_date": "2026-01-21T21:00:00.000Z",
    "home_team": "Marseille",
    "away_team": "Liverpool",
    "status": "scheduled",
    "home_score": null,
    "away_score": null,
    "id": 9,
    "tour": "7ème journée"
  }
]

```

> Codes d'état courants : `200` (OK), `400` (mauvaise requête), `500` (erreur serveur / DB).

## Dépannage ⚠️

- Si l'API ne démarre pas : vérifiez les logs et que les variables d'environnement (`DB_*`) sont correctement renseignées.
- Si la connexion MySQL échoue : vérifiez l'accessibilité du serveur MySQL, les credentials, et le port.

---

