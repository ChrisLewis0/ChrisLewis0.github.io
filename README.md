## Predicting Midterm Elections

## Exploratory Data Analysis

- What data are we dealing with?
- How have we explored the data (initial explorations, data cleaning and reconciliation, etc)? 
- Visualizations and captions that summarize the noteworthy findings of the EDA.
- A revised project question based on the insights you gained through EDA (specific to data).
- A baseline model.

### Project Goal 
The primary goal of this project is to explain the outcomes of the 2018 midterm
elections in the House. Any piece of information from before election day can be used to perform
this analysis, but the suggested feature set should include past elections, polling data, and demographic information of congressional districts.

### House District Candidate Data

We sourced raw candidate data detailing the total votes for each candidate in each district in the country going back to 1976. This data also included the party affiliation of each candidate which allowed us to obtain the total votes for each party by district for the last 40 years. We then cleaned the data extensively so that it would be in a useable form to analyze. 

### How do states traditionally vote?

![](https://github.com/ChrisLewis0/ChrisLewis0.github.io/blob/master/Party%20Voting%20Averages%20by%20State.png)

### House Seat Changes by President

**Are there differences in House seats lost by Democratic vs Republican Presidents?**

![](https://github.com/ChrisLewis0/ChrisLewis0.github.io/blob/master/Distributions%20of%20Change%20in%20House%20Seats.png)

### Data Cleaning and Merging

**Trim our features into something useable for an exploratory regression**

We noticed that candidates outside the major two parties basically never win, so we decided to focus our attention on the two major parties: Democrats and Republicans.

We also need to merge rows for tickets that were competing in the same election, where district and year are equal, as our predictive task will be predicting the winner.

We then assinged boolean values for party, 0 for Democrats and 1 for Republicans. We changed our winner variable here from representing success to representing the party that won, once we merge the tickets, making the data cleaner and easier to use. 

We needed to transition some of the demographic variables such as sex and ethnicity into percentages instead of absolute numbers. We did this by dividing the absolute values by the total population values. Otherwise any normalization applied across the whole data set won't account for differences in population between elections. 

## Related Work

## Modeling the Data

### Exploratory Baseline Models

**Linear Model**

We produced a simple exploratory linear regression to get a feel for what predictors would provide the most influence on the results, and thus would be the most useful predictors. After producing this exploratory regression, we employed bootstrapping to determine p values for each of our predictors. This allowed us to determine quantitatively which predictors were statistically significant in a linear regression, which allowed us to get a sense of which predictors will be the most important for us as we moved towards more advanced models.

We were able to determine that many of our predictors were not statistically significant. To look into this further, we bootstrap across many samples of the data to produce a more accurate picture of which predictors are significant in our linear regression.

**Ridge Model**

We use a Ridge linear regression model to further get a sense of which predictors were influential in a regression. Ridge regression provides protections against overfitting to the train data by penalizing excessively large coefficients. This increases the predictive accuracy on the test data, and provides coefficients that we can use to more accurately predict the importance of each predictor. 

**Lasso Model**

We use a Lasso linear regression to try perform some variable selection on the data. Lasso regression is notorious for its tendency to prefer the removal of insignificant predictors. Thus, by using Lasso regression, we can get an even better sense of which predictors are effectively irrelevant. We discarded those predictors and focused on the remaining ones. 

### Random Forests 

![](https://github.com/ChrisLewis0/ChrisLewis0.github.io/blob/master/rf_top_preds.png)

### Boosting

Continuing with our more advanced modeling, we 

![](https://github.com/ChrisLewis0/ChrisLewis0.github.io/blob/master/boost_test_150.png)
![](https://github.com/ChrisLewis0/ChrisLewis0.github.io/blob/master/boost_both_150.png)

### Neural Networks

## Interpretation

## Conclusion
