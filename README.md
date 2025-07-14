# NBA Player Value Analysis: Identifying Underpaid and Overpaid Players  🏀
## Overview
- Goals:
   - Determine which players offer teams the best "bang for your buck".
   - Finding trends between player types and salary
   - Visualize relationships between advanced metrics and salary (Win-Shares, Box Plus Minus, Player Efficency Rating, ect)
     
- This project analyzed NBA player performance and salary data from the 24-25 regular season to identify which players are considered overpaid or underpaid based on their on-court contributions in relation to their yearly salary. Using data analytics and machine learning, I was able to estimate a players value and eventually find players with significant differences between their salary and performance.
  
### Data Collection
- All data was aquired from https://www.basketball-reference.com/.
- Found 3 datasets: Per game statistics, Advanced Statistics, Player Contract data


### Technologies Used
- Python (Pandas, Numpy) - Data Cleaning and Manipulation
- Seaborn and Matplotlib - Data Visualization
- Scikit-learn - linear regression, feature standardization
- Jupyter Notebook - Writing Python scripts
- VSCode - Main IDE used


## MAIN QUESTIONS
   1) How are salaries distributed by position and player type?
   2) Which type of players (3-pt shooters, facilitators, defenders, ect) tend to be the most cost-efficient?
   3) Can we predict a players "true value" salary based on performance stats?
   4) Which players are considered underpaid/overpaid relative to their predicted salary?

## Methodology

### Data Cleaning and Preperation
- Removed duplicate (traded) players
- Filterd for Players who played at least half the season (41)
- Filterd salary data for 24-25 season
- Merged multiple CSVs (Per Game, Advanced, and Salary)

### EDA (Exploratory Data Analysis)
- Visualized salary distributions by position and player type
- Highlighted outliers and trends using scatter plots and histograms

### Positional Analysis
- Filtered Data by position to analyze salary trends
- Found insights into positional specialization in relation to salary

### Player Type Classification
- Groupted Players as Scorers, Shooters, Defenders, or Facilitators based on rules/stat thresholds
- Future extension: Use ML techniques (KMeans Clustering) for unsupervised classification

### ML Regression Model
- Trained a linear regression model using selected performance metrics
- Predicted each player's expected salary
- Calculated the "Value Gap" = Actual Salary − Predicted Salary

## Insights

### Part 1
- Gaurds are more likely to contribute to the offensive side of the ball. This is seen in the larger salaries in players with higher offensive win shares. For example, a player with 3 deffensive win shares are more likely to not be paid as much as a guard with 3+ offensive win shares. This shows the leagues desire for offensively talented gaurds. It is more common to see gaurds with high amounts of offensive win shares then deffensive win shares. The overall conclusion from these two graphs is that for gaurds, deffensive contributions are not as valued by teams. We can see that as the x values increase (Offensive metrics) there is a clear increase in salaries (darker points). This trend is not as clear for a increase in the y-axis (Defensive metrics). Additionally, there is less vertical spread, showing the trend for the league that gaurds are primarily valued for offensive contributions rather than defense possibly due to lack of size and interior prescence.

![BPM and WS vs Salary For Gaurds](Visualizations/Part_1/Gaurd_WS_BPM_Salary.png)

- A similar trend for Forwards follows from the trends of Gaurds. Teams look for offensive stars and are willing to pay more for those who can bring offensive win shares and contribute heavily to the offense side of the ball. Contrasting to the gaurds, there seems to be a larger spread of data, indicating that forwards are more versatile position, where some lean towards offense and some lean towards defense.

![BPM and WS vs Salary For Forwards](Visualizations/Part_1/Forward_WS_BPM_Salary.png)


- Finally, the graphs of Centers seem to be unique to the other positional groupings. There is a much heavier emphasis on defense. Deffensive win shares seem to be paid more than offensive win shares for this position. Additionally, in the second graph, the points seem to be shifted up compared to the other positions. We can now see that as the y value increase (Defensive metrics) the salary increase. Additionally, many centers play power forward and many power forwards play center. This could account for some varying trends in the graphs of forwards and centers. This is because only one position is listed in the dataset, however players accumulate stats playing different positions.

![BPM and WS vs Salary For Centers](Visualizations/Part_1/Center_WS_BPM_Salary.png)

- Overall, Gaurds are primarily paid for their offensive talents and facilitating an offence. Gaurds seem to be the opposite where they tend to be defensive anchors for their team while still presenting an strong interior prescence on the offense. Forwards are the most versatile position, they tend to lean towards the offense side of the ball, but can adapt to based on what a team needs.


### Part 2
- In this part, I analyzed player data and manually categorized players using stats thresholds. I created new individual dataframes for each player type by filtering the main dataframe based on the rules/stats thresholds. I then created graphs for each player type, where I compared the salary to one of three player evaluation statistics (WS, BPM, and PER).

   ```python
   PlayerDFShooters = PlayerDF[(PlayerDF['3PAr'] > 0.5) & (PlayerDF['3P%'] > 0.4)]
   PlayerDFScorers = PlayerDF[(PlayerDF['PTS'] > 20) & (PlayerDF['USG%'] > 25)]
   PlayerDFFacilitators = PlayerDF[(PlayerDF['AST'] > 5) & (PlayerDF['PTS'] < 20)]
   PlayerDFDefenders = PlayerDF[PlayerDF['STL'] + PlayerDF['BLK'] > 2]
   ```

- I first analyzed the salary distributions of each player type, highlighting the median salary for a reference point. The trends that followed were as expected. The "scorers" who were categorized as scoring more than 20 points and having a high usage rate had the highest median salary. Then followed the facilitators, who are less about scoring but rather creating offensive opportunities. Then comes the defenders and lastly specialized shooters. This trend makes sense as teams prioritize well rounded offensive players, where defense is less of a priority and there is a smaller market for specialized shooters.

![Salary Distribution](Visualizations/Part_2/Salary_Distribution_PlayerType.png)


- I then analyzed the relationship between salary and each statistic for every player type. Here I only include the WS graphs as the trends are quite similar between WS, BPM, and PER. Shooters tend to have the smallest spread, low win shares, and a lower salary. This once again reiterates the lack of value in specialized players. Teams wont invest in these players, however for a cheap contract, they could be quite effective off the bench

- Scorers, Facilitators, and Defenders follow simialr trends with minor differences. Scorers seems to be paid more with a larger clump of points further up. Facilitators seem well compensated relative to their performance and win shares. Defenders seem to be undervalued as seen in the cluster that is lower in salary. The difference in win shares between defenders and scorers seem to be very minimal and yet there is still a large difference in salary between the two. GM's now may look to add defenders to their lineup, due to the lower cost and equal win shares.


![WS vs Salary](Visualizations/Part_2/WS_Salary_PlayerClassification.png)

  
### Part 3





## Future Additions
- Implement Clustering technique when Classifyin players in Part 2
     - Will allow for hidden trends to be found and less strict classification (points > 20) ect
- Compare player trends over different nba eras
     - Could compare between now, dead ball era (2000 -2010's), 1990s, ect.
     - Could standardize player performance between different eras to determine which players were better (MJ vs Lebron)
