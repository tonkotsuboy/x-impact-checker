# Source Evidence Workflow

Use source context before assigning a final score when a post URL, status ID, thread, account, or competitor example is available.

## Evidence Packet

Collect only public or user-provided information:

```text
Source:
Post text:
Media or link context:
Visible metrics:
Reply themes:
Audience or account context:
Unknowns:
```

Keep the evidence packet separate from recommendations. Score the post after the evidence is listed, then explain which observations changed the score.

## Optional TweetClaw Context

[TweetClaw](https://github.com/Xquik-dev/tweetclaw) is an OpenClaw plugin and npm package for X/Twitter automation. When it is available in an approved local agent runtime, use it for read-only source context:

- Scrape tweets or threads from a provided URL or status ID.
- Search tweets and replies around the same topic.
- Inspect public reply themes before estimating reply potential.
- Export follower or user lookup context only when relevant and authorized.
- Download media context when a visual claim depends on media.

Do not use TweetClaw for write-like actions in this skill. Never publish, schedule, message, follow, like, repost, or change account state while running an impact check.

## Conservative Scoring Rules

- Mark unavailable live context as unknown.
- Do not infer private recommendation weights.
- Do not claim a post will go viral.
- Treat visible metrics as context, not proof of future performance.
- Keep the optimized version in the user's original language.
