# Démos MCP (Model Context Protocol)

Idées de démonstrations utilisant MCP pour connecter les LLM à des outils et services réels.

## Qu'est-ce que MCP ?

Le **Model Context Protocol** est un standard ouvert (Linux Foundation / Agentic AI Foundation) qui permet aux LLM de se connecter à n'importe quel outil ou source de données via un protocole unifié. Pensez-y comme "USB-C pour l'IA" — une prise universelle.

**Chiffres clés (mars 2026)** :
- 97M+ téléchargements SDK mensuels
- 10 000+ serveurs actifs (5 000+ communautaires)
- 2 000+ entrées dans le registre officiel
- Supporté par : Claude, ChatGPT, Cursor, Gemini, VS Code, Replit, Copilot

---

## MCP Servers impressionnants pour démos

### Outils créatifs
| Serveur | Ce qu'il fait |
|---------|--------------|
| **Blender MCP** | Contrôle de modélisation 3D par langage naturel |
| **Figma MCP** | Lecture/création de designs depuis VS Code |
| **Ableton Live MCP** | Production musicale conversationnelle |
| **After Effects MCP** | Montage vidéo piloté par IA |
| **OBS MCP** | Contrôle de streaming live |

### Data & Enterprise
| Serveur | Ce qu'il fait |
|---------|--------------|
| **Stripe MCP** | Facturation, clients, remboursements en langage naturel |
| **Neo4j / FalkorDB MCP** | Knowledge graphs, requêtes Cypher auto |
| **Octagon MCP** | Données financières : filings, earnings, market data |
| **Google DB Toolbox** | Requêtes DB cloud natives via MCP |
| **Supabase MCP** | CRUD complet sur votre DB Supabase |

### Automation & Workflow
| Serveur | Ce qu'il fait |
|---------|--------------|
| **Zapier MCP** | Connexion à 5 000+ apps sans code custom |
| **n8n MCP** | Workflows serverless paramétrés par l'agent |
| **Pipedream MCP** | Node.js/Python workflows déclenchés par l'agent |

### Dev & Security
| Serveur | Ce qu'il fait |
|---------|--------------|
| **GitHub MCP** | Search code, PRs, issues dans les repos |
| **Ghidra MCP** | Reverse engineering de binaires par IA |
| **Semgrep MCP** | Audit sécurité statique automatisé |
| **Sentry MCP** | Monitoring d'erreurs, diagnostic IA |

### Web & Data
| Serveur | Ce qu'il fait |
|---------|--------------|
| **Firecrawl MCP** | N'importe quel site web → données propres pour LLM |
| **Apify MCP** | Web scraping structuré à grande échelle |
| **Bright Data MCP** | Extraction de données web premium |

### Serveurs officiels (reference)
| Serveur | Ce qu'il fait |
|---------|--------------|
| **Filesystem** | Lecture/écriture fichiers sécurisée |
| **Git** | Opérations Git complètes |
| **Memory** | Mémoire persistante par knowledge graph |
| **Sequential Thinking** | Raisonnement étape par étape externalisé |
| **Fetch** | Récupération web + conversion Markdown |

---

## Idées de démos MCP

### 1. **"Design to Deploy" — Figma → App en 5 min**

**Pitch** : Montrez une maquette Figma et regardez Claude la transformer en app déployée, sans toucher au code.

**Chaîne MCP** :
```
Figma MCP (lire le design)
  -> Filesystem MCP (générer le code)
    -> Git MCP (commit)
      -> GitHub MCP (créer PR)
        -> Preview (vérifier dans le navigateur)
```

**Wow factor** : La boucle complète design → code → deploy en conversation
**Complexité** : Moyen (1-2 jours)
**Public cible** : Designers, product managers, CTOs

---

### 2. **"AI Music Producer" — Créer un morceau par conversation**

**Pitch** : "Crée un beat lo-fi hip-hop 8 mesures avec du jazz piano et du vinyl crackle" → Ableton crée le morceau en temps réel.

**MCP** : Ableton Live MCP
**Wow factor** : Manipulation en temps réel de tracks, effets, mixing — tout conversationnel
**Complexité** : Moyen (1-2 jours)
**Public cible** : Musiciens, créatifs, producteurs

---

### 3. **"3D World Builder" — Scène 3D par description**

**Pitch** : Décrivez un monde en texte, Blender le construit. Puis itérez : "rends l'éclairage plus dramatique", "ajoute du brouillard", "change le matériau en verre".

**MCP** : Blender MCP
**Wow factor** : Voir une scène 3D émerger du texte et évoluer en temps réel
**Complexité** : Moyen (1-2 jours)
**Public cible** : Game designers, architectes, créatifs

---

### 4. **"Financial Analyst Agent" — Memo d'investissement auto**

**Pitch** : L'IA pull les données financières, construit un knowledge graph des relations entre entreprises, et produit un memo d'investissement complet avec citations.

**Chaîne MCP** :
```
Octagon MCP (earnings + filings)
  -> Neo4j MCP (knowledge graph relations)
    -> Memory MCP (persister les findings)
      -> Output: Investment memo structuré
```

**Wow factor** : De "analyse cette entreprise" à un rapport pro de 10 pages
**Complexité** : Complexe (3-4 jours)
**Public cible** : Finance, VC, analystes

---

### 5. **"Security Audit Bot" — Audit de sécurité automatisé**

**Pitch** : L'IA reverse-engineer un binaire, identifie les vulnérabilités, et produit un rapport structuré — le tout automatiquement.

**Chaîne MCP** :
```
Ghidra MCP (décompiler + analyser)
  -> Semgrep MCP (scan statique code source)
    -> Filesystem MCP (écrire le rapport)
      -> Git MCP (commit le rapport)
```

**Wow factor** : Audit de sécurité complet en 10 min au lieu de 2 jours
**Complexité** : Complexe (3-5 jours)
**Public cible** : DevSecOps, pentesters, CTOs

---

### 6. **"Workflow Orchestrator" — Planifier un offsite d'équipe**

**Pitch** : "Organise notre offsite d'équipe à Marseille" → L'IA cherche des lieux, vérifie les calendriers, propose des options dans Slack, et réserve une fois approuvé.

**Chaîne MCP** :
```
Google Maps MCP (trouver des lieux)
  -> Google Calendar MCP (checker dispos)
    -> Slack MCP (poster les propositions)
      -> Stripe MCP (payer la réservation)
```

**Wow factor** : Orchestration multi-outil en une seule conversation
**Complexité** : Moyen (2-3 jours)
**Public cible** : Office managers, dirigeants, RH

---

### 7. **"Live Dashboard Builder" — DB → Dashboard en 5 min**

**Pitch** : Connectez votre base de données, posez des questions en français, obtenez un dashboard interactif.

**Chaîne MCP** :
```
Database MCP (requêter les données)
  -> Sequential Thinking MCP (raisonner sur les visualisations)
    -> Filesystem MCP (générer HTML/React dashboard)
      -> Preview (afficher et itérer live)
```

**Wow factor** : "Montre-moi les ventes par région ce trimestre" → graphique interactif en 30s
**Complexité** : Moyen (1-2 jours)
**Public cible** : Data analysts, dirigeants, product managers

---

### 8. **"Code Migration Agent" — Moderniser un legacy codebase**

**Pitch** : L'IA analyse un vieux codebase, réécrit les fichiers dans un framework moderne, crée des PRs avec explications.

**Chaîne MCP** :
```
Git MCP (analyser le code existant)
  -> Filesystem MCP (réécrire les fichiers)
    -> GitHub MCP (créer PRs avec descriptions)
      -> Sentry MCP (vérifier pas de regression)
```

**Wow factor** : Migration Express.js → Hono/Fastify en une conversation
**Complexité** : Complexe (3-5 jours)
**Public cible** : Tech leads, développeurs, CTOs

---

### 9. **"Zapier on Steroids" — Automatisation par conversation**

**Pitch** : "Quand je reçois un email de @client.com, extrais les données, mets-les dans le CRM, et envoie un accusé de réception personnalisé."

**MCP** : Zapier MCP (5000+ apps) ou n8n MCP
**Wow factor** : Créer des automatisations complexes sans interface graphique, juste en parlant
**Complexité** : Rapide (2-4h)
**Public cible** : Ops, sales, dirigeants PME

---

### 10. **"MCP Hub" — Démo meta : montrer MCP lui-même**

**Pitch** : Démonstration pédagogique de MCP. Montrez comment ajouter un nouveau serveur MCP en 5 min et donnez de nouveaux pouvoirs à l'IA en live.

**Flow** :
1. Claude sans MCP → "Je ne peux pas accéder à vos fichiers"
2. Ajout Filesystem MCP → "Maintenant je vois votre projet"
3. Ajout GitHub MCP → "Je peux aussi voir vos PRs"
4. Ajout custom MCP → "Et votre API interne aussi"

**Wow factor** : Le public comprend le concept en voyant l'IA gagner des capacités en direct
**Complexité** : Rapide (1-2h)
**Public cible** : Développeurs, architectes, décideurs tech

---

## Tips pour démos MCP

### Ce qui impressionne le plus
1. **Le chaînage multi-MCP** : Un seul prompt déclenche 3-4 outils différents
2. **L'effet "plug and play"** : Ajouter un serveur = nouvelle capacité instantanée
3. **Le contrôle d'outils créatifs** : Blender, Figma, Ableton répondent à la voix
4. **L'orchestration invisible** : L'IA choisit seule quels outils utiliser

### Pièges à éviter
- Tester TOUS les MCP servers avant la démo (certains sont instables)
- Avoir des fallbacks si un serveur est lent
- Ne pas empiler trop de MCP — 3-4 max pour une démo claire
- Préparer des exemples de prompts qui montrent bien le chaînage

### Registres MCP pour découvrir des serveurs
| Registre | URL |
|----------|-----|
| **Registre officiel** | registry.modelcontextprotocol.io |
| **MCP.so** | mcp.so |
| **MCPServers.org** | mcpservers.org |
| **mcp-awesome.com** | mcp-awesome.com |
| **APITracker** | apitracker.io/mcp-servers |
