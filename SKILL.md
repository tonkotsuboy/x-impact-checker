---
name: x-impact-checker
description: >
  Analyze X (Twitter) posts for viral potential using the actual recommendation algorithm.
  Use when user wants to: (1) Check if a post will go viral, (2) Optimize a tweet for engagement,
  (3) Improve post performance. Triggers: "Check if this will go viral", "Make this post buzz",
  "Will this tweet perform well?", "Optimize my tweet", "How can I make this viral?",
  "バズるかチェックして", "Xでバズる投稿にして", "伸びるかチェックして", "この投稿を伸ばして",
  "投稿を改善して", "ツイートを最適化して"
---

# X Impact Checker

Analyze X posts for viral potential based on the open-source recommendation algorithm.

## Scoring System (100 points)

| Factor | Max | Scoring Guide |
|--------|-----|---------------|
| Reply Potential | 25 | 25: Direct question/debatable claim, 15: Invites response, 5: Statement only |
| Retweet Potential | 20 | 20: Actionable insight/surprising fact, 10: Interesting but niche, 0: No share value |
| Favorite Potential | 15 | 15: Emotionally resonant/personal story, 8: Useful reference, 0: Low appeal |
| Quote Potential | 12 | 12: Strong opinion inviting commentary, 6: Thought-provoking, 0: No quote value |
| Dwell Time | 10 | 10: Long-form/detailed content, 5: Medium depth, 0: Skimmable |
| Share Potential | 8 | 8: DM/external share worthy, 4: Limited appeal, 0: No share value |
| Profile Click | 5 | 5: Creates author curiosity, 2: Shows expertise, 0: Generic voice |
| Follow Potential | 5 | 5: Demonstrates ongoing value, 2: Shows potential, 0: One-off content |

### Penalties (subtract from total)

| Risk | Range | Trigger |
|------|-------|---------|
| Not Interested | -5 to -15 | Clickbait, irrelevant content |
| Mute Risk | -5 to -15 | Repetitive, annoying patterns |
| Block Risk | -10 to -25 | Offensive, aggressive tone |
| Report Risk | -15 to -30 | Policy violations, spam signals |

## Grades

| Score | Grade |
|-------|-------|
| 90-100 | S (Exceptional) |
| 75-89 | A (Strong) |
| 60-74 | B (Good) |
| 45-59 | C (Average) |
| 30-44 | D (Below average) |
| 0-29 | F (Low potential) |

## Output Format

1. **Score**: `XX/100 (Grade: X)`

2. **Breakdown Table**:
```
| Factor | Score | Assessment |
|--------|-------|------------|
| Reply | X/25 | [reason] |
| ... | ... | ... |
| Total | XX/100 | Grade: X |
```

3. **Top 3 Improvements**: Specific, actionable suggestions

4. **Optimized Version**: Rewritten post with improvements applied

## Improvement Strategies

- **Reply**: End with question, make debatable claim, ask for opinions
- **Retweet**: Add statistics, create takeaways, use numbered lists
- **Favorite**: Add emotional resonance, share personal insight
- **Quote**: Take clear stance, challenge conventional wisdom
- **Dwell**: Add examples, use thread format for complex topics

## Language Handling

Detect input language. Respond in same language. Keep optimized version in original language.

## Algorithm Reference

See [references/algorithm-weights.md](references/algorithm-weights.md) for weight details from X's open-source algorithm.
