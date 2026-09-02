# IMPACT FINANCES — 17 au 20 septembre 2026

Site d'inscription aux ateliers de l'événement **Impact Finances** organisé par ICC Liège,
du jeudi 17 au dimanche 20 septembre 2026.

## Pages

| Fichier | Rôle |
|---|---|
| `index.html` | Page publique : programme des 4 jours, parcours recommandés, les 16 ateliers du samedi 19 répartis en 4 sessions, et le formulaire d'inscription (prénom, nom, e-mail). |
| `admin/index.html` | Tableau de bord interne des inscriptions (non référencé, non lié depuis le site). |
| `ateliers.html` | Redirection vers la page d'accueil — l'inscription y était hébergée avant. |

## Activer les inscriptions

Le site est statique (GitHub Pages), il ne peut pas stocker les réponses lui-même.
Les inscriptions passent par un **Google Form**, qui envoie automatiquement la
confirmation par e-mail et enregistre tout dans un Google Sheet.

1. Créer un Google Form avec, dans cet ordre : **Prénom**, **Nom**, **Adresse e-mail**,
   puis 4 questions à choix multiple **Session 1** à **Session 4**. Les options doivent
   reprendre exactement les libellés des attributs `value=` des boutons radio
   dans `index.html`.
2. Dans les réglages du formulaire : activer **« Collecter les adresses e-mail »** et
   **« Envoyer une copie des réponses aux répondants »**.
3. Formulaire → ⋮ → **« Obtenir le lien pré-rempli »**, remplir puis copier le lien :
   il contient un `entry.XXXXXXX` par champ.
4. Reporter ces valeurs dans le bloc `CONFIGURATION` en haut du `<script>` de
   `index.html` (`FORM_ACTION`, `ENTRY`) et passer `FORM_CONFIGURED` à `true`.
5. Sur le Sheet des réponses : **Fichier → Partager → Publier sur le web**, format CSV,
   puis coller le lien dans `CSV_URL` en haut du script de `admin/index.html`.

> `admin/` n'est pas protégée par mot de passe : elle est simplement non référencée.
> Toute personne connaissant l'URL exacte peut la consulter.

## Déploiement

Automatique sur GitHub Pages à chaque push sur `main`, via
`.github/workflows/deploy-pages.yml`.

En ligne : <https://incognitoresolve-alt.github.io/hub-hub/>
