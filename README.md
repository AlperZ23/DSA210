**Clash Royale Meta Analysis: Card Usage and Performance in High Level Play**

**Introduction**

Clash Royale is a card based strategy game where developers routinely update cards to maintain game balance. This project explores the relationship between card  usage distribution and performance among top 200, top 1000, ranked and ladder players. By analyzing current card usage rates and win rates among top tier and ranked Clash Royale players, can infer which cards are strong or weak in practice and how top player and ranked players choice differ from the broader competitive player base. This approach provides insight into the effectiveness of the game's balance as it stands now, and can still indirectly highlight the impact of past balance decisions by revealing which cards dominate or underperform in the current meta.

**Project Goal**

The primary goal is to analyze the current Clash Royale meta by quantifying card usage and evaluating how it relates to card performance among top 200, top 1000, ranked and ladder players. In particular, this project aims to identify which cards are most revalent in top 200, top 1000, ranked and ladder player gameplay and assess whether their popularity is justified by strong performance. Also, compare the behavior of the elite players with a slightly broader set of competitive players to see if the very top players favor different cards or achieve different results with those cards. In summary, the study will use current data to answer: Which cards are popular in the current meta, how well do those cards perform, and how does this differ between the top of the ladder and the broader competitive scene?

**Motivation**

Understanding the current meta is crucial for competitive Clash Royale players who must decide which decks to play in order to succeed.By analyzing current usage and win rates, can provide  insights. For instance, if a card is extremely common but has only average win rates, it might indicate that players use it for its utility or synergy rather than raw power. Conversely, a card with a high win rate but low usage might be a noticeable utility that could gain popularity in future metas. These insights help players understand whether following the crowd is justified or if there are opportunities to exploit less popular but effective cards. Finally, this project’s findings could guide competitive players in making informed deck building decisions and also reflect on how well the game’s balance aligns with player behavior.

**Data Sources**

Because there is no official API available through the API tool, data will be collected from publicly accessible websites and manual logging.

| Data Type | Description | Source |
| ----- | ----- | ----- |
| **Card Usage & Win Rate** | Card usage rate and win rate. | Third‑party analytics sites such as [RoyaleAPI](https://royaleapi.com/?lang=en).  |
| **Game Insight** | General Information about cards, players and leaderboards. | [Clash Royale API](https://developer.clashroyale.com/#/) |
| **Player Deck Data** | Battle logs and deck compositions for top ladder  | [RoyaleAPI](https://royaleapi.com/?lang=en) provides battle logs. |

These datasets will enable a comprehensive analysis of the current meta. 

**Methodology**

1. **Data Collection & Preprocessing:**  This stage is about deciding what data to gather, from where, over what time window, and how to clean and structure it before analysis.  
     
2. **Define Data Scope:** Choose a recent time window (7 days) and specific competitive brackets (top 200, top 1000, ranked and ladder\\) so the data represents the current meta and allows comparison across skill levels.  
     
3. **Collect Usage and Win Rate Stats:** Pull each card’s usage rate and win rate for both brackets from third-party analytics sites and record them with consistent card naming.  
     
4. **Manual Data Verification:** A sample of the collected stats to ensure the manually entered values are accurate and reliable.  
     
5. **Handle Missing or Rare Data:** Set a minimum usage or games played threshold and exclude cards below it from statistical tests to avoid unstable results from tiny samples.  
     
6. **Data Organization:** Store all cleaned values in a structured table  with columns for card name and stats per bracket to enable easy calculations and comparisons.

**Exploratory Data Analysis (EDA)**

This step uses summaries and visualizations to understand patterns in the current meta before running formal statistical tests.

1. **Descriptive Statistics**: Compute and report simple summaries of usage and win rates to get a baseline picture of the meta.  
     
2. **Meta Concentration Analysis:** Measure how much of total usage is captured by the most popular cards to see whether the meta is dominated by a few options or spread across many.  
     
3. **Usage vs. Win Rate Relationship:** Plot and correlate usage rates with win rates for all cards to see whether more popular cards also tend to perform better.  
     
4. **Cross Bracket Usage Comparison:** Compare card usage between top 200, top 1000, ranked and ladder to determine whether elite players favor a different set of cards.  
     
5. **Cross Bracket Performance Comparison:** Compare card win rates between top 200, top 1000, ranked and ladder to see if top players achieve systematically better or worse results with specific cards.

**Hypotheses and Statistical Tests**

Based on the research questions and exploratory findings, we formulate the following concrete hypotheses to test statistically. Each hypothesis targets a specific aspect of the relationship between balance, usage, and performance in the current meta. We define null and alternative hypotheses for each and outline the planned statistical test to evaluate them:

       
1. **Hypothesis 1:** Usage Distribution Across Skill Brackets

     **Null Hypothesis:** Top 200, Top 1000, ladder and ranked players use the same set of cards to the same extent.
     
     **Alternative Hypothesis:** Top 200, Top 1000, ladder and ranked players have significantly different usage patterns.   

       

2. **Hypothesis 2:** Card Performance Across Skill Brackets

     **Null Hypothesis:** Card win rates are the same for Top 200, Top 1000, ladder and ranked players.
     
     **Alternative Hypothesis:** At least some cards have significantly different win rates between Top 200, Top 1000, ladder and ranked players.
     
**Findings**

* **Hypothesis 1 (Usage across brackets):**

  * Contingency table: 4×122 (brackets × cards, using UsagePct).

  * Chi-square test: χ² \= 425.04, df \= 363, p \= 0.0136.

  * Conclusion: Reject H0 at 5% level. Card usage distributions differ across brackets. Top 200 / Top 1000 players do not use exactly the same mix of cards as Ladder or All Ranked players.

* **Hypothesis 2 (Win rates across brackets):**

  * For each of 113 cards, a 2×4 win/loss × bracket table was built from UsagePct and WinPct.

  * Smallest raw p-value: Skeleton Barrel, p ≈ 0.0396.

  * Bonferroni-adjusted threshold: α\_Bonf ≈ 0.000442.

  * No card passes this threshold.

  * Conclusion: After correcting for multiple comparisons, no card’s win rate pattern is significantly different across brackets under the approximated-counts model.

  
**Machine Learning Methods**

The dataset contains card performance statistics across different player brackets (Top 200, Top 1000, All Ranked, Ladder). For each card in each bracket: UsagePct (percentage of decks using the card), WinPct (win rate when the card is in a deck), and Rating (an overall card strength rating).

## **Regression: Predicting Win Rate (WinPct)**

Build models to predict a card’s win percentage (WinPct) from its usage percentage (UsagePct), overall rating (Rating), and bracket category. The data will use one hot encoding for the Bracket feature to include it as variables. An 80/20 train test split is used. Two models are trained: a Linear Regression (baseline linear model) and a Gradient Boosting Regressor (a non linear ensemble model).Lastly, evaluate performance with the Root Mean Squared Error (RMSE) and R² score on the test set.

### **Data Preparation and Train Test Split**

Select the features and target for regression, then split the dataset into training and testing sets .Ensure the random seed differs from that of the classification task. Also set up a preprocessing pipeline to one hot encode the Bracket feature while leaving numeric features unchanged.

### **Linear Regression Model**

Create a pipeline that applies the above preprocessing and then fits a linear regression model. This model will learn a linear combination of UsagePct, Rating, and bracket dummy features to predict WinPct. After training, evaluate the model on the test set and compute the RMSE and R² metrics:

### **Gradient Boosting Regressor Model**

Next, train a Gradient Boosting Regressor on the same training data. This ensemble model can capture non linear relationships and interactions. After fitting, evaluate it on the test set using the same metrics.

### **. Regression (Predicting Card Win Rate)**

* **Target:** WinPct

* **Features Used:** UsagePct, Rating, Bracket

* **Train/Test Split:** 80/20 holdout (random\_state=10)

* **Preprocessing:** One hot encoding of Bracket

* **Models & Performance :**

  * **Linear Regression:** RMSE \= **4.361**, R² \= **0.488**

  * **Gradient Boosting Regressor:** RMSE \= **1.891**, R² \= **0.904**

* **Model Interpretation (Gradient Boosting Feature Importances):**

  * Highest importance feature: Rating (dominant driver in the fitted model), followed by bracket indicators and then UsagePct.

## **Classification: Categorizing Card Popularity**

Classify each card’s popularity level (Low, Medium, High) based on its usage percentage. The data will create a categorical target by binning the UsagePct into three quantile based tiers. The features used for classification are UsagePct, WinPct, Rating, and the one hot encoded Bracket indicator. Two models are trained: a Multinomial Logistic Regression and a Random Forest Classifier. Evaluate these models with overall accuracy, macro averaged F1 score, and examine the confusion matrix for the Random Forest.

**Creating the Popularity Category Target**

The popularity classes using usage percentage quantiles. Specifically, split the UsagePct values into three groups of roughly equal size: the bottom \~33% as Low popularity, middle \~33% as Medium, and top \~33% as High. This is done using pd.qcut, which calculates quantile cut points then confirms the class distribution.

This shows the dataset is divided into 252 low popularity, 211 medium popularity, and 184 high popularity instances (which is approximately one third in each, as intended). Predict this Popularity class using the card’s other metrics.

**Data Preparation and Train Test Split**

Prepare the feature matrix X and target y for classification. X includes the numeric features UsagePct, WinPct, Rating and the categorical Bracket. The target y is the new Popularity class. Perform an 80/20 stratified split (with random\_state=42 for reproducibility). Use a similar preprocessing pipeline to one hot encode the bracket feature.

**Multinomial Logistic Regression Model**

Train a logistic regression classifier with a multinomial setting. The model will learn linear decision boundaries in the feature space to separate the Low, Medium and High classes. The pipeline (preprocessing \+ logistic regression) on the training data and then evaluate on the test set.

**Random Forest Classifier Model**

Also train a Random Forest classifier, an ensemble of decision trees, on the same data. This model can capture non linear relationships and typically handles feature interactions automatically. After training,  evaluate its performance similarly.

**2\. Classification (Popularity Tier Prediction)**

* **Target:** Popularity (created by tertiles of UsagePct via pd.qcut, labels \= Low / Medium / High)  
* **Class Distribution:** Low \= 252, Medium \= 211, High \= 184  
* **Features Used:** UsagePct, WinPct, Rating, Bracket  
* **Train/Test Split:** 80/20 stratified holdout (random\_state=42)  
* **Preprocessing:** Standard scaling for numeric features \+ one hot encoding for Bracket   
* **Models & Performance (holdout set):**  
  * **Logistic Regression:** Accuracy \= **0.908**, Macro F1 \= **0.905**  
  * **Random Forest (random\_state=42):** Accuracy \= **1.000**, Macro F1 \= **1.000**  
* **Random Forest Confusion Matrix (test set; Low/Medium/High):**  
  * Perfect diagonal classification: Low \= 51, Medium \= 42, High \= 37\.

## 


**Limitations**

* Only aggregated percentages (UsagePct, WinPct) were available, not raw battle counts.

* Counts were reconstructed using an arbitrary baseline (1000 uses per bracket per card). This is standard when only percentages exist, but actual p-values would differ if true sample sizes were known.

* For Hypothesis 1, the chi-square test was applied to usage percentages treated as counts. This captures structure in the table (and clearly shows different usage patterns), but the exact p-value should be interpreted as approximate rather than exact.

Within these constraints, the main qualitative conclusions are:

1. Usage patterns clearly differ by bracket (H0 rejected).

2. Win rate differences by bracket are not statistically strong after correction (H0 accepted).

