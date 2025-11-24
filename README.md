# **Introduction**

Clash Royale is a card based strategy game where developers routinely update cards to maintain game balance. This balance changes strategies and refreshes the meta. Supercell’s own blog notes that balance updates before major tournaments consist almost entirely of nerfs. This project explores the relationship between balance updates and card usage among high level players. By analyzing changes in usage before and after updates, The project can assess whether developer’s adjustments achieve their intended effect.

## **Project Goal**

The primary goal is to quantify how balance changes affect card usage among high level Clash Royale players. The project mainly focuses on cards that receive nerfs in a major update and examine their usage before and after the update with correlation analysis, regression modeling and visual exploration.

## **Motivation**

Understanding how updates influence player behavior is especially important for competitive Clash Royale players who need to adjust decks quickly after each balance change. As an active follower of the top ladder meta and balance updates, often see certain cards disappear from popular decks immediately after a nerf, while others remain common despite being targeted. This project comes from a desire to move beyond anecdotal impressions and quantify these changes using data.

* **Impact of updates:** Do balance changes significantly change  the usage of affected cards among high‑level players?

* **Usage of Cards:** Are some cards more likely to see usage drops after nerfs than others?

* **Meta Evolution:** How do changes in usage relate to win rates and deck performance?

* **Cross Segment Differences:** Do usage changes vary across different competitive brackets ?

By addressing these questions, the study aims to provide data  insights into how balance updates shape the meta.

## **Data Sources**

Because there is no official API available through the API tool, data will be collected from publicly accessible websites and manual logging.

| \# | Data Type | Description | Source |  |
| ----- | ----- | ----- | ----- | ----- |
| 1 | **Card Usage & Win Rate** | Card usage rate and win rate. | Third‑party analytics sites such as [Stats Royale](https://statsroyale.com/) and [RoyaleAPI](https://royaleapi.com/?lang=en).  
| 2 | **Balance Update Details** | Official notes on balance changes. | [Supercell’s official blog posts](https://supercell.com/en/news/blog/games/)  
| 3 | **Player Deck Data** | Battle logs and deck compositions for top ladder  | [RoyaleAPI](https://royaleapi.com/?lang=en) provides battle logs.


These datasets will enable an idea analysis of how card usage responds to balance changes.

## **Methodology**

### **Data Cleaning & Preprocessing**

* **Define analysis:** For each update, select a pre update window (14 days before) and a post update window (14 days after).  
  **Normalize card names:** Ensure that cards are consistently identified to avoid miscounting usage as top ladder players often play both variants.  
* **Compute usage rate:** For each card and time window, calculate the proportion of decks in the sample that include the card.  
*  **Handle missing data:** Some cards may have insufficient sample size. Using minimum sample thresholds.

  ### **Exploratory Data Analysis (EDA)**

* **Descriptive statistics:** Summarize average usage rates, win rates for each card. Visualize the distribution of usage changes across all nerfed cards.

* **Correlation analysis:** Examine the relationship between usage changes and the magnitude of the nerf.

* **Tier comparison:** Plot usage changes separately for Top 200 and Top 1000 to see whether effects differ by competitive level.

* **Time series visualization:** For selected cards, plot usage rate over time to identify immediate versus gradual responses to nerfs.
# Nerfed Card Usage – Statistical Hypotheses

# Nerfed Card Usage – Statistical Hypotheses

This document defines the concrete, testable hypotheses that will be used to analyze the impact of balance nerfs on card usage in a competitive game setting. Each hypothesis maps directly to a planned statistical test.

---

## Notation

Let:

mean usage rate of a nerfed card in the 14 days **before** the update  
mean usage rate of the same card in the 14 days **after** the update  

variance of usage rates before the update  
variance of usage rates after the update 

 average change in usage  for nerfed cards among **Top 200** players  
 average change in usage for nerfed cards among **Top 1000** players  

---

## Hypothesis 1: Effect of Nerfs on Mean Usage

**Goal:** Test whether nerfs reduce the average usage of affected cards.

- **Null hypothesis** :  
  Nerfs have **no effect** on the mean usage rate of the affected cards.

- **Alternative hypothesis** :  
  
  Nerfs lead to a **significant decrease** in the mean usage rate of the affected cards.

---

## Hypothesis 2: Effect of Nerfs on Variance of Usage (F-test)

**Goal:** Test whether nerfs change how concentrated or spread out card usage is.

- **Null hypothesis**:  
  
  Nerfs do **not** change the variance of card usage.

- **Alternative hypothesis** :  

  Nerfs **do** change how concentrated or spread out card usage is.

---

## Hypothesis 3: Differences Between Competitive Brackets

**Goal:** Test whether top players react differently to nerfs compared to a broader competitive bracket.

- **Null hypothesis**:  
  On average, nerfed cards change in usage by the **same amount** in Top 200 and Top 1000 brackets.

- **Alternative hypothesis**:  

  Usage changes caused by nerfs **differ** between Top 200 and Top 1000 players.

---

## Planned Tests (Summary)

- **Hypothesis 1:** Paired test on means (e.g., paired t-test) comparing pre vs. post usage per card.  
- **Hypothesis 2:** **F-test** on variances comparing pre vs. post usage distributions.  
- **Hypothesis 3:** Two-sample test on between Top 200 and Top 1000 (e.g., two-sample t-test or nonparametric equivalent).

These hypotheses form the core of the analysis for evaluating the competitive impact of card nerfs.
