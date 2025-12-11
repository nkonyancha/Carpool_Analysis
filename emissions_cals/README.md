# Notebook Summary — Emissions & Carpool Adoption Analysis

## Objective
- Simulate and analyze the effect of carpool adoption on per-trip emissions.
- Predict adjusted emissions and identify features associated with emission reductions.

## Data Source
- Loaded simulated dataset: `../simulated_carpool_data.csv` (N = 2000 rows).
- Saved encoded dataset to `../dataset_encoded.csv`.

## Preprocessing & Transformations
- Converted categorical ranges into numeric simulations:
    - `travel_distance` → `travel_distance_exp` via random integers in specified bands.
    - `age` → `age_exp` with age ranges sampled as integers.
    - `income` → `income_exp` through randomized integer mapping per bracket.
- Converted `mode_transportation` → `emissions_exp` using per-mode random emissions:
    - Private, Taxi, Motorcycle, Public Transport (scaled), Walking (0).
- One-hot encoded categorical features: `gender`, `status`, `location`, `mode_transportation`, `purpose`, `infrastructure_adequacy`, `adoption` (with `drop_first=True`).
- Converted `trip_frequency` values to numeric (Daily → 7, etc).
- Created `adjusted_emissions`: if `adoption_yes == True`, simulated emissions reduced by using a random taxi emission divided by 3; otherwise used `emissions_exp`.
- Constructed features (`X`) and target (`y` = `adjusted_emissions`) while dropping irrelevant columns: `['emissions_exp','id','age','income','travel_distance','adjusted_emissions','trip_cost','g_per_km']`.
- Train-test split: 80% train / 20% test stratified by `adoption_yes` to preserve adoption rates.

## Models Trained
- Linear Regression (lrmodel).
- Voting Regressor combining:
    - LinearRegression, DecisionTreeRegressor, RandomForestRegressor, SVR.

## Evaluation Metrics (Linear Regression)
- MSE: 403.07
- RMSE: ~20.08
- MAE: ~15.19
- R²: ~0.836 (model explains ~83.6% of variance in adjusted emissions)

## Feature Importances & Key Findings
- Top predictors (both models) based on feature importance:
    1. mode_transportation_Walking — largest negative effect (strong emission reduction).
    2. mode_transportation_Public Transport — strong negative effect.
    3. adoption_yes — significant negative coefficient (~ -27.84), supporting hypothesis that adoption reduces emissions.
    4. mode_transportation_Taxi & mode_transportation_Private — positive predictors of emissions.
- Most numeric features (travel_distance_exp, age_exp, income_exp) had small coefficients and lower relative importance.
- Trip frequency had a small negative coefficient (slight reduction per unit in the linear model, but minor importance overall).

## Interpretations
- Walking and public transport correspond to much lower per-trip emissions (as expected).
- `adoption_yes` is associated with a meaningful emission reduction in the simulated data. Linear regression coefficient is found to be -28.23
- A t-test conducted on emissions vs adoption resulted in a P-value of `1.47e^-29` so we conclude that Adoption has a significant impact on emissions
- The models achieve strong explanatory power (R² ~ 0.836); however, the dataset is artificially randomized (mappings used are random samples), so real-world interpretation should be cautious.

## Dataset & Modeling Assumptions / Limitations
- Many numeric columns were simulated using random integers per category — this is synthetic and may not reflect real distributions.
- The `adjusted_emissions` reduction for adopters is simulated by dividing a taxi emission by 3 for a subset of adopters — this is an assumption rather than empirically derived.
- Emissions mapping for public transport uses scaled ranges that differ from realistic values.
- Randomness is used in mapping: results will vary unless seeds are fixed.
- No hyperparameter tuning or cross-validation was applied to ensemble models; the VotingRegressor uses base estimators with default params.

## Recommendations & Next Steps
- Replace random mappings with empirically measured distributions or domain-informed statistics.
- Validate assumptions on adoption emissions reductions with domain experts or real data.
- Perform cross-validation and hyperparameter tuning (GridSearchCV/RandomizedSearchCV) for the RandomForest and SVR components.
- Add interactions and polynomial features if nonlinear effects are expected.
- Compare per-person and per-year emissions impact (aggregate over frequency).
- Compute and visualize residuals, prediction vs. actual scatter, and calibration plots.
- Consider models that quantify uncertainty and perform ablation studies for policy recommendations.

## Visualizations Already Included
- Bar charts for:
    - Linear regression coefficients by absolute value with sign (color-coded).
    - Voting regressor averaged feature importances.

## Conclusion
- Within the simulated dataset, carpool adoption and active transport modes (walking, public transport) show meaningful emission reductions.
- Findings support the hypothesis that carpooling (adoption) can reduce per-trip emissions, but confirmatory analysis with real-world data and improved assumptions is required to apply conclusions for policy.