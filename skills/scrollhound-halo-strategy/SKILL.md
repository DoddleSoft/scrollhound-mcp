---
name: scrollhound-halo-strategy
description: "Halo strategy customer research: the pains, fears and desires of a market in their own words, from buyers' subreddits and the comments under the top YouTube and TikTok videos for one keyword, with exact quotes, counts, links and buyer signals. Use when the user wants customer research before writing copy or ads, pain points, fears and desires, the Halo strategy, voice of customer across platforms, objections, or the market's own words for headlines. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.1"
---

# Halo strategy: pains, fears and desires

The Halo strategy is forum foraging: read where buyers talk, and sort what they say into what
hurts now, what they're afraid of and what they want. This skill does it on Reddit, YouTube and
TikTok in one pass, keeps every quote's link, and marks the quotes that come from people who say
they bought.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **One keyword**: the word most buyers would type for what the user sells ("protein powder",
  not "sports nutrition solutions").
- **Subreddits** where buyers talk, if the user knows them.

## Steps

1. **Find the buyers' subreddits** if none were given. A broad search finds jokes and recipes,
   not buyers. Connector `reddit_search` (`q`, `in: "subreddits"`) · CLI
   `scrollhound reddit search "<keyword>" --in subreddits`. Pick the 3 where people discuss buying.
2. **The most discussed threads**: Connector `reddit_search` (`q`, `subreddit`,
   `sort: "comments"`, `time: "year"`) · CLI
   `scrollhound reddit search "<keyword>" --sub <name> --sort comments --time year`. Read the 4
   most discussed with up to 200 comments: `reddit_get_post` / `scrollhound reddit post <url> --comments 200`.
3. **Buyer phrases**: search comments for "switched from", "worth it", "regret", "wish" with the
   keyword (`in: "comments"`).
4. **YouTube**: Connector `yt_search` (`q: "<keyword> review"`, `sort: "views"`) then
   `yt_get_comments` on the 2 most-watched · CLI `scrollhound yt search "<keyword> review" --sort views`,
   `scrollhound yt comments <url> --limit 100`.
5. **TikTok**: Connector `tiktok_search` then `tiktok_get_comments` on the 2 most-played · CLI
   `scrollhound tiktok search "<keyword>"`.

## What to deliver

1. **Pains**, **Fears** and **Desires**: themes from most to least mentioned, each with the
   count of comments seen and two exact quotes with links. Mark a quote **BUYER** when the person
   says they bought, use, switched from or cancelled something.
2. The market's own words: phrases worth using in copy.
3. The objections a buyer would raise.
4. Three headline ideas, each answering one pain, fear or desire.

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

> Run the Halo strategy on "protein powder". What are buyers in pain about, afraid of and wishing
> for?
