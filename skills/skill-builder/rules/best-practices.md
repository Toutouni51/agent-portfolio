# Bonnes pratiques pour créer des skills

## Organisation

### Nommage

✅ **Bon**
- `api-rest-generator`
- `react-component-builder`
- `git-commit-helper`

❌ **Mauvais**
- `mySkill` (camelCase)
- `skill_builder` (snake_case)
- `helper` (trop vague)
- `super-mega-advanced-tool` (trop long)

**Règles** :
- Utiliser kebab-case
- 2-4 mots maximum
- Descriptif et spécifique
- Éviter les acronymes obscurs

### Structure de fichiers

```
skill-name/
├── SKILL.md                    # Toujours présent
└── rules/                      # Si le skill est complexe
    ├── getting-started.md      # Commencer par ici
    ├── advanced-usage.md       # Fonctionnalités avancées
    ├── troubleshooting.md      # Problèmes courants
    └── assets/                 # Exemples de code réutilisables
        ├── template.tsx
        └── example.ts
```

**Principes** :
- 1 règle = 1 fichier (sauf si très courte)
- Noms de fichiers explicites
- Ordre logique (du simple au complexe)
- Assets séparés si > 50 lignes

## Rédaction

### Déclencheurs clairs

✅ **Bon**
```markdown
## Quand utiliser ce skill

Utilise ce skill quand l'utilisateur :
- Dit "créer un composant React"
- Mentionne "nouveau component"
- Demande de "générer une UI"
```

❌ **Mauvais**
```markdown
## Quand utiliser

Utilise ce skill pour React.
```

**Règles** :
- Être spécifique et exhaustif
- Lister 3-7 déclencheurs
- Inclure variations de langage
- Mentionner le contexte si nécessaire

### Description concise

✅ **Bon**
```yaml
description: Génère des composants React avec TypeScript et bonnes pratiques
```

❌ **Mauvais**
```yaml
description: Ce skill permet de créer des composants pour React en utilisant TypeScript et en suivant les meilleures pratiques de l'industrie
```

**Règles** :
- 1 ligne maximum
- 5-15 mots idéalement
- Verbe d'action au début
- Pas de jargon inutile

### Exemples de code

✅ **Bon**
```markdown
### Créer un endpoint GET

```typescript
router.get('/users/:id', async (req, res) => {
  const { id } = req.params;
  const user = await User.findById(id);

  if (!user) {
    return res.status(404).json({ error: 'User not found' });
  }

  res.json(user);
});
```
```

❌ **Mauvais**
```markdown
Voici comment faire :
```
router.get(...)
```
```

**Règles** :
- Code complet et fonctionnel
- Pas de `...` ou pseudocode
- Commentaires si nécessaire
- Syntaxe highlighting appropriée

## Performance

### Taille des fichiers

| Type | Taille recommandée | Taille max |
|------|-------------------|-----------|
| SKILL.md | 100-300 lignes | 500 lignes |
| Règle simple | 50-150 lignes | 300 lignes |
| Règle complexe | 150-400 lignes | 600 lignes |
| Asset | Variable | 200 lignes |

**Si dépassement** :
- Diviser en plusieurs fichiers
- Créer des sous-sections
- Utiliser des assets externes

### Nombre de règles

- **Skill simple** : 0 règle (tout dans SKILL.md)
- **Skill moyen** : 2-5 règles
- **Skill complexe** : 5-15 règles
- **Au-delà** : Considérer diviser en plusieurs skills

## Contenu

### Scope approprié

✅ **Bon** : Un skill = une responsabilité claire
- `react-hooks-generator` : Génère des hooks React
- `api-auth-setup` : Configure l'authentification API
- `docker-compose-builder` : Crée des fichiers docker-compose

❌ **Mauvais** : Trop large ou trop étroit
- `react-helper` : Trop vague
- `create-useState-hook` : Trop spécifique
- `fullstack-app-generator` : Trop large

### Documentation progressive

**Niveau 1** : SKILL.md - Vue d'ensemble
```markdown
Ce skill génère des APIs REST avec Express.js
```

**Niveau 2** : Rules - Détails pratiques
```markdown
## Créer un endpoint

1. Définir la route
2. Implémenter le controller
3. Ajouter la validation
```

**Niveau 3** : Assets - Code réutilisable
```typescript
// Template complet prêt à copier
```

**Principe** : L'utilisateur peut s'arrêter à n'importe quel niveau

## Maintenance

### Versioning

Si le skill évolue significativement :

```markdown
---
name: api-generator
description: Génère des APIs REST (v2 - Express + Fastify)
metadata:
  version: 2.0.0
  tags: api, rest, express, fastify
---

## Changelog

### v2.0.0 (2024-03-01)
- Ajout support Fastify
- Nouvelle structure de projet

### v1.0.0 (2024-01-15)
- Version initiale avec Express
```

### Mise à jour

Quand mettre à jour un skill :
- ✅ Framework/outil a une nouvelle version majeure
- ✅ Nouvelles bonnes pratiques émergent
- ✅ Bugs ou imprécisions détectés
- ✅ Feedback utilisateur
- ❌ Changement cosmétique mineur

### Deprecation

Pour retirer un skill obsolète :

```markdown
---
name: old-skill
description: [DEPRECATED] Utilise `new-skill` à la place
---

## ⚠️ Ce skill est obsolète

Utilise plutôt : [new-skill](../new-skill/SKILL.md)

Raison : [Explication de pourquoi]

Ce skill sera supprimé le : [Date]
```

## Qualité

### Checklist de qualité

Avant de considérer un skill "terminé" :

- [ ] Le nom est clair et unique
- [ ] La description est concise (< 15 mots)
- [ ] 3+ déclencheurs sont listés
- [ ] Les exemples de code sont complets
- [ ] Les liens relatifs fonctionnent tous
- [ ] Pas de fautes d'orthographe
- [ ] Le skill a été testé en conditions réelles
- [ ] La documentation est claire pour un débutant

### Testing

```bash
# Vérifier la structure
tree ~/.claude/skills/mon-skill/

# Vérifier le YAML
head -10 ~/.claude/skills/mon-skill/SKILL.md

# Tester l'invocation
# Dire à Claude une phrase déclencheur
```

### Feedback loop

1. Créer une première version simple
2. Tester avec des cas réels
3. Noter ce qui manque
4. Enrichir progressivement
5. Demander du feedback
6. Itérer

## Anti-patterns

### ❌ Skill trop générique

```markdown
---
name: helper
description: Aide avec le code
---
```

→ Trop vague, personne ne sait quand l'utiliser

### ❌ Duplication

Créer `react-component-generator` alors que `react-builder` existe déjà

→ Étendre l'existant plutôt que dupliquer

### ❌ Dépendances cachées

```markdown
## Installation

Exécute : `npm install super-tool`
```

Sans mentionner que `super-tool` nécessite Python 3.11

→ Documenter TOUTES les dépendances

### ❌ Exemples incomplets

```typescript
// Créer un serveur
const app = express();
// ... configure ici
app.listen(3000);
```

→ Fournir du code réellement exécutable

### ❌ Pas de contexte

```markdown
Utilise `myCommand --flag`
```

Sans expliquer quand, pourquoi, ou ce que ça fait

→ Toujours donner le contexte

## Ressources

### Templates réutilisables

- Copier un skill similaire existant
- Adapter la structure à votre besoin
- Garder ce qui marche, changer ce qui diffère

### Documentation de référence

- Voir `/skills/remotion/` pour un exemple complexe
- Voir ce skill (`skill-builder`) pour un exemple moyen
- Consulter les autres skills disponibles

### Aide

Si bloqué :
1. Regarder des exemples similaires
2. Commencer très simple
3. Demander du feedback tôt
4. Itérer par petites améliorations
