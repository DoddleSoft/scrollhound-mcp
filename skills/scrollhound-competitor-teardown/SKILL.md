---
name: scrollhound-competitor-teardown
description: "Competitor YouTube channel teardown: list a channel's recent uploads, find the videos that beat its usual views, read their transcripts and break down topics, titles, hooks and structure. Use when the user names a competitor or creator on YouTube and asks why their videos work, what topics break out, or what to learn from their channel. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.0"
---

# Competitor channel teardown

Find what a channel's best videos have in common, from what they actually say. Views are compared
with the channel's own median, so the breakouts stand out from the channel's normal.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The channel**: an @handle, channel URL or channel ID.
- **How many top videos to read in full** (default 3).

## Steps

1. **List the recent uploads** with views, likes and comments (up to 50).
   - Connector: `yt_get_channel_videos` with `ref` and `limit: 50`
   - CLI: `scrollhound yt channel <@handle> --limit 50`
2. **Work out the median views** of what you listed, and mark each video's views as a multiple of
   it. Pick the top videos by that multiple.
3. **Read their transcripts** word for word.
   - Connector: `get_transcript` with the video `url`
   - CLI: `scrollhound transcript <video url>`
4. **Compare.** Topic, title pattern, the first 30 seconds (the hook and the promise), structure
   and length, and the call to action.

## What to deliver

1. A table of the recent uploads: title, date, views, multiple of median.
2. For each top video: why it likely broke out, with the opening lines quoted and a link.
3. What the top videos share: topic angles, title patterns, hook types, structure.
4. Five video ideas for the user that apply the pattern to their own niche.

Close with the number of uploads listed and transcripts read.

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

> Why do @mkbhd's best videos from the last few months work? Read the top 3.
