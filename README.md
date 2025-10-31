# **Introduction**

Clash Royale is a card based strategy game where developers routinely update cards to maintain game balance. This balance changes strategies and refreshes the meta. Supercell’s own blog notes that balance updates before major tournaments consist almost entirely of nerfs. This project explores the relationship between balance updates and card usage among high level players. By analyzing changes in usage before and after updates, The project can assess whether developer’s adjustments achieve their intended effect.

## **Project Goal**

The primary goal is to quantify how balance changes affect card usage among high level Clash Royale players. The project mainly focuses on cards that receive nerfs in a major update and examine their usage before and after the update with correlation analysis, regression modeling and visual exploration.

## **Motivation**

Understanding how updates influence player behavior and cards are nerfed due to high usage, top ladder players need to adapt quickly. This project is driven by the following questions:

* **Impact of updates:** Do balance changes significantly change  the usage of affected cards among high‑level players?

* **Usage of Cards:** Are some cards more likely to see usage drops after nerfs than others?

* **Meta Evolution:** How do changes in usage relate to win rates and deck performance?

* **Cross Segment Differences:** Do usage changes vary across different competitive brackets ?

By addressing these questions, the study aims to provide data  insights into how balance updates shape the meta.

## **Data Sources**

Because there is no official API available through the API tool, data will be collected from publicly accessible websites and manual logging.

| \# | Data Type | Description | Source |  |
| ----- | ----- | ----- | ----- | ----- |
| 1 | **Card Usage & Win Rate** | Card usage rate and win rate. | Third‑party analytics sites such as [Stats Royale](https://statsroyale.com/) and [RoyaleAPI](https://royaleapi.com/?lang=en).  |  |
| 2 | **Balance Update Details** | Official notes on balance changes. | [Supercell’s official blog posts](https://supercell.com/en/news/blog/games/)  |  |
| 3 | **Player Deck Data** | Battle logs and deck compositions for top ladder  | [RoyaleAPI](https://royaleapi.com/?lang=en) provides battle logs. |  |
| 4 |  |  |  |  |

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

  ## **Hypothesis**

* **Null Hypothesis (H₀):** Balance updates (nerfs) have no significant effect on card usage among high level players.

* **Alternative Hypothesis (H₁):** Nerfs lead to a significant decrease in the usage of the affected cards among high level players.


