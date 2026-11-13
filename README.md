# Fourth Feed MCP server and agent skill

[Fourth Feed](https://fourthfeed.com) is a directory of AI video tools (generators, avatars, lip-sync, editors, captions, dubbing, lyric videos, faceless shorts and video APIs) with dated pricing, free-tier rules, monthly traffic, verified revenue and agent-readiness (`llms.txt`, MCP server, public API). This repository holds the connection details for its remote MCP server and an [Agent Skill](skills/fourthfeed/SKILL.md) that teaches an agent to query it. The service is hosted; there is nothing to install or run.

- **MCP endpoint:** `https://fourthfeed.com/mcp` (Streamable HTTP)
- **Auth:** none. Free, no API key, no account. Rate limit: 60 requests per minute per IP.
- **Registry name:** `com.fourthfeed/fourthfeed` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.fourthfeed/fourthfeed)
- **Docs:** [fourthfeed.com/about](https://fourthfeed.com/about) · [llms.txt](https://fourthfeed.com/llms.txt)

## Connect

**Claude Code**

```bash
claude mcp add --transport http fourthfeed https://fourthfeed.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "fourthfeed": { "url": "https://fourthfeed.com/mcp" }
  }
}
```

**Codex** (`~/.codex/config.toml`)

```toml
[mcp_servers.fourthfeed]
url = "https://fourthfeed.com/mcp"
```

In Claude Desktop or ChatGPT, add `https://fourthfeed.com/mcp` as a custom connector.

## Tools

| Tool | What it does |
| --- | --- |
| `search_tools` | Search AI video tools by keyword (`q`), `category` id, or `agent_ready` (`llms.txt`, MCP registry entry or public API) |
| `get_tool` | Full dated record for one video tool by `domain`: summary, pricing, free tier, agent-readiness, traffic, revenue (with source and date), referral code if available, and page URL |
| `list_categories` | List all AI video tool categories with tool counts |
| `list_new_tools` | Newly discovered AI video tools, optionally filtered by `since` (`YYYY-MM-DD`) |
| `compare_tools` | Compare 2 to 5 AI video tools side by side by domain |
| `list_referrals` | Active referral links and promo codes for AI video tools, with plain-English disclosures of what the user gets |
| `submit_tool` | Suggest an AI video tool URL or domain for listing (queued for verification; free, no key needed) |

## HTTP & Markdown endpoints

Every page on Fourth Feed can also be read directly without MCP:

- `https://fourthfeed.com/api/v1/tools` and `https://fourthfeed.com/api/v1/tools/<domain>`
- Append `.md` or `.json` to any tool or comparison URL (for example `https://fourthfeed.com/tools/runwayml-com.md`)

## Agent skill

[`skills/fourthfeed/SKILL.md`](skills/fourthfeed/SKILL.md) follows the [Agent Skills](https://agentskills.io) format. Install it with

```bash
npx skills add fourthfeed/fourthfeed-mcp
```

or copy the folder into your agent's skills directory (for Claude Code, `~/.claude/skills/fourthfeed/`).


### One-line prompt for any AI agent

Paste into Claude Code, Cursor, Codex, or Gemini CLI:

```text
Read https://raw.githubusercontent.com/fourthfeed/fourthfeed-mcp/main/skills/fourthfeed/SKILL.md and compare AI video tools, pricing, and free tiers.
```

## Support

support@fourthfeed.com

## License

The files in this repository are MIT licensed. Directory data on fourthfeed.com is covered by the site's terms at [fourthfeed.com/about](https://fourthfeed.com/about).
