---
name: scrollhound-outlier-hunt
description: "Outlier hunt: find the videos that got far more views than their own channel usually does, across several YouTube, TikTok or Instagram accounts, with each video's multiple of the channel median, the outliers' opening lines from their transcripts, and what they share. Use when the user asks for outliers, breakout or viral videos in a niche, what's working for competitors or creators, video ideas to remix, or which hooks and topics beat a channel's average. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.0"
---

# Outlier hunt: videos that beat their own channel

Raw views reward big channels. An outlier is a video that beat its **own** channel's usual views,
so a small creator's breakout counts as much as a big one's. This skill ranks several accounts'
videos by their multiple of the channel median, reads how the biggest outliers open, and says what
they share that the usual videos don't.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The accounts**: 3 to 10 channels or creators, with their platform. Competitors, or creators
  the user's audience watches.
- **How many outliers** to read in full (default 5).

## Steps

1. **Each account's last 30 videos with views.**
   - YouTube: Connector `yt_get_channel_videos` (`ref`, `limit: 30`) · CLI
     `scrollhound yt channel <@handle> --limit 30`. The uploads tab can include Shorts.
   - TikTok: `tiktok_get_user_videos` (`handle`, `limit: 30`) · `scrollhound tiktok videos <@handle> --limit 30`.
   - Instagram: `ig_get_user_posts` (`handle`, `tab: "reels"`) · `scrollhound ig posts <@handle> --tab reels`.
   Skip pinned posts and anything under 7 days old (it hasn't finished collecting views).
2. **Medians.** For each account, take the median views separately for short videos (under 3
   minutes) and long ones, so Shorts aren't compared with hour-long videos. Give every video its
   multiple of its own median. Work it out from the numbers you read; don't estimate.
3. **Rank and read.** Rank every video by multiple. For the biggest outliers at 3× or more, read
   the transcript: Connector `get_transcript` (`url`) · CLI `scrollhound transcript <video url>`.
   Note the opening lines word for word, and whether the video or its description says it's
   sponsored or an ad.

## What to deliver

1. A table: account, title or caption (linked), length, views, multiple and which median, and the
   opening line word for word. Mark sponsored videos.
2. What the outliers share that each account's usual videos don't: topic, title pattern, hook
   type, format, length.
3. Which accounts had no outlier at 3× (that's a finding too).
4. Three video ideas that remix the outliers for the user's audience, each with a first line.

## Rules

- **Quote, don't paraphrase.** Opening lines are copied from the transcript, in quotation marks,
  with the video's link.
- **Show the arithmetic.** Give each median and how many videos it came from. A median from fewer
  than 5 videos is shaky: say so.
- **Paid promotion counts.** A sponsored video may have been boosted with ads. Mark it, and don't
  build the conclusions on sponsored videos alone.
- **Say what you read.** End with how many accounts, videos and transcripts you read, and the date
  range.
- **Never invent.** No made-up views, multiples or quotes. If a transcript isn't available, say so.
- **Stay in scope.** Each read uses the user's Scrollhound credits: 30 videos per account and
  transcripts for the outliers only, unless the user asks for more.
- **Read only.** Scrollhound never posts, likes, follows or messages anyone.

## Example request

> Run an outlier hunt on @ColinandSamir, @VanessaLau and @kallawaymarketing on YouTube. Which
> videos beat their channel, and how do they open?
