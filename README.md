# NBA Player Value Analysis

# Goals For Data Analysis
Which players offer the best "bang for your buck"
- Defensive
- Offensive
- Overall 
## Which players are getting overpaid
## How are the top players paid, relative to their contributions
## What rookies or minimum salary players are doing the best. Could give insight into valuable prospects. 

## Which teams do the best job of budgeting their salaries in order to get wins. Win-share or team EPM per $
## Look at top playoff teams and make comparisons. Need indivudal datasets for each one. 
## Positional differences in salary. PG vs C ect. How does positional flexibility affect salary. 


# For importing data. Import 3 seperate datasets from basektball reference.com. All are from regular season 24-25
 ## Dataset 1: Per Game statistics
 ## Dataset 2: Advanced statistics
 ## Dataset 3: Adjusted Shooting
 ## Dataset 4: Player Salary Data



# MAIN QUESTIONS  (For finding outliers, can do so visually, or use skicit library to find residuals and sort accordingly.)

    Part 1
    # Which Positions provide the most impact per dollar

    Part 2
    # Can we cluster player types and determine the value of each category (Shooting, Scoring, Defending, Passing)
        # Will use scikit learn to classify players using kmeans clustering. From there can analyze to find different player groups. If not present, then can do manual classification

    Part 3
    # Which players offer the best usage:salary ratio. Which players are the most efficient per dollar
    # How are bench/low volume high efficency players valued in the nba. (TJ McConel)
    # Who are the most undervalued/overvalued players in the nba (linear Regression)

    

# After Analysis
    # Decide Most Vital statistics to determine value and calculate a new metric based on salary and these performance stats. 