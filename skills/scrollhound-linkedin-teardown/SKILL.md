---
name: scrollhound-linkedin-teardown
description: "LinkedIn teardown: a company's or creator's recent LinkedIn posts ranked by likes and comments, what the best ones have in common, and the ads the company runs in LinkedIn's Ad Library. Use when the user asks what a competitor posts on LinkedIn, which LinkedIn posts land, B2B content benchmarks, or what ads a company is running on LinkedIn. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.0"
---

# LinkedIn teardown

See what a company or creator posts on LinkedIn, which posts actually land, and (for companies)
what they're paying to promote. Good for B2B competitor research and client benchmarks.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The account**: a company (`company/<name>` or its URL) or a person (`in/<name>` or URL).
- **Ads**: for a company, whether to include its ads (default yes, last 30 days).

## Steps

1. **Recent posts with stats.**
   - Connector: `linkedin_get_posts` with `ref` and `stats: true`
   - CLI: `scrollhound linkedin posts <company/name or in/name> --stats`
   Stats add one read per post; 10 posts is enough.
2. **Rank by engagement** against the account's median likes, and pick the top 3.
3. **Read the top posts** for their full text and the comments LinkedIn shows.
   - Connector: `read_url` with the post `url` · CLI: `scrollhound read <post url>`
   LinkedIn shows logged-out readers only a sample of comments; say so.
4. **Ads (companies).** Connector `linkedin_search_ads` with `company` and `since: "30d"` · CLI
   `scrollhound linkedin ads --company <name> --since 30d`.

## What to deliver

1. A table of recent posts: date, format, likes, comments, multiple of median.
2. What the top posts share: topic, format, opening line (quoted), length, call to action.
3. Ads: count, formats, offers and landing pages, and the messages they repeat.
4. How the organic feed and the ads differ (audience, promise, tone).
5. Three post ideas for the user based on what lands.

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

> What does Canva post on LinkedIn, which posts do best, and what ads are they running?
