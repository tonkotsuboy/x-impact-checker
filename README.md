# X Impact Checker

A Claude Code skill that analyzes X (Twitter) posts for viral potential using X's actual recommendation algorithm.

## Installation

```bash
npx add-skill tonkotsuboy/x-impact-checker
```

## Usage

Trigger the skill with phrases like:

**English:**
- "Check if this will go viral: [your post]"
- "Make this post buzz: [your post]"
- "Optimize my tweet: [your post]"

**Japanese:**
- "バズるかチェックして: [投稿内容]"
- "Xでバズる投稿にして: [投稿内容]"
- "伸びるかチェックして: [投稿内容]"

## Scoring System (100 points)

| Factor | Max Points |
|--------|------------|
| Reply Potential | 25 |
| Retweet Potential | 20 |
| Favorite Potential | 15 |
| Quote Potential | 12 |
| Dwell Time | 10 |
| Share Potential | 8 |
| Profile Click | 5 |
| Follow Potential | 5 |

## Algorithm Source

Based on X's open-source recommendation algorithm:
- https://github.com/xai-org/x-algorithm

## License

Apache 2.0

---

# X Impact Checker (日本語)

X（旧Twitter）の公式推薦アルゴリズムに基づいて、投稿のバイラル可能性を分析するClaude Codeスキルです。

## インストール

```bash
npx add-skill tonkotsuboy/x-impact-checker
```

## 使い方

- "バズるかチェックして: [投稿内容]"
- "Xでバズる投稿にして: [投稿内容]"
- "伸びるかチェックして: [投稿内容]"

## ライセンス

Apache 2.0
