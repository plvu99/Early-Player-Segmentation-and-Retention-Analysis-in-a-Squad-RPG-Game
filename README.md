# Early Player Segmentation and Retention Analysis (Squad RPG Game)

## Overview

This project analyzes **early player behavior (Day 0–Day 1)** in a Squad RPG mobile game to identify patterns that drive player retention and early monetization.

Using behavioral data from gameplay activity, **clustering techniques** were applied to segment players into meaningful groups based on engagement, spending behavior, and gameplay preferences. The goal is to help game developers better understand early player behavior and design targeted retention strategies.

The analysis is based on a real mobile game dataset provided for academic research. 

## Business Problem

Player retention is one of the most critical metrics in mobile games. Many players churn within the first few days after installation.

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
- Gameplay modes activity (Campaign Missions, PvP Matches, Side Missions) 
- Player session duration

In Squad RPG games, players build teams of characters and complete missions across different gameplay modes to progress and earn rewards.

## Methodology

The analysis followed these steps:

### 1. Feature Engineering

Key behavioral features were derived from gameplay data, including:
- Total sessions played on D0-D1
- Total playtime on D0-D1
- Total spend on D0-D1
- Campaign Missions won/lost/retreat
- PvP Matches won/lost/retreat
- Side Missions won/lost/retreat

These features capture how actively players engage with different gameplay modes.

### 2. Player Segmentation

A segmentation analysis for for early spenders (players who have spent on D0 or D1 or both days) and D1 retained players by computing total missions under each game mode, total engagement on D0/D1, session length or playtime quality on D0/D1, then computing mean behavior for each segment.

A clustering analysis with two clustering algorithms were applied: K-Means Clustering and DBSCAN

The models grouped players based on similarities in early gameplay behavior and engagement patterns.

Performance comparison was used to determine the more meaningful segmentation structure.

## Key Insights

### Segmentation Analysis 

The segmentation analysis revealed 4 distinct player types:
1. Early churners (Non-spender, Not Retained)
2. Engaged free players (Non-spender, D1 Retained)
3. Early spenders (Early Spender, Not Retained)
4. High-value retained players (Early Spender, D1 Retained)

Key findings:
- D1 retained players played 2–5 times more Day-0 content than churners. This confirms that early gameplay depth is a major driver of short-term retention.
- Early spenders are extremely small (<0.3%) but 84% (102 players) retained. They exhibit the highest Day-0 and Day-1 activity. This segment is critical for long-term revenue.
- The largest segment is early churners (75%), who barely engage and have very low mission completion. This suggests onboarding friction or insufficient “first session excitement.”
- Returning non-spenders form a healthy engaged segment with strong Day-0 and Day-1 activity. This group represents high future monetization potential.
- D1 session length differentiates low-value vs. high-value retained players. Non-spender retained ~21 minutes per session, while spender retained ~33 minutes per session. Longer sessions signal deeper goal-oriented behavior.

### Clustering Analysis
When comparing K-Means and DBSCAN on the D0 and D1 behavioral data, the two algorithms produced very different outcomes due to the heavily skewed nature of player activity that also included lots of outliers. K-Means performed poorly for this dataset, grouing 86% of players into one dominant cluster and creating a tiny cluster of 9 players driven entirely by outliers, which indicates that its assumption of spherical, evenly sized clusters does not fit real game behavior. This resulted in clusters that were imbalanced, difficult to interpret, and not actionable for segmentation.

In contrast, DBSCAN performed significantly better by adapting to the natural density structure of the data. It identified a meaningful set of clusters: casual players, light-moderate players, mid-core players. It also correctly isolated over 4,800 high-engagement outliers, including potential whales, as noise instead of forcing them into artificial centroids. DBSCAN also revealed several small but meaningful microsegments that K-Means could not detect. Because DBSCAN handles skew, non-linear cluster shapes, and extreme outliers while producing more interpretable and behaviorally distinct groups, it provides a significantly more accurate and useful clustering solution than K-Means in this scenario.

## Business Recommendations

Based on the segmentation results:
- Target high-engagement players by providing rewards and progression incentives to maintain engagement
- Improve onboarding for low-engagement players by simplifying early missions and tutorials
- Design targeted monetization offers by focusing on high-engagement segments likely to convert
- Encourage exploration across game modes by introducing early incentives to try PvP and side missions

## Tools & Technologies
- Python (Pandas, NumPy, Scikit-learn)
- Clustering methods (K-Means, DBSCAN)
- Jupyter Notebook/Google Colab
