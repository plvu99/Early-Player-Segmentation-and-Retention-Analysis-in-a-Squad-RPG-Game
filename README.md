# Early Player Segmentation and Retention Analysis (Squad RPG Game)

## Overview

This project analyzes **early player behavior (Day 0–Day 1)** in a Squad RPG mobile game to identify patterns that drive player retention and early monetization.

Using behavioral gameplay data, **segmentation and clustering techniques** were applied to group players based on engagement, spending behavior, and gameplay preferences. The goal is to help game developers better understand early player behavior and design targeted retention strategies.

The analysis is based on a real mobile game dataset provided for academic research. 

## Business Problem

Player retention is one of the most critical metrics in mobile games, as many players churn within the first few days after installation.

Understanding early behavioral signals can help game teams:
- Identify players likely to become long-term users
- Detect high-value players early
- Design targeted onboarding and engagement strategies
- Improve player progression and monetization design

This project focuses on Day 0–Day 1 activity, when early engagement patterns are formed.

## Dataset

The dataset contains early gameplay behavior from players of a Squad RPG mobile game, including:
- Gameplay sessions
- Playtime
- Spending behavior
- Activity across gameplay modes (Campaign Missions, PvP Matches, Side Missions)
- Player session duration

In Squad RPG games, players build teams of characters and complete missions across different gameplay modes to progress and earn rewards.

## Methodology

The analysis followed these steps:

### 1. Feature Engineering

Key behavioral features were derived from gameplay data, including:
- Total sessions played on Day 0–Day 1
- Total playtime on Day 0–Day 1
- Total spend on Day 0–Day 1
- Campaign Missions won/lost/retreat
- PvP Matches won/lost/retreat
- Side Missions won/lost/retreat

These features capture how actively players engage with different gameplay modes.

### 2. Player Segmentation

A segmentation analysis was conducted to compare early spenders (players who spent on Day 0 or Day 1) and Day-1 retained players.

Segments were defined by evaluating:
- Total engagement across gameplay modes
- Total missions played
- Session length and playtime quality on Day 0–Day 1

Mean behavioral patterns were then computed for each segment.

### 3. Clustering Analysis

Two clustering algorithms were applied:
- K-Means
- DBSCAN

Players were grouped based on similarities in early gameplay engagement patterns.

Performance comparison between the two algorithms was conducted to determine the most meaningful clustering structure.

## Key Insights

### Segmentation Analysis 

The segmentation analysis revealed four distinct player types:
1. Early churners _(Non-spender, Not retained)_
2. Engaged free players _(Non-spender, D1 retained)_
3. Early spenders _(Spender, Not retained)_
4. High-value retained players _(Spender, D1 retained)_

Key findings:
- D1 retained players played 2–5× more Day-0 content than churners, confirming that early gameplay depth strongly predicts short-term retention.
- Early spenders are extremely rare (<0.3%) but highly retained (84%). These players exhibit the highest Day-0 and Day-1 activity and represent critical long-term revenue potential.
- Early churners make up the largest segment (75%). Their minimal engagement suggests onboarding friction or insufficient early-game motivation.
- Returning non-spenders form a healthy engaged segment with strong early gameplay activity, indicating high potential for future monetization.
- Session length strongly differentiates player value.
  - Non-spender retained players: ~21 minutes/session
  - Spender retained players: ~33 minutes/session

### Clustering Analysis

When comparing K-Means and DBSCAN, the algorithms produced different outcomes due to the heavily skewed distribution of player activity and presence of extreme outliers.

K-Means performed poorly, grouping 86% of players into a single dominant cluster while creating a tiny cluster of only nine players driven entirely by outliers. This occurs because K-Means assumes spherical and evenly sized clusters, which does not reflect real player behavior patterns.

DBSCAN performed significantly better, as it adapts to the natural density structure of the data. It identified several meaningful behavioral groups:
- Casual players
- Light–moderate players
- Mid-core players

Additionally, DBSCAN correctly isolated over 4,800 high-engagement outliers (including potential whales) as noise instead of forcing them into artificial clusters.

Because DBSCAN handles skewed distributions, irregular cluster shapes, and extreme outliers, it produced more interpretable and actionable player segments compared to K-Means.

## Business Recommendations

Based on the segmentation results:
- Target high-engagement players with rewards and progression incentives to sustain engagement.
- Improve onboarding for low-engagement players by simplifying early missions and tutorials.
- Design targeted monetization offers for highly engaged segments likely to convert.
- Encourage exploration across gameplay modes by introducing early incentives to try PvP and side missions.

## Tools & Technologies
- Python (Pandas, NumPy, Scikit-learn)
- Clustering methods (K-Means, DBSCAN)
- Jupyter Notebook/Google Colab
