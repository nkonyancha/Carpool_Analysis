# Project Essay: Smart Carpooling for Environmental and Economic Impact in Nairobi

Urban mobility in Nairobi is deeply congested, environmentally costly, and increasingly expensive for everyday commuters. With rising fuel prices, long queues, and heavy CO₂ emissions from private cars, matatus, taxis, and boda bodas, the city faces a mobility challenge that affects both the environment and the economy. My project proposes an intelligent carpooling optimization system designed to reduce emissions, lower transport costs, and encourage shared mobility adoption using data-driven insights.

At the center of the project is a machine-learning model that predicts potential carpool adoption among users based on demographic features, travel frequency, distance, and cost sensitivities. The model incorporates multiple transportation emission profiles—including cars, taxis, matatus, and motorcycles—to simulate how individual choices contribute to total daily emissions. By introducing a realistic “adoption scenario,” the system adjusts each user’s emission footprint when they switch from their original transport mode to a more efficient shared ride. This allows the platform to quantify the environmental benefits of carpooling in measurable terms such as reduced CO₂ emissions per kilometer.

Economically, the system evaluates how shared mobility can cut transport expenses for students, workers, and low-income commuters who often spend a significant portion of their income on travel. By modeling cost-sharing between riders, the project demonstrates how carpooling reduces individual trip costs while increasing vehicle occupancy, making transport more inclusive and affordable. The model also incorporates behavioral factors, recognizing that adoption is not uniform; stratification and predictions are designed to reflect real Nairobi commuting patterns.

The final output of the project is an interactive dashboard and analytical engine that visualizes environmental savings, economic benefits, and predicted adoption rates under different scenarios. Users can see how emissions decrease when carpooling replaces taxis or private vehicles, how trip costs drop when shared, and how Nairobi’s overall carbon footprint could change if even a small percentage of commuters adopted shared mobility.

This project aims not only to showcase technical ability—data preprocessing, feature engineering, linear regression modelling, simulation design—but also to highlight a real solution with meaningful social impact. Nairobi’s transport future depends on systems that are both sustainable and affordable. By combining machine learning with environmental modeling, this project demonstrates how technology can drive greener mobility choices and create economic opportunity for thousands of everyday commuters.

# Hypothesis
- Ho: `Adoption` has no effect on `Emissions`, Ha: `Adoption` has a significant effect on `Emissions`
- Ho: `Adoption` has no significant impact on `App income`, Ha: `Adoption` has a significant impact on `App income`

### Data Acquired from SEKU study 
- https://repository.seku.ac.ke/bitstream/handle/123456789/6610/Kioko_Analysis%20of%20travel%20pattern%20of%20a%20university%20community%20in%20a%20rural%20area.pdf?sequence=1&isAllowed=y
- Where student and staff means of transportation to and from school was studied 
### STUDY SUMMARY
- Random sampling was used 
- 8612 total school population at the time, 8162 student and 486 staff
- 165 responses considered after removing invalid responses
- involved 71.5% males(118), 28.5% females(47)
- population split 69.7% staff(115),30.3% students(50)

* CAR/TAXI
    - comfort(81.3%)
    - car ownership(85.7%)
    - Trip origin(66.7%)
    - Travel time(52.4%)
    - safety(50%)
* MATATU
    - trip cost(69.6%)
    - travel time(~41%)
    - safety(~45%)
* MOTORBIKE
    - trip distance(~11%)
    - trip cost(<10%)
    - travel time(<10%)
* Walking
    - trip distance(~18%)
    - trip cost(10%)
## ASSUMPTIONS MADE
- average emissions of a toyota vitz (116.0 g/km of CO2) and suvs used Rav4 (178 g/km) according to Mauritius Revenue Authority https://www.mra.mu/download/CO2EmissionDB251115.pdf
- Average matatu trip cost (30-50)as per the SEKU study, i will however use 80 to account for inflation and people using more than one matatu to get to school
- As per the study the university is in a remotte location 18km away from the closest shopping center. Using little cab app a trip from Nairobi school to USIU (17.1 KM) costs around 760 for economic trip, i shall use 700 as my average trip cost to ease calculations
- for private cars. vitz(17km/L) Rav4(17km/L) according to simple google searches, using current fuel prices (185ksh/L) this brings average trip price for private cars to be ((trpdist/17km)*185)
- Separate taxi users from car users using age, income and status as weights.
- i shall pick 20% adoption among students/staff who use cars/taxis. This will be those with less income. I shall pick 15% adoption of app from people using matatus. due to their low number i shall ignore people walking and using motorbikes.
- Lastly i shall generalise the trends found from the study. Although the low number of participants may mean this is inaccurate
- I shall assume that in the current study all participants in car/taxi use a different car/taxi (no sharing)
- I shall assume 260 g/km for matatu emissions. i will divide this by 14 to get emissions for each passenger in the matatu and use that figure (18.6 g/km) for each matatu user in the dataset
- Little cab commission 18% of all trips according to https://www.little.bz/scbov.pdf

## Findings Summary
- With a P-value of 1.47e^-29 We reject the first Ho and conclude that `Adoption` has a significant impact on emissions and the coefficient of -28.23 shows it has a negative impact so more adoption reduces emissions
- With a P-value of 