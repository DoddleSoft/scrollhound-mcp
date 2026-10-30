---
name: scrollhound-short-form-teardown
description: "Short-form video teardown for TikTok and Instagram Reels: list a creator's recent videos with plays, find the ones that beat their median, read the transcripts and break down hook, structure, length and call to action. Use when the user asks why a creator's TikToks or Reels go viral, wants short-form hooks, or wants to model a creator's format. Uses Scrollhound."
metadata:
  scrollhound-version: "1.0.0"
---

# Short-form video teardown

Show why a creator's best TikToks or Reels work, from what they actually say in the first seconds.
Plays are compared with the creator's own median, so the breakouts are clear.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The creator**: a TikTok or Instagram @handle.
- **Platform**: TikTok or Instagram (ask if the handle could be either).
- **How many top videos to read** (default 3).

## Steps

1. **List recent videos** with plays.
   - TikTok: Connector `tiktok_get_user_videos` (`handle`, `limit: 30`) · CLI
     `scrollhound tiktok videos <@handle> --limit 30`
   - Instagram: Connector `ig_get_user_posts` (`handle`, `limit: 36`) · CLI
     `scrollhound ig posts <@handle> --limit 36`
   Skip pinned videos (they're listed first and skew the numbers).
2. **Compute the median plays** and rank videos by their multiple of it. Pick the top ones.
3. **Read their transcripts.** Connector `get_transcript` (`url`) · CLI
   `scrollhound transcript <video url>`. If a transcript says it's pending, try again in about a
   minute.
4. **Break each one down**: the first line (hook type and what it promises), structure, length,
   pacing cues in the words, and the call to action.

## What to deliver

1. A table: video, date, plays, multiple of median, length.
2. For each top video: the hook quoted word for word, why it works, structure and call to action,
   with a link.
3. The pattern across the top videos.
4. Five hooks the user could film, written in the same pattern for their topic.

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

> Why do @garyvee's best TikToks this month work? Break down the hooks.
