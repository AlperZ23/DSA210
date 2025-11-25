# **Clash Royale Meta Analysis: Card Usage and Performance in High Level Play**

## **Introduction**

Clash Royale is a card based strategy game where developers routinely update cards to maintain game balance. This project explores the relationship between card usage among high level players. By analyzing current card usage rates and win rates among top tier Clash Royale players, can infer which cards are strong or weak in practice and how top player choices differ from the broader competitive player base. This approach provides insight into the effectiveness of the game's balance as it stands now, and can still indirectly highlight the impact of past balance decisions by revealing which cards dominate or underperform in the current meta.

## **Project Goal**

The primary goal is to analyze the current Clash Royale meta by quantifying card usage and evaluating how it relates to card success among high level players. In particular, this project aims to identify which cards are most revalent in top tier gameplay and assess whether their popularity is justified by strong performance. Also, compare the behavior of the elite players with a slightly broader set of competitive players to see if the very top players favor different cards or achieve different results with those cards. In summary, the study will use current data to answer: Which cards are popular in the current meta, how well do those cards perform, and how does this differ between the top of the ladder and the broader competitive scene?

## **Motivation**

Understanding the current meta is crucial for competitive Clash Royale players who must decide which decks to play in order to succeed.By analyzing current usage and win rates, can provide  insights. For instance, if a card is extremely common but has only average win rates, it might indicate that players use it for its utility or synergy rather than raw power. Conversely, a card with a high win rate but low usage might be a noticeable utility that could gain popularity in future metas. These insights help players understand whether following the crowd is justified or if there are opportunities to exploit less popular but effective cards. Finally, this project’s findings could guide competitive players in making informed deck building decisions and also reflect on how well the game’s balance aligns with player behavior.

## **Data Sources**

Because there is no official API available through the API tool, data will be collected from publicly accessible websites and manual logging.

| \# | Data Type | Description | Source |  |
| ----- | ----- | ----- | ----- | ----- |
| 1 | **Card Usage & Win Rate** | Card usage rate and win rate. | Third‑party analytics sites such as [Stats Royale](https://statsroyale.com/) and [RoyaleAPI](https://royaleapi.com/?lang=en).  |  |
| 2 | **Balance Update Details** | Official notes on balance changes. | [Supercell’s official blog posts](https://supercell.com/en/news/blog/games/)  |  |
| 3 | **Player Deck Data** | Battle logs and deck compositions for top ladder  | [RoyaleAPI](https://royaleapi.com/?lang=en) provides battle logs. |  |
| 4 |  |  |  |  |

These datasets will enable a comprehensive analysis of the current meta. 

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

## **Hypotheses and Statistical Tests**

Based on the research questions and exploratory findings, we formulate the following concrete hypotheses to test statistically. Each hypothesis targets a specific aspect of the relationship between balance, usage, and performance in the current meta. We define null and alternative hypotheses for each and outline the planned statistical test to evaluate them:

1. **Hypothesis 1: Usage vs. Win Rate Alignment**  
     
   * **Null Hypothesis:** There is no significant correlation between a card’s usage rate and its win rate.   
   * **Alternative Hypothesis:** There is a significant correlation between usage and win rate for cards.  
       
2. **Hypothesis 2: Usage Distribution Across Skill Brackets**

   * **Null Hypothesis:** Top 200 and Top 1000 players use the same set of cards to the same extent.   
   * **Alternative Hypothesis:** Top 200 and Top 1000 players have significantly different usage patterns.   
       
3. **Hypothesis 3: Card Performance Across Skill Brackets**  
     
   * **Null Hypothesis:** Card win rates are the same for Top 200 and Top 1000 players.

   * **Alternative Hypothesis:** At least some cards have significantly different win rates between Top 200 and Top 1000\.

