# cluster_industry
Cluster stocks by industries at a more granular level:
    Use Victor's indicators like CAPEX, Revenue, EV, EBITDA, etc...

How will we conduct dimensionality reduction?
https://www.analyticsvidhya.com/blog/2018/08/dimensionality-reduction-techniques-python/#h-2-why-is-dimensionality-reduction-required

    1. Missing Value Ratio: Highly unlikely that we will need this, since our quarterly data should be fairly easy to gather, and it should be already clean. Nonetheless, if yfinance does not do its job (or in the future, if we need to conduct), then we need to either impute the missing values or completely get rid of the feature entirely (NOTE: WE ARE NOT DROPPING THE EMPTY CELLS, WE ARE DROPPING THE WHOLE VARIABLE). The decision to drop or not will be made on the basis of the number of missing values - we need to agree on an arbitrary threshold. Say, if 20% of the values are missing, we drop the variable. Else, we can choose to impute the empty variables using a variety of methods. The best ones to use with our relatively small dataset will probably be *multiple imputation, MLE, or regression imputation* (we can look this up later if need be, since it depends on the type of missing data: MCAR, MAR, or MNAR).

    2. Low Variance Filter: This is fairly obvious; all we need to do is find the variance of a certain feature, Var(F). If Var(F) is proportionately low as compared to other features, then we can safely drop the feature.

    3. High Correlation Filter: Since high correlation between two features can bring down the performance of some models (like linear and regression models) drastically, we should aim to prevent this from happening. If we have n features that are highly correlated to each other, we can drop n-1 features. However, dropping a variable is highly subjective and should always be done keeping the domain in mind. As a general guideline, we should keep those variables which show a decent or high correlation with the target variable. Further, if the correlation between a pair of features is greater than 0.5-0.6, we should typically consider dropping one of those variables.

    4. 