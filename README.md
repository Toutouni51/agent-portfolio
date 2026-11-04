# Portfolio d'agents IA

Agents et skills pour [Claude Code](https://claude.com/claude-code) que j'utilise pour déléguer, prospecter et préparer des démonstrations d'IA.

## Agents

Un agent travaille dans son propre contexte et renvoie son résultat à l'assistant principal.

| Agent | Modèle | Rôle |
|---|---|---|
| [deep-reasoner](agents/deep-reasoner.md) | Opus | Planification, architecture, débogage complexe et conception d'algorithmes. Renvoie une recommandation, pas tout le raisonnement. |
| [Executor](agents/executor.md) | Sonnet | Tâches mécaniques dont l'approche est déjà décidée : tests, renommages, code répétitif. |
| [prospection-clubs-foot](agents/prospection-clubs-foot.md) | Opus | À partir d'un département, trouve les clubs de football de R1, N2 et N1 et leurs contacts publics, puis remplit un fichier Excel en indiquant les sources et un niveau de confiance. |

`deep-reasoner` et `Executor` fonctionnent ensemble : le premier décide quoi faire, le second l'exécute avec un modèle moins coûteux.

## Skills

Un skill est un ensemble d'instructions que l'assistant charge et suit dans la conversation en cours.

| Skill | Rôle |
|---|---|
| [ai-demo-ideator](skills/ai-demo-ideator/SKILL.md) | Génère des idées de démonstrations d'IA générative, avec outils et plateformes peu connus. |
| [skill-builder](skills/skill-builder/SKILL.md) | Guide la création de nouveaux skills. |
| [school-contacts](skills/school-contacts/SKILL.md) | Recherche les responsables académiques d'une école supérieure privée à partir de sources publiques. |
| [sponsors-evenement-local](skills/sponsors-evenement-local/SKILL.md) | Trouve et note des entreprises locales susceptibles de sponsoriser un événement sportif associatif. |

## Installation

Copie les fichiers voulus dans ton dossier Claude Code :

```bash
cp agents/*.md ~/.claude/agents/
cp -R skills/* ~/.claude/skills/
```

## Bon usage

Les outils de prospection se limitent aux sources publiques et n'inventent aucune coordonnée. Vérifie les informations trouvées, et respecte le RGPD et les règles de prospection applicables avant tout contact.
