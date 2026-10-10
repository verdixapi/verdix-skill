# Verdix skill: check the recipient before you send

An agent skill that has the agent check a Base address with [Verdix](https://api.verdixapi.com) **before** it sends funds there: OFAC sanctions, scam and phishing lists, address-poisoning lookalikes, burn addresses, phishing-lure tokens, flagged deployers, and (from the quick tier up) address age, contract signals and on-chain behaviour.

The answer is `safe`, `caution` or `danger` with reasons (the $0.01 lite tier answers `no_known_risk` instead of `safe`). The skill tells the agent what to do with each one: don't send on `danger`, ask the user on `caution`.

- **Instructions only.** No code runs, no API key, no environment variables. It never asks for a private key or seed phrase.
- **Paid per check** via [x402](https://x402.org) in USDC on Base, from the x402 wallet the agent already uses: lite $0.01, quick $0.02, standard $0.10, deep $0.50. The skill tells the agent to get the user's OK before the first paid check.
- **Not charged when a check can't finish.** If a data source is down, Verdix answers 503 and the payment is never settled.
- **Base only.**

## Install

[skills.sh](https://skills.sh) (Claude Code, Cursor, Codex and other agents):

```bash
npx skills add verdixapi/verdix-skill
```

[ClawHub](https://clawhub.ai) (OpenClaw):

```bash
clawhub install @verdixapi/verdix
```

Or copy [`skills/verdix/SKILL.md`](skills/verdix/SKILL.md) into your agent's skills folder.

## What's inside

```
skills/verdix/SKILL.md   the skill: endpoints, prices, spending rules, how to read each verdict
```

## Other ways to use Verdix

- MCP server: [`verdix-mcp`](https://github.com/verdixapi/verdix-mcp) (`npx -y verdix-mcp`)
- Vercel AI SDK tools: [`verdix-ai-sdk`](https://github.com/verdixapi/verdix-ai-sdk)
- x402 client guard: [`verdix-guard`](https://github.com/verdixapi/verdix-guard)
- Docs for agents: https://api.verdixapi.com/llms.txt · OpenAPI: https://api.verdixapi.com/openapi.json

## Limits

Verdix reports known risk signals. A brand-new scam address may not be on any list yet, so `safe` lowers the risk but does not remove it. Before a large send, compare the full address with the user.

## License

[MIT](LICENSE). Copies published on ClawHub are licensed MIT-0 by ClawHub's terms.
