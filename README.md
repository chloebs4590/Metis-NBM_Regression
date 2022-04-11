## What's behind the sticker price of private college tuition and fees?

### Abstract

The goal of this project was to use regression to predict tuition and fees prices at private non-profit colleges/universities in the U.S. in order to ultimately help individuals considering higher education choices -- especially when cost is a major factor -- make more informed decisions knowing what's behind those prices. I scraped my dataset from the National Center on Education Statistics. By leveraging feature engineering and multiple types of regression models, including linear, polynomial and LassoCV to refine my models, I identified the amount of financial aid a school offers and its graduation rate as being the most important indicators of the price of its tuition and fees.

While college tuition and fees increased at historically low rates in 2021, those at private non-profit college/universities still rose at a higher rate than at their public counterparts. And the average college tuition and fees is still significantly higher than it was twenty years ago -- even after adjusting for inflation -- thus, playing a major factor in many people's decision-making around where to pursue higher education studies.

Private non-profit colleges/universities, although oftentimes having higher sticker prices for tuition and fees, also offer more financial aid than public schools, sometimes making themselves the cheaper option.

In order to both a) evaluate how important of a predictor the amount of financial aid is as a factor in predicting tuition and fees at private non-profit colleges/universities offering Bachelor's degrees and b) identify other important features of these schools that can help explain their published tuition and fees, I built regression models in two rounds: round 1 did not include financial aid in the feature set and round 2 did.

### Data

I compiled the dataset using scraped data from the National Center for Education Statistics. The scraped data contained records of 1332 private non-profit colleges/universities offering Bachelor's degrees and 30 statistics about each. Through data cleaning and exploratory data analysis, I refined the final dataset used for modeling to contain 1322 records and 21 features.

### Algorithm

*Feature Engineering*

- Converting categorical features to binary dummy variables
- Re-scaling continuous features to be on the same scale before performing regularization

*Models*

Linear, LassoCV and polynomial regressions were evaluated before ultimately choosing LassoCV regression models for each round. While the LassoCV regression models were not the best fit in either round (the polynomial models were), they were selected for the combination of simplification, lower error (the error in the polynomials was the highest), less inconsistencies in error, and more normally distributed residuals with a zero mean.

*Model Evaluation and Selection*

For each round, the entire dataset of 1322 records was split into 80/20 training vs. holdout. Only training data was used to fit each iteration of each round's model. After fitting each model, I performed 5-fold cross-validation on the training data and noted these scores. The evaluation metric used was Root Mean Squared Error (RMSE). Once I refined each round's model, I ran the models on the 20% heldout data and reported those final average RMSEs below.

- **RSME of holdout data in round 1 (feature set not containing financial aid):** 10,048.67
- **RSME of holdout data in round 2 (feature set containing financial aid):** 6,505.23

### Tools

- BeautifulSoup for web scraping
- Numpy and Pandas for data manipulation
- Matplotlib and Seaborn for plotting
- Scikit-learn and Statsmodels for modeling

### Communication

My complete code and presentation slides are available in this project's repo.
