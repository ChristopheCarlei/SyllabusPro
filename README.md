# Handoff : Accueil Moodle — « Professionnalisation & intervention » (752501)

## Mission pour Claude Code

Ce dossier contient un **site statique fini et prêt à déployer** — ce n'est PAS une maquette à recréer.
Ta mission :

1. Créer un dépôt GitHub (suggestion de nom : `accueil-pro-752501`) et y pousser le contenu de ce dossier **tel quel**, `index.html` à la racine.
2. Connecter le dépôt à **Netlify** (l'utilisateur a déjà un compte — il héberge déjà `prointer.netlify.app` de la même façon). Aucun build : site 100 % statique, publier la racine (`publish directory: /`, pas de commande de build).
3. Donner à l'utilisateur l'URL Netlify finale et le code iframe Moodle ci-dessous, avec l'URL remplacée.

⚠️ **Licence de police — IMPORTANT** : `assets/fonts/` contient TheSans (LucasFonts), police sous licence de l'Université de Genève. **Mettre le dépôt GitHub en PRIVÉ** pour ne pas redistribuer publiquement les fichiers .otf. Netlify peut servir un dépôt privé sans problème.

## Ce que c'est

Page d'accueil interactive du cours « Professionnalisation & intervention » (UNIGE, FPSE, code 752501, Printemps 2027), destinée à être **intégrée en iframe en tête du Moodle** du cours. Elle remplace une présentation Genially. Charte graphique FPSE/UNIGE (teal `#00B1AE` / `#00857F`, rose `#CF0063`, police TheSans).

Scène fixe **16:9 (1600×900)** auto-redimensionnée au viewport (letterbox sombre). Hub central à 7 tuiles + timeline cliquable ; 7 vues de section ; navigation par hash (`#plan`, `#evaluation`…), pastilles 1–7 dans chaque en-tête, clavier (←/→ entre sections, Échap = accueil).

## Structure

```
index.html          ← tout le site (HTML + CSS spécifique + JS vanilla inline)
styles.css          ← point d'entrée tokens (@import uniquement)
tokens/             ← fonts.css, colors.css, typography.css, spacing.css, base.css
assets/fonts/       ← TheSans .otf ×5 (licence UNIGE — repo PRIVÉ)
assets/logos/       ← logoFPSE.png, AFFORDENS_TR.png
```

Aucune dépendance externe, aucun framework, aucun build. Fonctionne en `file://`.

## Code iframe pour Moodle (à remettre à l'utilisateur)

Dans Moodle : activité « Texte et média » (ou zone HTML), mode code `</>` :

```html
<div style="position:relative;width:100%;max-width:1280px;margin:0 auto;aspect-ratio:16/9;">
  <iframe src="https://VOTRE-SITE.netlify.app/"
    style="position:absolute;inset:0;width:100%;height:100%;border:0;border-radius:8px;"
    title="Accueil du cours Professionnalisation &amp; intervention"
    loading="lazy" allowfullscreen></iframe>
</div>
```

Astuce : on peut pointer directement une section, ex. `https://VOTRE-SITE.netlify.app/#plan`.

## Contenu à maintenir (badges « à confirmer »)

Les données 2027 suivantes sont **provisoires** et marquées par des badges jaunes `badge-tbc` dans `index.html` ; l'utilisateur les confirmera plus tard :
- Thèmes des séances S06–S13 (tableau de la vue Plan)
- Dates des évaluations intermédiaire (S08 · 20 avril) et finale (S13 · 25 mai)
- Échéances des 8 livrables (vue Dates importantes)
- Créneau de travail de groupe M2140 (vue Informations)
- Liste des projets (édition 2026, à actualiser)

Pour les modifier : tout est dans `index.html`, sections `<!-- ===== PLAN ===== -->`, etc. Aucune donnée n'est dupliquée ailleurs.

## Design tokens (si retouches)

Définis dans `tokens/colors.css` & co, consommés via `var(--…)` :
`--teal:#00B1AE` · `--teal-deep:#00857F` · `--rose:#CF0063` · `--rose-deep:#A8004F` · `--ink:#172033` · `--muted:#5A6477` · `--line:#E4E7EC` · fonds teintés `--bg-teal:#EAF6F5` / `--bg-rose:#FBEAF1` · rayon cartes 14px · TheSans 300/400/600/700/800.

## Fidélité

**Haute-fidélité, production.** Ne pas restyler, ne pas porter vers un framework. Déployer tel quel.
