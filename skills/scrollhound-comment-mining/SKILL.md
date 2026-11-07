---
name: scrollhound-comment-mining
description: "Mine a comment section for content: the questions people ask, objections, praise and exact phrases worth reusing, from the comments under a YouTube video, TikTok, Instagram Reel, Reddit thread or X post. Use when the user shares a post or video and wants content ideas, FAQ topics, hooks, objections or audience language from its comments. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.0"
---

# Mine the comments

The comments under a popular post are a list of what the audience wants next. This skill turns one
comment section (or a few) into questions, objections and phrases the user can build content on.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **One or more links**: a YouTube video, TikTok, Instagram post or Reel, Reddit thread or X post.
- **A focus** if the user has one ("objections to the price", "what beginners struggle with").

## Steps

1. **Read the comments**, by platform:
   - YouTube: top 100 comments. Connector `yt_get_comments` (`ref`, `limit: 100`) · CLI
     `scrollhound yt comments <video> --limit 100`
   - TikTok: up to 100 comments. Connector `tiktok_get_comments` (`ref`) · CLI
     `scrollhound tiktok comments <video> --limit 100`
   - Instagram: the 60 newest comments. Connector `ig_get_comments` (`ref`) · CLI
     `scrollhound ig comments <post> --limit 60`
   - Reddit: the post with up to 300 comments. Connector `reddit_get_post` (`ref`, `comments: 300`)
     · CLI `scrollhound reddit post <url> --comments 300`
   - X: the top 100 replies. Connector `x_get_replies` (`ref`, `sort: "top"`, `limit: 100`) · CLI
     `scrollhound x replies <post> --sort top --limit 100`
2. **With a focus**, keep only the comments that speak to it (YouTube can filter at the source:
   `search` / `--search "<word>"`).
3. **Sort what you read** into questions, objections and complaints, praise and requests, and
   phrases that are vivid enough to reuse.

## What to deliver

1. The 10 questions people ask most, grouped where they overlap, each with a quote and link.
2. Objections and complaints.
3. What people praise or ask for more of.
4. 10 exact phrases worth reusing in a hook, caption or ad.
5. Three content ideas that answer the most common questions.

Close with what you read (for example "top 100 of 2,300 comments on one YouTube video").

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

> Read the comments on this video and tell me what people keep asking: https://www.youtube.com/watch?v=…
