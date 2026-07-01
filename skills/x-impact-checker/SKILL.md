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

Analyze X posts for viral potential based on the open-source recommendation algorithm (19-element scoring system).

## Optional Hermes Tweet Context

When running inside Hermes Agent, Hermes Tweet can supply public X/Twitter context before scoring:

1. Install Hermes Tweet and set `XQUIK_API_KEY`.
2. Keep `HERMES_TWEET_ENABLE_ACTIONS` unset for analysis-only use.
3. Use Hermes Tweet's read-only tools to inspect public post, profile, or recent timeline context for a supplied URL or handle.
4. Use that context as evidence for scoring, but keep the 19-element scoring system below unchanged.

## Scoring System (100 points)

### Tier 1: Core Engagement (60 points)

Conversation drivers and strong sharing signals.

| Factor | Max | Scoring Guide |
|--------|-----|---------------|
| Reply Potential | 22 | 22: Direct question/debatable claim, 12: Invites response, 4: Statement only |
| Retweet Potential | 16 | 16: Actionable insight/surprising fact, 8: Interesting but niche, 0: No share value |
| Favorite Potential | 12 | 12: Emotionally resonant/personal story, 6: Useful reference, 0: Low appeal |
| Quote Potential | 10 | 10: Strong opinion inviting commentary, 5: Thought-provoking, 0: No quote value |

### Tier 2: Extended Engagement (25 points)

Media interactions and sustained attention metrics.

| Factor | Max | Scoring Guide |
|--------|-----|---------------|
| Dwell Time | 6 | 6: Long-form/detailed content, 3: Medium depth, 0: Skimmable |
| Continuous Dwell Time | 4 | 4: Thread/story arc requiring sustained attention, 2: Medium complexity, 0: Quick read |
| Click Potential | 5 | 5: Compelling link with clear CTA, 3: Link with context, 1: Bare URL, 0: No link |
| Photo Expand Potential | 4 | 4: Multiple images/visual storytelling, 2: Single image reference, 0: No visual content |
| Video View Potential | 3 | 3: Long-form video with hook (>5s), 2: Short clip, 0: No video |
| Quoted Click Potential | 3 | 3: Bold claim inviting verification, 2: Interesting claim, 0: Self-contained |

### Tier 3: Relationship Building (15 points)

Author discovery and long-term value signals.

| Factor | Max | Scoring Guide |
|--------|-----|---------------|
| Profile Click | 5 | 5: Creates author curiosity, 3: Shows expertise, 0: Generic voice |
| Follow Potential | 4 | 4: Demonstrates ongoing value, 2: Shows potential, 0: One-off content |
| Share Potential | 2 | 2: General sharing value, 1: Limited appeal, 0: No value |
| Share via DM | 2 | 2: Personal/relatable "send to friend" content, 1: Somewhat relatable, 0: Generic |
| Share via Copy Link | 2 | 2: Reference/bookmark worthy, 1: Useful but not evergreen, 0: Ephemeral |

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

Use emojis throughout the report for better visual clarity and engagement.

### Progress Tracking

Use TodoWrite tool to show analysis progress with these tasks:

1. **Analyzing post content** (in_progress → completed)
   - activeForm: "Analyzing post content"
   - content: "Analyze post content"

2. **Calculating scores across all elements** (in_progress → completed)
   - activeForm: "Calculating scores across all elements"
   - content: "Calculate scores across all elements"

3. **Generating top 5 priority improvements** (in_progress → completed)
   - activeForm: "Generating top 5 priority improvements"
   - content: "Generate top 5 priority improvements"

4. **Creating optimized version** (in_progress → completed)
   - activeForm: "Creating optimized version"
   - content: "Create optimized version"

Mark each task as completed immediately after finishing that step.

### Report Structure

1. **Score**: `🎯 XX/100 (Grade: X)`

2. **Breakdown Table**:
```
| Category | Factor | Score | Max | Assessment |
|----------|--------|-------|-----|------------|
| **💬 Core Engagement** | | | 60 | |
| | 💭 Reply Potential | X/22 | 22 | [reason] |
| | 🔄 Retweet Potential | X/16 | 16 | [reason] |
| | ❤️ Favorite Potential | X/12 | 12 | [reason] |
| | 💬 Quote Potential | X/10 | 10 | [reason] |
| **⏱️ Extended Engagement** | | | 25 | |
| | 👀 Dwell Time | X/6 | 6 | [reason] |
| | ⏳ Continuous Dwell Time | X/4 | 4 | [reason] |
| | 🔗 Click Potential | X/5 | 5 | [reason] |
| | 🖼️ Photo Expand | X/4 | 4 | [reason] |
| | 🎥 Video View | X/3 | 3 | [reason] |
| | 🔍 Quoted Click | X/3 | 3 | [reason] |
| **🤝 Relationship Building** | | | 15 | |
| | 👤 Profile Click | X/5 | 5 | [reason] |
| | ➕ Follow Potential | X/4 | 4 | [reason] |
| | 📤 Share Potential | X/2 | 2 | [reason] |
| | 💌 Share via DM | X/2 | 2 | [reason] |
| | 📋 Share via Link | X/2 | 2 | [reason] |
| **⚠️ Negative Signals** | | | | |
| | 😐 Not Interested Risk | -X | 0 to -15 | [reason] |
| | 🔇 Mute Risk | -X | 0 to -15 | [reason] |
| | 🚫 Block Risk | -X | 0 to -25 | [reason] |
| | 🚨 Report Risk | -X | 0 to -30 | [reason] |
| **🏆 TOTAL** | | **XX/100** | | **Grade: X** |
```

3. **📈 Top 5 Priority Improvements**: Specific, actionable suggestions across different categories
   - Use emojis like ✅, 💡, 🎯 to highlight key improvements

4. **✨ Optimized Version**: Rewritten post with improvements applied (in original language)

## Detailed Scoring Criteria & Improvement Strategies

### Tier 1: Core Engagement

#### Reply Potential (22 points)

**Evaluation Criteria:**
- Direct questions: "What do you think?", "How would you solve this?"
- Debatable claims: "X is better than Y"
- Opinion invitations: "Agree or disagree?"
- Open-ended prompts
- Controversial but thoughtful statements

**Improvement Strategies:**
- ❌ Bad: "Just shipped a new feature."
- ⚠️ Better: "Just shipped a new feature. Thoughts?"
- ✅ Best: "Should features ship fast but buggy, or slow but stable? We chose speed—was it the right call?"

#### Retweet Potential (16 points)

**Evaluation Criteria:**
- Actionable insights: "Here's how..."
- Surprising facts: "X% of developers don't know..."
- Numbered lists: "3 ways to...", "10 lessons from..."
- Data-driven content
- Shareable takeaways
- Universal truths

**Improvement Strategies:**
- ❌ Bad: "I learned something today."
- ⚠️ Better: "I learned React hooks can reduce bundle size by 30%."
- ✅ Best: "🧵 3 React patterns that cut my bundle size by 30%:\n\n1. Lazy loading hooks\n2. Code splitting by route\n3. Tree-shaking unused exports"

#### Favorite Potential (12 points)

**Evaluation Criteria:**
- Emotional resonance: joy, frustration, triumph
- Personal stories: "When I was..."
- Relatable moments: "We've all been there..."
- Inspirational content
- Vulnerability and authenticity
- Useful references worth saving

**Improvement Strategies:**
- ❌ Bad: "Debugging is hard."
- ⚠️ Better: "Spent 3 hours debugging a typo."
- ✅ Best: "Spent 3 hours debugging a production issue. The fix? A missing semicolon I added during 'quick cleanup' at 2am. Never touching working code past midnight again 😅"

#### Quote Potential (10 points)

**Evaluation Criteria:**
- Strong opinions: "X is dead", "Y is overrated"
- Challenges conventional wisdom
- Invites commentary and counter-arguments
- Takes clear stance on controversial topics
- Thought-provoking perspectives

**Improvement Strategies:**
- ❌ Bad: "TypeScript is useful."
- ⚠️ Better: "TypeScript prevents bugs."
- ✅ Best: "TypeScript's biggest value isn't catching bugs—it's documentation. The type errors are just a bonus. Fight me."

---

### Tier 2: Extended Engagement

#### Dwell Time (6 points)

**Evaluation Criteria:**
- Long-form content requiring reading time
- Detailed explanations with examples
- Technical depth
- Multi-paragraph structure
- Educational content

**Improvement Strategies:**
- Add concrete examples: "For instance, when building X..."
- Include numbers and data: "This reduced latency from 200ms to 50ms"
- Structure with clear sections

#### Continuous Dwell Time (4 points)

**Evaluation Criteria:**
- Thread indicators: "🧵", "Thread:", "1/", numbered series
- Narrative structure: beginning, middle, end
- Complexity requiring re-reading
- Educational depth with layers
- Story arcs that unfold
- "And then..." structures

**Difference from Dwell Time:**
- **Dwell Time**: Initial reading duration (how long to read once)
- **Continuous Dwell Time**: Sustained attention (re-reading, contemplation, multi-part consumption)

**Improvement Strategies:**
- ❌ Bad: "Here's how I built X. [long explanation]"
- ⚠️ Better: "🧵 How I built X in 30 days"
- ✅ Best: "🧵 How I went from idea to $10k MRR in 30 days (1/8)\n\nDay 1-7: Validation\nDays 8-14: MVP\nDays 15-30: Launch\n\nHere's what nobody tells you..."

#### Click Potential (5 points)

**Evaluation Criteria:**
- Link presence and context quality
- Call-to-action strength: "Read more", "Discover", "Learn how"
- Preview/teaser effectiveness
- Curiosity gap creation: "The results were shocking..."
- Clear value proposition

**Improvement Strategies:**
- ❌ Bad: "https://example.com/article"
- ⚠️ Better: "Read more here: [link]"
- ✅ Best: "How I 10xed revenue in 3 months (full breakdown with screenshots): [link]"

#### Photo Expand Potential (4 points)

**Evaluation Criteria:**
- Image markers: [photo], [image], "pic.twitter.com"
- Visual language: "see", "look", "view", "check this out"
- Emojis suggesting visuals: 📸, 🎨, 👀, 📷, 🖼️
- Before/after comparisons
- Multiple image storytelling: "Swipe through..."
- Visual evidence: "Here's proof 👇"

**Improvement Strategies:**
- ❌ Bad: "My dashboard looks great now."
- ⚠️ Better: "Check out my new dashboard design."
- ✅ Best: "Before/after of my analytics dashboard redesign 👇\n\nWent from cluttered mess to clean insights in 2 days.\n\n[visual indicators suggest images present]"

#### Video View Potential (3 points)

**Evaluation Criteria:**
- Video markers: [video], "▶️", "watch", "tutorial", "demo"
- Duration hints: "2-min", "quick demo", "full walkthrough"
- Content preview describing what viewers will see
- Timestamp highlights: "Skip to 1:30 for..."
- Hook/teaser: "Wait for the ending..."

**VQV Eligibility (Conditional):**
Full scoring (3 points) applies only if video appears to be >5 seconds (long-form).
Inferred from: "full tutorial", "in-depth", "complete guide" vs "quick clip", "snippet"

**Improvement Strategies:**
- ❌ Bad: "Made a video."
- ⚠️ Better: "Watch my new tutorial ▶️"
- ✅ Best: "Full 8-minute breakdown: How to build this UI in Next.js ▶️\n\n0:00 Setup\n2:15 Components\n5:30 Animations\n\nBest part at 6:45"

#### Quoted Click Potential (3 points)

**Evaluation Criteria:**
- Provocative but incomplete statements
- Statistics or claims needing verification
- Hot takes inviting source investigation: "80% of startups fail because..."
- "Wait, what?" factor creating curiosity
- Source credibility questions
- Bold claims: "This changes everything"

**Improvement Strategies:**
- ❌ Bad: "Read this interesting study about developer productivity."
- ⚠️ Better: "New study shows remote developers are 20% more productive."
- ✅ Best: "New Stanford study: Remote developers write 35% more code but with 50% fewer bugs.\n\nThis destroys the 'office collaboration' myth."

---

### Tier 3: Relationship Building

#### Profile Click (5 points)

**Evaluation Criteria:**
- Creates author curiosity: "Who is this person?"
- Demonstrates expertise: "I built X at Y company"
- Shows unique perspective or background
- Credibility signals: credentials, experience
- Intriguing bio-worthy content

**Improvement Strategies:**
- ❌ Bad: "I think React is good."
- ⚠️ Better: "After 5 years with React, I think it's good."
- ✅ Best: "After architecting React apps for Airbnb, Netflix, and 50+ startups, here's what I wish I knew on day one:"

#### Follow Potential (4 points)

**Evaluation Criteria:**
- Demonstrates ongoing value: "I ship weekly tutorials on..."
- Shows consistent expertise
- Promises future content: "More on this tomorrow"
- Establishes content cadence
- Creates expectation of quality

**Improvement Strategies:**
- ❌ Bad: "Here's a React tip."
- ⚠️ Better: "Here's a React tip. I post these daily."
- ✅ Best: "React tip #47: [insight]\n\nI break down advanced React patterns every Monday. Following along? Tomorrow's is about suspense boundaries."

#### Share Potential (2 points)

**Evaluation Criteria:**
- General sharing value to broader audience
- Universal relevance
- Broad appeal across communities

**Improvement Strategies:**
- Make universally relevant, not niche-specific
- Focus on common problems everyone faces

#### Share via DM (2 points)

**Evaluation Criteria:**
- Personal relevance: "Tag someone who...", "Send this to..."
- Inside jokes or shared experiences
- Emotional resonance for 1-on-1 sharing: "This is so you 😂"
- Relatable scenarios: "We all have that friend..."
- "You need to see this" quality

**Improvement Strategies:**
- ❌ Bad: "Debugging is frustrating."
- ⚠️ Better: "Debugging production issues is stressful."
- ✅ Best: "Tag your developer friend who 'just quickly fixes' production on Friday at 5pm and breaks everything 😂"

#### Share via Copy Link (2 points)

**Evaluation Criteria:**
- Reference value: guides, lists, frameworks, cheatsheets
- Evergreen quality (not time-sensitive)
- Professional sharing context (Slack, email, bookmarks)
- "Save this" or "Bookmark" language
- Educational/tutorial content
- Resource library worthy

**Improvement Strategies:**
- ❌ Bad: "Here are some Git commands I use."
- ⚠️ Better: "Useful Git commands for daily work."
- ✅ Best: "📌 Bookmark this: 15 Git commands that saved me 100+ hours this year\n\n[Well-structured list with examples]\n\nPrint this and keep it next to your monitor."

---

## Score Normalization

The algorithm applies normalization to balance positive and negative signals:

```
Final Score = Base Score (0-100) + Penalties (-75 to 0)
Normalized Score = max(0, min(100, Final Score))
```

**Penalty Capping:**
- Total penalties ≤ -20: Applied at full weight
- Total penalties > -20: Gradual dampening begins
- Total penalties > -75: Hard cap at -75 to prevent over-penalization

This prevents a single negative signal from completely dominating the score while maintaining their importance in the algorithm.

---

## Text Analysis Limitations

This skill performs heuristic text-based analysis, not ML prediction.

### What This Skill Cannot Detect

**Missing Metadata:**
- Actual media presence (photos, videos)
- Real video duration or quality
- Actual click-through rates
- True engagement metrics
- Author reputation/follower count
- Tweet timestamps or virality history

**Cannot Access:**
- Phoenix ML model predictions
- User interaction history
- Network graph relationships
- Real-time engagement signals

### What This Skill Infers From

**Text-Based Heuristics:**
- Language patterns and structure
- Content formatting (threads, lists, etc.)
- Emotional tone and style
- Visual indicators (emojis, markdown)
- Call-to-action strength
- Question vs. statement structure

**Scoring Approach:**
- **Conservative**: Unknown elements get baseline scores
- **Pattern-Based**: Detects language cues (e.g., 📸 for photos, 🧵 for threads)
- **Optimization-Focused**: Best used for pre-publishing content improvement

### Best Use Case

Pre-publishing optimization to maximize engagement potential, not post-hoc analytics or prediction of actual engagement numbers.

---

## Language Handling

Detect input language. Respond in same language. Keep optimized version in original language.

### Bilingual Display for Category and Factor Names

**When input is in Japanese:**
- Display Category and Factor names as: `日本語訳（English Original）`
- Examples:
  - Category: `コアエンゲージメント（Core Engagement）`
  - Factor: `返信潜在力（Reply Potential）`
  - Factor: `リツイート潜在力（Retweet Potential）`

**When input is in English:**
- Display Category and Factor names in English only
- Examples:
  - Category: `Core Engagement`
  - Factor: `Reply Potential`

**Japanese translations with emojis for reference:**
- 💬 Core Engagement → コアエンゲージメント
- ⏱️ Extended Engagement → 拡張エンゲージメント
- 🤝 Relationship Building → 関係構築
- ⚠️ Negative Signals → ネガティブシグナル
- 💭 Reply Potential → 返信潜在力
- 🔄 Retweet Potential → リツイート潜在力
- ❤️ Favorite Potential → いいね潜在力
- 💬 Quote Potential → 引用潜在力
- 👀 Dwell Time → 滞在時間
- ⏳ Continuous Dwell Time → 継続滞在時間
- 🔗 Click Potential → クリック潜在力
- 🖼️ Photo Expand → 写真展開潜在力
- 🎥 Video View → 動画視聴潜在力
- 🔍 Quoted Click → 引用クリック潜在力
- 👤 Profile Click → プロフィールクリック
- ➕ Follow Potential → フォロー潜在力
- 📤 Share Potential → 共有潜在力
- 💌 Share via DM → DM経由共有
- 📋 Share via Link → リンクコピー共有
- 😐 Not Interested Risk → 興味なしリスク
- 🔇 Mute Risk → ミュートリスク
- 🚫 Block Risk → ブロックリスク
- 🚨 Report Risk → 報告リスク

## Algorithm Reference

See [references/algorithm-weights.md](references/algorithm-weights.md) for complete weight details from X's open-source algorithm (19-element system).
