# CYCLISTIC BIKE-SHARE ANALYSIS CASE STUDY

<br><br>
## INTRODUCTION
This capstone project is the final part of completing the **Google Data Analytics Professional Certificate course**. In this case study I have analyzed a public dataset for a fictitious company, Cyclistic. For this analysis, I have used R programming language because of its statistical computing capabilities, rich ecosystem of packages, and strong visualization tools. To cater the relevant question, I have followed the six phases approach of the data analysis: **Ask, Prepare, Process, Analyze, Share, and Act**.<br><br>

## SCENARIO
Cyclistic is a bike-share company in Chicago. In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The company offers three types of flexible pricing plans: single-ride passes, full-day passes, and annual memberships. Single-ride passes and full-day passes riders are referred as Casual riders.

The finance analysts at Cyclistic concluded that **annual members are much more profitable than the casual riders**. Although the pricing flexibility helps Cyclistic attract more customers, Lily Moreno, the director of marketing, is convinced that maximizing the number of annual members will be the key to future growth. Moreno believes there’s a solid opportunity in **converting casual riders into full-fledged members**, instead of focusing on all-new customers, as casual riders are already familiar with the Cyclistic program and have consciously chosen Cyclistic for their transportation needs.<br><br>

## **DATA ANALYSIS PROCESS**
<br>

## **1. ASK PHASE:**

•	**Business Objective:** The business objective is to increase the number of annual Cyclistic members in order to enhance profitability and ensure business growth. By converting more casual riders into annual members, Cyclistic aims at creating a more stable revenue stream.

•	**Business Task:** To understand: 
1. How do annual members and casual riders use Cyclistic bikes differently? 
2. Why would casual riders buy Cyclistic annual memberships? 
3. How can Cyclistic use digital media to influence casual riders to become members? <br><br>


## **2. PREPARE PHASE:**

This phase of data analysis involves data collection and preparation. Identifying the data sources, gathering relevant data and verifying if it is accurate and useful for answering the questions.

**Data Description:** For this case study, I have used a public dataset, made available by Motivate International Inc. I focused on the data from first quarter of 2019 and 2020, which was organised in two separate CSV files. 2019 Q1 CSV file contains 12 columns and 3,65,070 rows, while 2020 Q1 CSV file contains 13 columns and 4,26,888 rows. 

* **Data Credibility:** The data used in this study meets the ROCCC standards of data credibility.
1.*Reliable:* The data is trustworthy, accurate, complete, and unbiased, having undergone verification to ensure its suitability for the intended purpose.
2.*Original:* The data is sourced directly from the primary, authentic provider.
3.*Comprehensive:* The data encompasses all essential information necessary to address the question or resolve the problem at hand.
4.*Current:* Given its monthly release schedule, the data remains up-to-date and pertinent.
5.*Cited:* The data is appropriately referenced and attributed in the project.

* **Data Licensing:** The data for this project is provided by Motivate International Inc. under the [Data License Agreement for Divvy Bikes Data](http://divvybikes.com/data-license-agreement). All personal information has been removed to protect user’s privacy. The data is shared only for analysis purposes as allowed by the license.<br><br>



## **3. PROCESS PHASE:**

Given the large-scale nature of the dataset, **R** was selected as the preferred tool because it offers powerful data analysis packages like ggplot2, dplyr and tidyr, etc, which are highly efficient for reshaping, transforming and visualizing the data. 

This phase involves- 

* Combining all the downloaded files into one.
* Cleaning and organizing the data to simplify the analysis.
* Removing the inconsistancies, filling in missing values and,
* Ensuring that the data is ready before starting the analysis. <br><br>



### **Exploring the Data**
During the data exploration phase, I identified several inconsistencies within the dataset. The following steps were taken to examine and understand the data:

- Used the head() function to preview the first six rows of the data frame.

- Checked the structure of the datasets:


     ~ 2019 Dataset: 365,069 rows and 12 columns


     ~ 2020 Dataset: 426,887 rows and 13 columns


     ~ Total Data Points: Approximately 9,930,359, indicating a large dataset not suitable for spreadsheet tools.


- Utilized functions such as str(), colnames(), nrow(), and dim() to gain deeper insights into the structure, column names, and dimensions of the dataset.<br><br>

### **Cleaning the Data**
To ensure high data quality and prepare it for analysis, the following cleaning steps were performed:

- Missing and Irrelevant Data: Removed 6,406 rows that contained missing values, negative ride lengths, or were related to bike quality check rides.

- Outlier Removal: Excluded trips with a duration of less than one minute, as they were considered invalid or outliers.

- **Data Transformation:**
  

     ~ Performed typecasting and variable renaming where needed.
  
     ~ Used the rename() function to update column names for better clarity.
  
     ~ Applied the mutate() function to convert data types and create new variables.
  

- Added 6 new columns to enhance the dataset:  ride_length, date, month, year, day_of_week, and hour

- Data Reduction: Dropped 7 unnecessary columns to streamline the dataset and focus on relevant information.<br><br>


## **4. ANALYSIS PHASE:**

Out of a total of **785,550** rides, **91%** (717,799 rides) were taken by Annual Members, while only **9%** (67,751 rides) were taken by Casual Riders.
         
          
 - Casual Riders took the most rides on **Sunday (18,612 rides)**, accounting for **27.47%** of all rides by Casual Riders.
          
 
 
 - Annual Members had the highest number of rides on **Tuesday (127,578 rides)**, which is **17.77%** of their total. <br><br>

**Ride Duration:**


 - *Average ride duration:*


     Casual Riders: **89.70 minutes**


     Annual Members: **13.29 minutes**<br><br>



  
 - *Maximum ride duration:*

     Casual Riders: **177,200 minutes**



     Annual Members: **101,607 minutes**<br><br>

 

 
 - *Highest average ride duration:*


      Casual Riders: **141 minutes** on Thursday

   
      Annual Members: **16 minutes** on Saturday and Sunday<br><br>




**Ride Timing Patterns:**



- Annual Members most frequently rode at **8 AM** and **5 PM**, with the least rides occurring at **3 AM**.


     
- Casual Riders most frequently rode at **3 PM**. There was little variation in ride volume from **1 PM** to **5 PM**, suggesting this is their peak usage period. The fewest rides occurred at **12 AM (midnight)**.<br><br>









**Popular Station:**


The station with the highest number of ride starts and ends was **"Canal St & Adams St"**, with 14,155 rides started and 15,067 rides ended there.<br><br>




### Summary of Data:
- Most rides: **Annual Members**
- Longest ride duration: **Casual Riders**
- Highest average ride duration: **Casual Riders**
- Top station for ride starts and ends (Casual Riders): **Streeter Dr & Grand Eve station**
- Busiest days of the week for casual riders: **Saturday and Sunday**
- Busiest time of the day: **Afternoon between 1pm to 5pm**<br><br>



## **5. SHARE PHASE:**


I analyzed the data and found useful insights. To help meet the needs of the stakeholders, I created clear and effective visualizations that show how the data supports their goals. I also built a dashboard that brings all the information together in one place, making it easier for users to understand and make smart decisions.



[Tableau Dashboard](https://public.tableau.com/views/CapstoneProjectDashboard_17454151012450/Dashboard2?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)


![Image](https://github.com/user-attachments/assets/2aca44fa-1f97-4926-afcb-44314c02c86f)

## **6. ACT PHASE:**

### Key Findings and Recommendations
**What we learned from the data:**

- Casual riders take longer and more frequent rides than Annual Members.

- Most casual riders ride on weekends and between 1 PM to 5 PM.

- Many of them may not realize that becoming a member could save them money and offer more benefits.

This is a great opportunity to encourage casual riders to become members and improve their experience.<br><br>

### What We Recommend
**1. Help Casual Riders Understand the Benefits of Membership**

Many casual riders might not know how much they could save or how easy it is to become a member. To help:

- Share simple messages online and at stations showing how membership works and how it helps save money.

- Use social media, the app, and emails to share quick videos, tips, or rider stories.<br><br>

**2. Promote Membership at Busy Stations**

Popular stations like Streeter Dr & Grand Ave and Canal St & Adams St are perfect spots to reach riders:

- Set up small booths or have staff hand out flyers during the busy hours (1 PM – 5 PM).

- Offer on-the-spot discounts or QR codes they can scan to join easily.<br><br>

**3. Offer Special Deals and Collect Feedback**

Encourage more riders to become members and keep current members engaged:

- Give new members their first month free or ride discounts.

- Offer rewards for riding more during quiet days.

- Ask riders for feedback through quick surveys to learn what they like or want improved.
