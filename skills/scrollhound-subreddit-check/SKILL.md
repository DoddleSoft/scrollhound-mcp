---
name: scrollhound-subreddit-check
description: "Check a subreddit before posting: read its full rules in the moderators' words, its posting requirements (post types, flair, title and link rules) and wiki, and its top posts this month, then check the user's draft against them. Use when the user wants to post or promote on Reddit, asks whether a post is allowed, wants to avoid removal or bans, or asks what gets traction in a subreddit. Uses Scrollhound."
metadata:
  scrollhound-version: "1.2.1"
---

# Check a subreddit before you post

Many subreddits remove self-promotion, links or certain flairs, and some ban accounts for it. This
skill reads the rules as the moderators wrote them and shows what does well there, before the
user posts.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The subreddit** (`SaaS`, `r/SaaS` or its URL).
- **The draft post**, if the user has one.

## Steps

1. **Read the subreddit's description, posting requirements and full rules.** The requirements
   say which post types are allowed, whether a flair is required (and which ones exist), and any
   title or link rules.
   - Connector: `reddit_get_subreddit` with `name` · CLI: `scrollhound reddit sub <name>`
2. **Read the wiki page the rules point to**, if any (many subreddits keep the full rules or a
   self-promotion policy there).
   - Connector: `read_url` with `https://www.reddit.com/r/<name>/wiki/<page>`
   - CLI: `scrollhound read reddit.com/r/<name>/wiki/<page>`
3. **Read the top posts of the month** to see what gets traction.
   - Connector: `reddit_list_posts` with `subreddit`, `sort: "top"`, `time: "month"`
   - CLI: `scrollhound reddit posts <name> --sort top --time month`
4. **Check the draft** against each relevant rule and requirement: post type, flair, title
   format, self-promotion, links, required disclosures, posting days or megathreads.

## What to deliver

1. The rules and requirements that matter for this post, quoted exactly (and the flair to pick).
2. A verdict: fits, fits with changes, or don't post here (and why).
3. If it needs changes: the specific edits, or a rewritten draft that follows the rules.
4. What gets traction this month (formats and topics of the top posts, with links).
5. If promotion isn't allowed: where it is (a weekly thread or a different subreddit), only if the
   rules or top posts say so.

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

> I want to share my tool in r/SaaS. Here's my draft. Will it get removed?
