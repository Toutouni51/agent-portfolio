# Exemples de skills

Cette page présente des exemples de skills pour différents cas d'usage.

## Exemple 1 : Skill simple (sans règles)

### Structure
```
~/.claude/skills/commit-helper/
└── SKILL.md
```

### SKILL.md
```markdown
---
name: commit-helper
description: Crée des commits Git avec messages formatés selon Conventional Commits
metadata:
  tags: git, commit, version-control
---

## Quand utiliser ce skill

Utilise ce skill quand l'utilisateur demande :
- "commit mes changements"
- "créer un commit"
- "enregistrer le code"
- Mentionne "conventional commits"

## Ce que fait ce skill

Ce skill automatise la création de commits Git en :
1. Analysant les changements avec `git status` et `git diff`
2. Générant un message au format Conventional Commits
3. Créant le commit avec le bon format

## Format des messages

```
<type>(<scope>): <description>

[body optionnel]

[footer optionnel]
```

### Types disponibles
- **feat**: Nouvelle fonctionnalité
- **fix**: Correction de bug
- **docs**: Documentation
- **style**: Formatage (pas de changement de code)
- **refactor**: Refactoring
- **test**: Ajout/modification de tests
- **chore**: Tâches de maintenance

### Exemples
```bash
feat(auth): add login with OAuth2
fix(api): correct user validation error
docs(readme): update installation instructions
```

## Processus

1. Exécuter `git status` et `git diff`
2. Analyser les changements
3. Proposer un type et scope appropriés
4. Générer la description
5. Créer le commit :
   ```bash
   git add [fichiers]
   git commit -m "type(scope): description"
   ```
```

---

## Exemple 2 : Skill moyen (avec règles)

### Structure
```
~/.claude/skills/react-component-generator/
├── SKILL.md
└── rules/
    ├── functional-component.md
    ├── class-component.md
    └── hooks.md
```

### SKILL.md
```markdown
---
name: react-component-generator
description: Génère des composants React avec bonnes pratiques
metadata:
  tags: react, component, generator, typescript
---

## Quand utiliser ce skill

Utilise ce skill quand l'utilisateur demande :
- "créer un composant React"
- "nouveau composant [nom]"
- "générer un component"
- Mentionne TypeScript + React

## Ce que fait ce skill

Ce skill génère des composants React en :
1. Demandant le type (fonctionnel/classe)
2. Créant la structure du fichier
3. Ajoutant TypeScript types
4. Incluant les bonnes pratiques

## Comment utiliser

Selon le type de composant :

- [rules/functional-component.md](rules/functional-component.md) - Composants fonctionnels (recommandé)
- [rules/class-component.md](rules/class-component.md) - Composants classe (legacy)
- [rules/hooks.md](rules/hooks.md) - Hooks personnalisés

## Structure de fichier générée

```
src/components/ComponentName/
├── ComponentName.tsx
├── ComponentName.module.css
├── ComponentName.test.tsx
└── index.ts
```
```

### rules/functional-component.md
```markdown
# Composants fonctionnels React

## Description

Génère un composant fonctionnel React avec TypeScript et bonnes pratiques modernes.

## Template de base

```tsx
import React from 'react';
import styles from './ComponentName.module.css';

interface ComponentNameProps {
  // Props ici
}

export const ComponentName: React.FC<ComponentNameProps> = (props) => {
  return (
    <div className={styles.container}>
      {/* Contenu */}
    </div>
  );
};
```

## Avec hooks

```tsx
import React, { useState, useEffect } from 'react';
import styles from './ComponentName.module.css';

interface ComponentNameProps {
  initialValue?: string;
}

export const ComponentName: React.FC<ComponentNameProps> = ({
  initialValue = ''
}) => {
  const [value, setValue] = useState(initialValue);

  useEffect(() => {
    // Side effects
  }, [value]);

  return (
    <div className={styles.container}>
      <input
        value={value}
        onChange={(e) => setValue(e.target.value)}
      />
    </div>
  );
};
```

## Bonnes pratiques

1. **Props interface** : Toujours typer les props
2. **Destructuring** : Déstructurer les props dans les paramètres
3. **Default props** : Utiliser les valeurs par défaut ES6
4. **CSS Modules** : Importer les styles localement
5. **Export named** : Utiliser des exports nommés
```

---

## Exemple 3 : Skill complexe (avec assets)

### Structure
```
~/.claude/skills/api-rest-generator/
├── SKILL.md
└── rules/
    ├── project-setup.md
    ├── routes.md
    ├── controllers.md
    ├── models.md
    ├── middleware.md
    └── assets/
        ├── route-example.ts
        ├── controller-example.ts
        └── model-example.ts
```

### SKILL.md
```markdown
---
name: api-rest-generator
description: Génère une API REST complète avec Express.js et TypeScript
metadata:
  tags: api, rest, express, typescript, backend
---

## Quand utiliser ce skill

Utilise ce skill quand l'utilisateur :
- Veut créer une API REST
- Demande d'ajouter des endpoints
- Mentionne Express.js
- Veut structurer un backend

## Ce que fait ce skill

Ce skill génère automatiquement :
1. Structure de projet API complète
2. Routes REST (GET, POST, PUT, DELETE)
3. Controllers avec logique métier
4. Models (TypeScript interfaces ou ORM)
5. Middleware (auth, validation, error handling)
6. Configuration TypeScript

## Comment utiliser

### Démarrage
[rules/project-setup.md](rules/project-setup.md) - Initialiser le projet

### Composants
- [rules/routes.md](rules/routes.md) - Créer des routes
- [rules/controllers.md](rules/controllers.md) - Implémenter les controllers
- [rules/models.md](rules/models.md) - Définir les models
- [rules/middleware.md](rules/middleware.md) - Ajouter des middleware

## Architecture générée

```
api-project/
├── src/
│   ├── routes/
│   │   └── users.routes.ts
│   ├── controllers/
│   │   └── users.controller.ts
│   ├── models/
│   │   └── user.model.ts
│   ├── middleware/
│   │   ├── auth.ts
│   │   └── validation.ts
│   ├── types/
│   │   └── index.ts
│   ├── utils/
│   │   └── errors.ts
│   └── index.ts
├── tsconfig.json
└── package.json
```
```

### rules/routes.md
```markdown
# Créer des routes REST

## Description

Génère des routes Express.js avec TypeScript pour un endpoint REST.

## Template de base

Voir l'exemple complet : [./assets/route-example.ts](./assets/route-example.ts)

```typescript
import { Router } from 'express';
import { UserController } from '../controllers/user.controller';
import { authMiddleware } from '../middleware/auth';

const router = Router();
const controller = new UserController();

// GET /api/users
router.get('/', controller.getAll);

// GET /api/users/:id
router.get('/:id', controller.getById);

// POST /api/users
router.post('/', authMiddleware, controller.create);

// PUT /api/users/:id
router.put('/:id', authMiddleware, controller.update);

// DELETE /api/users/:id
router.delete('/:id', authMiddleware, controller.delete);

export default router;
```

## Bonnes pratiques

1. **Grouper par ressource** : Un fichier de routes par ressource
2. **Middleware** : Appliquer l'auth et validation au niveau des routes
3. **Versioning** : Préfixer avec `/api/v1`
4. **RESTful** : Respecter les conventions REST
```

### rules/assets/route-example.ts
```typescript
import { Router } from 'express';
import { UserController } from '../controllers/user.controller';
import { authMiddleware } from '../middleware/auth';
import { validateUser } from '../middleware/validation';

const router = Router();
const controller = new UserController();

/**
 * @route   GET /api/v1/users
 * @desc    Get all users
 * @access  Public
 */
router.get('/', controller.getAll);

/**
 * @route   GET /api/v1/users/:id
 * @desc    Get user by ID
 * @access  Public
 */
router.get('/:id', controller.getById);

/**
 * @route   POST /api/v1/users
 * @desc    Create new user
 * @access  Private
 */
router.post('/', [authMiddleware, validateUser], controller.create);

/**
 * @route   PUT /api/v1/users/:id
 * @desc    Update user
 * @access  Private
 */
router.put('/:id', [authMiddleware, validateUser], controller.update);

/**
 * @route   DELETE /api/v1/users/:id
 * @desc    Delete user
 * @access  Private
 */
router.delete('/:id', authMiddleware, controller.delete);

export default router;
```

---

## Exemple 4 : Skill pour environnement spécifique

### Google Antigravity Component Generator

```markdown
---
name: google-antigravity-component
description: Génère des composants pour Google Antigravity
metadata:
  tags: google, antigravity, component, ide
---

## Quand utiliser ce skill

Utilise ce skill dans Google Antigravity quand l'utilisateur :
- Demande de créer un composant Antigravity
- Veut générer une interface utilisateur
- Mentionne "panneau", "vue", ou "widget"

## Ce que fait ce skill

Ce skill génère des composants Antigravity en :
1. Créant la structure du composant
2. Ajoutant les imports Antigravity
3. Configurant le lifecycle
4. Intégrant avec l'IDE

## Template de composant

```typescript
import { Component, Panel } from '@google/antigravity';

export class MyComponent extends Component {
  private panel: Panel;

  constructor() {
    super();
    this.initPanel();
  }

  private initPanel() {
    this.panel = new Panel({
      title: 'My Component',
      position: 'sidebar'
    });
  }

  render() {
    return `
      <div class="antigravity-component">
        <!-- Contenu -->
      </div>
    `;
  }
}
```

## Intégration

```typescript
// Dans manifest.json
{
  "components": [
    {
      "id": "my-component",
      "class": "MyComponent",
      "activation": "onLoad"
    }
  ]
}
```
```

---

## Tips pour créer vos propres exemples

1. **Commencer du simple** : Faire un skill basique d'abord
2. **Tester rapidement** : Valider que ça fonctionne
3. **Enrichir progressivement** : Ajouter règles et assets
4. **Documenter clairement** : Exemples concrets et complets
5. **Réutiliser** : S'inspirer d'autres skills similaires
