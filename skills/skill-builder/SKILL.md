---
name: skill-builder
description: Guide pour créer de nouveaux skills personnalisés pour Codex
metadata:
  tags: skills, automation, meta, builder, tools
---

## Quand utiliser ce skill

Utilise ce skill dès que l'utilisateur mentionne :
- "créer un skill" / "nouveau skill" / "créer un nouveau skill"
- "automatiser une tâche" / "automatiser X"
- "construire un outil" / "construire un agent"
- "j'aimerais que tu saches faire X"
- "modifier un skill" / "améliorer un skill existant"
- "ajouter une fonctionnalité à un skill"

## Ce que fait ce skill

Ce skill guide la création de nouveaux skills personnalisés en :
1. Posant des questions pour comprendre les besoins
2. Générant la structure de fichiers appropriée
3. Créant le fichier SKILL.md avec le bon format
4. Ajoutant des fichiers de règles si nécessaire
5. Créant des exemples de code et assets

## Structure d'un skill

Un skill Codex suit cette structure :

```
~/.Codex/skills/nom-du-skill/
├── SKILL.md              # Fichier principal (requis)
└── rules/                # Règles détaillées (optionnel)
    ├── rule1.md
    ├── rule2.md
    └── assets/           # Exemples de code (optionnel)
        └── example.tsx
```

## Format du fichier SKILL.md

Référence : [./rules/skill-format.md](./rules/skill-format.md)

## Processus de création

Référence : [./rules/creation-process.md](./rules/creation-process.md)

## Exemples de skills

Référence : [./rules/examples.md](./rules/examples.md)

## Activation du skill

Après création, le skill sera automatiquement disponible. Pour créer un lien symbolique si nécessaire :

```bash
ln -s ~/.Codex/skills/nom-du-skill ~/.Codex/skills/nom-court
```

## Tips et bonnes pratiques

Référence : [./rules/best-practices.md](./rules/best-practices.md)
