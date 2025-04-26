# CYCLISTIC BIKE-SHARE ANALYSIS CASE STUDY

## INTRODUCTION
This capstone project is the final part of completing the Google Data Analytics Professional Certificate course. In this case study I will analyze a public dataset for a fictitious company, Cyclistic. For this analysis, I will be using R programming language because of its statistical computing capabilities, rich ecosystem of packages, and strong visualization tools. To cater the relevant question, I will follow the six phases approach of the data analysis: Ask, Prepare, Process, Analyze, Share, and Act.

## SCENARIO

Cyclistic is a bike-share company in Chicago. In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The company offers three types of flexible pricing plans: single-ride passes, full-day passes, and annual memberships. Single-ride passes and full-day passes riders are referred as casual riders.
The finance analysts at Cyclistic concluded that annual members are much more profitable than the casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Lily Moreno, the director of marketing, is convinced that maximizing the number of annual members will be the key to future growth. Moreno believes there’s a solid opportunity in converting casual riders into full-fledged members, instead of focusing on all-new customers, as casual riders are already familiar with the Cyclistic program and have consciously chosen Cyclistic for their transportation needs.
As a junior data analyst, I will follow the steps of the data analysis process as mentioned above and find out actionable insights for the stakeholders.

## **DATA ANALYSIS PROCESS**

### **1. Ask Phase:**

•	**Business Objective:** The business objective of is to increase the number of annual Cyclistic members in order to enhance profitability and ensure business growth. By converting more casual riders into annual members, Cyclistic aims at creating a more stable revenue stream.

•	**Business Task:** To design effective marketing strategies that focus on encouraging casual riders to purchase annual memberships. 

In order to do this, it is important to first address the following questions by analyzing the Cyclistic historical bike trip data to draw conclusions and identify trends.
1. How do annual members and casual riders use Cyclistic bikes differently? 
2. Why would casual riders buy Cyclistic annual memberships? 
3. How can Cyclistic use digital media to influence casual riders to become members? 

•	**Stakeholders:**

1. *Lily Moreno:* The director of marketing and your manager. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program. 

2. *Cyclistic’s Marketing Team:* The Marketing Team will be responsible for conducting the analysis and developing the marketing strategy based on the insights gained.

3. *Cyclistic executive team:* The notoriously detail-oriented executive team will decide whether to approve the recommended marketing program.


### **2. Prepare Phase:**

This phase of data analysis involves data collection and preparation. Identifying the data sources, gathering relevant data and verifying if it is accurate and useful for answering the questions.

**Data Description:** For this case study, I’ll be using a public dataset, made available by Motivate International Inc. My focus will be on the data from first quarter of 2019 and 2020, which is organised in two separate CSV files. 2019 first quarter CSV file contains 12 columns and 3,65,070 rows, while 2020 first quarter CSV file contains 13 columns and 4,26,888 rows. The data is organised in a way that will provide an opportunity to conduct a thorough analysis to identify ridership patterns and gain valuable insights. 

* **Data Credibility:** The data used in this study meets the ROCCC standards of data credibility.
1.*Reliable:* The data is trustworthy, accurate, complete, and unbiased, having undergone verification to ensure its suitability for the intended purpose.
2.*Original:* The data is sourced directly from the primary, authentic provider.
3.*Comprehensive:* The data encompasses all essential information necessary to address the question or resolve the problem at hand.
4.*Current:* Given its monthly release schedule, the data remains up-to-date and pertinent.
5.*Cited:* The data is appropriately referenced and attributed in the project.

* **Data Licensing:**
The data for this project is provided by Motivate International Inc. under the [Data License Agreement for Divvy Bikes Data](http://divvybikes.com/data-license-agreement). All personal information has been removed to protect user’s privacy. The data is shared only for analysis purposes as allows by the license.



### **3. Process Phase:**

Given the large-scale nature of the dataset, **R** was selected as the preferred tool because it offers powerful data analysis packages like ggplot2, dplyr and tidyr, etc, which are highly efficient for reshaping, transforming and visualizing the data. 

This phase involves- 

* Combining all the downloaded files into one.
* Cleaning and organizing the data to simplify the analysis.
* Removing the inconsistancies, filling in missing values and,
* Ensuring that the data is ready before starting the analysis. 

First, I installed and loaded all the required R packages and then imported the CSV files.


```{r}
install.packages("tidyverse")
library(tidyverse)
```
*Uploaded and assigned names to Divvy datasets (csv files) here* 
```{r}
q1_2019 <- read_csv("Divvy_trips_2019_Q1.csv")
q1_2020 <- read_csv("Divvy_trips_2020_Q1.csv")
```
*After importing the CSV files, I reviewed the files and compared the column names*
```{r}
head(q1_2019)
head(q1_2020)

colnames(q1_2019)
colnames(q1_2020)
```

*Changed the column names to match perfectly before joining both the files into one.*
```{r}
(q1_2019 <- rename(q1_2019
                   ,ride_id = trip_id
                   ,rideable_type = bikeid
                   ,started_at = start_time
                   ,ended_at = end_time
                   ,start_station_name = from_station_name
                   ,start_station_id = from_station_id
                   ,end_station_name = to_station_name
                   ,end_station_id = to_station_id))

(q1_2020 <- rename(q1_2020
                   ,usertype = member_casual))
```
*Next, I inspected the dataframe to look for incongruencies, using the str() function*
```{r}
str(q1_2019)
str(q1_2020)
```

*Changed the data type of the columns so that they match and converted ride_id and rideable_type to character so that they can join correctly.*

```{r}
q1_2019 <-  mutate(q1_2019, ride_id = as.character(ride_id)
                   ,rideable_type = as.character(rideable_type))
```

Now, after data types and column names are changed and matched perfectly, I combined both the dataframes into one big dataframe and removed the fields that were not required.


*Stacked individual quarter's data frames into one big data frame*
*Removed lat, long, birth year, and gender fields as this data was dropped in the beginning of 2020*
```[r]
total_trips <- bind_rows(q1_2019, q1_2020)

total_trips <- total_trips %>%  
  select(-c(start_lat, start_lng, end_lat, end_lng, birthyear, gender,  "tripduration"))
```
Then I created a new table

*Inspected  the new table*
```{r}
colnames(total_trips)  # List of column names
nrow(total_trips)  # Number of rows are in data frame
dim(total_trips)  # Dimensions of the data frame
head(total_trips)  # The first 6 rows of data frame.
str(total_trips)  # List of columns and data types
```

There were a few problems I needed to fix:

(1) In the "usertype" column, there were two names for members ("member" and "Subscriber") and two names for casual riders ("Customer" and "casual").

(2) The data was only grouped by each ride rightnow, which was too detailed. I added new columns like day, month, year and time to make it easier to organize and analyze the data over time.

(3) I added a new column for length of ride, "ride_length" to the entire dataframe for consistency.

(4) There were some rides where trip duration showed up as negative, including several hundred rides where Divvy took bikes out of circulation for Quality Control reasons.

*Began by seeing how many observations fall under each usertype and then reassigned to the desired values (I chose the current 2020 labels)*

```{r}
table(total_trips$usertype)
total_trips <-  total_trips %>% 
  mutate(usertype = recode(usertype
                                ,"Subscriber" = "member"
                                ,"Customer" = "casual"))
```

*Added columns that list the date, month, day, year and time of each ride*
```{r}
total_trips$date <- as.Date(total_trips$started_at) 
total_trips$month <- format(as.Date(total_trips$date), "%m")
total_trips$day <- format(as.Date(total_trips$date), "%d")
total_trips$year <- format(as.Date(total_trips$date), "%Y")
total_trips$day_of_week <- format(as.Date(total_trips$date), "%A")
total_trips$time <- format(as.POSIXct(total_trips$started_at), format = "%H")
```

*Added a "ride_length" calculation to total_trips (in minutes)*
```{r}
total_trips$started_at <- ymd_hms(total_trips$started_at)
total_trips$ended_at <- ymd_hms(total_trips$ended_at)
total_trips$ride_length <- difftime(total_trips$ended_at,total_trips$started_at, units = "mins")

# Inspected the structure of the columns

str(total_trips)
```

*Converted "ride_length" from Factor to numeric to run calculations on the data*
```{r}
is.factor(total_trips$ride_length)
total_trips$ride_length <- as.numeric(as.character(total_trips$ride_length))
is.numeric(total_trips$ride_length)
```

*Removed the entries when bikes were taken out of docks and checked for quality by Divvy or ride_length was negative*
*Created a new version of the dataframe (total_trips_new) since data was removed*
*Also removed the rows that contain missing values*
```{r}
total_trips_new <- total_trips[!(total_trips$start_station_name == "HQ QR" | total_trips$ride_length<=0),]
total_trips_new <- drop_na(total_trips_new)
```

### **4. Analyze**

In the analysis phase I analyzed the cleaned and transformed data, to gain a better understanding of its characteristics and patterns. I used *summary()* and *aggregate()* function for descriptive analysis.

*Descriptive analysis on ride_length*
```{r}
summary(total_trips_new$ride_length
```

*To compare members and casual users*
```{r}
aggregate(total_trips_new$ride_length ~ total_trips_new$usertype, FUN = mean)
aggregate(total_trips_new$ride_length ~ total_trips_new$usertype, FUN = median)
aggregate(total_trips_new$ride_length ~ total_trips_new$usertype, FUN = max)
aggregate(total_trips_new$ride_length ~ total_trips_new$usertype, FUN = min)


# To see the average ride time each day for members vs casual users
aggregate(total_trips_new$ride_length ~ total_trips_new$usertype + total_trips_new$day_of_week, FUN = mean)

        
# Noticed that the days of the week were out of order. Fixed that.
total_trips_new$day_of_week <- ordered(total_trips_new$day_of_week, levels=c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"))


# analyze ridership data by type and day_of_week
total_trips_new %>% 
   group_by(usertype, day_of_week) %>%  #groups by usertype and day_of_week
  summarise(number_of_rides = n()							#calculates the number of rides and average duration 
            ,average_duration = mean(ride_length)) %>% 		# calculates the average duration
  arrange(usertype, day_of_week)
```

**Data Visualization**

I used *ggplot2* to create charts, graphs and other visualization, that helped me to derive insights, and identify patterns.

##Total Rides
*Visualization to show Percentage of rides by Usertype*
```{r}
total_trips_new %>%
    count(usertype) %>%
    mutate(percentage = round(n/sum(n)*100)) %>%
    ggplot(aes(x = "", y = n, fill = usertype)) + 
    geom_bar(stat = "identity", width = 1) +
    coord_polar(theta = "y") +
    geom_text(aes(label = paste0(percentage, "%")), position = position_stack(vjust = 0.5)) +
    theme_void() +
    labs(title = "Percentage of Rides by User Types")
```




*Let's visualize the number of rides by rider type*

```{r}
total_trips_new %>% 
  mutate(day_of_week = wday(started_at, label = TRUE)) %>% 
  group_by(usertype, day_of_week) %>% 
  summarise(number_of_rides = n()
            ,average_duration = mean(ride_length)) %>% 
  arrange(usertype, day_of_week)  %>% 
  ggplot(aes(x = day_of_week, y = number_of_rides, fill = usertype)) +
  geom_col(position = "dodge") +
  geom_text(aes(label = number_of_rides), 
            position = position_dodge(width = 0.9), 
            vjust = -0.3) +
  scale_y_continuous(labels = label_comma(scale = 1/1000, suffix = "k")) +
  labs(title = "Total Number of Rides by User type")
```
