---
name: lightrag
description: Safe LightRAG knowledge retrieval skill for Claude. Use when setting up or querying a local RAG (Retrieval-Augmented Generation) pipeline using LightRAG — indexing personal documents, notes, or knowledge bases for Claude to search and retrieve context from.
---

# LightRAG (Safe Version)

⚠️ **Safety Notice:** LightRAG runs a local server on your machine and reads files from directories you explicitly configure. To stay safe:
- **Only point it at folders you own and trust**
- **Never expose it to the public internet** — keep it localhost only
- **Use authentication** — always set an API key
- **Never index sensitive files** (passwords, private keys, financial data, health records)
- **Firewall it** — block port 9621 from external access

---

## What is LightRAG?

LightRAG is a lightweight Retrieval-Augmented Generation system that indexes your documents into a **graph + vector hybrid store**, then retrieves the most relevant chunks when you ask questions. Unlike simple keyword search, it understands relationships between concepts across your documents.

**Best used for:**
- Personal knowledge bases (Obsidian vaults, notes)
- Project documentation
- Research paper collections
- Company wikis or internal docs
- Any large collection of text you want to query intelligently

## Installation

```bash
# Requires Python 3.10+
pip install lightrag-hku

# Optional: faster vector search
pip install lightrag-hku[faiss]
```

## Safe Setup

### Step 1 — Create a dedicated workspace
```bash
# Create a safe, isolated working directory
mkdir ~/lightrag-workspace
cd ~/lightrag-workspace

# Create a dedicated folder for documents you want indexed
mkdir ~/lightrag-docs
```

### Step 2 — Basic configuration
```python
# config.py — safe configuration template
import os

# ✅ SAFE: Only index a specific, trusted folder
DOCS_PATH = os.path.expanduser("~/lightrag-docs")

# ✅ SAFE: Store index in isolated workspace
WORKING_DIR = os.path.expanduser("~/lightrag-workspace")

# ✅ SAFE: Localhost only — never 0.0.0.0
HOST = "127.0.0.1"
PORT = 9621

# ✅ SAFE: Always require authentication
API_KEY = os.environ.get("LIGHTRAG_API_KEY", "change-this-key")

# ✅ SAFE: Use your existing LLM API key
OPENAI_API_KEY = os.environ.get("OPENAI_API_KEY")
# OR for Claude:
ANTHROPIC_API_KEY = os.environ.get("ANTHROPIC_API_KEY")
```

### Step 3 — Start the server
```bash
# Set your API key as environment variable
export LIGHTRAG_API_KEY="your-secret-key-here"
export ANTHROPIC_API_KEY="your-anthropic-key"

# Start LightRAG server (localhost only)
lightrag-server \
  --host 127.0.0.1 \
  --port 9621 \
  --working-dir ~/lightrag-workspace \
  --input-dir ~/lightrag-docs
```

### Step 4 — Index your documents
```bash
# Copy ONLY the documents you want indexed
cp your-notes.md ~/lightrag-docs/
cp project-docs/ ~/lightrag-docs/

# Trigger indexing via API
curl -X POST http://127.0.0.1:9621/documents/scan \
  -H "Authorization: Bearer your-secret-key-here"
```

## Querying LightRAG

### Via API
```python
import requests
import os

LIGHTRAG_URL = "http://127.0.0.1:9621"
API_KEY = os.environ["LIGHTRAG_API_KEY"]

def query(question: str, mode: str = "hybrid") -> str:
    """
    Modes:
    - "naive"  : simple keyword search
    - "local"  : searches nearby concepts
    - "global" : searches broad themes
    - "hybrid" : combines local + global (recommended)
    """
    response = requests.post(
        f"{LIGHTRAG_URL}/query",
        json={"query": question, "mode": mode},
        headers={"Authorization": f"Bearer {API_KEY}"}
    )
    return response.json()["response"]

# Example usage
answer = query("What are my notes on productivity systems?")
print(answer)
```

### Query Modes Explained

| Mode | Best For |
|------|----------|
| `naive` | Simple keyword lookups |
| `local` | Specific facts, direct questions |
| `global` | Themes, summaries, big picture |
| `hybrid` | Most questions — recommended default |

## Integration with Claude

### n8n Workflow
```
[Chat Trigger] → [LightRAG Query Node] → [Claude with context] → [Response]
```

### Claude Code Integration
Add to `~/.claude/settings.json`:
```json
{
  "mcpServers": {
    "lightrag": {
      "command": "python",
      "args": ["-m", "lightrag.mcp_server"],
      "env": {
        "LIGHTRAG_API_KEY": "your-secret-key",
        "LIGHTRAG_URL": "http://127.0.0.1:9621"
      }
    }
  }
}
```

### Manual context injection
```python
# Get relevant context then pass to Claude
context = query("user's question here", mode="hybrid")

# Feed to Claude as context
prompt = f"""
Based on the following context from the user's knowledge base:

{context}

Answer the question: [user question]
"""
```

## What to Index (Safe Choices)

| ✅ Safe to Index | ❌ Never Index |
|-----------------|---------------|
| Personal notes | Passwords or API keys |
| Project docs | SSH private keys |
| Research papers | Financial statements |
| Blog drafts | Medical records |
| Book highlights | Legal documents with PII |
| Meeting notes | Anything with others' private data |

## Security Checklist

- [ ] Server bound to `127.0.0.1` only (not `0.0.0.0`)
- [ ] API key set via environment variable (not hardcoded)
- [ ] API key is strong and unique
- [ ] Input directory is a dedicated folder (not your entire home dir)
- [ ] Port 9621 blocked in firewall for external access
- [ ] No sensitive files in the indexed folder
- [ ] Server stopped when not in use (`Ctrl+C`)
- [ ] Working directory backed up regularly

## Stopping the Server

```bash
# Stop gracefully
Ctrl+C

# Or find and kill the process
lsof -i :9621
kill -9 [PID]
```

## Pairing with Other Skills

- **Obsidian Skill** — index your Obsidian vault for smart search
- **ClaudeMem** — use LightRAG for long-term document memory
- **n8n-MCP** — automate indexing when new files are added
- **GSD** — query your project notes for context during planning

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Server won't start | Check Python 3.10+, try `pip install --upgrade lightrag-hku` |
| No results returned | Run `/documents/scan` to trigger indexing |
| Slow queries | Use `faiss` backend: `pip install lightrag-hku[faiss]` |
| Port already in use | Change port or kill existing process on 9621 |
| Auth errors | Check `LIGHTRAG_API_KEY` env var is set correctly |
