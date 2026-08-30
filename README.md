# DROPZONE GENERATOR

Base complète Next.js / TypeScript / Tailwind pour le projet DropZone Generator.

## Installation

```bash
npm install
cp .env.example .env.local
npm run dev
```

Ouvre http://localhost:3000.

## Compte administrateur initial

Email : `dropzone@dc.ru`
Mot de passe initial : `123`

À la première connexion, le compte doit obligatoirement changer son mot de passe avant l'accès à l'administration.

## Architecture

- `app/` : routes App Router et API
- `components/` : UI réutilisable
- `lib/repositories/` : abstraction des données
- `lib/services/` : logique métier
- `lib/server/` : session/auth serveur
- `data/` : stockage JSON temporaire
- `types/` : modèles TypeScript

Les repositories sont conçus pour pouvoir être remplacés plus tard par des repositories Supabase/PostgreSQL sans réécrire les composants.

## Données

Les fichiers JSON sont initialisés automatiquement au premier lancement.

## Sécurité

- mots de passe hashés avec bcrypt
- session signée avec HMAC
- validation Zod
- contrôles d'accès côté serveur
- aucune clé secrète dans le client
- aucun mot de passe dans les logs


## ULTIMATE GLOW UP
Refonte visuelle : grille animée, halos, scanline, texture noise, glass/metal, shine, micro-interactions et dashboard admin renforcé.

## Changement du mot de passe admin
Le flux initial est maintenant fonctionnel : connexion avec le compte initial -> `/change-password` -> hash bcrypt -> désactivation de `mustChangePassword` -> redirection `/admin`.

## FX ULTIMATE
- Neige animée avec profondeur et dérive naturelle.
- Halos, grille animée, scanlines, grain/noise et effets de lumière.
- Musique ambiante locale `public/relaxing-dropzone.wav`, volontairement très basse (12% par défaut).
- Boutons flottants pour activer/désactiver neige et musique.
- Les paramètres d'expérience sont persistés dans `data/settings.json` et une copie dédiée est disponible dans `data/effects.json`.
- Tous les contenus persistants du projet utilisent les repositories JSON (`users.json`, `products.json`, `orders.json`, `logs.json`, `settings.json`).

## Correctif hydration + audio
- Les flocons ne sont plus générés avec `Math.random()` pendant le rendu SSR.
- Les flocons sont générés uniquement côté client après montage, avec des valeurs déterministes.
- L'audio utilise un élément HTML Audio côté client, volume par défaut 12 %, boucle activée et démarrage après interaction pour respecter les restrictions autoplay des navigateurs.
- Le logo est préchargé avec `next/image` pour éviter les retards visuels.


## Musique
La musique d'ambiance utilise la vidéo YouTube `MuVh4zR-5DM`, démarre à 00:23 et vise 45% de volume via l'API du lecteur. Le navigateur peut exiger une interaction utilisateur avant la lecture avec le son.

## Upload images
Dans Admin > Paramètres, les champs Logo et Image Hero acceptent la sélection de fichier et le glisser-déposer. Les fichiers sont stockés dans `public/uploads/` et l'URL est sauvegardée dans `data/settings.json`.

## Lancement Windows
`START-DROPZONE.bat` utilise uniquement des commandes ASCII afin d'éviter les erreurs Windows du type `DROPZONE n'est pas reconnu...`.
