# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
Analyze the relationship between bike availability and nearby POIs.
Store, clean, and enrich bike station data using API calls.
Bulild the Regression Model.
Convert a regression model into a classification problem.

## Process
### step 1: Find the list of Bike station
# trying to get data for the city Toronto. 
# Get the list of networks to confirm Toronto exists
- Toronto is selected for the city. 
- From the Api Find if the Toronto exist
- Get the API URL fromt he network data
- extract the statrion data from API
- Phrase the data in dataframe
- Save the data in csv for future use
### step 2 : Extract data from Four Square and Yelp Data
- Load the required libraries
- Extract csv data to get the longtude and latitude
- FOR each longititude and Latitude extract the data from API to get POI (Point of Intrest) places
- Apply Clustering to decrease number of API call. Clustering groups the station . e.g. for 100 station, instead of 100 API call if we cluster by 10 for 100 station, it loops 10 times instead of 100
- Extract the data from both the APIs and store in in csv for future use

### Step 3 : Joining the data
- import the data from the csv saved.
- Ensure both the result set from Foursquare and Yelp has same column name
- Concat both the POIs
- Create cluster to match the data with POIS
- Merge the data as per cluster of POIs and station data
- Created the bar Chart and Scatter plot to analyse data
- Conclusion from the chart: While some stations with the most nearby POIs have high bike availability, the relationship isn't strictly linear. Other factors may influence bike availability, such as time of day, day of the week, or station capacity.


avg_rating: average rating of nearby POIs

### Step 4: Building Regression
    step1: load required libraries
    Step2: Connect to your database and load data
        We need a dataset where each row corresponds to a bike station, and the columns include:
        bikes_available (target/dependent variable)
        Features based on POIs nearby, such as:
        num_pois: number of POIs near the station
    Step 3: Aggregate POI characteristics per station
    Step4: Build the regression model
    Step4: Interpret the Results

## Results
Key Insights:
Stations with ~100 nearby POIs tend to include some of the highest bike availability values (over 40 bikes).
However, high POI count doesn’t consistently correlate with high bike availability—some stations with many POIs still have very few bikes.
There is a dense cluster of stations with both low POI counts and low bike availability.
As the number of POIs increases, the variability in bike availability also increases, indicating that POI count alone doesn’t explain the trend.

Interpretation:
The regression model shows no statistically significant relationship between:
    - The number of POIs (num_pois)
    - The average POI rating (avg_poi_rating)and 
    - The number of bikes available

The R-squared value is extremely low, meaning the model fails to explain the variance in bike availability.

## Challenges 
Weak correlation between features and target: The chosen features—number of POIs and average POI rating—did not show meaningful predictive power in determining bike availability.

Missing temporal and contextual data: Important variables such as time of day, weather conditions, day of the week, or station capacity were not included, limiting model performance.

API rate limits and efficiency concerns: Collecting POI data for each station was constrained by API limits, requiring the use of clustering to reduce calls (e.g., 10 clusters for 100 stations).

Noisy real-world data: The data may contain inconsistencies or inaccuracies in location coordinates or POI metadata that could affect model quality.

## Future Goals
Include temporal and environmental factors in the model, such as Time of day, Day of the week, Weather conditions,Special events

Enhance feature engineering by: Incorporating station-specific characteristics like bike dock capacity or recent usage patterns.

Exploring proximity to public transit hubs, parks, or universities.

Reframe the problem as classification (stretch goal), e.g.:Predict whether a station has low, medium, or high bike availability based on POI and other features.

