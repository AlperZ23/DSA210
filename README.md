# **Clash Royale Meta Analysis: Card Usage and Performance in High Level Play**

## **Introduction**

Clash Royale is a card based strategy game where developers routinely update cards to maintain game balance. This project explores the relationship between card  usage distribution and performance among top 200, top 1000, ranked and ladder players. By analyzing current card usage rates and win rates among top tier and ranked Clash Royale players, can infer which cards are strong or weak in practice and how top player and ranked players choice differ from the broader competitive player base. This approach provides insight into the effectiveness of the game's balance as it stands now, and can still indirectly highlight the impact of past balance decisions by revealing which cards dominate or underperform in the current meta.

## **Project Goal**

The primary goal is to analyze the current Clash Royale meta by quantifying card usage and evaluating how it relates to card performance among top 200, top 1000, ranked and ladder players. In particular, this project aims to identify which cards are most revalent in top 200, top 1000, ranked and ladder player gameplay and assess whether their popularity is justified by strong performance. Also, compare the behavior of the elite players with a slightly broader set of competitive players to see if the very top players favor different cards or achieve different results with those cards. In summary, the study will use current data to answer: Which cards are popular in the current meta, how well do those cards perform, and how does this differ between the top of the ladder and the broader competitive scene?

## **Motivation**

Understanding the current meta is crucial for competitive Clash Royale players who must decide which decks to play in order to succeed.By analyzing current usage and win rates, can provide  insights. For instance, if a card is extremely common but has only average win rates, it might indicate that players use it for its utility or synergy rather than raw power. Conversely, a card with a high win rate but low usage might be a noticeable utility that could gain popularity in future metas. These insights help players understand whether following the crowd is justified or if there are opportunities to exploit less popular but effective cards. Finally, this project’s findings could guide competitive players in making informed deck building decisions and also reflect on how well the game’s balance aligns with player behavior.

## **Data Sources**

Because there is no official API available through the API tool, data will be collected from publicly accessible websites and manual logging.

| \# | Data Type | Description | Source |  |
| ----- | ----- | ----- | ----- | ----- |
| 1 | **Card Usage & Win Rate** | Card usage rate and win rate. | Third‑party analytics sites such as  [RoyaleAPI](https://royaleapi.com/?lang=en).  |  |
| 2 | **Player Deck Data** | Battle logs and deck compositions for top ladder, ranked and ladder  | [RoyaleAPI](https://royaleapi.com/?lang=en) provides battle logs. | 3 | **Card Data** | General Card Information about Clash Royale  | [Clash Royale API](https://developer.clashroyale.com/#/) provides basic information about game.


These datasets will enable a comprehensive analysis of the current meta. 

**Methodology**

**Data Collection & Preprocessing** – This stage is about deciding what data to gather, from where, over what time window, and how to clean and structure it before analysis.

* **Define Data Scope** – Choose a recent time window and specific competitive brackets (Top 1000 and Top 200\) so the data represents the current meta and allows comparison across skill levels.

* **Collect Usage and Win Rate Stats** – Pull each card’s usage rate and win rate for both brackets from third-party analytics sites and record them with consistent card naming.

* **Manual Data Verification** – A sample of the collected stats to ensure the manually entered values are accurate and reliable.

* **Handle Missing or Rare Data** – Set a minimum usage or games played threshold and exclude cards below it from statistical tests to avoid unstable results from tiny samples.

* **Data Organization** – Store all cleaned values in a structured table  with columns for card name and stats per bracket to enable easy calculations and comparisons.

  ---

**Exploratory Data Analysis (EDA)** – This step uses summaries and visualizations to understand patterns in the current meta before running formal statistical tests.

* **Descriptive Statistics** – Compute and report simple summaries of usage and win rates to get a baseline picture of the meta.

* **Meta Concentration Analysis** – Measure how much of total usage is captured by the most popular cards to see whether the meta is dominated by a few options or spread across many.

* **Usage vs. Win Rate Relationship** – Plot and correlate usage rates with win rates for all cards to see whether more popular cards also tend to perform better.

* **Cross Bracket Usage Comparison** – Compare card usage between Top 200 and Top 1000 to determine whether elite players favor a different set of cards.

* **Cross Bracket Performance Comparison** – Compare card win rates between Top 200 and Top 1000 to see if top players achieve systematically better or worse results with specific cards.

## **Hypotheses and Statistical Tests**

Based on the research questions and exploratory findings, we formulate the following concrete hypotheses to test statistically. Each hypothesis targets a specific aspect of the relationship between balance, usage, and performance in the current meta. We define null and alternative hypotheses for each and outline the planned statistical test to evaluate them:
       
2. **Hypothesis 1: Usage Distribution Across Skill Brackets**

   * **Null Hypothesis:** Top 200, Top 1000, ladder and ranked players use the same set of cards to the same extent.
     
   * **Alternative Hypothesis:** Top 200, Top 1000, ladder and ranked players have significantly different usage patterns.   
       
3. **Hypothesis 2: Card Performance Across Skill Brackets**  
     
   * **Null Hypothesis:** Card win rates are the same for Top 200, Top 1000, ladder and ranked players.

   * **Alternative Hypothesis:** At least some cards have significantly different win rates between Top 200, Top 1000, ladder and ranked players \.

