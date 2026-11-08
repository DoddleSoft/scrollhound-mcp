---
name: scrollhound-trending-in-my-niche
description: "Trending in my niche: what's trending on TikTok, Instagram Reels and YouTube Shorts this week, filtered to the user's niche, plus a hashtag search, with the hooks from the top videos' transcripts and ideas to post. Use when the user asks what's trending or going viral in their niche, which formats, sounds or hashtags are working on short-form video, or wants video ideas for this week. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.1"
---

# Trending in my niche

The trending feeds show what's taking off right now but aren't filtered by topic; a keyword or
hashtag search is filtered but not ranked by momentum. This skill uses both, then reads the
transcripts of the best videos so the hooks are quoted, not guessed.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The niche**, in a few words ("skincare routine", "home workouts").
- **A hashtag** the niche uses, if the user has one.
- **A country** for TikTok's trending feed (default US).

## Steps

1. **Trending feeds**: Connector `get_trending` with `platform: "tiktok"` (and `region`), then
   `"instagram"` and `"youtube"` · CLI `scrollhound trending --platform tiktok --region <country>`,
   `scrollhound trending --platform instagram`, `scrollhound trending --platform youtube`. Keep
   only videos that are really about the niche, and count how many of the trending videos were.
2. **Search the niche**: Connector `tiktok_search` (`q`, or `hashtag`) and `ig_search` (`q` with
   `within: "week"`, or `hashtag`) · CLI `scrollhound tiktok search "<niche>"`,
   `scrollhound tiktok search --hashtag <tag>`, `scrollhound ig search "<niche>" --within week`,
   `scrollhound ig search --hashtag <tag>`. Keep videos from the last 7 days.
3. **Read the transcripts** of the 5 most viewed videos that fit: Connector `get_transcript`
   (`url`) · CLI `scrollhound transcript <video url>`. If a transcript is in another language or
   caught background audio instead of speech, say so and use the caption's first line.
4. **Optional**: when the same sound keeps coming up, read it (`read_url` / `scrollhound read`
   with the tiktok.com/music/… or instagram.com/reels/audio/… link) to see the videos using it.

## What to deliver

1. The formats and topics that are working, with links and views.
2. The first sentence of each of the 5 videos, word for word, with its hook type (question, bold
   claim, number, story, contrarian, how-to).
3. Sounds and hashtags that repeat.
4. Three video ideas for this week, each tied to a video you read.

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

> What's trending in skincare on TikTok and Reels this week? I'm in the UK.
