# Udacity-Stage-3-FordGO-Bike-Data-Exploration-Project

## By Oluwabamise Omolaso

***FordGO Biked DataExploration** - 

The dataset contains data related to individual bike rides taken in a bike-sharing system that operates across the larger region of San Francisco Bay area in the year 2019 and spanned 1st of February to 1st of March. 

Summarise the steps you took in your data exploration:

### Preliminary Wrangling
Dataset shape: (183412, 16)
Dataset Columns 
'duration_sec', 'start_time', 'end_time', 'start_station_id',
'start_station_name', 'start_station_latitude',
'start_station_longitude', 'end_station_id', 'end_station_name',
'end_station_latitude', 'end_station_longitude', 'bike_id', 'user_type',
'member_birth_year', 'member_gender', 'bike_share_for_all_trip'],
dtype='object'

Cleaning Steps:
- Checked for duplicate and null values - no duplicate values but null values were dropped (8265 records in member birth year and gender)
- Feature engineering:
  -  New columns - time of day, day of week and hour of day were generated from the time columns and duration in mins was derived from duration_sec
  -  Age and age group columns were generated from the member_birth_year
  -  Distance (km) column was generated from the latitudes and longitudes
  -  Age group column was found to contain null values and upon investgating were found to have ages greater than 100 and were also dropped.
- Datatype transformations:
  - Member_birth_year was changed from flaot to integer datatype
  - start_time and end time changed from object to datetime format  
  - ordinal variables were encoded as category (age_group, user_type, membe_gender, bike_share_for_all_trip, day_of_week)
- Dataset shape afer initial wrangling - (174880, 23)

***Summary of Findings** - 
- Univariate Plots:
- In terms of frequency there were more, user type - subscribers than customers. More male riders than female and others. The working class were the major age groups. Majority of the trips were not shared.
- Duration was found to have a right skew with majority of the rides being less than 200mins. A log transformation was done and it showed that there was a unimodal gaussian distribution
- Distance (km) covered was found to have a similar distribtion to duration with majority of the trips below 10km. An outlier was discovered using a box plot and dropped.
- It was seen that most trips took place in the morning at 8am and evening by 5pm and most rides occur during the weekdays which is in line with the working class population
- Longitude and latitude locations were clustered around three major zones

- Bivariate Plots;
-  Relationship between distance and duration - it can be seen that there is some mismatch in the data as one would expect longer distances to take more time but that is not the case here as there seems to be an inverse relationship where shorter distances take even the most time.
-  Relationship between distance and categorical variables (user_type, member_gender, age group, bike_share_for_all_trips) - it can be seen that there are quite a number of outliers across all categorical variables for distance as majority of the trips lie below 1hr which makes it difficult to tell the differences for each group. The subscibers in the univariate plot had a higher count however, customers cover more distances. Although we saw that the male gender was the most prominent by count, the distances covered by the genders did not vary much. On the contrary for the bike share for all trips where the higher count was recorded for No and in terms of distance travelled, those not in the sharing scheme have a higher amount. The distribution of distance covered among age groups give a not so surprising information as majority of the rides fall within the working class group and the average ride distance for the 60+ group apperars to be nearly as the 30-39 and despite having a far lesser count in the univariate plots which can mean older people in this category take longer bike trips or there are large outliers.
- Relationship between distance and categorical variables - distance travvelled did not seem to vary much among the different categories. Similar pattern for durarion is seen for user_type and member gender where customers with lesser count travel more distances than subscribers. It could be the effect of outliers
- Relationship between Age with distance and duration - younger people travel more distances and for longer durations than older people

- Multivariate Plots explored the relationships better;
- Upon further investigations  on the relationships between the trip duration, the member_genders and the user_types and it shows that the females and others gender categories have higher average trip durations despite lesser counts from the univariate plots and more trips happen on weeekdays or weekends and there are three major clusters for the station locations based on the longitude and latitude. The duration travelled decreases with increasing age which is expected

***Key Insights for Presentation** - 

- Relationship between duration and distance: this was chosen because there is an inverse relationship rather than a direct one.
- Relationship between age with duration and distance - this was chosen because it was seen that there is an inverse relationship where duration travelled and distances covered decrease with increasing age
- Distribution of trips by hour of day - the relationship here shows there are more rides during the weekdays over weekends
- Distribution of trips by age - the relationship here shows there are more rides in the younger age groups
- Distribution of trips by gender - there are more male riders in terms of count, but female riders cover longer durations.

Overall, the fordgobike data exploration showed that there needs to be more investigation on the data collection process as it reveals an indirect relationship between duration and distance, a tendency for more female trip durations despite having fewer rides and seems inconsistent with reality.

