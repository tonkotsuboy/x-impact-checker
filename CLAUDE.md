# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

X Impact Checker is a Claude skill that analyzes X (Twitter) posts for viral potential based on X's official recommendation algorithm.

**Purpose**: Predict engagement and provide optimization suggestions before posting using X's official recommendation algorithm scoring system

**Technology**: Documentation-based skill (markdown only, no codebase)

## Repository Structure

```
/
├── skills/x-impact-checker/
│   ├── SKILL.md                          # Skill definition and detailed scoring criteria
│   └── references/algorithm-weights.md   # Complete reference for X's official algorithm
├── README.md                             # Project documentation (English/Japanese)
└── LICENSE                               # Apache 2.0
```

## Core Components

### 1. SKILL.md
Defines the main skill logic:
- **Scoring system**: Tier 1 (Core Engagement 60 points), Tier 2 (Extended Engagement 25 points), Tier 3 (Relationship Building 15 points), Negative Signals (penalties)
- **Evaluation criteria**: Detailed scoring guides for each element
- **Improvement strategies**: ❌ Bad / ⚠️ Better / ✅ Best examples
- **Output format**: Score, breakdown table, top 5 priority improvements, optimized version

### 2. algorithm-weights.md
Technical reference for X's official algorithm:
- **Engagement signals**: Positive and negative engagement probabilities predicted by Phoenix ML model
- **Weights**: Actual weight coefficients from `weighted_scorer.rs`
- **Conditional logic**: VQV (Video Quality View) 5-second threshold, etc.
- **Normalization**: Offset/dampening/penalty capping

## Scoring System Architecture

**100-point system**:
```
Final Score = Base Score (0-100) + Penalties (-75 to 0)
Normalized = max(0, min(100, Final Score))
```

**Key algorithm characteristics**:
1. Reply (22 points) is most important - conversation-driving content ranks highest
2. Multiple share actions (general/DM/link copy) are distinguished
3. Two types of dwell time measured (initial read/continuous engagement)
4. Videos score fully only at 5+ seconds (VQV condition)
5. Negative signals are dampened to prevent excessive penalization

## Documentation Standards

### Language Separation
- **English Section**: Lines 1-68 in README.md
- **Japanese Section**: Lines 70-131 in README.md
- Each section is completely independent (no cross-translations)

### Attribution Requirements
- Maintain explicit reference to X's official algorithm (https://github.com/xai-org/x-algorithm)
- Apache 2.0 license compliance
- Use "based on publicly documented specifications" rather than "derivative work"

## Common Tasks

### Updating Skill Specifications
1. Edit `skills/x-impact-checker/SKILL.md` (scoring criteria/improvement strategies)
2. Synchronize updates to both language sections in `README.md`
3. Update reference in `algorithm-weights.md` if needed

### Documentation Consistency Check
```bash
# Verify scoring element count across 3 files
grep -c "points\|潜在力" README.md skills/x-impact-checker/SKILL.md skills/x-impact-checker/references/algorithm-weights.md
```

### Version Control
- `.DS_Store` excluded via `.gitignore`
- Commit messages in Japanese (e.g., "19要素スコアリングシステムに拡張")

## Key Design Decisions

1. **Codeless architecture**: Heuristic text analysis, not ML model
2. **Conservative scoring**: Unknown elements receive baseline scores
3. **Optimization-focused**: Tool for pre-publishing improvement, not post-hoc analytics
4. **Language-agnostic**: Detects input language and responds/optimizes in same language

## Limitations (Text Analysis)

**Cannot detect**:
- Actual media presence/quality
- User engagement history
- Author reputation/follower count
- Phoenix ML model prediction values

**Can infer from**:
- Language patterns (question format, controversial claims)
- Content structure (threads, lists)
- Emotional tone
- Visual indicators (emojis, markdown)

## License Compliance

- **This project**: Apache 2.0 (Copyright 2026 tonkotsuboy)
- **Reference source**: X Algorithm (Apache 2.0, xai-org)
- **Relationship**: Independent implementation based on algorithm specifications (not direct code port)
