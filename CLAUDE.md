# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

X Impact Checker is a Claude skill that analyzes X (Twitter) posts for viral potential based on X's official recommendation algorithm.

**Purpose**: Predict engagement and provide optimization suggestions before posting using X's official recommendation algorithm scoring system

**Technology**: Documentation-based skill (markdown only, no codebase)

## Repository Structure

```
/
├── .claude/rules/project-conventions.md  # Language and commit standards
├── skills/x-impact-checker/
│   ├── SKILL.md                          # Skill definition and scoring criteria
│   └── references/algorithm-weights.md   # X algorithm reference
├── README.md                             # Bilingual documentation (EN/JP)
└── LICENSE                               # Apache 2.0
```

## Core Components

### SKILL.md
Main skill logic with 3-tier scoring system (Core/Extended/Relationship Engagement + Negative Signals), evaluation criteria, and improvement strategies in ❌ Bad / ⚠️ Better / ✅ Best format.

### algorithm-weights.md
Technical reference for X's algorithm: engagement signals, weight coefficients from `weighted_scorer.rs`, conditional logic (VQV threshold), and normalization.

## Scoring Architecture

100-point system with penalty dampening:
```
Final Score = Base Score (0-100) + Penalties (-75 to 0)
Normalized = max(0, min(100, Final Score))
```

**Key characteristics**:
- Reply (22 points) is highest weighted - conversation drives visibility
- Multiple share types distinguished (general/DM/link copy)
- Two dwell time types (initial read/continuous engagement)
- Videos require 5+ seconds for full score (VQV condition)
- Negative signals dampened to prevent over-penalization

## Design Decisions

1. **Codeless architecture**: Heuristic text analysis, not ML model
2. **Conservative scoring**: Unknown elements get baseline scores
3. **Optimization-focused**: Pre-publishing tool, not post-hoc analytics
4. **Language-agnostic**: Detects input language, responds in same language

## Text Analysis Limitations

**Cannot detect**: Actual media, user history, author reputation, Phoenix ML predictions

**Infers from**: Language patterns, content structure, emotional tone, visual indicators

## License

Apache 2.0 (Copyright 2026 tonkotsuboy). Based on X Algorithm specifications (Apache 2.0, xai-org).
