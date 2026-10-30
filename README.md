<p align="center">
  <img src="assets/logo.png" width="96" height="96" alt="Scrollhound">
</p>

<h1 align="center">Scrollhound</h1>

<p align="center">
  Social research for your AI. Claude, ChatGPT and other AI tools read Reddit, X, YouTube, TikTok,
  Instagram, LinkedIn and Hacker News in full, and quote what they read with a link on every quote.
</p>

<p align="center">
  <a href="https://scrollhound.com">Website</a> ·
  <a href="https://scrollhound.com/docs/">Docs</a> ·
  <a href="https://scrollhound.com/recipes/">Recipes</a> ·
  <a href="https://scrollhound.com/#pricing">Pricing</a>
</p>

---

This repository holds what you need to add Scrollhound to an AI app: the connector details, the
Claude plugin and the research skills. Scrollhound itself is a hosted service; there is no server
code to run here.

## What it reads

| Platform | What your AI gets |
| --- | --- |
| Reddit | Subreddits with their full rules, top and new posts, search, and posts with their comment trees |
| X | Posts, threads, replies, quotes, Articles, a creator's posts, search and trends |
| YouTube | Videos with full transcripts, comments, channel uploads and search |
| TikTok | Videos with transcripts, comments, a creator's videos and search |
| Instagram | Posts and Reels with transcripts, comments, a creator's posts and Reels search |
| LinkedIn | Posts, profiles, company pages, post search and the Ad Library |
| Hacker News | Stories, comment trees and search |

Every item comes back with its link, so answers can be checked and cited. Scrollhound only reads:
it never posts, likes, follows or messages anyone, and it never asks for your social media
passwords.

## Connect it

One link works everywhere:

```text
https://api.scrollhound.com/mcp
```

Sign in with your email and a one-time code when your app asks. A new account starts with 100
free reads, no card needed.

| App | How |
| --- | --- |
| Claude (web, desktop, Cowork) | Customize → Connectors → + Add → Add custom connector, paste the link. [Steps](https://scrollhound.com/docs/mcp/claude-ai/) |
| ChatGPT | Plugins → + → Add custom MCP server, paste the link, choose OAuth. [Steps](https://scrollhound.com/docs/mcp/chatgpt/) |
| Claude Code | `claude mcp add --transport http scrollhound https://api.scrollhound.com/mcp`, or install the plugin below |
| Cursor, VS Code, Codex, Gemini CLI | [Setup guides](https://scrollhound.com/docs/) |
| Grok, Perplexity, Le Chat, Muse, Manus, n8n | [Setup guides](https://scrollhound.com/docs/mcp/agent-apps/) |
| OpenClaw, Cline, Zed, Warp, goose and other agents | [Setup guides](https://scrollhound.com/docs/mcp/agent-harnesses/) |

## Claude plugin

The plugin adds the connector and the research skills to Claude Code and Cowork in one step:

```bash
claude plugin marketplace add DoddleSoft/scrollhound-mcp
claude plugin install scrollhound@scrollhound
```

## Research skills

Skills teach your AI how to do a research job well: which sources to read, how much, and how to
present the result with quotes and links. They work with the connector or with the
[`scrollhound` CLI](https://www.npmjs.com/package/scrollhound).

| Skill | What it does |
| --- | --- |
| [Voice of customer](skills/scrollhound-voice-of-customer/SKILL.md) | Pains and wants from Reddit, as a table of pain, exact quote and link |
| [Mine the comments](skills/scrollhound-comment-mining/SKILL.md) | Questions, objections and reusable phrases from a comment section |
| [Competitor channel teardown](skills/scrollhound-competitor-teardown/SKILL.md) | What a YouTube channel's breakout videos have in common |
| [Short-form video teardown](skills/scrollhound-short-form-teardown/SKILL.md) | Hooks, structure and length of a creator's best TikToks or Reels |
| [Hook research](skills/scrollhound-hook-research/SKILL.md) | A creator's best opening lines on X or YouTube, by hook type |
| [LinkedIn teardown](skills/scrollhound-linkedin-teardown/SKILL.md) | Which posts land for a company or creator, and the ads a company runs |
| [Weekly niche brief](skills/scrollhound-weekly-brief/SKILL.md) | The week in a niche across Reddit, X and YouTube, with sources |
| [Check a subreddit before you post](skills/scrollhound-subreddit-check/SKILL.md) | The rules, what gets traction, and a check of your draft |
| [Brand mentions digest](skills/scrollhound-brand-mentions/SKILL.md) | What people said about a brand this week: complaints, praise, questions |

**Install them**

- **Claude Code and Cowork:** install the plugin above.
- **Claude (web and desktop):** zip a skill's folder and upload it in Claude's skills settings,
  with the Scrollhound connector added.
- **Terminal agents:** `npm i -g scrollhound`, then `scrollhound skill install` (add `--openclaw` for
  OpenClaw).

## Pricing

100 free reads to start, then monthly plans or pay-as-you-go reads. See
[scrollhound.com/#pricing](https://scrollhound.com/#pricing).

## Privacy and support

- Privacy notice: [scrollhound.com/privacy](https://scrollhound.com/privacy/)
- Terms: [scrollhound.com/terms](https://scrollhound.com/terms/)
- Support: [hello@scrollhound.com](mailto:hello@scrollhound.com)

## License

The files in this repository (skills, manifests and docs) are under the [MIT License](LICENSE).
The Scrollhound service is provided under its [terms of service](https://scrollhound.com/terms/).
Scrollhound is a product of Doddle Software Limited.
