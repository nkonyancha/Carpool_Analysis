### Data Acquired from SEKU study 
- https://repository.seku.ac.ke/bitstream/handle/123456789/6610/Kioko_Analysis%20of%20travel%20pattern%20of%20a%20university%20community%20in%20a%20rural%20area.pdf?sequence=1&isAllowed=y
- Where student and staff means of transportation to and from school was studied 
### STUDY SUMMARY
- Random sampling was used 
- 8612 total school population at the time, 8162 student and 486 staff
- 165 responses considered after removing invalid responses
- involved 71.5% males(118), 28.5% females(47)
- population split 69.7% staff(115),30.3% students(50)

### Other Elements studied
- monthly income (<20000, 21000-40000, 41000-60000, 61000-80000, 81000-100000, >100000)
- Age(<25,26-50,51>)
- Trip purpose(work,study,both)
- infrastructure adequacy(yes,no) 

In the study, Extra analysis on what led people to choose their preferred mode of transportation was done. And the results were as follows

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
in the next part i will be doing calculations which will show the economic and atmospheric impact that adaption of car pooling would have from the population
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
