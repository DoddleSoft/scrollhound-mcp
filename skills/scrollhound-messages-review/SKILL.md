---
name: scrollhound-messages-review
description: "Monthly messages review: this month's objections, repeated questions and trending angles for a brand and its competitors from Reddit and video comments, what their ads say now, better-faster-cheaper, gaps no ad answers, and where to release each message (article, plain-text email, Reddit or YouTube answer, landing page). Use when the user plans next month's marketing messages, wants new angles, a messaging review, objections to answer, or a monthly marketing meeting prepared. Uses Scrollhound."
metadata:
  scrollhound-version: "1.1.0"
---

# Monthly messages review

A one-person marketing team decides each month what to say next: which objections to answer,
which questions keep coming up, what's trending that a message could ride. This skill prepares
that meeting from what the market said in the last 30 days and what competitors are paying to
say right now.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The brand** (the user's or their client's).
- **Two or three competitors.**
- **The category**, in buyers' words ("social media scheduler").

## Steps

1. **Mentions this month**: Connector `reddit_search` (`q: "<brand>"`, `in: "comments"`,
   `time: "month"`), then the same for each competitor · CLI
   `scrollhound reddit search "<brand>" --in comments --time month`.
2. **The category's discussions**: Connector `reddit_search` (`q: "<category>"`,
   `sort: "comments"`, `time: "month"`) and `reddit_get_post` with up to 100 comments on the top 3
   · CLI `scrollhound reddit search "<category>" --sort comments --time month`.
3. **Video comments**: Connector `yt_search` (`since: "30d"`, `sort: "views"`) and
   `yt_get_comments` on the top 2, then `tiktok_search` and `tiktok_get_comments` · CLI
   `scrollhound yt search "<category>" --since 30d --sort views`, `scrollhound yt comments <url> --limit 100`.
4. **Ads running now**: Connector `ads_search` (`platform: "meta"`, `company`) for the brand
   and each competitor · CLI `scrollhound ads search --platform meta --company <name>`. Note
   which messages started this month.

## What to deliver

Each point with its count and two exact quotes with links:

1. Objections: why people say they won't buy, or left.
2. Questions people keep asking.
3. Trending angles: anything new this month a message could ride.
4. Better, faster or cheaper: which one the market says the brand wins on, and which a competitor
   wins on.
5. What competitors' ads say now, and which messages are new this month.
6. Gaps: what the market talks about that no ad answers.
7. Five messages for next month, each with where to release it (website article, plain-text
   email, Reddit answer after checking the subreddit's rules, YouTube answer, landing page line)
   and its first line written out.

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

> Prepare my monthly messages review for Hootsuite against Buffer and Later. What should we be
> saying next month?
