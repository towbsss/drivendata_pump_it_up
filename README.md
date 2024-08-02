# Pump It Up: DrivenData.org Competition

Website link: 
- https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/

References:
- DrivenData. (2015). Pump it Up: Data Mining the Water Table. Retrieved [July 19, 2024] from https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table.

## Process
#### First Stage: EDA
- Looked at all features individually.
- 2-3 features to be dropped (either same information, or unable to interpret)
- Some missing data, to be imputed in next stage
- Mostly categorical variables, to be encoded in next stage

#### Second Stage: Preprocessing & Feature Engineering
- Categorical features that are unseen in submission dataset are combined as 'Other' based on a threshold (started at < 10)
- (Round 1) Label encoding of all categorical features
- (Round 2) Label encoding categorical features with >100 categories, OHE for 100 or less
  - (did worse than Round 1)

#### Third Stage: Model Selection
- (Round 1 & 2) Baseline RF, CatBoost (CB), LGBM, & DT - used RF, CB, and LGBM for submission
- (Round 3) Control tree depth (~10) to prevent overfitting.
- Adjusted categorical variable threshold and used GridSearch with RF
  - Best score of threshold 200. Highest competition score at the moment
- Separate notebook for CB because different preprocessing
  - Used internal gridsearch function
  - TBD adjust class weights; may also try SMOTE
- ongoing...
