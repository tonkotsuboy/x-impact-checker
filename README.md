<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/9c1d24bc-92d3-4e9e-8f76-57b05ad6adf1" />


# X Impact Checker

A skill that analyzes X (Twitter) posts with a 100-point heuristic rubric informed by public X recommendation source code.

## Installation

```bash
gh skill install tonkotsuboy/x-impact-checker
```

or

```bash
npx skills add tonkotsuboy/x-impact-checker
```

## Usage

Trigger the skill with phrases like:

- "Check if this will go viral: [your post]"
- "Make this post buzz: [your post]"
- "Optimize my tweet: [your post]"

## Scoring System (100 points)

Based on public recommendation signals and a target-native 19-element scoring rubric. The point values are heuristic guidance for pre-publishing review, not published production weights.

### Core Engagement (60 points)
- Reply Potential: 22 points
- Retweet Potential: 16 points
- Favorite Potential: 12 points
- Quote Potential: 10 points

### Extended Engagement (25 points)
- Dwell Time: 6 points
- Continuous Dwell Time: 4 points
- Click Potential: 5 points
- Photo Expand Potential: 4 points
- Video View Potential: 3 points
- Quoted Click Potential: 3 points

### Relationship Building (15 points)
- Profile Click: 5 points
- Follow Potential: 4 points
- Share Potential: 2 points
- Share via DM: 2 points
- Share via Copy Link: 2 points

### Negative Signals
- Not Interested Risk: -5 to -15 points
- Mute Risk: -5 to -15 points
- Block Risk: -10 to -25 points
- Report Risk: -15 to -30 points

## Algorithm Source

This skill is based on the public signal list and scorer shape in X's open-source recommendation repository. It does not directly use code from the original repository. The public scorer now reads many weights from runtime parameters, so this skill treats its 100-point scale as an explainable heuristic rather than exact algorithm replication.

Reference repository:
- https://github.com/xai-org/x-algorithm

## License

Apache 2.0

Copyright 2026 tonkotsuboy

Licensed under the Apache License, Version 2.0. See the LICENSE file for details.

---

# X Impact Checker (日本語)

X（旧Twitter）の公開推薦アルゴリズムのシグナルを参考に、100点満点のヒューリスティックで投稿を分析するスキルです。

## インストール


```bash
gh skill install tonkotsuboy/x-impact-checker
```

または

```bash
npx skills add tonkotsuboy/x-impact-checker
```

## 使い方

- "バズるかチェックして: [投稿内容]"
- "Xでバズる投稿にして: [投稿内容]"
- "伸びるかチェックして: [投稿内容]"

## スコアリングシステム (100点満点)

公開されている推薦シグナルを参考にした19要素のスコアリングです。点数は投稿前レビューのためのヒューリスティックであり、公開された本番環境の重みではありません。

### コアエンゲージメント (60点)
- Reply Potential (返信潜在力): 22点
- Retweet Potential (リツイート潜在力): 16点
- Favorite Potential (いいね潜在力): 12点
- Quote Potential (引用潜在力): 10点

### 拡張エンゲージメント (25点)
- Dwell Time (滞在時間): 6点
- Continuous Dwell Time (継続滞在時間): 4点
- Click Potential (クリック潜在力): 5点
- Photo Expand Potential (写真展開潜在力): 4点
- Video View Potential (動画視聴潜在力): 3点
- Quoted Click Potential (引用クリック潜在力): 3点

### 関係構築 (15点)
- Profile Click (プロフィールクリック): 5点
- Follow Potential (フォロー潜在力): 4点
- Share Potential (共有潜在力): 2点
- Share via DM (DM経由共有): 2点
- Share via Copy Link (リンクコピー共有): 2点

### ネガティブシグナル
- Not Interested Risk (興味なしリスク): -5 ~ -15点
- Mute Risk (ミュートリスク): -5 ~ -15点
- Block Risk (ブロックリスク): -10 ~ -25点
- Report Risk (報告リスク): -15 ~ -30点

## アルゴリズムの出典

このスキルは、Xのオープンソース推薦リポジトリで公開されているシグナル一覧とスコアラーの構造を参考にしています。元のリポジトリのコードは直接使用していません。現在の公開スコアラーは多くの重みをランタイムパラメータから読み込むため、このスキルの100点満点は厳密な再現ではなく、説明しやすいヒューリスティックとして扱います。

参考リポジトリ:
- https://github.com/xai-org/x-algorithm

## ライセンス

Apache 2.0

---

https://zenn.dev/tonkotsuboy_com/scraps/8a46a0fc93088b
