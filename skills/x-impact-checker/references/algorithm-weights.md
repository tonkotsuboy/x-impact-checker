# X Algorithm Signal Reference

Public-source signal map for the X Impact Checker skill.

This file documents the public signal list and scorer shape used to inform the skill. It is not a table of published production weights. The skill's 100-point scale is an explainable heuristic for pre-publishing review.

## Source Check

- Repository: https://github.com/xai-org/x-algorithm
- Checked commit: `0bfc2795d308f90032544322747caacd535f75ae`
- Checked date: June 2026
- Phoenix actions: `phoenix/runners.py`
- Legacy weighted scorer: `home-mixer/scorers/weighted_scorer.rs`
- Current ranking scorer: `home-mixer/scorers/ranking_scorer.rs`

## What The Public Source Shows

The public repository exposes a two-stage scoring shape:

1. Phoenix predicts action probabilities for public engagement and feedback signals.
2. A scorer combines those model outputs with weights and normalization before ranking.

Important source constraints:

- `ranking_scorer.rs` reads many weights from runtime parameters with `params.get(...)`.
- Exact current production weights are not published in the checked source.
- Negative feedback is included with positive engagement signals.
- Video quality view scoring depends on video duration eligibility.
- The scorer normalizes positive and negative totals before ranking.
- Additional adjustments such as author diversity can apply after the weighted score.

## Phoenix Signals

Phoenix includes these action outputs:

```text
favorite_score
reply_score
repost_score
photo_expand_score
click_score
profile_click_score
vqv_score
share_score
share_via_dm_score
share_via_copy_link_score
dwell_score
quote_score
quoted_click_score
follow_author_score
not_interested_score
block_author_score
mute_author_score
report_score
dwell_time
```

The current scorer also references additional signals such as quoted video quality view, click dwell time, and not-dwelled feedback.

## Skill Weight Mapping

The skill redistributes public signal importance into a readable 100-point rubric. These points are not published X weights.

### Tier 1: Core Engagement (60 points)

| Source Signal | Skill Factor | Points | Review Rationale |
| --- | --- | ---: | --- |
| `reply_score` | Reply Potential | 22 | Conversation starters often create visible distribution loops. |
| `repost_score` | Retweet Potential | 16 | Reposts amplify beyond the author's audience. |
| `favorite_score` | Favorite Potential | 12 | Likes show broad affinity and save value. |
| `quote_score` | Quote Potential | 10 | Quote posts add commentary and secondary reach. |

### Tier 2: Extended Engagement (25 points)

| Source Signal | Skill Factor | Points | Review Rationale |
| --- | --- | ---: | --- |
| `dwell_score` | Dwell Time | 6 | Dense, useful content can hold initial attention. |
| `dwell_time` | Continuous Dwell Time | 4 | Threads and layered ideas can earn sustained attention. |
| `click_score` | Click Potential | 5 | Links need clear context and a reason to open. |
| `photo_expand_score` | Photo Expand Potential | 4 | Visual proof and before/after content invite expansion. |
| `vqv_score` | Video View Potential | 3 | Video value depends on real duration and quality hints. |
| `quoted_click_score` | Quoted Click Potential | 3 | Claims that invite verification can drive source clicks. |

### Tier 3: Relationship Building (15 points)

| Source Signal | Skill Factor | Points | Review Rationale |
| --- | --- | ---: | --- |
| `profile_click_score` | Profile Click | 5 | Expertise and curiosity can move readers to the profile. |
| `follow_author_score` | Follow Potential | 4 | Repeatable value can turn a post into author interest. |
| `share_score` | Share Potential | 2 | Broad relevance increases general sharing. |
| `share_via_dm_score` | Share via DM | 2 | Personal relevance increases 1-to-1 sharing. |
| `share_via_copy_link_score` | Share via Copy Link | 2 | Evergreen references are easier to save and circulate. |

### Negative Signals

| Source Signal | Skill Factor | Range | Review Rationale |
| --- | --- | ---: | --- |
| `not_interested_score` | Not Interested Risk | -5 to -15 | Clickbait and irrelevant content can trigger dismissals. |
| `mute_author_score` | Mute Risk | -5 to -15 | Repetitive or annoying patterns can hurt the author. |
| `block_author_score` | Block Risk | -10 to -25 | Hostile tone can trigger stronger negative feedback. |
| `report_score` | Report Risk | -15 to -30 | Spam or policy-risk content needs severe penalties. |

## Conditional Logic

### Video Quality View

Video scoring should not assume full credit from the word "video" alone. Use duration hints when present:

- Full tutorial, long walkthrough, webinar, or in-depth demo: stronger video score.
- Quick clip, short demo, snippet, or no duration clue: lower video score.
- No video marker: 0 video points.

### Source Evidence

The strongest reviews combine draft text with visible context. When a post URL, status ID, account, or competitor example is available, gather a short source evidence packet before scoring. TweetClaw can help collect public X/Twitter evidence when it is available in the user's approved runtime.

Never treat inferred context as private metrics. If live metrics, reply themes, media details, or author history are unavailable, mark them unknown and keep the score conservative.

## Text Analysis Limits

This skill is not an ML predictor and cannot access production ranking state. It cannot determine:

- User interaction history
- Private network graph relationships
- Exact production weights
- Unseen media quality
- True future engagement
- Private account-level reputation

Use the score to improve a draft before publishing, not to guarantee performance.
