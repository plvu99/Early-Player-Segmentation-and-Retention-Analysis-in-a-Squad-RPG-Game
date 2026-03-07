# Early Player Segmentation and Retention Analysis (Squad RPG Game)

## 🔎 Overview

This project analyzes **early player behavior (Day 0–Day 1)** in a Squad RPG mobile game to identify patterns that drive player retention and early monetization.

Using behavioral gameplay data, **segmentation and clustering techniques** were applied to group players based on engagement, spending behavior, and gameplay preferences. The goal is to help game developers better understand early player behavior and design targeted retention strategies.

## 🔐 Business Problem

Player retention is one of the most critical metrics in mobile games, as many players churn within the first few days after installation.

Understanding early behavioral signals can help game teams:
- Identify players likely to become long-term users
- Detect high-value players early
- Design targeted onboarding and engagement strategies
- Improve player progression and monetization design

This project focuses on Day 0–Day 1 activity, when early engagement patterns are formed.

## 📊 Dataset

The dataset contains 42K+ records of gameplay behavior from players of a Squad RPG mobile game, including:
- Player and acquisition details 
- Total sessions played
- Total playtime
- Spending behavior
- Activity across gameplay modes (Campaign Missions, PvP Matches, Side Missions)

In Squad RPG games, players build teams of characters and complete missions across different gameplay modes to progress and earn rewards.

## 📍 Methodology

This project combines segmentation and clustering analysis.

Segmentation evaluates player behavior across predefined business groups (spending and retention), while clustering identifies natural behavioral player types directly from gameplay data.

### Segmentation Analysis

A segmentation analysis was conducted to compare early spenders (players who spent on Day 0 or Day 1) and Day-1 retained players.

Key behavioral features were engineered from gameplay data, including:
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

## 🔑 Key Insights

### Segmentation Analysis 

Four distinct player types were revealed:
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

DBSCAN performed significantly better, as it adapts to the natural density structure of the data. It identified several meaningful behavioral groups, including casual players, light–moderate players, and mid-core players.

<img width="714" height="547" alt="image" src="https://github.com/user-attachments/assets/d6ab6af7-5afc-4a6c-97ae-4a931a7f0b48" />

<img width="1648" height="494" alt="Screenshot 2026-03-05 at 9 27 09 PM" src="https://github.com/user-attachments/assets/9a0ba00e-d660-4f39-9526-9c6262863fc9" />

<img width="1102" height="478" alt="Screenshot 2026-03-05 at 9 27 19 PM" src="https://github.com/user-attachments/assets/66e3a182-5229-485f-9335-bfba33debf44" />

<img width="1655" height="357" alt="Screenshot 2026-03-05 at 9 27 34 PM" src="https://github.com/user-attachments/assets/006c18cc-1fbd-4e95-a123-ab5f0324d506" />

<img width="1653" height="369" alt="Screenshot 2026-03-05 at 9 27 43 PM" src="https://github.com/user-attachments/assets/d2926a7c-c342-42cb-8005-8967ac23c18b" />

Additionally, DBSCAN correctly isolated over 4,800 high-engagement outliers (including potential whales) as noise instead of forcing them into artificial clusters.

Because DBSCAN handles skewed distributions, irregular cluster shapes, and extreme outliers, it produced more interpretable and actionable player segments compared to K-Means.

## ✍️ Business Recommendations

Based on the segmentation and clustering results, several actionable strategies can improve player retention and monetization.

### 1. Strengthen early engagement for new players

Players who churn early typically complete very few missions and spend little time in the game.

Possible improvements:
- Simplify the first 3–5 campaign missions to ensure quick early wins.
- Introduce guided objectives or tutorial prompts to help players understand core mechanics.
- Provide early rewards (gear, characters, or in-game currency) for completing initial missions.

Goal: Increase early gameplay depth, which strongly correlates with Day-1 retention.

### 2. Convert engaged free players into future spenders

Engaged non-spenders represent a large segment with strong gameplay activity but no early purchases.

Potential strategies:
- Offer limited-time starter bundles after players complete several missions.
- Introduce discounted beginner packs that accelerate squad progression.
- Provide progression-based offers triggered by milestones (e.g., completing a campaign chapter).

Goal: Encourage first purchases among players who already demonstrate strong engagement.

### 3. Retain high-value players with deeper progression

Early spenders and highly engaged players show the longest sessions and highest gameplay activity.

To retain these players:
- Unlock advanced PvP leagues or competitive events earlier.
- Introduce daily challenges or leaderboards to maintain long-term engagement.
- Provide exclusive rewards or cosmetic items tied to high-level gameplay achievements.

Goal: Sustain engagement among the most valuable player segments.

### 4. Encourage exploration across gameplay modes

Many low-engagement players primarily interact with a single game mode.

Potential solutions:
- Provide cross-mode incentives (e.g., rewards for trying PvP after campaign missions).
- Add daily quests requiring participation in different modes.
- Introduce mode-specific bonuses that encourage experimentation.

Goal: Increase gameplay variety, which often correlates with higher retention.

## ⚙ Tools & Technologies

- Python (Pandas, NumPy, Scikit-learn)
- Clustering methods (K-Means, DBSCAN)
- Jupyter Notebook/Google Colab
