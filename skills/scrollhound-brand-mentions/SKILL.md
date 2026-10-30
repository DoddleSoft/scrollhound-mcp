---
name: scrollhound-brand-mentions
description: "Brand mentions digest: what people said about a brand, product or competitor in a recent window across X, Reddit, YouTube, TikTok, LinkedIn and Hacker News, sorted into praise, complaints, questions and comparisons, with quotes and links. Use when the user asks what people are saying about a brand, wants social listening, brand monitoring, sentiment, a mentions report, or a competitor's reputation. Uses Scrollhound."
metadata:
  scrollhound-version: "1.0.0"
---

# Brand mentions digest

A readable report of what people said about a brand in the past week or month, with every quote
linked. It reads public posts on demand rather than monitoring all the time, so it suits a weekly
or monthly check.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The brand or product name**, plus common misspellings or handles if relevant.
- **The window**: past 7 days by default, or 30 days.
- **Platforms**, if the user wants to narrow it (default: X, Reddit and YouTube; add TikTok,
  LinkedIn or Hacker News when the brand's audience is there).

## Steps

1. **X**: Connector `x_search_posts` (`q`, `since: "7d"`, `sort: "latest"`, `limit: 50`) · CLI
   `scrollhound x search "<brand>" --since 7d --sort latest --limit 50`. Exclude the brand's own
   posts with `-from:<handle>` in the query.
2. **Reddit**: Connector `reddit_search` (`q`, `sort: "new"`, `time: "week"`) · CLI
   `scrollhound reddit search "<brand>" --sort new --time week`. Open the threads with real
   discussion (`reddit_get_post` / `scrollhound reddit post <url> --comments 100`).
3. **YouTube**: Connector `yt_search` (`q`, `since: "7d"`) · CLI
   `scrollhound yt search "<brand>" --since 7d`. For a review video, read its comments.
4. **Optional**: TikTok (`tiktok_search` / `scrollhound tiktok search "<brand>"`), LinkedIn
   (`linkedin_search_posts` with `within: "week"` /
   `scrollhound linkedin search "<brand>" --within week`), Hacker News (`hn_search` /
   `scrollhound hn search "<brand>"`).
5. **Drop false matches** (another meaning of the name) and the brand's own posts. Tag each real
   mention: praise, complaint, question, comparison with a competitor, or news.

## What to deliver

1. **Headline**: how many real mentions you read and the overall tone, in one sentence (no
   invented sentiment score).
2. **Complaints**, **praise**, **questions** and **comparisons**, each with the strongest quotes
   and links.
3. **Anything that needs a reply today** (an unhappy customer, a wrong claim, a viral thread).
4. A short table: platform, mentions read, notable posts.

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

> What did people say about Notion this week? Focus on complaints and comparisons with competitors.
