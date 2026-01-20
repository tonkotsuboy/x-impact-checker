---
paths:
  - "**/*.md"
  - ".git/COMMIT_EDITMSG"
---

# Project Conventions

## Language Standards

### Git Commits
- **All commit messages MUST be in English**
- Use conventional commit format: `<type>: <description>`
- Examples:
  - `feat: Add new scoring element`
  - `docs: Update algorithm reference`
  - `fix: Correct scoring calculation`

### Documentation
- **SKILL.md MUST be written in English**
- **algorithm-weights.md MUST be written in English**
- **README.md** maintains bilingual structure:
  - English section (lines 1-68)
  - Japanese section (lines 70-131)
  - Keep sections fully independent (no cross-translations)

## File Editing Guidelines

### When updating SKILL.md
- Write all content in English
- Maintain 3-tier scoring structure (Core/Extended/Relationship)
- Keep improvement strategies in ❌ Bad / ⚠️ Better / ✅ Best format
- Update corresponding sections in README.md (both English and Japanese)

### When updating algorithm-weights.md
- Document algorithm changes in English
- Reference official X algorithm repository (xai-org/x-algorithm)
- Maintain technical accuracy with source code references
