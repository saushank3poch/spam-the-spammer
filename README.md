# Spam the Spammer

Got a spam call? Fight back.

This Claude Code plugin automatically posts public shaming messages to a company's Twitter, email, and Instagram every hour until they get the message.

Every post is generated fresh by Claude at runtime - no templates, no repetition. Just creative, escalating internet rage.

## What It Does

1. You run `/spam-the-spammer`
2. Tell it the phone number and company that spammed you
3. It finds their Twitter, email, and Instagram handles (or you provide them)
4. It fires a test tweet for your approval
5. Then it posts a new, unique shaming tweet every hour automatically
6. Campaign auto-stops after 24h, 48h, or 1 week (your choice)

### Escalation Tiers

The tone automatically escalates the longer they ignore you:

- **Hours 1-8**: Witty callouts - "bro I asked for peace, not a life insurance pitch"
- **Hours 9-24**: Full meme mode - "nobody:", "POV:", ratio energy
- **Hours 25+**: Maximum pressure - hashtags, "Day N" counters, community rallying

## Setup

### Required

- **[Claude Code](https://claude.ai/code)** - the CLI tool this plugin runs in
- **[Typefully](https://typefully.com)** account connected as an MCP server - this is how tweets get posted

### Optional

- **Gmail CLI** (`gmail-cli`) - to also send complaint emails. Must be authenticated before use.
- **Claude in Chrome** - to also post on Instagram via browser automation (flaky, but fun)

## Install

```bash
claude plugin add saushank3poch/spam-the-spammer
```

Or clone and copy manually:
```bash
git clone https://github.com/saushank3poch/spam-the-spammer.git
cp -r spam-the-spammer/skills/spam-the-spammer ~/.claude/commands/
```

## Usage

```
/spam-the-spammer
```

Or with company name:

```
/spam-the-spammer Bajaj Finance
```

It will ask you for everything else interactively.

### Stop a Campaign

```
disable scheduled task spam-spammer-bajaj-finance
```

Or just tell Claude "stop the spam campaign" and it'll figure it out.

## How It Works Under the Hood

- **Twitter**: Creates and publishes tweets via Typefully API (reliable)
- **Email**: Sends complaint emails via Gmail CLI (optional)
- **Instagram**: Posts via Chrome browser automation (optional, less reliable)
- **Scheduling**: Uses Claude Code scheduled tasks with a cron job that runs every hour
- **Auto-stop**: A one-shot scheduled task fires at the end time and disables the campaign

## Note on MCP Tool Names

The plugin uses generic MCP tool names in its config. If your Typefully MCP server has a different ID in your Claude Code setup, update the `allowed-tools` in the SKILL.md to match your specific server IDs.

## License

MIT
