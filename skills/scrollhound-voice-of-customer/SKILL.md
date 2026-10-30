---
name: scrollhound-voice-of-customer
description: "Voice-of-customer research from Reddit: find the pains, frustrations and wants people describe about a problem, product or category, in their own words, as a table of pain, exact quote and link. Use when the user asks for customer research, pain points, objections, what people hate or wish for, audience language for copy, or evidence for a client or positioning. Uses Scrollhound."
metadata:
  scrollhound-version: "1.0.0"
---

# Voice of customer from Reddit

Turn Reddit discussions into a pain–quote–link table a marketer can put in front of a client or use
to write copy. The pains and the wording live in the comments, so the threads are read in full.

Use the **Scrollhound connector** tools when they're available (Claude, ChatGPT, Cursor and
other AI apps), or the **`scrollhound` CLI** in a terminal. Each step names both.

## What you need

- **The problem or category**, in the words customers would use ("scheduling posts", not
  "social media management software"). Ask if it isn't clear.
- **Subreddits** where these customers talk, if the user knows them. Otherwise find them in step 1.

## Steps

1. **Find the threads.** Search for the problem, sorted by top posts of the past year. If the user
   named subreddits, search inside each one; a search across all of Reddit sorted by top tends to
   return viral posts that are off topic.
   - Connector: `reddit_search` with `q`, `subreddit`, `sort: "top"`, `time: "year"`
   - CLI: `scrollhound reddit search "<problem>" --sub <name> --sort top --time year`
2. **Pick the 5 most discussed threads** that are really about the problem (comment count matters
   more than points).
3. **Read each thread in full**, with up to 200 comments.
   - Connector: `reddit_get_post` with `ref` and `comments: 200`
   - CLI: `scrollhound reddit post <url> --comments 200`
4. **Group the pains.** Merge pains that are the same thing said differently, and count how many
   of the comments you read mention each one.

## What to deliver

A table, most mentioned pain first:

| Pain | How often (in what you read) | Exact quote | Link |
| --- | --- | --- | --- |

Then: the words customers use for the problem (useful for headlines and ads), what they've tried
and why it failed, and what they say they wish existed. Close with the threads you read and the
total comments read.

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

> What do freelancers hate about getting paid? Use r/freelance and r/smallbusiness, and give me quotes I can show a client.
