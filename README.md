# econ3916-lab06-sampling

# Sampling for Machine Learning — Train-Test Splits

## Objective
The goal of this lab was to understand how different sampling methods affect machine learning, compare train-test splits, and learn how to prevent data leakage when preparing datasets.

## Methodology
- Explored the Titanic dataset, which contained 891 passengers, and examined how survival rates differed across passenger classes.
- Compared naive and stratified train-test splits using an 80/20 split to see how well each method preserved the overall survival rate.
- Used stratified sampling to maintain similar proportions of passenger classes and survival outcomes across the training and test sets.
- Identified and corrected data leakage when using StandardScaler and SimpleImputer by fitting them only on the training data.
- Wrote a function called `split_by_share()` that divides a dataset into training and test sets using a specified test share and random seed.
- Tested my function using a 70/30 split and verified that it passed the lab's automated checks.
- Examined the UCI Adult Income Dataset as an example of selection bias and discussed how a better sampling design could improve representation.

## Key Findings
- The overall survival rate in the original Titanic dataset was 38.4%, with first-class passengers having a much higher survival rate (63.0%) than third-class passengers (24.2%).
- After removing passengers with missing ages, the dataset contained 714 passengers with an overall survival rate of 40.6%.
- The naive split produced survival rates of 41.0% for training and 39.2% for testing, while the stratified split kept both rates at approximately 40.6%.
- I found that fitting a scaler or imputer before splitting the data creates data leakage because information from the test set is used during training.
- When correcting the imputation process, the training data produced an Age fill value of 29.8077, while the mean Age in the test set was 29.3746.
- My `split_by_share()` function successfully divided the dataset into 499 training rows and 215 test rows, with survival rates of 40.3% and 41.4%, respectively.

## Conclusion
My biggest takeaway from this lab was that how we split and prepare our data matters when building machine learning models. Stratified sampling can help keep important proportions consistent, while preventing data leakage makes sure the test set provides a fair evaluation of the model. I also learned that a larger dataset doesn't automatically mean better results if the sample isn't representative of the population we're trying to study.
