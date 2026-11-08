---
name: scrollhound-brand-mentions
description: "Brand mentions digest: what people said about a brand, product or competitor in the past week across Reddit comments, X posts and mentions, Instagram tagged posts, TikTok and YouTube, sorted into complaints, praise, questions and comparisons, with quotes and links. Use when the user asks what people are saying about a brand, wants social listening, brand monitoring, sentiment, a mentions report, UGC or creator mentions, or a competitor's reputation. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.1"
---

# Brand mentions digest

A readable report of what people said about a brand in the past week or month, with every quote
linked. It reads public posts on demand rather than monitoring all the time, so it suits a weekly
or monthly check.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The brand or product name**, plus common misspellings if relevant.
- **Its handles** on X and Instagram, if the user knows them. If not, find them in step 1; don't
  guess a handle from the name.
- **The window**: past 7 days by default, or 30 days.
- **Platforms**, if the user wants to narrow it (default: Reddit, X, Instagram, TikTok and
  YouTube; add LinkedIn or Hacker News when the brand's audience is there).

## Steps

1. **Find the accounts** when you don't have the handles: Connector `find_accounts` (`q`,
   `platform: "x"` or `"instagram"`) · CLI `scrollhound find accounts "<brand>" --platform x`.
   Pick the verified or obviously official account.
2. **Reddit comments**: Connector `reddit_search` (`q`, `in: "comments"`, `time: "week"`) · CLI
   `scrollhound reddit search "<brand>" --in comments --time week`. Then the posts with real
   discussion: `reddit_search` (`q`, `sort: "top"`, `time: "week"`) /
   `scrollhound reddit search "<brand>" --sort top --time week`, and open the busiest with
   `reddit_get_post` (`comments: 100`) / `scrollhound reddit post <url> --comments 100`.
3. **X**: Connector `x_search_posts` (`q: "<brand> -from:<handle>"`, `since: "7d"`,
   `sort: "latest"`, `limit: 50`) · CLI
   `scrollhound x search "<brand> -from:<handle>" --since 7d --sort latest --limit 50`. Then
   mentions of the account: `x_get_user_posts` (`handle`, `kind: "mentions"`, `limit: 50`) /
   `scrollhound x posts <@handle> --mentions --limit 50`.
4. **Instagram tagged posts** (UGC and creator mentions): Connector `ig_get_user_posts`
   (`handle`, `tab: "tagged"`) · CLI `scrollhound ig posts <@handle> --tab tagged`.
5. **TikTok and YouTube**: Connector `tiktok_search` (`q`) and `yt_search` (`q`, `since: "7d"`) ·
   CLI `scrollhound tiktok search "<brand>"`, `scrollhound yt search "<brand>" --since 7d`. Read
   the comments on the two most viewed videos (`tiktok_get_comments` / `yt_get_comments`,
   `limit: 50`; CLI `scrollhound tiktok comments <video> --limit 50`,
   `scrollhound yt comments <video> --limit 50`).
6. **Optional**: LinkedIn (`linkedin_search_posts` with `within: "week"` /
   `scrollhound linkedin search "<brand>" --within week`), Threads (`threads_search` with
   `since: "7d"` / `scrollhound threads search "<brand>" --since 7d`), Hacker News (`hn_search` /
   `scrollhound hn search "<brand>"`).
7. **Drop false matches** (another meaning of the name) and the brand's own posts. Tag each real
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
