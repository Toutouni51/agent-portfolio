# Guide d'implémentation technique

Stacks recommandées, estimations de temps et pièges à éviter pour vos démos IA.

## Architectures types

### Architecture 1 : **Simple Web App**
**Pour** : Démos rapides, POCs, interfaces simples

```
Frontend (React/Next.js)
    |
Claude API / OpenAI API
    |
Response -> UI
```

**Stack recommandée** :
- **Frontend** : Next.js 15 (App Router) + Tailwind
- **API** : Route handlers Next.js
- **LLM** : Claude Sonnet 4.6 via SDK (`claude-sonnet-4-6`)
- **Deploy** : Vercel (1-click)

**Temps d'implémentation** : 2-4h

**Template starter** :
```bash
npx create-next-app@latest ai-demo
cd ai-demo
npm install @anthropic-ai/sdk
```

---

### Architecture 2 : **Multimodal App**
**Pour** : Vision, audio, fichiers

```
Frontend (Upload + Display)
    |
Backend (Processing)
    |
Multiple AI Services (Claude, GPT Image 1.5, Whisper)
    |
Aggregation + Response
```

**Stack recommandée** :
- **Frontend** : React + Vite + Tailwind
- **Backend** : Node.js + Express (ou Next.js API)
- **Storage** : S3 / Cloudflare R2 (fichiers temporaires)
- **LLMs** : Claude Opus 4.6 (vision) + OpenAI (Whisper, GPT Image 1.5)
- **Deploy** : Railway / Render

**Temps d'implémentation** : 1-2 jours

---

### Architecture 3 : **Agentic System**
**Pour** : Workflows complexes, agents autonomes

```
User Input
    |
Orchestrator (Claude Agent SDK / LangGraph)
    |
+-------------+-------------+-------------+
Agent 1       Agent 2       Agent 3
(Research)    (Execute)     (Verify)
+-------------+-------------+-------------+
    |
Result Aggregation
    |
Output + Memory Update
```

**Stack recommandée** :
- **Orchestration** : Claude Agent SDK / LangGraph / CrewAI
- **LLM** : Claude Opus 4.6 (extended thinking + tool use)
- **MCP** : Filesystem + Git + Memory + services métier
- **Memory** : Redis + PostgreSQL (vector embeddings)
- **Deploy** : Docker Compose

**Temps d'implémentation** : 3-5 jours

---

### Architecture 4 : **MCP-Powered App**
**Pour** : Intégration multi-outils, workflows connectés

```
User (Claude Code / Chat)
    |
Claude + MCP Client
    |
+--------+--------+--------+--------+
MCP 1    MCP 2    MCP 3    MCP 4
(Slack)  (GitHub) (DB)     (Custom)
+--------+--------+--------+--------+
    |
Orchestrated Actions
```

**Stack recommandée** :
- **Client** : Claude Code / Claude Desktop / SDK custom
- **LLM** : Claude Opus 4.6 ou Sonnet 4.6
- **MCP Servers** : Combinaison officiel + communautaire
- **Transport** : Streamable HTTP (remote) ou stdio (local)
- **Auth** : OAuth 2.1 pour les serveurs tiers

**Temps d'implémentation** : 1-3 jours (selon nombre de MCP)

---

### Architecture 5 : **Real-time / Streaming**
**Pour** : Chat, live analysis, collaborative

```
WebSocket Connection
    |
Stream Processing
    |
LLM Streaming Response
    |
Progressive UI Update
```

**Stack recommandée** :
- **Frontend** : React + Socket.io-client
- **Backend** : Node.js + Socket.io
- **LLM** : Claude SDK (streaming mode)
- **Deploy** : Fly.io (WebSocket support)

**Temps d'implémentation** : 1-2 jours

---

## Stack Recommendations par Use Case

### Use Case : **Document Analysis**

**Stack** :
```typescript
// Upload
react-dropzone + Next.js API route

// Parsing
pdf-parse (PDF) | mammoth (DOCX) | xlsx (Excel)

// Processing
Claude Opus 4.6 (1M context) — model: 'claude-opus-4-6'

// Display
react-pdf + highlight.js
```

**Exemple code** :
```typescript
// app/api/analyze/route.ts
import Anthropic from '@anthropic-ai/sdk';
import pdfParse from 'pdf-parse';

export async function POST(request: Request) {
  const formData = await request.formData();
  const file = formData.get('file') as File;

  const buffer = await file.arrayBuffer();
  const pdfData = await pdfParse(Buffer.from(buffer));

  const anthropic = new Anthropic({ apiKey: process.env.ANTHROPIC_API_KEY });
  const response = await anthropic.messages.create({
    model: 'claude-sonnet-4-6',
    max_tokens: 4096,
    messages: [{
      role: 'user',
      content: `Analyze this document and extract key information:\n\n${pdfData.text}`
    }]
  });

  return Response.json({ analysis: response.content[0].text });
}
```

**Temps** : 3-4h

---

### Use Case : **Image Generation + Analysis**

**Stack** :
```typescript
// Generate
GPT Image 1.5 (via OpenAI API) ou FLUX 2 Pro

// Analyze
Claude Sonnet 4.6 (vision) — model: 'claude-sonnet-4-6'

// Display
Next.js Image component + Framer Motion

// Storage (if persistent)
Cloudflare R2 (S3-compatible)
```

**Exemple code** :
```typescript
// Generate image
const imageResponse = await openai.images.generate({
  model: "gpt-image-1.5",
  prompt: userPrompt,
  size: "1024x1024",
  quality: "hd",
});

// Analyze with Claude
const analysisResponse = await anthropic.messages.create({
  model: 'claude-sonnet-4-6',
  max_tokens: 1024,
  messages: [{
    role: 'user',
    content: [
      {
        type: 'image',
        source: {
          type: 'url',
          url: imageResponse.data[0].url
        }
      },
      {
        type: 'text',
        text: 'Analyze this generated image and suggest improvements.'
      }
    ]
  }]
});
```

**Temps** : 2-3h

---

### Use Case : **Voice Interaction**

**Stack** :
```typescript
// Input
Web Audio API (browser mic)

// Transcription
Whisper API (OpenAI)

// Processing
Claude Sonnet 4.6

// Output
ElevenLabs Conversational AI 2.0

// Playback
HTML5 Audio API
```

**Temps** : 1 jour

---

### Use Case : **RAG (Retrieval Augmented Generation)**

**Stack** :
```typescript
// Embeddings
text-embedding-3-small (OpenAI) ou Cohere Embed v4

// Vector DB
Pinecone | Qdrant | Supabase (pgvector)

// Retrieval + Generation
LangChain + Claude Opus 4.6 (1M context)

// Frontend
Next.js + streaming responses
```

**Exemple code** :
```typescript
import { OpenAIEmbeddings } from '@langchain/openai';
import { PineconeStore } from '@langchain/pinecone';
import { ChatAnthropic } from '@langchain/anthropic';

const embeddings = new OpenAIEmbeddings();

const vectorStore = await PineconeStore.fromExistingIndex(embeddings, {
  pineconeIndex: index
});
const docs = await vectorStore.similaritySearch(query, 3);

const model = new ChatAnthropic({ modelName: 'claude-opus-4-6' });
const response = await model.invoke([
  {
    role: 'user',
    content: `Context:\n${docs.map(d => d.pageContent).join('\n\n')}\n\nQuestion: ${query}`
  }
]);
```

**Temps** : 1-2 jours

---

### Use Case : **Agent avec MCP**

**Stack** :
```typescript
// Agent framework
Claude Agent SDK (Python) ou @anthropic-ai/sdk (Node)

// MCP Servers
@modelcontextprotocol/server-filesystem
@modelcontextprotocol/server-git
+ serveurs custom

// Orchestration
Multi-turn conversation avec tool_use
```

**Exemple code** :
```python
# Agent SDK avec MCP
from claude_agent_sdk import Agent, MCPServer

agent = Agent(
    model="claude-sonnet-4-6",
    mcp_servers=[
        MCPServer("filesystem", command="npx @modelcontextprotocol/server-filesystem /path"),
        MCPServer("github", command="npx @modelcontextprotocol/server-github"),
    ],
    instructions="You are a code review agent. Analyze repos and suggest improvements."
)

result = await agent.run("Review the latest PR and suggest improvements")
```

**Temps** : 1-2 jours

---

## Estimation de temps réaliste

### Facteurs qui influencent la durée

| Facteur | Impact |
|---------|--------|
| Déjà un template | -50% temps |
| API familière | -30% temps |
| UI complexe | +50% temps |
| Première fois avec techno | +100% temps |
| Besoin auth | +2-4h |
| Besoin DB | +3-6h |
| Besoin deploy | +1-2h |
| Setup MCP servers | +1-3h |

### Estimation par type de démo

#### Rapide (2-4h)
- 1 seule API (Claude ou OpenAI)
- UI simple (1-2 écrans)
- Pas de DB / Pas d'auth
- Deploy simple (Vercel)

**Exemples** : Text analyzer, prompt optimizer, chatbot, image describer

#### Moyen (1-2 jours)
- 2-3 APIs
- UI multi-étapes
- File upload/processing
- Streaming responses
- 1-2 MCP servers

**Exemples** : Document analyzer, voice assistant, MCP workflow demo

#### Complexe (3-5 jours)
- Multiple services + MCP
- DB persistante + Auth
- Background jobs
- Agentic workflows

**Exemples** : Multi-agent system, RAG complet, plateforme multi-user

---

## UI/UX pour démos

### Principe : **Show, don't tell**

**Bon** : Résultat visible immédiatement
**Mauvais** : Logs techniques / loading infini

### Components recommandés

**Librairies** :
- **UI** : shadcn/ui (Tailwind components)
- **Animation** : Framer Motion
- **Charts** : Recharts
- **Markdown** : react-markdown
- **Code** : Shiki
- **Toast** : Sonner
- **Forms** : React Hook Form

---

## Pièges à éviter

### 1. **Rate Limits**
```typescript
import pRetry from 'p-retry';

const result = await pRetry(
  () => anthropic.messages.create({
    model: 'claude-sonnet-4-6',
    // ...
  }),
  { retries: 3 }
);
```

### 2. **Coûts incontrôlés**
```typescript
if (usageToday > MAX_REQUESTS_PER_DAY) {
  throw new Error('Demo limit reached');
}
```

### 3. **Slow responses**
```typescript
// Toujours streamer
const stream = await anthropic.messages.stream({
  model: 'claude-sonnet-4-6',
  // ...
});

for await (const chunk of stream) {
  updateUI(chunk.delta.text);
}
```

### 4. **Prompts fragiles**
```typescript
const systemPrompt = `You are an expert analyst.
Always respond in JSON format:
{
  "summary": "...",
  "key_points": ["...", "..."],
  "confidence": 0.9
}`;

const response = await anthropic.messages.create({
  model: 'claude-sonnet-4-6',
  system: systemPrompt,
  messages: [...],
});
```

### 5. **MCP servers qui crashent**
```typescript
// Toujours tester les MCP en local avant la démo
// Avoir un fallback si un serveur MCP est down
try {
  const result = await mcpClient.callTool('tool_name', params);
} catch (error) {
  // Fallback: appel API direct ou résultat caché
  return cachedFallback;
}
```

---

## Checklist avant démo

- [ ] API keys dans .env (pas hardcodées)
- [ ] Model IDs à jour (claude-sonnet-4-6, gpt-5.4, etc.)
- [ ] Error handling sur tous les appels API
- [ ] Loading states clairs
- [ ] Rate limiting implémenté
- [ ] Coûts estimés et limités
- [ ] MCP servers testés en local
- [ ] Testé avec inputs edge cases
- [ ] Fallback si API/MCP down
- [ ] Mobile responsive (si web)
- [ ] Performance optimisée (< 3s response)

---

## Ressources utiles

### Documentation
- [Anthropic Claude Docs](https://docs.anthropic.com)
- [Claude Agent SDK](https://docs.anthropic.com/en/docs/agents)
- [MCP Specification](https://modelcontextprotocol.io)
- [OpenAI API Docs](https://platform.openai.com/docs)
- [LangChain Docs](https://js.langchain.com)

### MCP
- [MCP Registry](https://registry.modelcontextprotocol.io)
- [MCP.so](https://mcp.so)
- [MCPServers.org](https://mcpservers.org)

### Templates & Starters
- [Vercel AI SDK Examples](https://github.com/vercel/ai)
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook)

### UI Components
- [shadcn/ui](https://ui.shadcn.com)
- [Aceternity UI](https://ui.aceternity.com)
- [Magic UI](https://magicui.design)
