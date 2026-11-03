---
name: scrollhound-creator-shortlist
description: "Creator shortlist: find creators in a niche on TikTok or Instagram by account search and video search, then compare their followers, median views of recent posts, how often they post about the niche and visible sponsors, optionally with TikTok followers by country (26 credits per creator). Use when the user wants influencers or creators to work with, influencer vetting, a creator list for a campaign, or to check whether a creator's audience is in their market. Uses Scrollhound."
metadata:
  scrollhound-version: "1.1.0"
---

# Creator shortlist

Follower counts don't say whether a creator still gets views or still posts about the niche. This
skill finds candidates, reads what they posted recently and compares them on the numbers that
matter for a brand deal.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The niche**, in the words creators use.
- **The platform**: TikTok (default) or Instagram.
- **A market**, only if the audience's country matters; that adds TikTok followers by country,
  which **costs 26 credits per creator**. Ask before running it on more than three creators.

## Steps

1. **Find candidates two ways.**
   - By name or keyword: Connector `find_accounts` (`q`, `platform`) · CLI
     `scrollhound find accounts "<niche>" --platform tiktok`.
   - By what performs: Connector `tiktok_search` (`q`) or `ig_search` (`q`, `within: "month"`) ·
     CLI `scrollhound tiktok search "<niche>"`, `scrollhound ig search "<niche>" --within month`.
     Take the creators behind the most viewed recent videos.
   Pick the 5 who appear to post about the niche most often.
2. **Read each profile and their last 10 posts.**
   - TikTok: `tiktok_get_user` and `tiktok_get_user_videos` (`limit: 10`) · CLI
     `scrollhound tiktok user <@handle>`, `scrollhound tiktok videos <@handle> --limit 10`.
   - Instagram: `ig_get_user` and `ig_get_user_posts` (`limit: 12`) · CLI
     `scrollhound ig user <@handle>`, `scrollhound ig posts <@handle> --limit 12`.
   Skip pinned posts at the top of the profile (often old) when working out the median.
3. **Optional, TikTok only**: followers by country for the top 3. Connector `tiktok_get_user`
   with `audience: true` · CLI `scrollhound tiktok user <@handle> --audience` (26 credits each).

## What to deliver

1. A table: handle and link, followers, median views of the recent posts read (and over which
   dates), how many of them are about the niche, the best recent post with its views, and
   sponsored posts you can see (the brand named in the caption).
2. If asked: the share of followers in the user's market, per creator.
3. The two creators to contact first, with one sentence each on why.
4. Leave out emails, phone numbers and other contact details from bios: the user can open the
   profile.

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

> Find me 5 TikTok creators in budget travel who still get views. We sell to the UK, so check where their followers are.
