# AGENTS.md

## Aperçu du projet

Ce dépôt contient une collection de recettes culinaires stockées au format `.cook` (Cooklang). Le but est de tenir un recueil organisé de recettes, par catégorie, avec métadonnées structurées et fichiers d'images associés.

Le dépôt est principalement un catalogue de données, pas une application logicielle traditionnelle. La plupart des modifications portent sur :

- la création ou la mise à jour de fichiers `.cook`
- la gestion de dossiers par type de recette
- la mise à jour d'images ou de références d'images
- la validation des fichiers de recettes

## Structure du dépôt

- `README.md` : description générale du dépôt et organisation des recettes
- `images/` : images de recettes
- `boisson/` : boissons
- `collation/` : collations et encas
- `dessert/` : desserts et pâtisseries
- `plat/` : plats principaux
- `.github/skills/` : compétences GitHub Copilot spécifiques au domaine
- `.github/workflows/validate-recipes.yml` : validation automatique des recettes

## Convention des fichiers de recette

Les fichiers de recette utilisent l'extension `.cook`.

Chaque fichier doit commencer par un bloc YAML en frontmatter avec `---` :

```cooklang
---
title: Nom de la recette
description: Brève description
image: images/mon_fichier.jpg
prep_time: 10 minutes
cook_time: 20 minutes
time_required: 30 minutes
servings: 4
cuisine: Française
course: Plat
---

Instructions de la recette...
```

Règles importantes :

- Utiliser toujours `---` pour le frontmatter, jamais `>>`
- Les recettes sont écrites en syntaxe Cooklang
- Les ingrédients doivent être notés avec la syntaxe Cooklang, par exemple :
  - `@farine{200%g}`
  - `@oeufs{2}`
  - `@beurre{50%g}`
- Les ustensiles doivent être écrits avec `#`, par exemple :
  - `#poêle{}`
  - `#casserole{}`
- Les timers peuvent être indiqués comme :
  - `~{10%minutes}`
  - `~oven{25%minutes}`
- Les étapes doivent être séparées par des paragraphes vides
- Les fichiers de recette doivent rester lisibles et structurés

## Conventions de nommage

- Utiliser des noms descriptifs, en minuscules, avec underscores ou tirets selon la convention déjà présente
- Les recettes sont souvent classées par dossier fonctionnel
- Les noms de fichiers doivent rester cohérents avec le libellé du titre
- Les images associées doivent être conservées dans `images/` et référencées de manière relative

## Validation

Le dépôt valide automatiquement les recettes avec CookCLI.

Commande à utiliser localement si nécessaire :

```bash
cook doctor validate --strict
```

Pour les agents / contributeurs :

- Ne pas introduire de syntaxe Cooklang invalide
- Vérifier que les références d'images existent
- Vérifier que le frontmatter est bien fermé par `---`
- Respecter les conventions de structure déjà présentes dans le dépôt

## Règles de contribution

- Préférer les petites modifications ciblées
- Ne pas réécrire des recettes existantes sans nécessité
- Conserver la langue principale du dépôt (français) pour les titres, descriptions et commentaires
- Maintenir les catégories existantes (boisson, collation, dessert, plat)
- Ne pas créer de nouveaux formats de recette non standard
- Si une recette est ajoutée, vérifier qu'elle correspond à une catégorie logique du dépôt

## Exemple de recette acceptable

```cooklang
---
title: Thé simple
description: Une tasse de thé chaud simple et rapide à préparer
image: images/tea.jpg
prep_time: 2 minutes
cook_time: 5 minutes
time_required: 7 minutes
servings: 1
cuisine: Britannique
course: Boisson
---

Faire bouillir @eau{2%tasses} dans une #bouilloire{}.

Plonger @sachet de thé{1} dans @eau{2%tasses} dans une #tasse{}.

Laisser infuser ~{5%minutes} et retirer le sachet de thé.

Servir chaud.
```

## Points importants pour les agents

- Ce dépôt n'est pas un projet JavaScript/TypeScript classique ; il s'agit surtout d'un dépôt de recettes
- Les changements doivent rester cohérents avec le style documentaire et culinaire du dépôt
- Quand on crée une recette, privilégier une structure claire, des métadonnées complètes et une syntaxe Cooklang correcte
- Les validations sont essentielles avant de conclure une modification

## Référence supplémentaire

Les sous-dossiers `.github/skills/*/SKILL.md` documentent les tâches habituelles liées à la création, la validation, la recherche et l'organisation des recettes. Les suivre si un agent a besoin de contexte pour une opération spécifique.
