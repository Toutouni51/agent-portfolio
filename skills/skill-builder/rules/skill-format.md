# Format du fichier SKILL.md

## Structure du frontmatter YAML

Chaque SKILL.md doit commencer par un bloc YAML entre `---` :

```markdown
---
name: nom-du-skill
description: Description concise du skill (1 ligne)
metadata:
  tags: tag1, tag2, tag3
---
```

### Champs requis

- **name** : Identifiant unique du skill (kebab-case recommandé)
- **description** : Description brève et claire (affichée dans la liste des skills)

### Champs optionnels

- **metadata.tags** : Tags pour catégoriser le skill (séparés par des virgules)

## Sections recommandées

### 1. "Quand utiliser ce skill" (When to use)

Décrit les déclencheurs et contextes d'utilisation :

```markdown
## Quand utiliser ce skill

Utilise ce skill quand :
- L'utilisateur demande X
- Tu détectes le pattern Y
- Le projet contient Z
```

### 2. "Ce que fait ce skill" (What it does)

Explique les fonctionnalités principales :

```markdown
## Ce que fait ce skill

Ce skill permet de :
1. Première fonctionnalité
2. Deuxième fonctionnalité
3. Troisième fonctionnalité
```

### 3. "Comment utiliser" (How to use)

Instructions d'utilisation et références vers les règles :

```markdown
## Comment utiliser

Pour [cas d'usage 1], consulte [./rules/rule1.md](./rules/rule1.md)
Pour [cas d'usage 2], consulte [./rules/rule2.md](./rules/rule2.md)

Liste des règles disponibles :
- [rules/getting-started.md](rules/getting-started.md) - Démarrage rapide
- [rules/configuration.md](rules/configuration.md) - Configuration
```

### 4. Sections additionnelles (optionnelles)

- **Exemples** : Cas d'usage concrets
- **Configuration** : Paramètres et options
- **Troubleshooting** : Problèmes courants
- **Ressources** : Liens externes utiles

## Exemples complets

### Skill simple (sans règles)

```markdown
---
name: git-helper
description: Automatise les opérations Git courantes
metadata:
  tags: git, version-control, automation
---

## Quand utiliser ce skill

Utilise ce skill quand l'utilisateur demande :
- "commit mes changements"
- "créer une branche"
- "synchroniser avec origin"

## Ce que fait ce skill

Ce skill simplifie les opérations Git en :
1. Créant des commits avec des messages formatés
2. Gérant les branches automatiquement
3. Synchronisant avec le remote

## Commandes principales

### Commit rapide
```bash
git add .
git commit -m "type(scope): message"
```

### Créer une branche
```bash
git checkout -b feature/nom-de-la-branche
```
```

### Skill avec règles

```markdown
---
name: api-builder
description: Génère des APIs REST avec bonnes pratiques
metadata:
  tags: api, rest, backend, express
---

## Quand utiliser ce skill

Utilise ce skill quand l'utilisateur veut :
- Créer une nouvelle API
- Ajouter des endpoints REST
- Configurer la validation

## Ce que fait ce skill

Ce skill génère automatiquement :
1. Structure de projet API
2. Endpoints CRUD complets
3. Validation et gestion d'erreurs

## Comment utiliser

Consulte les règles suivantes :

- [rules/project-setup.md](rules/project-setup.md) - Initialiser un projet API
- [rules/endpoints.md](rules/endpoints.md) - Créer des endpoints REST
- [rules/validation.md](rules/validation.md) - Validation des données
- [rules/error-handling.md](rules/error-handling.md) - Gestion des erreurs
```

## Conseils de rédaction

1. **Sois concis** : Le SKILL.md est un overview, les détails vont dans les rules
2. **Sois spécifique** : Décris clairement quand et comment utiliser le skill
3. **Utilise des exemples** : Illustre avec du code quand c'est utile
4. **Liens relatifs** : Utilise toujours des chemins relatifs vers les rules
5. **Markdown propre** : Utilise la syntaxe Markdown standard (GitHub-flavored)
