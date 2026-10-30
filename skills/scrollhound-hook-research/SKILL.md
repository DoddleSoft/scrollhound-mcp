---
name: scrollhound-hook-research
description: "Hook research: collect a creator's best-performing opening lines on X or YouTube, group them by hook type and explain what each promises. Use when the user wants hook examples, wants to write better first lines, or asks which openings work for a creator or niche. Uses Scrollhound."
metadata:
  scrollhound-version: "1.0.0"
---

# Hook research

The first line decides whether anyone reads or watches the rest. This skill ranks a creator's
posts or videos by engagement and studies the openings of the best ones.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The creator**: an X @handle or a YouTube channel.
- **Platform**: X or YouTube. For TikTok or Reels, use the short-form teardown skill instead.

## Steps

1. **Get the best performers.**
   - X: Connector `x_get_user_posts` (`handle`, `sort: "top"`, `limit: 200`) · CLI
     `scrollhound x posts <@handle> --sort top --limit 200`
   - YouTube: Connector `yt_get_channel_videos` (`ref`, `limit: 50`) · CLI
     `scrollhound yt channel <@handle> --limit 50`, then read the transcripts of the top 5 with
     `get_transcript` / `scrollhound transcript <url>`
2. **Take the top 15 to 20** by engagement against the creator's median.
3. **Classify each opening**: question, bold claim, number or result, story, contrarian take,
   "how to", warning, curiosity gap, or something else (name it).
4. **Note what each promises** the reader or viewer, and the exact words that do the work.

## What to deliver

1. The hook types that perform best for this creator, with 2–3 verbatim examples each and links.
2. Words and structures that repeat.
3. A swipe file of 10 hooks rewritten for the user's own topic (marked as rewrites, not quotes).

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

> Show me @levelsio's best opening lines on X and what types of hooks they are.
