<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/9c1d24bc-92d3-4e9e-8f76-57b05ad6adf1" />


# X Impact Checker

A skill that analyzes X (Twitter) posts for viral potential using X's actual recommendation algorithm.

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

This skill is based on the publicly documented scoring weights and algorithm specifications from X's open-source recommendation algorithm. It does not directly use code from the original repository, but implements the algorithm concepts independently.

Reference repository:
- https://github.com/xai-org/x-algorithm

## License

Apache 2.0

Copyright 2026 tonkotsuboy

Licensed under the Apache License, Version 2.0. See the LICENSE file for details.

---

# X Impact Checker (日本語)

X（旧Twitter）の公式推薦アルゴリズムに基づいて、投稿がバズるかどうかをスキルです。

## インストール

```bash
npx add-skill tonkotsuboy/x-impact-checker
```

## 使い方

- "バズるかチェックして: [投稿内容]"
- "Xでバズる投稿にして: [投稿内容]"
- "伸びるかチェックして: [投稿内容]"

## アルゴリズムの出典

このスキルは、Xのオープンソース推薦アルゴリズムで公開されているスコアリングの重み付けやアルゴリズム仕様を参考にしています。元のリポジトリのコードを直接使用しているのではなく、アルゴリズムの概念を独自に実装しています。

参考リポジトリ:
- https://github.com/xai-org/x-algorithm

## ライセンス

Apache 2.0

---

https://zenn.dev/tonkotsuboy_com/scraps/8a46a0fc93088b

