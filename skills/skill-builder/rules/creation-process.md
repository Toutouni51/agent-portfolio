# Processus de création d'un skill

## Étape 1 : Collecte d'informations

Pose ces questions à l'utilisateur pour comprendre ses besoins :

### Questions essentielles

1. **Quel est l'objectif du skill ?**
   - Qu'est-ce que ce skill doit automatiser ?
   - Quel problème résout-il ?

2. **Quand doit-il être utilisé ?**
   - Quels mots-clés/phrases doivent le déclencher ?
   - Dans quel contexte (type de projet, fichiers, etc.) ?

3. **Quel est le nom du skill ?**
   - Nom court et descriptif (kebab-case)
   - Éviter les noms trop génériques

4. **Complexité du skill ?**
   - **Simple** : Un seul fichier SKILL.md suffit
   - **Moyen** : SKILL.md + 2-5 fichiers de règles
   - **Complexe** : Structure complète avec règles et assets

### Questions pour skills complexes

5. **Quelles sont les sous-fonctionnalités ?**
   - Lister les différentes tâches/règles nécessaires
   - Chaque règle majeure = un fichier .md séparé

6. **Y a-t-il des exemples de code à inclure ?**
   - Templates
   - Snippets réutilisables
   - Fichiers d'exemple complets

7. **Environnement/outils spécifiques ?**
   - Framework (React, Vue, Django, etc.)
   - CLI ou API
   - Fichiers de configuration

## Étape 2 : Créer la structure de base

```bash
# Créer le dossier du skill
mkdir -p ~/.claude/skills/nom-du-skill/rules/assets

# Créer le fichier principal
touch ~/.claude/skills/nom-du-skill/SKILL.md
```

## Étape 3 : Rédiger le SKILL.md

Utilise le template suivant :

```markdown
---
name: nom-du-skill
description: Description concise (1 ligne max)
metadata:
  tags: tag1, tag2, tag3
---

## Quand utiliser ce skill

Utilise ce skill quand l'utilisateur :
- [Déclencheur 1]
- [Déclencheur 2]
- [Déclencheur 3]

## Ce que fait ce skill

Ce skill permet de :
1. [Fonctionnalité 1]
2. [Fonctionnalité 2]
3. [Fonctionnalité 3]

## Comment utiliser

[Pour les skills simples : mettre le contenu directement ici]
[Pour les skills complexes : référencer les fichiers de règles]

- [rules/rule1.md](rules/rule1.md) - Description de la règle 1
- [rules/rule2.md](rules/rule2.md) - Description de la règle 2
```

## Étape 4 : Créer les fichiers de règles

Pour chaque fonctionnalité majeure, crée un fichier dans `rules/` :

### Template de fichier de règle

```markdown
# Nom de la règle

## Description

Explication claire de ce que fait cette règle.

## Quand l'utiliser

Contexte spécifique pour cette règle :
- Cas d'usage 1
- Cas d'usage 2

## Comment faire

### Étape 1 : [Titre de l'étape]

Instructions détaillées...

```bash
# Commandes si nécessaire
```

### Étape 2 : [Titre de l'étape]

Plus d'instructions...

```javascript
// Exemple de code si nécessaire
```

## Exemples

### Exemple 1 : [Titre]

```[language]
// Code d'exemple complet
```

### Exemple 2 : [Titre]

```[language]
// Autre exemple
```

## Bonnes pratiques

- Bonne pratique 1
- Bonne pratique 2
- Bonne pratique 3

## Erreurs courantes

- Erreur 1 : Comment l'éviter
- Erreur 2 : Comment la corriger
```

## Étape 5 : Ajouter des assets (si nécessaire)

Pour les exemples de code complets :

```bash
# Créer un fichier d'exemple
touch ~/.claude/skills/nom-du-skill/rules/assets/example.tsx
```

Puis référence-le dans les règles :

```markdown
Voir l'exemple complet : [./assets/example.tsx](./assets/example.tsx)
```

## Étape 6 : Tester le skill

1. **Vérifier la structure** :
   ```bash
   ls -R ~/.claude/skills/nom-du-skill/
   ```

2. **Vérifier le format YAML** :
   - Le frontmatter est correct
   - Les liens relatifs fonctionnent

3. **Tester l'invocation** :
   - Dire une phrase déclencheur à Claude
   - Vérifier que le skill est utilisé

## Étape 7 : Créer un lien symbolique (optionnel)

Pour un nom court ou alias :

```bash
ln -s ~/.claude/skills/nom-du-skill ~/.claude/skills/alias
```

## Checklist finale

- [ ] Le nom du skill est unique et descriptif
- [ ] La description est concise et claire
- [ ] Les déclencheurs sont bien définis
- [ ] Le SKILL.md suit le format standard
- [ ] Tous les liens relatifs fonctionnent
- [ ] Les exemples de code sont complets et fonctionnels
- [ ] Le skill a été testé avec des phrases déclencheurs
- [ ] La documentation est claire et sans ambiguïté

## Exemples de durée de création

- **Skill simple** : 5-10 minutes
- **Skill moyen** : 15-30 minutes
- **Skill complexe** : 30-60 minutes

## Tips

1. Commence simple, enrichis progressivement
2. Copie la structure d'un skill existant similaire
3. Teste fréquemment pendant la création
4. Documente au fur et à mesure
5. Demande du feedback à l'utilisateur
