# Session State

**Project:** From Chatbot to Personal AI
**Last session:** 2026-05-22 — FromChatbotToPersonalAI - 02

---

## Where We Left Off

OpenClaw is installed and configured. Gateway runs with Ollama (gemma4:latest primary, llama3.2:3b fallback). Vault is connected as an MCP filesystem server. Session closed while gemma4 was loading on first query — no test outputs captured yet.

---

## First Task Next Session

Verify gateway + gemma4 is working, then run all three test queries.

Start the gateway (in one terminal tab):
```bash
nvm use 22 && openclaw gateway run
```

Run query 1 (in a second tab):
```bash
nvm use 22 && openclaw agent --agent main --message "What are the open blockers across my current projects?"
```

---

## Config State

- Config: `~/.openclaw/openclaw.json`
- Primary model: `ollama/gemma4:latest`
- Fallback: `ollama/llama3.2:3b`
- Vault MCP: `@modelcontextprotocol/server-filesystem` → `~/Documents/experiments/from-chatbot-to-personal-ai/vault`
- Gateway auth token: `mysecrettoken123`

---

## Key Decisions From Session 02

- Obsidian NOT required. Vault connects via MCP filesystem server.
- `openclaw configure --section model` is the real model config flow (not `openclaw config set`)
- OpenRouter free tier: unreliable for testing (rate limits, content filters, stuck sessions)
- Ollama is the right choice for setup validation sessions
- Workspace stays at `~/.openclaw/workspace`. Content sources added as MCP servers.

---

## Pending

| Item | Note |
|---|---|
| All three test query outputs | First priority next session |
| Resource usage table in Setup-A | Requires successful run |
| Setup time table in Setup-A | Requires successful run |
| "What surprised us" section | Fill after queries run |
| Vault connection section in Setup-A | Still describes Obsidian path — update to MCP path |
| ZeroClaw setup (Setup-B) | After Setup-A is fully complete |

---

## Pending Decisions (Carried Forward)

- "22% shadow AI" stat: needs citation before Article 4 can publish
- memU: defer until after other 5 setups
