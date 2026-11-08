---
name: scrollhound-ad-swipe-file
description: "Ad swipe file: competitors' longest-running ads across the Meta (Facebook and Instagram), TikTok, Google and LinkedIn ad libraries, sorted by how long each has run, with the copy quoted, the landing page and links. Use when the user wants a swipe file, winning ads, ads that work, the ads a competitor keeps running, ad inspiration backed by evidence, or to know which competitor messages are proven and which are new tests. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.1"
---

# Ad swipe file: competitors' longest-running ads

Nobody keeps paying for an ad that loses money, so an ad that has run for months is the closest
public signal of a winner. This skill reads several competitors' ads in four libraries, works out
how long each has run, and sorts the swipe file longest first.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **Two to five competitors**, as they advertise. Ask if the user only gave a category.
- **Their websites**, for Google's ad library (searched by domain).
- **A country**, if the user cares about one market.

## Steps

1. **Meta**, for each competitor: Connector `ads_search` (`platform: "meta"`, `company`) · CLI
   `scrollhound ads search --platform meta --company <name>`. Without `since` it lists the ads
   running now, each with the date it started.
2. **Google**: Connector `ads_search` (`platform: "google"`, `domain`) · CLI
   `scrollhound ads search --platform google --domain <site>`. The list shows each ad's dates but
   no text: open the longest-running ones with `read_url` / `scrollhound ads get <ad url>`.
3. **TikTok**: Connector `ads_search` (`platform: "tiktok"`, `company`) · CLI
   `scrollhound ads search --platform tiktok --company <name>`.
4. **LinkedIn**: Connector `linkedin_search_ads` (`company`) · CLI
   `scrollhound linkedin ads --company <name>`.
5. **Check every match.** Each search prints which advertiser it matched (`matched "…" to …`).
   Short names often match the wrong company ("Later" matched "Buy Now Pay Later"): search again
   with the right id as `company`, or rely on the website for Google, and say so.
6. **Days running** for each ad: from its first-shown date to its last-shown date, or to today if
   it's still running. Mark 365+, 90+, 30+ days, or new (started in the last 30 days).
7. **Landing pages**: open the top three ads' landing pages with `read_url` when it can read them.

## What to deliver

1. The top 15 ads, longest-running first: competitor, platform, days running, format, headline
   and text word for word, call to action, landing page, link.
2. Per competitor: the messages it has kept running longest, and the ones started in the last 30
   days (tests, not yet proven).
3. What the long runners have in common: offer, angle, proof, format.
4. Five ideas for the user's own ads, each tied to a long-running ad.

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

> Build me a swipe file of Hootsuite, Buffer and Later's ads. Which ones have they kept running
> longest?
