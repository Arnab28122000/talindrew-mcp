# Talindrew MCP server: molecular biology tools for Claude, ChatGPT, Codex and Cursor

**Talindrew** is a browser-based molecular biology platform (plasmid editor, cloning design, primer design,
lab notebook, protein structure prediction and drug discovery). Its remote **MCP server** gives any MCP
client **90 molecular biology tools** that run on Talindrew's engines, so numbers like a primer's Tm or a
digest's fragment sizes are computed, not recalled from a model's memory.

```
https://mcp.talindrew.com/mcp
```

- Transport: Streamable HTTP
- Sign-in: OAuth with your Google account (the first sign-in creates a free Talindrew account)
- Server name: `talindrew`
- Website and per-client guides: https://www.talindrew.com/mcp

This repository holds the connection details and setup instructions only. The server is hosted by Talindrew;
there is nothing to install or run locally.

## Connect

### Claude (claude.ai, desktop and mobile)

1. Open **Customize → Connectors** (claude.ai/customize/connectors), click **+ Add → Add custom connector**.
2. Paste `https://mcp.talindrew.com/mcp`, click **Connect**, sign in with Google and click **Allow**.
3. In a chat, ask for something Talindrew does and approve the tool when Claude asks.

Team and Enterprise: an owner adds it under Organization settings → Connectors; members then click Connect.
Guide: https://www.talindrew.com/mcp/claude

### Claude Code

```bash
claude mcp add --transport http --scope user talindrew https://mcp.talindrew.com/mcp
```

Then run `/mcp`, choose `talindrew` and **Authenticate**. Guide: https://www.talindrew.com/mcp/claude-code

### ChatGPT

1. Open chatgpt.com/plugins, click **+** and choose **Add custom MCP server**.
2. Name it Talindrew, paste `https://mcp.talindrew.com/mcp` as the server URL and choose **OAuth**.
3. Create it as a plugin and sign in with Google when asked. In a chat, type **@** and pick Talindrew.

Guide: https://www.talindrew.com/mcp/chatgpt

### Codex

```bash
codex mcp add talindrew --url https://mcp.talindrew.com/mcp
codex mcp login talindrew
```

Guide: https://www.talindrew.com/mcp/codex

### Cursor, VS Code, Windsurf, Zed, Cline and other JSON-configured clients

```json
{
  "mcpServers": {
    "talindrew": { "type": "http", "url": "https://mcp.talindrew.com/mcp" }
  }
}
```

Step-by-step pages for 23 clients, including Gemini CLI, Goose, opencode, Continue, Kiro, Warp, LM Studio,
Raycast, Perplexity, Mistral and Microsoft Copilot Studio: https://www.talindrew.com/mcp

## What you can ask

- "Fetch pUC19 from Addgene, cut it with EcoRI and PvuII and show me the gel."
- "Design primers to clone GFP into pET-28a by Gibson assembly, and check them for hairpins."
- "Find SpCas9 guides in the first exon of human TP53 and rank them."
- "Codon-optimise this protein for E. coli and give me the CAI."
- "Find recent PubMed papers on base editing in iPSCs and summarise the abstracts."
- "Write today's cloning into my lab notebook with the map and the primer table."

## Tools

| Group | Tools | Plan |
|---|---|---|
| Sequence analysis | `analyze_sequence`, `find_restriction_sites` (600+ enzymes, Dam/Dcm), `digest_sequence`, `detect_features`, `find_orfs`, `translate_dna`, `align_sequences`, `simulate_gel` | Free |
| Primers, CRISPR and proteins | `design_primers`, `primer_tm` (nearest-neighbour, Wallace, salt-adjusted), `mutagenesis_primers`, `find_crispr_guides`, `protein_properties`, `optimize_codons`, `reverse_translate`, `ligation_calculator` | Free |
| Cloning workspace (OpenCloning-compatible) | `create_workspace`, `import_sequence`, `import_from_repository` (Addgene, Benchling, SnapGene, iGEM, Euroscarf, NCBI), `add_cloning_step` (restriction, ligation, Gibson, Golden Gate, Gateway, PCR, recombination, CRISPR), `design_cloning_primers`, `check_primers`, `check_sequencing`, `domesticate_part`, `export_workspace` and more | Free |
| Literature and databases | `search_pubmed`, `get_pubmed_abstracts`, `search_europepmc`, `search_genes` (NCBI Gene), `search_addgene` | Free |
| Your Talindrew account | sequences, workspaces, lab-notebook entries, exports (PDF, Word, Markdown) and sharing | Free |
| Structure prediction and drug discovery | `run_model` (Boltz-2, AlphaFold 2, ESMFold, DiffDock and more), `start_foldrx_run` (fold → pockets → screen → dock → rank) | Pro / Max |

The full, current list is on https://www.talindrew.com/mcp.

## Pricing

Connecting is free. The Free plan includes 25 tool calls a week (reset every Monday, 00:00 UTC). **Plus**
($9/month or $99/year, 7-day free trial) makes tool calls unlimited. Structure prediction and drug-discovery
runs need **Pro** or **Max**. Details: https://www.talindrew.com/pricing

## Privacy and access

Each client gets its own OAuth token scoped to your account, and you can revoke it any time in Talindrew under
Settings → Connected apps. Read-only scopes cannot write. Nothing in your account is shared unless you share it.
Privacy policy: https://www.talindrew.com/privacy

## Links

- Website: https://www.talindrew.com
- MCP server guide: https://www.talindrew.com/mcp
- Videos: https://www.talindrew.com/videos/talindrew-mcp-in-a-minute
- Changelog: https://www.talindrew.com/changelog
