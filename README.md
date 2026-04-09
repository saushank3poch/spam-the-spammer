# Spam the Spammer

A Claude Code plugin that fights back against spam callers with automated public shaming campaigns.

When you get a spam call, run `/spam-the-spammer` and this plugin will:

1. Look up the company's Twitter, email, and Instagram handles
2. Post a test tweet for your approval
3. Set up an hourly scheduled task that generates **fresh, unique, meme-culture** shaming messages
4. Auto-stop after your chosen duration (24h / 48h / 1 week)

Every message is generated at runtime by Claude - no templates, no repetition. Messages escalate from witty callouts to full meme mode to community rallying with hashtags.

## Prerequisites

You need these MCP tools connected in Claude Code:

| Tool | Purpose | Required? |
|------|---------|-----------|
| [Typefully](https://typefully.com) | Post tweets via API | Yes |
| Protonmail MCP (or any email MCP) | Send complaint emails | Optional |
| Claude in Chrome | Instagram posting via browser | Optional |
| Scheduled Tasks | Hourly recurring posts | Yes (built into Claude Code) |

## Install

```bash
claude plugin add saushank/spam-the-spammer
```

Or manually: clone this repo and copy the `skills/spam-the-spammer/` directory into your `~/.claude/commands/` or install as a plugin.

## Usage

```
/spam-the-spammer
```

Or with a company name pre-filled:

```
/spam-the-spammer Bajaj Finance
```

The skill will interactively ask you for:
- Phone number that spammed you
- Company name
- Their social handles (or auto-looks them up)
- How long to run the campaign
- Which of your Typefully accounts to post from

## How It Works

### Channels
- **Twitter/X**: Posts via Typefully API (reliable, API-based)
- **Email**: Sends formal complaints via Protonmail (optional)
- **Instagram**: Posts via Chrome browser automation (optional, less reliable)

### Escalation Tiers
Messages automatically escalate based on how long the campaign has been running:

- **Tier 1 (hours 1-8)**: Witty but firm callouts
- **Tier 2 (hours 9-24)**: Full meme mode - "nobody:", "POV:", ratio jokes
- **Tier 3 (hours 25+)**: Maximum pressure - hashtags, community rallying, "Day N" counters

### Auto-Stop
Campaigns auto-disable after your chosen duration via a one-shot scheduled task. You can also stop manually:

```
disable scheduled task spam-spammer-{company-slug}
```

## MCP Tool Names

The SKILL.md uses generic MCP tool names. If your Typefully or Protonmail MCP servers have different IDs in your Claude Code setup, update the `allowed-tools` in the SKILL.md to match. Your MCP server IDs look like `mcp__{uuid}__{tool_name}` - check your Claude Code settings.

## License

MIT
