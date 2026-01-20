# X Algorithm Weight Reference

Based on X's open-source recommendation algorithm.

## Source

- Repository: https://github.com/twitter/the-algorithm
- Weighted Scorer: `home-mixer/scorers/weighted_scorer.rs`
- ML Model: Phoenix (Grok-based transformer)

## Engagement Predictions

Phoenix predicts probabilities for:

```
P(favorite), P(reply), P(retweet), P(quote), P(click),
P(profile_click), P(video_view), P(photo_expand), P(share),
P(share_via_dm), P(share_via_copy_link), P(dwell),
P(follow_author), P(not_interested), P(block), P(mute), P(report)
```

## Score Calculation

```rust
combined_score =
    favorite_score * FAVORITE_WEIGHT
  + reply_score * REPLY_WEIGHT
  + retweet_score * RETWEET_WEIGHT
  + quote_score * QUOTE_WEIGHT
  + dwell_score * DWELL_WEIGHT
  + share_score * SHARE_WEIGHT
  + profile_click_score * PROFILE_CLICK_WEIGHT
  + follow_author_score * FOLLOW_AUTHOR_WEIGHT
  + not_interested_score * NOT_INTERESTED_WEIGHT  // negative
  + block_author_score * BLOCK_AUTHOR_WEIGHT      // negative
  + mute_author_score * MUTE_AUTHOR_WEIGHT        // negative
  + report_score * REPORT_WEIGHT                  // negative
```

## Skill Weight Mapping

| Algorithm Signal | Skill Factor | Weight |
|-----------------|--------------|--------|
| REPLY_WEIGHT | Reply Potential | 25% |
| RETWEET_WEIGHT | Retweet Potential | 20% |
| FAVORITE_WEIGHT | Favorite Potential | 15% |
| QUOTE_WEIGHT | Quote Potential | 12% |
| DWELL_WEIGHT | Dwell Time | 10% |
| SHARE_WEIGHT (combined) | Share Potential | 8% |
| PROFILE_CLICK_WEIGHT | Profile Click | 5% |
| FOLLOW_AUTHOR_WEIGHT | Follow Potential | 5% |

## Key Insights

1. **Reply dominates**: Conversations drive visibility
2. **Negative signals matter**: Block/mute/report have negative weights
3. **Multi-action prediction**: Not single relevance score, but many action probabilities
