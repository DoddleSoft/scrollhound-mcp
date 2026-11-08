---
name: scrollhound-competitor-ads
description: "Competitor ads: every ad a company is running in the Meta (Facebook and Instagram), TikTok, Google and LinkedIn ad libraries, grouped by offer and call to action, with the copy quoted and links. Use when the user asks what ads a competitor runs, wants ad research, creative inspiration, a competitor's messaging or offers, or to see a brand's Facebook, Instagram, TikTok, Google or LinkedIn ads. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.1"
---

# Competitor ads

Public ad libraries show what a company pays to say. This skill reads all four Scrollhound covers
and groups the ads by what they offer and what they ask people to do, so the user sees the
strategy, not just a feed of creatives.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The company's name** as it advertises.
- **Its website**, for Google's ad library (searched by domain).
- **A country**, if the user cares about one market (Meta and Google filter by country).

## Steps

1. **Meta** (Facebook and Instagram): Connector `ads_search` (`platform: "meta"`, `company`,
   `since: "30d"`, optional `country`) · CLI
   `scrollhound ads search --platform meta --company <name> --since 30d`.
2. **TikTok**: Connector `ads_search` (`platform: "tiktok"`, `company`) · CLI
   `scrollhound ads search --platform tiktok --company <name>`.
3. **Google**: Connector `ads_search` (`platform: "google"`, `domain`) · CLI
   `scrollhound ads search --platform google --domain <site>`. The list has no ad text, so open
   the 5 newest: `read_url` / `scrollhound ads get <ad url>`.
4. **LinkedIn**: Connector `linkedin_search_ads` (`company`, `since: "30d"`) · CLI
   `scrollhound linkedin ads --company <name> --since 30d`.
5. **Check the match.** Each search prints which advertiser it matched (`matched "…" to …`) and
   other candidates; if it's the wrong one, search again with that one's id as `company`.
6. **Optional**: for a Meta video ad worth studying, read its transcript (`get_transcript` /
   `scrollhound transcript <ad url>`).

## What to deliver

1. A table grouped by offer (product, free trial, report, event, discount, hiring…): number of
   ads, platforms, formats, and an ad quoted word for word with its link.
2. The calls to action and buttons they use, and how often.
3. What the mix says about who they target, and what changed from their older ads.
4. Three ideas for the user's own ads.

## Rules

- **Quote, don't paraphrase.** Use people's exact words in quotation marks, and put the link after
  every quote so the user can open the source.
- **Say what you read.** End with how many posts, comments, videos or transcripts you actually
  read, and the date range. If a thread was cut off (`shown N of M comments`), say so.
- **Never invent.** No made-up quotes, numbers or trends. If what you read doesn't support a
  point, say that instead.
- **Stay in scope.** Each read uses the user's Scrollhound credits. Stick to the amounts in these
  steps unless the user asks for more, and re-use what you already read in this conversation.
- **Read only.** Scrollhound never posts, likes, follows or messages anyone. If the user wants to
  reply or post, write the draft for them to publish themselves.

## Example request

> What ads is Canva running right now on Facebook, TikTok and LinkedIn? Group them by offer.
