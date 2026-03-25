Exploratory Data Analysis: The Future of U.S. Data Center Locations 

As of early 2026, the construction of new data centers (measured in total dollars spent) has surpassed the construction of new office space for the first time in history. This represents a shift from traditional human labour to leveraging big data for artificial intelligence, cloud computing, web services, ect... Building these facilities requires careful consideration of tradeoffs involving things like real estate costs, electricity demand and water consumption. 

My chosen source for this project is posted to the U.S. Department of Energy
Office of Scientific and Technical Information website: https://www.osti.gov/biblio/2571680

As listed in the description "IM3 Projected US Data Center Locations This dataset contains model projections of new data center facilities in the contiguous United States (CONUS) through 2035 using the CERF – Data Centers model" The goal of my project is to understand how data that makes projections (such as the one used for my analysis) may influence the decision-making of those building these data centers in the coming decade. 

I combined their various datasets into one .csv file and put that into a pandas dataframe. The concatenated dataset contains 16,645 rows and 15 features. The key features I set out to focus on were:

- growth_scenario: data center demand growth scenario (ie. low, moderate, high,
higher)
- market_gravity_weight: market gravity weight scenario (ie. 0% market gravity means that siting decisions were entirely determined by the locational cost in each feasible location. 100% market gravity means that only market proximity was considered when siting)
- region: name of region (i.e., US State)
- total_cost_million_usd: locational siting cost ($million)
- mechanical_cooling_frac: fraction of year when data center uses mechanical cooling system
- water_cooling_frac: fraction of year when data center uses evaporative cooling system
- weighted_siting_score: total weighted siting score of locational cost and gravity score

note: I particularly ignored some of the features such as campus_size_square_ft and data_center_it_power_mw as they appear to have been standardized as constants. 

Plot #1
Strip Plot to illustrate the projected cost of building data centers for each region under two opposite conditions: one that prioritized absolutely being near big cities and the other that prioritized the cheapest location (in each region). This revealed a clearly statistically significant tradeoff, absolutely prioritizing proximity to population almost always cost millions of dollars more than not prioritizing it at all.

Plot #2
Point Plot to compare the weighted_siting_score (which is essentially the datasets winning score on how good a location is overall) with the market_gravity_weight mentioned in plot 1 (100% being we care absolutely about being close to major cities and 0% being we don't care at all). This revealed that on either extreme, the "winning score" was very low but the closer we approach an ≈ 50% market gravity weight, the better the score seems to be. This means that according to the predictive model, a nearly perfectly balanced location, not too close but not too far from major hotspots, is potentially the best bet. 

Plot #3
Box Plot for the projected financial costs of different cooling methods (Mechanical vs Water cooling). The plot has four different groups: only water cooling, only mechanical cooling, half & half, and mostly mechanical partly water. From looking at this chart, I observed that the purely water cooled data centers have the potential to vary the most in terms of cost, they had the widest range and the most outliers. Furthermore, the half water, half mechanically cooled data centers appear to fall within the tightest, and in my opinion most reasonable price range of the four groups. Finally, the mostly mechanical partly water group seemed the most expensive.


All the code used to generate these plots is available in the accompanying Jupyter Notebook. 
