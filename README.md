## 1	Introduction
Cyclistic is a bike-sharing program operating in Chicago that offers a variety of pricing plans, including single-ride passes, day passes, and annual memberships. While the pricing flexibility has helped attract a broad customer base, finance analysts have concluded that annual members are much more profitable and key to future growth. <br>
To support this objective, Cyclistic aims to better understand how casual riders, who are single-ride or day pass users, and annual members use the service, in order to develop strategies for membership adoption. This analysis will focus on the first phase of that effort, where we observe how annual members and casual riders use Cyclistic differently. <br>
Using 12 months of historical trip data, this case study examines rider behavior across dimensions such as ride durations, trip frequency, and temporal usage patterns. These metrics are key in uncovering meaningful behavioral differences between the two groups and providing data-driven recommendations to support future membership growth initiatives. 


## 2   Business Statement
The objective of this analysis is to identify behavioral differences between casual riders and annual members in Cyclistic’s bike-share program. These insights will support the marketing team in designing strategies to convert casual riders into annual members, thereby increasing long-term profitability.

## 3   Data Source Description
Description: This dataset contains Cyclistic's trip data of over 5 million trips between May 2025 and April 2026, tracking the activity of riders across Chicago. 12 months of trip data is covered across 12 datasets, where each row denotes 1 bike trip. <br>
Access: The dataset is made available by Motivate International Inc. under this license https://divvybikes.com/data-license-agreement. <br>
Limitations: The dataset does not include personally identifiable information, preventing user-level tracking and demographic segmentation. Additionally, external factors that may influence riding behaviour, such as weather and trip purpose, are not included. <br>
Key metrics: The data in the dataset covers the timestamps, location endpoints, coordinate endpoints, bike type(classic/electric), and user types (member/casual). As such, the dataset is suitable for behavioral trend analysis. 

## 4	Documentation
### 4.1	Data Integrity
Prior to analysis, all datasets were checked for structural consistency, duplicate records, and completeness. Column names and data types were verified across all 12 monthly datasets before merging. No duplicate records were identified, and all records contained the critical fields required for analysis, including timestamps and rider type.

### 4.2	Calculating new columns 
Ride length
-	Converted started_at and ended_at to datetime
-	Ride length = ended_at – started_at

### 4.3	Cleaning 
Cleaning involved checking for missing values and anomalies in ride lengths.
#### 4.3.1	Missing values
- Missing values were evaluated based on their relevance to the business objective.
- 1,914,653 (33.61%) of 5,697,455 rows returned missing values. Among them, none contained crucial information such as timestamps, bike type, or rider type. Non-critical missing fields, such as station names/id and lat/long were retained to avoid unnecessary data loss. As such, no rows with missing values were removed. 
#### 4.3.2	Ride Length
Ride lengths that were negative, under a minute, or over 24 hours were removed. 
- A total of 161,465 rows were removed
    - 156 (0.0027%) rows contained negative ride times
    - 155,476 (2.73%) trips were under 1 minute
    - 5,833 (0.1%) trips were over 24 hours 
Rides over 24 hours generally indicate stolen bikes or users failing to properly dock the bike, whereas rides under 1 minute are usually false starts, accidental unlocks, or immediate returns due to a malfunctioning dock.

## 5	Visualizations and Key Findings

![member-green annual-orange](images/membercasual.png) 
 
Annual members accounted for 64.72% of all Cyclistic trips. Despite accounting for nearly two-thirds of rides, their total riding time is smaller, only accounting for 53.3%. This suggests a discrepancy between the average ride times of the two member types.
 
Upon further analysis, casual riders ride for an average of 19.72 minutes each trip, over 1.6 times longer than annual members’ average ride time of 12.26 minutes. 
Longer ride times are consistent with leisure and suggest casual riders using Cyclistic for recreational purposes.
 
Casual riders’ average ride lengths increase significantly during warmer periods (e.g., Summer - June to August), peaking to as high as 21.91 minutes in June. Annual members’ activity level remains relatively consistent all year round. 
 
Both annual and casual riders depict a similar trend, where total trips peak during warmer periods and decrease as it gets colder.
 
Annual members generated approximately 224% more trips than casual riders during weekdays. On the contrary, casual riders increase significantly over the weekends, signifying Cyclistic is being used for leisure, whereas annual members decrease, indicating that Cyclistic has become integrated into their daily commuting routines.


Annual members exhibit a clear pattern between 7am - 9am and 4pm - 6pm on weekdays, strongly suggesting that Cyclistic is being used for commuting purposes. They use the bikes to commute to work in the morning and from work in the evening. <br>
On the contrary, casual riders display a consistent pattern throughout the week. On weekdays, usage slowly builds where it peaks in the late afternoon, suggesting that casual riders are less dependent on Cyclistic for traditional work schedules and may be using them for errands, leisure, or flexible transportation purposes instead. <br>
Weekend behaviour is remarkably similar across both annual members and casual riders, where usage is minimal in the morning and gradually increases throughout the day, peaking between 12pm - 5pm.

## 6	Summary of Analysis
- Casual riders use Cyclistic for recreational purposes, whereas annual members use Cyclistic for commuting purposes. 
- Annual members account for nearly two-thirds of total trips, while casual riders spend 1.6x more time on average each ride. 
- Total trips by annual members are significantly higher than casual riders during weekdays, and converges during the weekends.
- Seasonally, activity level is at its peak during the warmer months (summer – June to August). Casual riders are more weather-dependent, seeing a significant increase in average ride lengths during this period.

## 7    Recommendations
- Incentivize frequent riding
    - Promote memberships as a cost-effective solution for riders who use Cyclistic regularly. The pronounced weekday patterns displayed by annual members show that memberships provide the greatest value to riders who use Cyclistic for regular commuting and routine travel.
        - Convenience denotes the idea that Cyclistic is a hassle-free and readily available option to get from point A to point B, without the hassle of having to wait for a bus or taxi, or deal with the troubles of driving (finding parking, sitting in traffic, etc.)
        - Reliability denotes the idea that users can depend on Cyclistic’s services regularly. 
- Create transition incentives during the summer peak
    - Offer discounted first-year memberships to casual riders who complete multiple rides during the summer, marketed aggressively specifically during this period where they are interacting with the service the most and likely to perceive value in continued usage.
- Target high-engagement casual riders
    - Target casual riders who use Cyclistic repeatedly with personalized offers. Because they already use the service so frequently, converting them may require less behavioural change compared to acquiring entirely new users.
