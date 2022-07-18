# SpaceshipTitanicCompetition

This repository is dedicated to my work in the Spaceship Titanic competition on Kaggle. Here is the competition page for reference:

[Spaceship Titanic Competition](https://www.kaggle.com/competitions/spaceship-titanic)

This is a knowledge-building competition, so neither points nor money are awarded for participation in it. I entered it in July 2022 as a way to reinforce my learnings on entropy/information gain-based methods such as random forests, XGBoost, and CatBoost, and also to compare their performance to distance-based methods like Logistic Regression.

Aside from choosing different classification methods, the major differences in my attempts centered around the feature engineering and the models I created from the feature sets. My very first attempts used basic models with very little feature engineering, which I used as a baseline to understand whether I was overfitting or underfitting the data.

__Summary of My Process__
1. Load and review data
  - Data provided in CSV format
  - Null, unique, and duplicate value checks for train and test sets
2. Clean data
  - Replace missing values
    - Categorical variables used most_frequent
    - Continuous variables used mean (Age) and median (all other continuous variables)
3. Feature engineering
  - Parsing variables that seemed to be combinations of other potential variables of interest (example: PassengerId, Cabin)
  - Combining variables (example: summing variables that tracked category spending per user)
  - Missingness indicators
7. Model building and finalization
  - Split training set into training and validation sets with validation equal to different amounts depending on the model size (20% or 10%).
  - Combination of GridSearchCV and StratifiedKFold to find the best parameter set from training.
9. Training and validation
  - Classification reports
  - Logloss and error charts (XGBoost)
10. Test predictions and competition submission

## Results Log
__11 July 2022:__ XGBoost + GridSearchCV + KFold; 78.629% accuracy on competition data.
- Minimal feature engineering- split Cabin variable, no transformation of spending variables.

__18 July 2022:__ XGBoost + GridSearchCV; 79.985% accuracy on competition data.
- Large model version- split PassengerId and Cabin variables, used missingness indicators, log(x+1) transformation of spending variables. All variables retained regardless of collinearity and VIF scores.
