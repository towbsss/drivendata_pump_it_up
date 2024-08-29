# Pump It Up: DrivenData.org Competition

Website link: 
- https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/

References:
- DrivenData. (2015). Pump it Up: Data Mining the Water Table. Retrieved [July 19, 2024] from https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table.

## General Process (more details in each notebook)
#### First Stage: EDA
- Looked at all features individually via bar charts
- 2-3 features to be dropped (either same information, or unable to interpret)
- Some missing data to be imputed in next stage
- Mostly categorical variables; to be encoded in next stage

#### Second Stage: Preprocessing & Feature Engineering
- Categorical features that are unseen in submission dataset are combined as 'INFREQUENT' based on a threshold (started at < 10)
- Despite semi-duplicate features (e.g. `region` & `region_code`, removing them hurt submission score)
- Random Forest (RF) requires more preprocessing steps
- LGBM and CatBoost (CB) did better with internal one hot encoding

#### Third Stage: Model Selection
- Created models with RF, LGBM, and CB
- Started with 70/30 train test split, then changed to 80/20
- Stratified 5-fold cross-validation for all models
- Hyperparameter tuning with Optuna for RF & LGBM; gridsearch for CB
- Hovered around an 80% accuracy score (classification rate)
 
#### Last Stage: Final Model
- Combine all models for a final prediction via soft voting
- Highest score from soft voting with 0.8212

#### Note:
- Initial scores were about ~80% but at some point, something went wrong and all scores went down to ~50% for all models.
- Tried everything to make the score go back up, but after a week of attempts (23 attempts, actually), I went back to the original preprocessing steps.
- After keeping the original preprocessing steps, it went smoothly again.
- Since all models scored similarly, it was likely due to a change in preprocessing steps.
