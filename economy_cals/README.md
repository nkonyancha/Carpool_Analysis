
# Summary of Notebook: Carpooling Adoption and Economic Impact Analysis

This notebook explores the impact of carpooling adoption on trip costs using a dataset of 2,000 entries with various transportation modes and demographic features. The analysis leverages feature engineering, regression modeling, and feature importance visualization to draw insights.

## Key Steps and Findings

### 1. Data Preparation & Feature Engineering
- The dataset was loaded and encoded, including variables such as trip frequency, travel distance, age, income, gender, student status, location, transportation mode, trip purpose, infrastructure adequacy, and carpooling adoption.
- Trip cost was calculated based on transportation mode and distance, with special handling for taxi fares.
- An adjusted trip cost was computed to simulate the effect of carpooling (e.g., dividing taxi costs by three for carpooling scenarios).

### 2. Regression Modeling
- **Linear Regression** and **Voting Regressor** (ensemble of Linear Regression, Decision Tree, and Random Forest) were trained to predict adjusted trip costs.
- The models achieved high accuracy, with R² scores close to 1, indicating excellent fit.

### 3. Feature Importance Analysis
- **Linear Regression** revealed that `travel_distance_exp`, `status_Students`, and `mode_transportation_Private` are the most influential features affecting trip cost.
- **Voting Regressor** confirmed similar findings, with `travel_distance_exp` and `status_Students` consistently ranking highest.

### 4. 
### 4. Economic Impact of Carpooling
- The simulation showed that carpooling significantly reduces trip costs, especially for taxi users.
- The analysis highlights that trip distance and student status are major drivers of cost, suggesting targeted policies could maximize economic benefits.

## Conclusion

Carpooling adoption leads to substantial economic savings, particularly for longer taxi trips. The most important factors influencing trip cost are travel distance, student status, and choice of private transportation. These insights can inform transportation policy and carpooling promotion strategies to optimize economic outcomes for commuters.






