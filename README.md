# Portfolio d'agents IA

Agents et skills pour [Claude Code](https://claude.com/claude-code) que j'utilise pour déléguer, prospecter et préparer des démonstrations d'IA.

## Agents

Un agent travaille dans son propre contexte et renvoie son résultat à l'assistant principal.

| Agent | Modèle | Rôle |
|---|---|---|
| [deep-reasoner](agents/deep-reasoner.md) | Opus | Planification, architecture, débogage complexe et conception d'algorithmes. Renvoie une recommandation, pas tout le raisonnement. |
| [Executor](agents/executor.md) | Sonnet | Tâches mécaniques dont l'approche est déjà décidée : tests, renommages, code répétitif. |
| [prospection-clubs-foot](agents/prospection-clubs-foot.md) | Opus | À partir d'un département, trouve les clubs de football de R1, N2 et N1 et leurs contacts publics, puis remplit un fichier Excel en indiquant les sources et un niveau de confiance. |

| [cadreur-business](agents/cadreur-business.md) | Opus | Évalue une idée avant de la construire : client, modèle économique, hypothèses risquées et verdict GO, À REVOIR ou STOP. |
| [testeur-utilisateur](agents/testeur-utilisateur.md) | Sonnet | Teste une application comme un vrai client et rend un rapport sans jargon, classé par gravité et appuyé sur des preuves. |
| [controleur-mise-en-ligne](agents/controleur-mise-en-ligne.md) | Opus | Contrôle les secrets, les données personnelles, les liens privés et les sauvegardes avant publication, et rend un feu vert, orange ou rouge. |

`deep-reasoner` et `Executor` fonctionnent ensemble : le premier décide quoi faire, le second l'exécute avec un modèle moins coûteux.

`cadreur-business`, `testeur-utilisateur` et `controleur-mise-en-ligne` accompagnent un projet no-code de l'idée à la mise en ligne. Ils sont inspirés d'agents de [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) et de [VoltAgent/awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents), publiés sous licence MIT. Chaque fichier cite ses sources.

## Skills

Un skill est un ensemble d'instructions que l'assistant charge et suit dans la conversation en cours.

| Skill | Rôle |
|---|---|
| [ai-demo-ideator](skills/ai-demo-ideator/SKILL.md) | Génère des idées de démonstrations d'IA générative, avec outils et plateformes peu connus. |
| [skill-builder](skills/skill-builder/SKILL.md) | Guide la création de nouveaux skills. |
| [school-contacts](skills/school-contacts/SKILL.md) | Recherche les responsables académiques d'une école supérieure privée à partir de sources publiques. |
| [sponsors-evenement-local](skills/sponsors-evenement-local/SKILL.md) | Trouve et note des entreprises locales susceptibles de sponsoriser un événement sportif associatif. |

## Skills externes que j'utilise

Ces projets ne sont pas de moi : ils appartiennent à leurs auteurs et ne sont pas copiés dans ce dépôt.

| Skill | Dépôt | Rôle |
|---|---|---|
| ppt-agent | [Akxan/ppt-agent-skill](https://github.com/Akxan/ppt-agent-skill), qui s'appuie sur [sunbigfly/ppt-agent-skills](https://github.com/sunbigfly/ppt-agent-skills) | Génère une présentation complète, de la recherche jusqu'au fichier PPTX. |
| remotion | [remotion-dev/skills](https://github.com/remotion-dev/skills) | Bonnes pratiques pour créer des vidéos en React avec Remotion. |
| find-skills | [vercel-labs/skills](https://github.com/vercel-labs/skills) | Aide à trouver et installer de nouveaux skills. |

## Installation

Pour installer les agents et skills de ce dépôt, copie les fichiers voulus dans ton dossier Claude Code :

```bash
cp agents/*.md ~/.claude/agents/
cp -R skills/* ~/.claude/skills/
```

## Bon usage

Les outils de prospection se limitent aux sources publiques et n'inventent aucune coordonnée. Vérifie les informations trouvées, et respecte le RGPD et les règles de prospection applicables avant tout contact.
