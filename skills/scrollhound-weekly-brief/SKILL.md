---
name: scrollhound-weekly-brief
description: "Weekly niche brief: what a niche talked about in the past 7 days on Reddit, X and YouTube, with the top threads, posts and videos and a link on every point. Use when the user asks what's happening in their niche, for a weekly or Monday briefing, trend or topic ideas for the week, or to set up a recurring research task. Uses Scrollhound."
metadata:
  scrollhound-version: "1.0.0"
---

# Weekly niche brief

One brief from the week's top Reddit posts, the most liked X posts and the most viewed YouTube
videos on a topic. Built to run every Monday, for example as a scheduled task in Claude.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The niche or topic** in a few words.
- **Subreddits** to include (1–3). Suggest some if the user has none, and confirm.

## Steps

1. **Reddit**: the top posts of the week in each subreddit.
   - Connector: `reddit_list_posts` with `subreddit`, `sort: "top"`, `time: "week"`
   - CLI: `scrollhound reddit posts <name> --sort top --time week`
2. **X**: the most liked posts on the topic from the past 7 days.
   - Connector: `x_search_posts` with `q`, `since: "7d"`, `min_likes: 50`, `sort: "top"`
   - CLI: `scrollhound x search "<topic>" --since 7d --min-likes 50 --sort top`
3. **YouTube**: the most viewed new videos.
   - Connector: `yt_search` with `q`, `since: "7d"`, `sort: "views"`
   - CLI: `scrollhound yt search "<topic>" --since 7d --sort views`
4. **Open the two biggest discussions** (Reddit post with comments, or X replies) to see what
   people are actually saying, not just the headlines.

## What to deliver

A brief with:
1. **The 3–5 conversations of the week**, each in two sentences, with the strongest quote and links.
2. **Questions people kept asking** (content ideas).
3. **What performed**: the top post, thread and video, with their numbers.
4. **Worth watching next week.**

Keep it to one screen. For a recurring brief, suggest scheduling this request weekly in the user's
AI app.

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

> Give me this week's brief on creator economy news: r/NewTubers and r/socialmedia, plus X and YouTube.
