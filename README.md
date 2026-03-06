# Early Player Segmentation and Retention Analysis (Squad RPG Game)

## Overview

This project analyzes **early player behavior (Day 0–Day 1)** in a Squad RPG mobile game to identify patterns that drive player retention and early monetization.

Using behavioral gameplay data, **segmentation and clustering techniques** were applied to group players based on engagement, spending behavior, and gameplay preferences. The goal is to help game developers better understand early player behavior and design targeted retention strategies.

## Business Problem

Player retention is one of the most critical metrics in mobile games, as many players churn within the first few days after installation.

Understanding early behavioral signals can help game teams:
- Identify players likely to become long-term users
- Detect high-value players early
- Design targeted onboarding and engagement strategies
- Improve player progression and monetization design

This project focuses on Day 0–Day 1 activity, when early engagement patterns are formed.

## Dataset

The dataset contains 42K+ records of gameplay behavior from players of a Squad RPG mobile game, including:
- Player and acquisition details 
- Gameplay sessions
- Playtime
- Spending behavior
- Activity across gameplay modes (Campaign Missions, PvP Matches, Side Missions)

In Squad RPG games, players build teams of characters and complete missions across different gameplay modes to progress and earn rewards.

## Methodology

This project combines segmentation and clustering analysis.

Segmentation evaluates player behavior across predefined business groups (spending and retention), while clustering identifies natural behavioral player types directly from gameplay data.

### Segmentation Analysis

A segmentation analysis was conducted to compare early spenders (players who spent on Day 0 or Day 1) and Day-1 retained players.

Key behavioral features were derived from gameplay data, including:
- Total sessions played on Day 1
- Total playtime on Day 1
- Total spend on Day 0–Day 1
- Total missions under each game mode (Campaign Missions, PvP Matches, Side Missions)
- Total engagement across gameplay modes on Day 0–Day 1
- Session length or playtime quality on Day 1

Mean behavioral patterns were then computed for each segment.

### Clustering Analysis

Two clustering algorithms were applied: K-Means vs. DBSCAN.

Players were grouped based on similarities in early gameplay engagement patterns.

Performance comparison between the two algorithms was conducted to determine the most meaningful clustering structure.

## Key Insights

### Segmentation Analysis 

The segmentation analysis revealed four distinct player types:
1. Early churners _(Non-spender, Not retained)_
2. Engaged free players _(Non-spender, D1 retained)_
3. Early spenders _(Spender, Not retained)_
4. High-value retained players _(Spender, D1 retained)_

<img width="220" height="163" alt="Screenshot 2026-03-05 at 9 09 29 PM" src="https://github.com/user-attachments/assets/1f9df4b2-5f0a-4617-b61f-7d02e20b61d7" />

<img width="1805" height="167" alt="Screenshot 2026-03-05 at 9 09 47 PM" src="https://github.com/user-attachments/assets/06f6bc83-e442-411b-ab57-e22cc7759bec" />

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

<img width="713" height="547" alt="image" src="https://github.com/user-attachments/assets/0e155246-2265-431c-86f9-44c2fb21a777" />

<img width="1489" height="1475" alt="image" src="https://github.com/user-attachments/assets/2b4f54df-9fc2-4265-b6a4-5bef60a773e1" />

DBSCAN performed significantly better, as it adapts to the natural density structure of the data. It identified several meaningful behavioral groups:
1. Casual players
2. Light–moderate players
3. Mid-core players

<img width="714" height="547" alt="image" src="https://github.com/user-attachments/assets/d6ab6af7-5afc-4a6c-97ae-4a931a7f0b48" />

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
