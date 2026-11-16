---
name: scrollhound-awareness-map
description: "Awareness map: sort a market's current competitor ads into the five stages of awareness (unaware, problem aware, solution aware, product aware, most aware), count them, add what buyers say on Reddit, and say which stage is crowded, which is open and what to write for the open one. Use when the user asks about awareness levels, market sophistication, which angle competitors are missing, or where a market's ads are crowded. Uses Scrollhound."
metadata:
  scrollhound-version: "1.3.0"
---

# Awareness map: which stage your market's ads are fighting over

Most markets pile their ads into one or two stages of awareness. This skill reads competitors'
current ads, sorts each into a stage, counts them, and checks the result against what buyers say on
Reddit, so the user can see which stage is crowded and which is open.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The competitors**: 3 to 6 names.
- **The buyer's problem**, in the words a buyer would use, for the Reddit search.

## Steps

1. **Read each competitor's current Meta ads**, one page each: Connector `ads_search`
   (`platform: "meta"`, `company`, `country` if it matters) · CLI
   `scrollhound ads search --platform meta --company <name> --since 30d`. Note how many the library
   holds against how many you read. If a competitor has none, say so.
2. **Sort every ad into one stage**, judged by its headline and first line:
   - **Unaware:** opens on a story, a joke or the viewer's life, and doesn't name the problem.
   - **Problem aware:** names the pain.
   - **Solution aware:** names a kind of solution or a new way of solving it.
   - **Product aware:** gives proof for this product over others (ratings, awards, people
     switching from a rival).
   - **Most aware:** an offer, a price, or just the product name and a button.
3. **Count** ads per stage and per competitor. Keep repeats in the count: running one message many
   times is a sign of where the money goes. Say when one message dominates.
4. **Read the buyers.** Connector `reddit_search` (`q`, `time: "year"`, `in: "posts"` or
   `"comments"`) and `reddit_get_post` (`ref`, `comments: 20`) · CLI
   `scrollhound reddit search "<what buyers say>" --time year` and
   `scrollhound reddit post <url> --comments 20`. Read the two or three most relevant threads.

## What to deliver

1. A table: stages down the side, competitors across the top, with totals.
2. One real ad per stage, quoted, with its link.
3. Which stage is crowded and which is open.
4. What the ads promise that real people say isn't enough, in their exact words.
5. Three ad lines for the open stage, built from people's own words.

## Rules

- **Words only.** The ad library gives the copy, not what's said in a video. Mark any ad whose
  stage could change once someone watches it.
- **Quote, don't paraphrase.** Ad copy and Reddit lines go in quotation marks, with their links.
- **One voice isn't a trend.** Say how many people said a thing, and flag posts that commenters
  doubt.
- **Say what you read.** End with how many ads per competitor (read against held), and how many
  threads and comments.
- **Never invent.** No made-up ads, counts or quotes.
- **Stay in scope.** Each read uses the user's Scrollhound credits: one page of ads per competitor
  and two or three threads, unless the user asks for more.
- **Read only.** Scrollhound never posts, likes, follows or messages anyone.

## Example request

> Run an awareness map on Monarch Money, Rocket Money and Copilot Money. The buyer's problem is
> "no idea where my money goes every month".
